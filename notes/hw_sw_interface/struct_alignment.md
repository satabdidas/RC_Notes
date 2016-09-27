# Struct Alignment

The primitive data types starts at the address divisible by the number of bytes. For instance, ints, floats, pointers start at address divisible by 4. The doubles should start at address divisible by 8.

## Satisfying the alignment requirement for structs

Each struct should start at the address which is divisible by the no. of bytes in the largest element in the struct.

## Saving space

Put the largest elements first.

```
struct abc {
       char c;
       int i[2];
       double d;
};
```

On IA 32 Linux, the size of the struct is = 1 + 3(padding) + 4 + 4 + 8 = 20 ( double aligned like a 4 byte data type )

On x86_64, the size of the struct is = 1 + 3(padding) + 4 + 4 + 4(padding) + 8 = 24;

Rearranging the elements

```
struct abc {
       double d;
       int i[2];
       char c;
};
```
Now on IA 32,t he size of the struct is = 8 + 4 + 4 + 1 = 17

## Array of structs

For array of structs, the rearrangement doesn't benefit much because of the requirement that each struct now should be aligned according to the largest element it has which in this example's case is double.

Hence for an array of 2 structs the size of the array will be = 17 + 7(padding) + 17