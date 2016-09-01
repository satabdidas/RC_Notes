# Pattern Rules and Automatic Variables

## Format
```
%.o : %.c
```

## Automatic Variables

### Target file name
```
%@
```

### First element in the list of prerequisites
```
$<
```

### All the prerequisites
```
$^
```

### All the prerequisites that are newer than the target
```
$?
```

## Static Patttern Rules
Application where
1. Has multiple targets
2. Has analogus prerequisites

```
targets: target pattern: prerequisite pattern
         recipe
```

```
objects = foo.o bar.o

all: $(objects)

$(objects): %.o: %.c
        $(CC) -c $(CFLAGS) $< -o $@
```

I can write
```
$(objects): %.o: %.c foo.h
        $(CC) -c $(CFLAGS) $< -o $@
```

foo.h is same for all the targets.

Each target specified must match the target pattern.