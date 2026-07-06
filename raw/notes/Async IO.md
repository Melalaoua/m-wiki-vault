tags:: #thelaboratory/coding 
source:: [Async IO in Python: A Complete Walkthrough](https://realpython.com/async-io-python/)


### Une vue d'ensemble.

**Paralellisme** : faire plusieurs opérations en même temps. Le parallelisme est une forme de **concurrence**.

**Multiprocessing** : même principe que parallelisme mais ce s'effectue au niveau du CPU qui va se diviser en plusieurs coeurs. Le multiprocessing est une forme de parallélisme.  

**Concurrence** : Plus large que le parallelisme. Implique le fait que des tâches peuvent se chevaucher. 

**Threading** : Plusieurs noeuds vont se relayer pour executer une tâche. Un processus peut contenir plusieurs noeuds. 

Le threading est meilleur pour des tâches IO (input/output).

Une tâche liée au CPU est caractérisée par les coeurs du CPU qui vont continuellement travailler jusqu'à finir la tâche. Une tâche IO est caractérisée par beaucoup de mise en attente pour que la tâche import/export soit complétée.![[Pasted image 20230211185226.png]]

>[!INFO]
**Concurrency** englobe le **multiprocessing** et le **threading**. 


### Un nouvel arrivant.
L'asynchronous IO n'est pas nouveau. Ce n'est pas du threading, ni du multiprocessing. L'async I/O utilise le **cooperative multitasking**. L'asyncio est une forme de concurrent programming. Mais ce n'est pas du parallélisme. 


Que veux dire **asynchronous** ? Deux propriétés : 
- Les routines asynchrones sont capables de s'arrêter pour attendre un résultat tout en laissant les autres routines s'effectuer.
- Le code asynchrone facilite l'éxécution d'un code en concurrence. 



Un exemple pour comprendre l'asyncio, paraphrase de Miguel Grinberg en 2017 :
> Chess master Judit Polgár hosts a chess exhibition in which she plays multiple amateur players. She has two ways of conducting the exhibition: synchronously and asynchronously.
> 
> Assumptions:
> -   24 opponents
> -   Judit makes each chess move in 5 seconds
> -   Opponents each take 55 seconds to make a move
> -   Games average 30 pair-moves (60 moves total)
> 
> **Synchronous version**: Judit plays one game at a time, never two at the same time, until the game is complete. Each game takes _(55 + 5) * 30 == 1800_ seconds, or 30 minutes. The entire exhibition takes _24 * 30 == 720_ minutes, or **12 hours**.
> 
> **Asynchronous version**: Judit moves from table to table, making one move at each table. She leaves the table and lets the opponent make their next move during the wait time. One move on all 24 games takes Judit _24 * 5 == 120_ seconds, or 2 minutes. The entire exhibition is now cut down to _120 * 30 == 3600_ seconds, or just **1 hour**. [(Source)](https://youtu.be/iG6fr81xHKA?t=4m29s)


### Async and await chez asyncio
Une coroutine est une fonction qui suspend son execution afin de return. Cette même coroutine peut passer le flambeau à une autre coroutine pendant un certain moment.

