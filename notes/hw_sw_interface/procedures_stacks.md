# Procedures and Stacks

## Memory layout

Stack
___________
Heap
___________
Static data
___________
Read only region
___________
Instruction


Heap grows upward and Stack grows downward. When they run into each other - if the stack goes too deep or the program asks for too much memory the program goes out of memory.

Instructions, Literals and Static data are initialized.

The Instructions are executable i.e. the bits there are CPU instructions.

## IA32 Call stack

$esp => points to the top element of the stack

## Push instruction

```
pushl src
```

Takes the value at src and adds that to the stack and decrement esp by 4. 4 because ```pushl```

## Pop instruction
```
popl dest
```
Load value form %esp and write that value to dest. Increment esp by 4
