#Functions

A function call can happen anywhere a variable reference can happen. The format is
```
$(function_name arg1, arg2,...)
```

## Comma and space in the argument text

Commas can not appear. But you can do it using variable reference. Space can not appear as the leading argument text

```
comma := ,
empty :
space := $(empty) $(empty)
foo = a b c
bar := $(patsubst $(space), $(comma), $(foo))
```

## subst
```
$(subst from, to, text)
```

## patsubst
```
$(patsubst pattern, replacement, text)
```

Finds whitespace separated words in the text that matches the pattern

```
objects = foo.o bar.o
$(patsubst %.c, %.o, $(objects))
```

The above can also be written simply as

```
$(objects:.c=.o)
```
or
```
$(objects:%.c=%.o)
```
