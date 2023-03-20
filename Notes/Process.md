 #software #os 

> [!quote]
> A program in execution

> [!faq]- What is the difference between program and process?
> Program is a passive entity (executable file) stored in the hard drive. Process is active. Program becomes process, when it is executing.

###### What is the memory layout of a process?
https://www.youtube.com/watch?v=m1UzSfgjA4Y
![[Screenshot 2023-02-25 at 22.01.38.png|500]]

![[Pasted image 20230225215954.png|500]]

OS allocates an unique process address space for each process. All the data belongs to process is stored in their. It consists of 5 segments, which are
1. Text & Code
	- Contains instructions for execution
	- Read only, cannot change during the excution
	- Placed in the lower memory addresses, so it is not getting overwritten by other memory segments
2. Data
	- All the global and static variables are stored here
	- It consists of two segments
		1. Uninitialized data 
		2. Initialized data
3. Heap
	- Dynamic memory allocation happening here
	- Memory must be managed by the program
	- If not managed properly, it will lead to memory leak problems
4. Stack
	- When a function is executing, an unique stack segment is pushed into the stack.
	- All the local variables belongs to a function is stored inside that specific segment
	- After the function had executed, it's stack segment is poped out from the segment
	- Stack and heap grow in opposite direction
1. Environment
	- Environment variables and command line arguments are stored here.

>[!faq]- What is stack overflow?
>

>[!faq]- What is stack pointer?

###### What are the states of a process?
https://www.youtube.com/watch?v=jZ_6PXoaoxo&t=201s
![[Screenshot 2023-02-25 at 22.33.10.png|500]]

- 'What are the activities process doing at the moment' is what it means by the state.
- Process changes it states as it executes
- There are 5 main states of a process
1. new
	- Process is being created
	- Program is loaded into the main memory
2. ready
	- Process is waiting to be assigned to a processor 
3. running
	- Instructions are being executed
4. waiting
	- Process is waiting for some event to occur
5. terminated
	- The process has finished it's execution

###### What are the operations on process?
1. [[Process creation]]
2. [[Process termination]]

###### What are the two types of process?
1. [[Independent process]]
2. [[Cooperating process]]

> [!faq]- What is the first process of an OS?
> Kernal

