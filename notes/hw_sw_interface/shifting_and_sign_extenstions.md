# Shifting and Sign Extensions

## Shift operation for unsigned integers

Logical shift. The vacant bit positions are filled with 0.

## Shift operation for signed integers

Arithmetic right shift. Compared to logical shift, in case of right shift, the MSB is replicated in the vacant bit position. And in case of left shift

## Sign extension

Given w-bit signed integer, convert it to w+k bit integer. k copies of the sign bit are made.

1. Converting from smaller data type to larger data type, the vacant bits are filled with the signed bit.