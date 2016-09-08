#Makefile Variables

## Overriding variables using command line

```
make CFLAG='-g -O' all
```

## Recursively expanded variables
```
FOO = foo
```

Disadvantages
1. The following will result into infinite recursion
```
FOO = $(FOO) bar
```
2. If any function is referenced, the function will be executed every time the variable is used. It will result into slower run time.

## Simply expanded variables
```
BAR := bar
ZENGA ::= bleh
```
The references are expanded once when the variable is defined.

## Another variable assignment
```
FOO ?= bar
```

is equivalent to -
```
ifeq ($(origin, FOO), undefined)
     FOO = bar
endif
```

## Substitution reference
```
BAR = abc.o def.o ghi.o
FOO = $(BAR:.o=.c)
```

FOO = abc.c def.c ghi.c

The above can also be written as
```
FOO = $(BAR:%.o=%.c)
```

## Appending to variables
```
FOO = foo
FOO += bar
```

The above is also equivalent to
```
FOO := foo
FOO = $(FOO) bar
```

## Environment variables
Environment variables can be accessed by make