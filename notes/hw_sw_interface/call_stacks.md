# Procedure Call Stack

## Procedure Call Linkage

The convention of where to leave/find things by the caller and callee functions. We are goining to see C on Linux.

## Procedure call

```
call <address of the callee>
```

Steps
1. push the return address on to the stack
2. jump to the label/address

The return address is the address immediately after the call instruction.

When the callee returns the steps are
1. pop the return address from the stack
2. jump to the address

## Call instruction
When a call instruction is encountered

1. the eip advances to the next instruction
2. push the next instruction from eip on to the stack
3. jump to the address in the call. One way of generating the address is to add the offset in the call instruction and add to the address in eip.


Return
1. pop the address and load it on to eip
2. jump the the address

## Return values

Convention is to store the return values onto %eax. Hence, before calling the callee, the caller saves the register. For return values greater than 4 bytes, best to return a pointer to it.

## Linux Stack Frame

The caller does the following

1. pushes the arguments to the callee onto the stack
2. pushes the return address

The callee does the following
1. pushes the ebp which points to the ebp of the caller. Hence the esp now points to the caller's ebp.
2. mov esp ebp. That means the ebp of the callee is being set and actually this ebp points to the ebp of the caller.
3. The arguments are accessed by indirect addressing using the ebp. e.g.
```
mov 12(%ebp) %ecx
mov 8(%ebp) %edx
```

Finishing the callee
At the end, the ebp and esp aree pointing to the same location.
1. Save and restore regsters
2. ```movl %ebp %esp``` which adjusts the stack.
3. ```popl %ebp``` which pops the stack and restores the caller's ebp and after this isntruction, the esp now points to the return address.
4. ret instruction - pops the stack and jump to the address


## leave instruction

is equivalent to
```
mov %ebp %esp
pop %ebp
```