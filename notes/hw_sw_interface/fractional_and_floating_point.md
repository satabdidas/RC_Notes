# Fractional and Floating point binary representation

# Fractional number
101.011 => 1 * 2^2 + 0 * 2^1 + 1 * 2^0 + 0 * 2^-1 + 1 * 2^-2 + 2 * 2^3
        => 4 + 0 + 1 + 0 + 0.25 + 0.125
        => 5.375


.11 => 3/4
.111 => 7/8
.111111 => 63/64
.010101[01] => .333333

# Floating point number

Represented in the following format = 1.M * 2^e

1 bit - sign
8 bits - exponent
23 bits - mantissa

*Equality comparison on floating point numbers are tricky*