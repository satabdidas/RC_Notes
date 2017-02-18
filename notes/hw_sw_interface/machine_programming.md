# Machine Programing

## Architecture vs Microarchitecture

Architecture - what's visible to the software. e.g. registers
Microarchitecture - how the architecture is implemented. e.g. cache, core frequency

## 3 important things in assembly programming - Program visible state

1. Program counter. EIP in IA32 and RIP in x86-64. Extended Instruction Pointers
2. Registers - holds data. Very fast memory. Close to the CPU
3. Condition codes - used for conditional branching, stores status information of the most recent arithmetic operation

## Memory

byte addressible. memory can be thought of as an array of bytes.

## Compiling into assembly
```
gcc -S abc.c
```

## 3 basic kind of assembly instructions
1. Arithmetic functions on registers and memory data
2. Transfer to and from memory
3. Transfer control
 a. Unconditional jumps
 b. Conditional jumps

## Assembly data types

1. Integer - 1, 2, 4 bytes of IA32 or 8 bytes for x86-64
2. Floating point data of 4, 8, 10 bytes

## Tool to see assembly code

```objdump``` disassembles from machine code to assembly

## Registers in IA32
8 registers - 32 bit
1. eax
2. ecx
3. edx
4. ebx
5. esi
6. edi
7. ebp (Stack base pointer)
8. esp (Stack pointer)

Some aliases to access the bytes of the registers partially -

1. %ax => lower 2 bytes
2. %ah => 2nd byte
3. %al => lease significant byte

|________|_%ah___|_%al___|

## Registers in x86-86
16 registers
1. rax
2. rcx
3. rdx
4. rbx
5. rsi
6. rdi
7. rbp
8. rsp
9. r8
10. r9
11. r10
12. r11
13. r12
14. r13
15. r14
16. r15

For backward compatibility, eax is part (first 32 bits) of the rax