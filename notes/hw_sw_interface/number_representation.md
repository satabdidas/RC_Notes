# Number representation

In two's complement. Because addition/subtraction becomes easier in two's complement system than in the sign magnitude form.

Sign magnitude form is 1001 => -1
Two's complement is    1111 => -1

How to get two's complement of x => ~x + 1

The addition we do is called module 2^w addition because we ignore carry bit. For example

7   0111
-4  1100
--------
3  10011
   ^
   |
  Ignore


## Signed and unsigned numbers

The signed numbers are cast into unsigned numbers in an expression if not specified explicitly.