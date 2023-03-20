---
tags: os  software
aliases: syscalls
---
Programmatic way to request a service from the [[Kernel]]

###### What is the purpose?
Establishing the connection between user programs and the [[System Services]]

###### Examples?
![[Pasted image 20230217084249.png]]

###### In which languages system calls are written in?
A high level language like C or C++

###### Why developers do not directly run sytem calls?
User is seperated from the kernel to prevent the user code from crashing the system.

###### How to access system calls?
Programs use higher level [[API]] rather than the direct system call use

###### What are the common API used for system calls?
- Win32 API - For windows
- [[POSIX API]] - For [[POSIX]] based systems like [[UNIX]], [[Linux]] and POSIX

###### How sytem call works?
- Each syscall has a number assosiated with it
- Thoese numbers are listed in a table by the [[System Call Interface]]
- System call interface invokes any system call in the kernel mode and return it's status and output to the user mode.
![[Pasted image 20230217080046.png]]

###### How to parse parameters with system calls?
1. Store the actual parameter in a [[Register]]. Then pass that register address as the parameter to the syscall.
2. Store parameters in a block in the memory. Then pass that single register address as the parameter to the syscall. Do not limit the number or length of the parameters. (Used in Linux and Solaris)
3. Parameters are pushed into a stack by the program. Then they are poped off by the OS. Do not limit the number or length of the parameters.

###### What are the types of syscalls?
- Process control
	- create/terminate process
	- end, abort
	- load, execute
	- get/set process attributes
	- wait for time
	- wait event, signal event
	- allocate and free memory
	- dump memory if error
	- debugger
		To determine bugs and single step execution
	- locks
		For managing access to shared data between processes
- Information maintenance
	- get/set time or date
	- get/set system data
	- get/set file or device attribute
- Communications
	- create/delete communication connections
	- send/receive messages
	- create and gain access to memory regions
	- transfer status info
	- attach/detach remote devices
- File management
	- create/delete file
	- open/close file
	- read/write and reposition file
	- get/set file attributes
- Device management
	- request/release device
	- read/write and reposition device
	- get/set device attributes
	- attach/detach devices logically
- Protection
	- get/set permissions
	- control access to resources
	- allow and deny users

