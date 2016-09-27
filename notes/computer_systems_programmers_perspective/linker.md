# Linkers

Linker is a process that combines object files into an executable. It can be performed during

1. compile time by the static linker
2. loading time by the loader
3. run time by the user application

## Compiler Driver

gcc is a compiler driver. It first invokes the preprocessor which generates a .i file, then the compiler which generates the assembly file (still in ASCII), then the assembler which generate the relocatable object code and then the linker which generates the executable.

When you run a program (for instance ./a.out on the shell), the shell invokes the loader which reads the executable from the disk and loads the text and data into the memory and transfer control to the beginning of the program.

## Static Linking

Static Linkers takes a collection of relocatable object files and creates an executable that can be run. It performs two tasks -

1. Symbol resolution - finds the symbol definition for a reference. There has to be only one symbol definition.
2. Relocation - ??

## Object Files

3 tyes
1. Relocatable object files - can be combined with other relocatable object files to generate executables.
2. Executable object files - can be loaded into the memory and run
3. Shared object files - can be loaded into the memory and linked dynamically either during the loading time or the run time

Some names of object files - COFF (common object file format), PE (Portable Executable Format), ELF(Executable and Linkable Format)

## Relocatable Object Files
ELF is a format used on Linux. ELF file contains ELF header, section headers and sections. A few sections that I keep on forgetting is -

.rel.text - list of locations in the text which need to be modified when the linker combines the object file with other object files
.rel.data - any initialized global variable whose initial value  is the address of a global variable

## Symbols and Symbol Table

Symbols can be -
1. Global variables used by the object module but defined in another module
2. Global variable defined by the object module and may be refered by another module
3. Local variables. For example, static variables.

Local variables to functions are defined on the stack.

## Symbol Resolution

The linker tries to find for each symbol reference exactly one symbol definition. When a compiler encounters a symbol that is not defined in the current object module, it assumes that it is defined in another object module and generates a symbol table entry for the linker.

## Name mangling strategies

Just an interesting fact - name mangling for C++ and Java are compatible.

### Name mangling strategy for classes
Number of characters in the class name + class name.

Foo is encoded as 3Foo.

### Name mangling stratefy gor class member methods
Original method name + __ + class name + single letter encoding of of each argument type.

Foo::bar(int, long) is encoded as bar__3Fooil