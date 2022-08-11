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

Ijiagunoba Anthony and Paul Ogbonna
