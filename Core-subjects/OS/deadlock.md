## A process in operating system uses resources in the following way. 

1. Requests a resource 
2. Use the resource 
3. Releases the resource 

## what is deadlock

Deadlock is a situation where a set of processes are blocked because each process is holding a resource and waiting for another resource acquired by some other process. 

Consider an example when two trains are coming toward each other on the same track and there is only one track, none of the trains can move once they are in front of each other. A similar situation occurs in operating systems when there are two or more processes that hold some resources and wait for resources held by other(s). For example, in the below diagram, Process 1 is holding Resource 1 and waiting for resource 2 which is acquired by process 2, and process 2 is waiting for resource 1. 
 
![image](https://media.geeksforgeeks.org/wp-content/cdn-uploads/gq/2015/06/deadlock.png)

## When Deadlock can arise

Deadlock can arise if the following four conditions hold simultaneously 
1. **Mutual Exclusion:** Two or more resources are non-shareable (Only one process can use at a time) 

2. **Hold and Wait:** A process is holding at least one resource and waiting for resources. 

3. **No Preemption:** A resource cannot be taken from a process unless the process releases the resource. 

4. **Circular Wait:** A set of processes are waiting for each other in circular form. 



## Methods for handling deadlock 

There are three ways to handle deadlock 
1. Deadlock prevention or avoidance: The idea is to not let the system into a deadlock state. 
One can zoom into each category individually, Prevention is done by negating one of above mentioned necessary conditions for deadlock. 
Avoidance is kind of futuristic in nature. By using strategy of “Avoidance”, we have to make an assumption. We need to ensure that all information about resources which process will need are known to us prior to execution of the process. We use Banker’s algorithm (Which is in-turn a gift from Dijkstra) in order to avoid deadlock. 

2. Deadlock detection and recovery: Let deadlock occur, then do preemption to handle it once occurred. 

3. Ignore the problem altogether: If deadlock is very rare, then let it happen and reboot the system. This is the approach that both Windows and UNIX take. 