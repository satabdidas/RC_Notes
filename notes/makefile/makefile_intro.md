# Introductory Tutorial on MakeFile

## Format

target: prerequisite
        recipe


## Prerequisites

There can order-only prerequisite apart from normal prerequisites. The order-only prerequisite don't invoke the recipe of the target as the normal prequisites do. They only mean that the recipes of order-only rerequisits have to be built before the target's recipe. For instance,

```
$(OBJS): | $(OBJDIR)

$(OBJDIR):
        mkdir $(OBJDIR)
```

## Wildcards and Pitfalls of Wildcards

```
objects = *.o

foo : $(objects)
        cc -o foo $(CFLAGS) $(objects)
```

Now, if you delete all the .o's, wildcard doesn't match any file and foo will depend on a file named *.o and make will throw an error.

## VPATH: Search path for all prerequisites

If a file listed as target or a preequisite is not found in the same directory, make will search for the file in VPATH.

```
VPATH = src:anothersrc

foo.o = foo.c => foo.o = anothersrc/foo.c
```

## Selective Search with vpath (note the lower case)

```
vpath %.h ../headers
```

The above asks make to search all the headers in the ../headers directory.

## -l<libname> in Prerequisite
```
foo : foo.c -lcurses
        cc $^ -o $@
```

First libcurses.so is searched in the current directory, vpath search path, VPATH search path and then /lib, /usr/lib and crazy other places. If the .so is not found, it searches for libcurses.a in the same way.

## Phony Targets
To avoid a conflict with a file of the same name and to improve performance.

## Built-in Targets

```
.SILENT # no printing of the recipe of the prerequisites of this target.
.INTERMEDIATE
.PHONY
```

## Multiple Rules for One Target

All the prerequisites are mereged into one list. If more than one recipe are found, then the last one is applied.

```
main.o : main.h foo.h

main.o : main.c
       $(CC) $(CFLAGS) -o $@ $^
```

## Double colon rule
If a target appears in multiple double colon rule, then all the recipes for double colon rules are applied.

There can not be mix between double colon and single colon rule for the same target.