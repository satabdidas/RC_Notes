# Memory Addressing Modes

Most general form -

D(Rb, Ri, S)

D -> Constant displacement. Can be 4, 8, 16
Rb -> Base register. Any of the integer registers
Ri -> Index register. Can't be ebp or esp
S -> Scale

D(Rb, Ri, S) = Mem[Reg(Rb) + Reg(Ri) * S + D]

Can use any combination. e.g (Rb, Ri), D(Rb), (Rb, Ri, S) etc.

## Address computation instruction
Load effective address
```
leal src dest
```

It just calculates the address and loads into the destination register. The src operand is a type of address mode expression.

```
leal (%edx, %eax, 4) %ecx
```
%ecx = %edx + 4 * %eax

### Use case
1. Computing adsresses without memory reference
```
p = &x[1];
```

## Some other instructions
```
addl src dest => dest = src + dest
subl src dest => dest = dest - src
imull src dest => dest = src * dest
sarl src dest => dest = dest >> src - arithmetic
shrl src dest => dest = dest >> src - logical
incl dest => dest = dest + 1
```