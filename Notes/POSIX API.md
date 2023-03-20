---
tag:  linux os programming
created: 2023-03-09
---
Include following headers when working with system calls to avoid compilatoion warnings
- `<sys/types.h>` - to include OS types 
- `<unistd.h>` - to include function definitions

>[!note]- Compilation warnings can be ignored by passing `-w` to gcc

# Process management
## fork()
Create a child process of the process(program) which is calling the function. Child process only contains the instructions after fork() is called.

> [!example]- Create a simple child process
> ```c
> //exercise1.c
>#include <stdio.h>
>int main(){
>	printf("I am Parent\n");
>	fork();
>	printf("Hello World\n");
>}
>```
>![[Pasted image 20230309104532.png]]

> [!example]- Create recursive child process
> ```c
> #include <stdio.h>
> int main(){
> 	fork();
> 	fork();
> 	fork();
> 	printf("Hello\n");
> }
> ```
> >[!note]- Number of process created = number of "Hello" printed
> 
>![[Pasted image 20230309111511.png]]

`fork()` returns a interger about the child process it created, but that return value is subjective to the process running
- Inside the child process - 0
- Inside the our program - positive number means pid of the child created, negative number means there is an error
> [!example]- Find if a process is child or parent
> ```c
> #include <stdio.h>
> int main(){
> 	int ret = fork();
>     if(ret == 0){
> 	    printf("Im the child process");
>     }
> 	 else if(ret > 0){
> 		 printf("Im the parent process and the child i created is: %d\n", ret);
> 	 }
> 	 else{
> 		 printf("IThe")
> 	 }
> }
> ```

Process id can be found by following functions
- `getpid()` - Get the pid of currently running process
- `getppid()` - Get parent pid of currently running process
>[!warning]-  `getppid()` is time dependent
> It will return an unexpected value when the original parent has died at the time of child's execution

> [!example]- Get the id of process and it's parent
> ```c
> #include <stdio.h>
> int main(){
> 	int ret = fork();
>     if(ret == 0){
> 	    printf("C: my id is - %d\n",getpid());
> 	    printf("C: my parent id is - %d\n",getppid());
>     }
> 	 else {
> 		 printf("P: my id is - %d\n", ret);
> 		 printf("P: my parent id is - %d\n",getppid());
> 		 printf("P: child created by fork() is - %d\n", ret)
> 	 }
> }
> ```
> ![[Pasted image 20230310070554.png]]
> >[!faq]- Why parent pid of C is not displayed as our expected value (9208)?
> > Because that parent has already died when the C was executing. It has assigned with a different parent. Such child are called `orphan process`

## system()
A way for the programs to interact with the operating system. It is used to execute a command within a process. The system call provides the services of the operating system to the user programs via Application Program Interface (API).
>[!example]- Execute a terminal command inside another process
>```c
>#include <stdio.h>
>#include <unistd.h>
>#include <sys/types.h>
>
>int main(){
>	printf("Before the command\n");
>	system("ls");
>	printf("After the command\n");
>}
>```
>![[Pasted image 20230310073729.png]]

## exec family
>[!faq]- What is the purpose of using `exec` syscalls?
>In UNIX, new process cannot be created. Because they gonna be empty when created. Therefor, we have to clone an existing process and replace it with a 

Only few members are explained, read the below page to find more.
```embed
title: 'exec(3) - Linux manual page'
image: 'https://man7.org/tlpi/cover/TLPI-front-cover-vsmall.png'
description: 'Pages that refer to this page: pmlogger(1), xargs(1), execve(2), getpid(2), ptrace(2), seccomp(2), statfs(2), vfork(2), atexit(3), clearenv(3), confstr(3), glob(3), libexpect(3), lttng-ust(3), on_exit(3),…'
url: 'https://man7.org/linux/man-pages/man3/exec.3.html'
```

A family of functions which replace the current process image with a different image specified. Each member of the family can be used with different arguments.

### execl()
Execute an absolute binary file. Arguments are provided in the linear manner, which are
1. Absolute bianry file(char*)
2. Cli arg0/ binary name (char*)
3. Cli arg1 (char*)
4. Cli arg2 (char*)
- ......
- NULL (to indicate the end of cli args)

>[!example]- Without cli args
>```c
>#include <stdio.h>
>int main(){
>	printf("Here comes the data\n");
>	execl("/bin/date", NULL);
>	printf("That was the date\n");
>}
>```
>![[Pasted image 20230310175322.png]]
>>[!note] Last line is note printed as the `date` has replaced our original program

>[!example]- With cli args
>```c
>#include <stdio.h>
>int main(){
>	execl("/bin/ls", "ls", "-l", "/home", NULL);
>}
>```
>![[Pasted image 20230310180911.png]]

### execv()
Execute an absolute binary file, arguments are provided as a vector, which are
1. Absolute binary file (char*)
2. Array of char*, last element must be NULL

>[!example]- 
>```c
>#include <unistd.h>
>int main(){
>	char *binary = "/bin/ls";
>	char *args[] = {"ls", "ls", "-l", "/home", NULL};
>	execv(binary, args);
>}
>```
>Output is same as the previous

### execve()
In addition to `execv()`, enviroment variables can be provided as an vector. Last element must be `NULL`
>[!example]- 
>```c
>#include <unistd.h>
>int main(){
>	char *binary = "/bin/ls";
>	char *args[] = {"ls", "-l", "/home", NULL,}
>	char *env[] = {"HOSTNAME=www.linuxhint.com", "PORT=8080", NULL};
>	execve(binary, args, env);
>}
>```
>Output is same as the previous

## sleep()
Execute a program in CPU without actually doing anything for a specific amount of time. A time argument must be provided in seconds. This function wastes the CPU time

>[!example]- 
>```c
>#include <stdio.h>
>#include <unistd.h>
>int main(){
>	int time = 5;
>	printf("This process is in the sleep mode for %d seconds\n", time);
>	sleep(time);
>}
>```

## exit()
Terminate a process from the process itselves. One argument can be passed to indicate the reason for exiting the process. Which are,
1. `EXIT_SUCCESS` - To indicate that process terminated successfully
2. `EXIT_FAILURE` - To indicate that process terminated because of an failure

## wait()
Stop a process from executing until the child is finished executing. Only use with a parent process
>[!note]- Header
>Function declaration for `wait()` is available in `<sys/wait.h>` header

>[!example]- 
>```c
>#include <stdio.h>
>#include <stdlib.h>
>#include <unistd.h>
>#include <sys/types.h>
>#include <sys/wait.h>
>
>int main(){
>	pid_t id = fork();
>	if(id == 0){
>		printf("My parent is %d\n", getppid());
>		sleep(5);
>		exit();
>		printf("My parent is still %d, it has waited until im finished\n", getppid());
>	}
>	else{
>		wait(NULL);
>	}
>}
>```


