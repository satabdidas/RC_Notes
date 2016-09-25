# Tiny ELF executables on Linux

One hell of a delightful article on making your executable smaller, smaller and even smaller.

Here's the link - http://www.muppetlabs.com/~breadbox/software/tiny/teensy.html

It first wrote it's own assembly code defining the main and generating the elf file using nasm and then generating the executable using gcc.

```
; tiny.asm
  BITS 32
  GLOBAL main
  SECTION .text
  main:
                mov     eax, 42
                ret
```

Then it was not happy with it and it defined the _start section and compiled with -nostartfiles. I think it can also be compiled with -nostdlib.
```
; tiny.asm
  BITS 32
  GLOBAL _start
  SECTION .text
  _start:
                mov     eax, 42
                ret
```

The above actually told gcc not to put the code related to start in the executable.

The above was segfaulting since

Then it was not happy with that size either since it was using _exit() function call which was a library function. It used the system call directly. That bummed down the size more.
