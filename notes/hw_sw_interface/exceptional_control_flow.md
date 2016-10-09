# Exceptional control flow

Control flow of a program means the processor executes intstruction from the start till end. The instructions to change control flow are

1. jmp
2. ret

But there can be other situations where a process needs to change its control flow. For instance a mouse click

exception is transfer of control to the OS in response to some event. Exception handler is some piece of code in the OS in case an exception happens. How does the OS know which code to execute. By the means of interrupt vector. And the control goes to the exception handler. For instance the interrup handler for "int 3" gives a SIGTRAP signal to the process.

jmp and ret can not be used to handle such situations.

These are called exceptional control flow.

There are two types of exceptional control flow

## Asynchronous exceptional control flow
For instance mouse click. There's/re interrupt pin(s) on the processor chip. Whenever an interupt signal arrives on that pin, and interrupt is raised.

## Synchronous exceptional control flow
Triggered by executing an instruction.

There are three types

### Traps
Intentional way of transfering the control flow to the OS.

For instance system calls, breakpoint handling. After the processor executes the instruction for the trap, the program counter points to the next address in the original control flow.

Let's consider a system call. It's "int 0x80". The control goes to the OS and the OS executes the system call. Then the control comes back to the next instruction in the process.

  |
  |____
  \    |
  | \  |
  |   \|

### Faults
Unintentional, but possibly recoverable.
For instance page faults(unrecoverable), divide by zero, segfaults(unrecoverable).
The processor comes back to the same instruction in case of page fault, in other case the process just aborts.

### abort
Unintentional and unrecoverable. Machine check or parity error.