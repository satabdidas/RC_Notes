# Executable Object File

Similar to a relocatable object file. The ELF header includes the program's entry point which is the address of the first instruction that ought to run when the program is executed

.text, .rodata and .data section are similar to that of the relocatable object file.

.init section defines a function _init which is called by the program's initialization code (What's initialization code?)

The way ELF file is loaded into the memory is contiguous chunks of ELF is mapped into contiguous memory segments. This mapping is described in the segment header table.