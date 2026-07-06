tags:: #thelaboratory/howto 
source:: [The "you" in CPU](https://cpu.land/the-basics)

Les ordinateurs sont relativement simplistes. Au fur et à mesure que tu vas t'enfoncer dans ce rabbit hole, garde en tête que les ordinateurs sont simples, pas plus, pas moins.

### Architecture des ordinateurs.
--
Le Central Processing Unit (CPU) est un ordinateur en charge de réaliser tout les calculs. Au moment même où l'ordinateur s'allume, le CPU commence à calculer.

Le premier CPU a été inventé en 1960 par le physicien italien Federico Faggin, avec une architecture 4 bits (les ordinateurs actuels sont en 64 bits).

Les instructions réalisés par les CPU sont exécutés en code binaire : un byte ou deux de  ==1 ou 0== pour représenter l'instruction suivi de la données nécessaire pour exécuter la tâche. Le "machine code" n'est rien de plus que ces instructions empilées les unes après les autres. L'[Assembly ou asm](https://en.wikipedia.org/wiki/Assembly_language) est une syntaxe utile pour lire et écrire du code machine plus facile à lire, écrire  pour les humains que du code binaire.

![[Pasted image 20230809175923.png]]

La RAM de l'ordinateur est la banque de mémoire principale, un espace multi-purpose qui stocke toutes les données utilisées par les programmes actifs sur l'ordinateur. La RAM prend en compte le program en lui-même, mais aussi le code au coeur de l'ordinateur. Le CPU lit toujours le machine code directement depuis la RAM, et le code ne peut pas être lu si il n'est pas mis en mémoire dans la RAM.

Le CPU stocke un *instruction pointer* qui pointe toujours vers la position dans la RAM où se trouve la prochaine instruction. Après chaque instruction, le CPU bouge le pointeur et recommence. C'est un cycle *fetch-execute*.

![[Pasted image 20230809180349.png]]

Après avoir effectué sa tâche, le pointeur bouge en avant immédiatement vers la tâche suivante dans la RAM, pointant vers la prochaine tâche. *The instruction code keeps chugging forward, executing machine code in the order in which it has been stored in memory.* Certaines instructions peuvent indiquer de pointer vers un autre endroit dans la ram, ou sauter vers différents endroits en fonction de certaines conditions, rendant le code réutilisable et les boucles conditionnelles possibles.

Le pointeur est stocké dans le ==register==. Les Registers sont de petites unités de stockages qui sont lues & écrites extrêmement rapidement par les CPU. Chaque architecture CPU a un nombre fixe de registers, utilisé pour tout et n'importe quoi (stockage de varaibles temporaires pour calcul, configuration du processeur, ...).

Certains registers sont accessibles directement depuis le machine code, comme *ebx* dans l'exemple plus tôt. D'autres registers peuvent seulemement être utilisé en interne par le CPU, mais peuvent parfois être mis à jour ou lus en utilisant des instructions spécifiques.

### Les processeurs sont naïfs.
--
Quand un exécutable est lancé sur l'ordinateur, beaucoup de choses ont lieu - on y revient plus tard - à la fin de ce processus, le code est stocké quelque part. L'OS charge le fichier quelque part dans la RAM et ordonne au CPU de déplacer le pointeur jusqu'à cette position dans la ram. Le CPU continue ensuite son fetch-execute programme as usual.

Les CPU ont une vue très basique du monde, ils voient seulement l'instruction pointer and a bit of internal state. Des questions se posent :
1. Si le CPU ne sait pas ce qu'est le multiprocessing et execute juste des instructions à la chaîne, pourquoi il ne se bloque pas dans le programme qu'il est en train d'executer ? Comment est-il capable d'executer plusieurs programmes à la fois ?
2. Si le programme tourne directement sur le CPU, et le CPU a un accès direct à la RAM, pourquoi le code ne peut-il pas coder un accès à la mémoire d'autres processus, voire même avoir un accès direct au kernel ?
3. Quel est le mécanisme qui empêche d'executer n'importe quelle instruction, n'importe quoi, sur l'ordinateur ? C'est quoi un SYSCALL ?

	La question sur la mémoire mérite sa propre section et sera traitée dans le [[The CPU in you - Chapter 5|chapitre 5]]
	TL;DR : is that most memory accesses actually go through a layer of misdirection that remaps the entire address space. For now, we’re going to pretend that programs can access all RAM directly and computers can only run one process at once. We’ll explain away both of these assumptions in time.

Il est temps de se plonger dans le rabbit hole des syscalls et security rings.

> C'est quoi un Kernel ?
> 	Déjà : L'operating system de l'ordinateur, comme macOS, Windows, Linux, une collection de logiciel qui tourne sur l'ordinateur et permet de faire les tâches les plus basiques sur une ordinateur. 
> 	
> 	Le kernel, cependant, c'est le coeur de l'operating system. Quand tu allumes ton ordinateur, l'instruction pointer commence un programme particulier : le kernel. Le Kernel a une accès **total** a la mémoire de l'ordinateur, les périphériques, autres ressources. Il est en charge de lancer le logiciel installé sur l'ordinateur (userland programs).
> 	
> 	Linux est juste un kernel avec beaucoup de logiciel userland comme shells. Le kernel chez macOS est XNU et Unix-like. Le kernel de windows est NT Kernel.


### Two rings to Rule Them All.
--
The *mode* (sometimes called privilege level or ring) est un processus qui contrôles qui est autorisé de faire quoi. Les architectures modernes ont au moins deux options : kernel/supervisor mode et user mode.

Bien qu'une architecture puisse supporter plus de deux modes, seul le kernel et l'user mode sont communément utilisé aujourd'hui.

En mode kernel, le CPU est autorisé à exécuter n'importe quelle instructions et accéder à n'importe quelle mémoire. En user mode, seul un substrat d'instructions et autorisé, I/O et accès mémoire sont bridés, beaucoup de paramètres CPU sont bloqués. Générallement, le kernel et drivers tourne sous le mode kernel tandis que les applications tourne en user mode.

Les processeurs sont en kernel mode. Avant d'exécuter un programme, le kernel initie le passage en mode user.

![[Pasted image 20230810103316.png]]

An example of how processor modes manifest in a real architecture: on x86-64, the current privilege level (CPL) can be read from a register called `cs` (code segment). Specifically, the CPL is contained in the two [least significant bits](https://en.wikipedia.org/wiki/Bit_numbering) of the `cs` register. Those two bits can store x86-64’s four possible rings: ring 0 is kernel mode and ring 3 is user mode. Rings 1 and 2 are designed for running drivers but are only used by a handful of older niche operating systems. If the CPL bits are `11`, for example, the CPU is running in ring 3: user mode.

### C'est quoi un syscall ?
--
Les programmes tournent en user mode car on ne doit pas leur faire confiance pour un accès total à l'ordinateur. Toutefois, les programmes ont besoin d'avoir un accès au I/O, allocation de mémoire, interaction avec l'OS. Ainsi, les programmes en user mode doivent pouvoir demander au kernel de l'aide. L'OS peut implémenter ses propres mesures de sécurité afin d'empêcher les programmes de faire des choses malicieuses.

Des fonctions comme open, read, fork, exit sont des syscalls, demandenat de l'aide à l'OS. Un syscall est une procédure spéciale qui permet à un programme de commencer une transition de l'espace utilisateur à l'espace kernel.

Le transfert de l'espace user à l'espace kernel est effectué par une fonction processeur ; *software interrupts* :
1. Lors du démarrage, l'OS stocke un tableau appelé *interrupt vector table* et l'enregistre dans la RAM grace au CPU. L'IVT maps interrupt numbers to handler code pointers.
2. Ensuite, les programmes userland peuvent utiliser les instruction INT pour dire au processeur de regarder les interrupt numbers dans l'IVT, passer en mode kernel, et récupérer le pointeur.

### Wrapper APIs : Abstracting Away Interrupts.
--
Here’s what we know so far about system calls:

- User mode programs can’t access I/O or memory directly. They have to ask the OS for help interacting with the outside world.
- Programs can delegate control to the OS with special machine code instructions like INT and IRET.
- Programs can’t directly switch privilege levels; software interrupts are safe because the processor has been preconfigured _by the OS_ with where in the OS code to jump to. The interrupt vector table can only be configured from kernel mode.

Programs need to pass data to the operating system when triggering a syscall; the OS needs to know which specific system call to execute alongside any data the syscall itself needs, for example, what filename to open. The mechanism for passing this data varies by operating system and architecture, but it’s usually done by placing data in certain registers or on the stack before triggering the interrupt.

The variance in how system calls are called across devices means it would be wildly impractical for programmers to implement system calls themselves for every program. This would also mean operating systems couldn’t change their interrupt handling for fear of breaking every program that was written to use the old system. Finally, we typically don’t write programs in raw assembly anymore — programmers can’t be expected to drop down to assembly any time they want to read a file or allocate memory.

![[Pasted image 20230811101457.png]]

So, operating systems provide an abstraction layer on top of these interrupts. Reusable higher-level library functions that wrap the necessary assembly instructions are provided by [libc](https://www.gnu.org/software/libc/) on Unix-like systems and part of a library called [ntdll.dll](https://learn.microsoft.com/en-us/windows-hardware/drivers/kernel/libraries-and-headers) on Windows. Calls to these library functions themselves don’t cause switches to kernel mode, they’re just standard function calls. Inside the libraries, assembly code does actually transfer control to the kernel, and is a lot more platform-dependent than the wrapping library subroutine.

When you call `exit(1)` from C running on a Unix-like system, that function is internally running machine code to trigger an interrupt, after placing the system call’s opcode and arguments in the right registers/stack/whatever. Computers are so cool!


Suite [[The CPU in you - Chapter 2]]