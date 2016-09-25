# Arrays and Structs

## Multi-dimensional vs multi-level array
```
int arr[2][3] = {{0, 1, 2},
                 {3, 4, 5}
                };
```
vs
```
int *arr[2] = { ptr1, ptr2, ptr3 };
```

### Memory accessing

In case of multi-dimensional array, there's only one memory access.

But in case of multi-level array, there are two. First to get the pointer stored at the correct index and then get the element stored at the index

```
return arr[i][j];
```
will be represented int eh assembly as
```
# %ecx = i
# %eax = j
leal (, %ecx, 4) %edx # 4 * i
movl arr(%edx) %edx # Mem[arr + 4 * i]
movl (%edx, %eax, 4), %eax # Mem[ ... + 4 * j]
```