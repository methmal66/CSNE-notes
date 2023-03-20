#software #os 
> Process Control Block, a data structure, in which OS stores data about each process. OS represents a process using a PCB

###### What are the data in the PCB
1. Process state
	- New, running, etc
2. Program counter
	- Location of the next instructions to be executed
3. Registers
	- Which type of registers is depend on the architecture 
4. Scheduling info
	- Process priority
	- Pointers to scheduling qeues
	- Scheduling parameters
5. Memory management info
	- Memory allocated to the process
6. Accounting info
	- CPU usage
	- Real time used
	- Time limits
	- Job or process numbers
7. I/O status info
	- List of open files
	- List of I/O devices