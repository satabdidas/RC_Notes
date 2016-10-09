# Processes

The OS uses the exception control flow to run multiple processes and giving the illusion that the processes are running in parallel.

Process is an instance of a running program. Program is a set of instructions.

Process provides 2 abstractions

1. Logical control flow - each process has exclusive use of the CPU
2. Private virtual address space - each process has control over the entire memory.

It simplifies writing the program a lot.

Processes can be concurrent or sequential

## Context switching

Switiching between two processes on the processor.

By the way, kernel is not a separate process but runs as part of the user process. Kernel is chunk of OS code which manages the processes. Kernel code has special privilege.

A process is running. There's a timer interrupt to the process. The process's state is saved. And another process starts running. Instruction pointer, register state and few other stuffs are saved.

## Fork and exec

fork create a copy of the current process - copies the code and address space of the parent process.
execve replaces the current process's code and address space with the new process and it doesn't return. It returns only when there's an error.

## Other processes

exit and atexit
zombies - when a process terminates but its resources are not cleaned up or released. Usually the parent cleans up the zomby processes.
wait - suspends the parent process until one of its child process terminates. It returns the pid of the terminated child process.
waitpid - wait for a particular child
