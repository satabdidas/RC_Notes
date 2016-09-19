# Assembly programming

## Transfer between memory and register

1. Load - from memory
2. Store - into memory

## movx instruction
```
movx source destination
```

x = l, for 4 bytes
  = w, for 2 bytes
  = b, for 1 byte

### Source
1. Constant e.g.
```
movl $0x0034 %eax
```

Only the source can be constant

2. Register
```
movl %eax %edx
```

3. Memory address
```
movl (%edx) %eax
```
The above means that load data from the memory address stored in the register edx into the register eax.

### Memory address mode

1. Indirect addressing
```
movl (%eax) %edx
```

2. Displacement
```
movl 8(%ebp) %edx
```

Mem[%ebp + 8] is loaded into the register edx.
