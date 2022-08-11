Simple Shell Project

Simple UNIX command interpreter
How does a shell work
The shell is an interface to the operating system. It acts as a command interpreter; it takes each command and passes it to the operating system. It then displays the results of this operation on the screen

What is a pid and a ppid
#PID & PPID

A process is an instance of an executing program, that has a unique process ID. This process ID is used by many functions and system calls to interact with and manipulate processes. In order to retrieve the current process’ ID, you can use the system call getpid (man 2 getpid): Each process has a parent: the process that created it. It is possible to get the PID of a parent process by using the getppid system call (man 2 getppid), from within the child process.

How to manipulate the environment of the current process
#Environment

We have seen that the shell uses an environment list, where environment variables are “stored”. The list is an array of strings, with the following format: var=value, where var is the name of the variable and value its value. As a reminder, you can list the environment with the command printenv: Actually, every process comes with an environment. When a new process is created, it inherits a copy of its parent’s environment. To access the entire environment within a process, you have several options:

via the main function and via the global variable environ (man environ)

What is the difference between a function and a system call
The main difference between system call and function call is that a system call is a request for the kernel to access a resource while a function call is a request made by a program to perform a specific task

How to create processes
#Creating processes

The system call fork (man 2 fork) creates a new child process, almost identical to the parent (the process that calls fork). Once fork successfully returns, two processes continue to run the same program, but with different stacks, datas and heaps. Using the return value of fork, it is possible to know if the current process is the father or the child: fork will return 0 to the child, and the PID of the child to the father.

What are the three prototypes of main
#main

So far we have seen that main could have different prototypes:

int main(void); int main(int ac, char **av);

There is actually another prototype:

int main(int ac, char **av, char **env); where env is a NULL terminated array of strings.

How does the shell use the PATH to find the programs
The shell tries each directory in the PATH , left-to-right, and runs the first executable program with the matching command name that it finds. Slashes in the pathname prevent the shell from using PATH to look up the command name, so the shell executes /bin/date directly.

How to execute another program with the execve system call
#Executing a program

The system call execve allows a process to execute another program (man 2 execve). Note that this system call does load the new program into the current process’ memory in place of the “previous” program: on success execve does not return to continue the rest of the “previous” program.

How to suspend the execution of a process until one of its children terminates
#Wait

The wait system call (man 2 wait) suspends execution of the calling process until one of its children terminates.

What is EOF / “end-of-file”?
The End of the File (EOF) indicates the end of input. In computing, end-of-file (EOF) is a condition in a computer operating system where no more data can be read from a data source

AUTHORS:

Ijiagunoba Anthony Chinedu and Paul Ogbonna
