# Condition codes, conditionals, loop and switch statements

Control flow change can be -

1. Conditional. e.g. if, for, while etc.
2. Unconditional. e.g. break, continue etc.

Branches are referred to as jumps in x86

## Instructions

```
jmp => unconditional jump
je => jump if equal to zero
```

## Instruction pointer

%eip stores the next instruction. It also stores the special codes for branch instructions. The following can be the status of recent test

```
ZF - Zero flag ( in case of t == 0)
SF - Sign flag (in case of t < 0)
CF - Carry flag (in case of unsigned overflow)
OF - Overflow flag (in case of signed overflow)
```

The branch instructions change the value of the %eip.

## Implicit setting of conditional codes
addl/addq  can set implicitly.

## Explicit setting of conditional codes

cmpl/cmpq instructions
```
cmpl b a
```
The above actually computes a - b without setting the destination. But it sets the conditional codes.

test instructions
```
test src2 src1
```
The above actually computes src1 & src2

ZF => if a & b == 0
SF => if a & b  < 0

It can be used to check if (a < 0)

## Read condition code

```
setg %al
```

If the comparison was for greater, %al will be set.

## Conditional branch example
```
if (x > y) {
   return x - y;
} else {
  return y - x;
}
```
One way to interpret the above is (in a pseudo assembly)
```
  cmpl x y
  jle .L7
  subl x y
.L7
  subl y x
```

### Some improvement in x86_64
x86_64 turns out to be better than x86 in certain aspects. One is accessing hte arguments. In x86, you have to load them from the stack into registers. But in x86_64, you do not need to give any instructions for that.

The improvement in respect of conditionals is that in x86_64 you do not need any branching and branchings are expensive. The same C code above can be translated to -```
movl %edi %eax # eax = x
movl %esi %edx # edx = y
subl %esi %eax # eax = x - y
subl %edi %edx # edx = y - x
cmpl %esi %edi # compute x - y and sets the conditional code
cmovle %edx %eax # Only move y - x if x <= y
ret
```

But overhead is both the branches are evaluated.

## PC relative addressing

```
0x102 je 0x70
...
0x172 add r3, r4
```

The above is relocatable.

## Loops in assembly

1. while loop

```
goto middle
loop:
   ...
   loop body
   ...
middle:
   loop condition
```

2. for loop

```
init value
goto middle
loop:
   ...
   loop body
   ...
   update value
middle:
   loop condition
```

## Switch Statements
Switch statement are implemented using

1. Jump tables - if the range of case statement values are in a small range. Otherwise jump tables are expensive

Each line int the jump table corresponds to the case statement value. Each entry in the jump table contains an address to the code block corresponding to the case statement. And an indirect jmp is used to jump to the corresponding code block location.

2. Normal branch instructions like if conditionals

## Some questions

1. In x86, the %eax holds the return value. What if a function returns something which is more than 8 bytes?
2. In x86_64 %edi, %esi stores the arguments. What if there are more than two arguments?