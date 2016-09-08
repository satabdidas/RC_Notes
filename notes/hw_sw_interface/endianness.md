# Endian_ness

## Big endian
The most significant bytes are put before the least significant bytes

0A0B0C0D => 0A | 0B | 0C | 0D
            0    1    2    3

## Little endian
Followed in x86 architecture

The least significant bytes are put before the most significant bytes

0A0B0C0D => 0D | 0C | 0B | 0A
            0    1    2    3

## How to figure out the endian ness of a machine

```
void find_endian_ness(int num) {
     char *arr = (char *) &num;
     for (int i = 0; i < 4; ++i) {
         printf("%p - %x\n", arr[i], &arr[i]);
     }
}
```