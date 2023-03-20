#os  #software 

> Parent process create children processes, which, in turn create other processes, forming a tree of processes.

![[Screenshot 2023-02-26 at 19.23.53.png|500]]

###### What property is used to identify and manage a process?
Process Identifier (pid)

###### What are the resource sharing options of parent and child process?
1. Share all resources
2. Child share subset of parent's resources
3. Share no resources

###### What are the execution options of parent and child process?
1. Execute concurrently 
2. Parent waits until child terminates

###### How is the address space of a child process is created?
1. Child shares the exact address space of the parent
2. Seperate address space is created for the child

