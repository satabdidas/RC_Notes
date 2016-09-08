# Implicit Rules

## How to use?

Two ways -
1. Don't give any recipe
2. Don't give any rule

Make passes the CFLAGS in the implicit rule.

## How to cancel implicit rules?

1. Define a new pattern rule with the same target and prerquisite but different recipe
2. Define a new pattern rule with the same target and prequisite but no recipe.

## Recipe for implicit rules for C/C++

For C,
```
$(CC) $(CPPFLAGS) $(CFLAGS) -c
```

For C++
```
$(CXX) $(CPPFLAGS) $(CXXFLAGS) -c’
```

Has implicit rules for generating .c from .l and .y

## Variables used by the implicit rules

1. Variables for name of executables. e.g. CC
2. Variables for arguments for other programs. e.g. CFLAGS

Some of the variables are -
*AR, CC (program for compiling C), CXX (program for compiling C++), CPP (program for running C Preprocessor), CPPFLAGS (extra flags to give to C preprocessor)*

## Intermediate Files
 * Don't understand this quite well *