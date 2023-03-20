#os #software 

> Selecting the next process to be executed among all the available [[Process]]es. 

###### What is the program responsible for process scheduling?
Process scheduler

###### What is the purpose?
Maximize the CPU usage, quickly switch processes into CPU

###### What are the two queues maintained by the process scheduler?
- Ready queue
	set of all processes residing in main memory, ready to execute
- Wait queue
	set of processes waiting for an event (i.e., I/O)
![[Screenshot 2023-02-26 at 16.27.09.png|400]]

###### What are the events that put a process into wait queue?
- I/O request
- Create child process
- Wait for an [[Interrupt]]

###### What are the events that put a process into ready queue?
- Expiring time slice
- Completing I/O operation
- Terminating child process
- Interrupt finishing occour

![[Screenshot 2023-02-26 at 16.34.11.png|500]]