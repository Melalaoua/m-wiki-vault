tags:: #thelaboratory/howto  

## Slice Dat Time

Disons que tu veux construire un OS et tu veux que les utilisateurs soient capables de tourner plusieurs programmes à la fois. Tu n'as pas un CPU avec plusieurs cœurs toutefois, donc ton CPU peut seulement tourner une instruction à la fois.

Par chance, tu es un développeur très malin. Tu sais que tu peux faire du "fake" parallélisme en laissant les processus prendre plusieurs tours sur le CPU chacun. Si tu cycle parmi les processus et tu réalises plusieurs instructions pour chaque, ils peuvent chacun être responsive sans que chacun bloque le CPU.


### Interruptions hardware.
--
Plus tôt, on a parlé de comment les interruptions systèmes sont utilisées pour donner le contrôle du programme dans l'userland, à l'OS en kernel mode. Ce sont des interruptions systèmes car elle sont volontairement induites par les programmes. Le machine code exécuté par le processeur et qui se fait dans un cycle classique fetch-execute dis au processeur de switch le contrôle en mode kernel. 

![[Pasted image 20230813100320.png]]

Les OS schedulers utilise des timer chips comme les PITs pour déclencher l'interruption hardware afin de réaliser du multitasking.

1. Avant de sauter dans le code programme, l'OS met en place la timer chip pour déclencher une interruption après un certains temps.
2. L'OS switch en user mode et saute à la prochaine instruction du programme.
3. Quand le timer se termine, il déclenche une interruption hardware afin de passer en kernel mode et sauter dans le code de l'OS.
4. L'OS peut maintenant sauvegarder où le programme s'est arrêté avant, charger un autre programme, et répéter le processus.

C'est ce qu'on appelle du *preemptive multitasking* : l'interruption du processus est appelé préemption. Disons que tu lis cet article sur ton navigateur et tu écoutes de la musique avec la même machine, ton ordinateur est probablement en train de suivre ce mécanisme, des milliers de fois à la seconde.


### Timeslice Calculation.
--
Un timeslice est le temps alloué par l'OS scheduler aux processus avant de le préempter. La manière la plus simple pour choisir une timeslice est de donner à tout les processus le même timeslice, par exemple une fenêtre de 10ms, et le cycle s'effectue ainsi, dans l'ordre. On appelle ça le *fixed timeslice round-robin scheduling.*

> Aside : fun jargon facts!
> Did you know that timeslices are often called “quantums?” Now you do, and you can impress all your tech friends. I think I deserve heaps of praise for not saying quantum in every other sentence in this article.

> Speaking of timeslice jargon, Linux kernel devs use the [jiffy](https://github.com/torvalds/linux/blob/22b8cc3e78f5448b4c5df00303817a9137cd663f/include/linux/jiffies.h) time unit to count fixed frequency timer ticks. Among other things, jiffies are used for measuring the lengths of timeslices. Linux’s jiffy frequency is typically 1000 Hz but can be configured when compiling the kernel.

Une manière un peu plus performantes que de choisir arbitrairement les fixed timeslice est de déterminer une *target latency* -- la longueur idéale pour qu'un processus réponde. La latence est le temps qu'il faut à un processus pour reprendre son execution après avoir été préempté. 

Les timeslices sont calculées en divisant la target latency par le nombre totale de tâche; c'est mieux que de choisir arbitraiement les timeslice car cette méthode élimine les changements de processus inutiles quand il y a peu de processus. Avec une target latency de 15ms et 10 processus, chaque processus reçoit 15/10 ou 1.5 ms pour tourner. Avec seulement 3 processus, chaque processus reçoit 5ms timeslice tout en atteignant la target latency.

Le changement de processus est computationally expensive car il demande de sauvegarder le processus entier et de restaurer un différent. Passé un certain point, une timeslice trop petite peut poser des problèmes de performances car les processus s'enchainent trop rapidement. Il est commun de définir une hard limit aux timeslices pour pas qu'elles soient trop petites (*minimum granularity*). Cela veut dire que la target latency est dépassée et il y a assez de processus pour mettre en place la minimum granularity.

Au moment où l'article a été écrit, Linux a une target latency de 6ms et un granularité minimale de 0.75ms.
![[Pasted image 20230813101551.png]]

Round-robin scheduling with this basic timeslice calculation is close to what most computers do nowadays. It’s still a bit naive; most operating systems tend to have more complex schedulers which take process priorities and deadlines into account. Since 2007, Linux has used a scheduler called [Completely Fair Scheduler](https://docs.kernel.org/scheduler/sched-design-CFS.html). CFS does a bunch of very fancy computer science things to prioritize tasks and divvy up CPU time.

Every time the OS preempts a process it needs to load the new program’s saved execution context, including its memory environment. This is accomplished by telling the CPU to use a different _page table_, the mapping from “virtual” to physical addresses. This is also the system that prevents programs from accessing each other’s memory; we’ll go down this rabbit hole in chapters [5](https://cpu.land/the-translator-in-your-computer) and [6](https://cpu.land/lets-talk-about-forks-and-cows) of this article.

### Note 1 : Kernel Preemptability
--
So far, we’ve been only talking about the preemption and scheduling of userland processes. Kernel code might make programs feel laggy if it took too long handling a syscall or executing driver code.

Modern kernels, including Linux, are [preemptive kernels](https://en.wikipedia.org/wiki/Kernel_preemption). This means they’re programmed in a way that allows kernel code itself to be interrupted and scheduled just like userland processes.

This isn’t very important to know about unless you’re writing a kernel or something, but basically every article I’ve read has mentioned it so I thought I would too! Extra knowledge is rarely a bad thing.

### Note 2 : A History Lesson
--
Ancient operating systems, including classic Mac OS and versions of Windows long before NT, used a predecessor to preemptive multitasking. Rather than the OS deciding when to preempt programs, the programs themselves would choose to yield to the OS. They would trigger a software interrupt to say, “hey, you can let another program run now.” These explicit yields were the only way for the OS to regain control and switch to the next scheduled process.

This is called [_cooperative multitasking_](https://en.wikipedia.org/wiki/Cooperative_multitasking). It has a couple major flaws: malicious or just poorly designed programs can easily freeze the entire operating system, and it’s nigh impossible to ensure temporal consistency for realtime/time-sensitive tasks. For these reasons, the tech world switched to preemptive multitasking a long time ago and never looked back.


Suite [[The CPU in you - Chapter 3]]