# Registers and local variables in a function

## Register saving conventions

1. Caller save - The caller procedure saves the values in the registers before calling other function.
eax, edx, ecx
2. Calle save - The callee saves the values in the registers before using them
evx, esi, edi

esp, ebp - special form of callee save.

Do remember that eax contains the return value of the callee.

## x86_64 bit conventions

### Usage convention

Not necessary to remember. But just o write them for the completeness of the note -
```
%rax - return value
%rbx - callee save
%rcx - Argument 4
%rdx - Argument 3
%rsi - Argument 2
%rdi - Argument 1
%rsp - Stack pointer
%rbp - Callee saved. No special meaning in x86_64 since no frame pointer.
%r8 - Argument 5
%r9 - Argument 6
%r10 - Caller saved
%r11 - Caller saved
%r12 - Callee saved
%r13 - Callee saved
%r14 - Callee saved
%r15 - Callee saved
```

### Highlights
1. Arguments upto first 6 in the registers. Hence faster
2. Local variables also in the register. Hence faster
3. callq rather than call which puts 64 bit address on to the stack
4. No %rbp since all references to the stack made relative to %rsp. (Not sure, I understand this correctly -->) This works because the functions can access memory upto 128 bytes beyond the %rsp.

Hence now a function can do away with a stack frame. The stack can contain only the return address. But a stack frame in x86_64 needed when

1. too many local variables
2. calls another function that has too many arguments
3. local variables that are struct or arrays
4. the address of the local variable is computed
5. needs to save the state of the callee-saved registers before using them.
