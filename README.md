# Context-Switching
A mini project on Context Switching in Operating System 

In this project, we measure the cost of a context switch.

 To measure that, we ran two processes on single CPU and set up two pipes between them; a pipe is just one of many ways processes can communicate with one another. 
The first process then issues a write to the first pipe, and waits for a read on the second; upon seeing the first process waiting for something to read from the second pipe, the OS puts the first process in the blocked state, and switches to the other process, which reads from the first pipe and then writes to the second. When the second process tries to read from the first pipe again, it blocks, and thus the back-and-forth cycle of communication continues. 

By measuring the cost of communicating like this repeatedly using clock_gettime we can make a good estimate of the cost of a context switch. 

In multiprocessors, in order to ensure that the context-switching processes are located on the same processor, we have used sched_setaffinity() system call to bind a process to a particular processor.

