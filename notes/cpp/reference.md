# Reference

## Assigning to a reference.
Writing this since this was a gotcha for me -

```
Foo& foo = obj1;
foo = obj2;
```

This means the obj1's value will be changed by obj2

## Method chaining and named parameter idiom

The following is method chaining -
```
obj1.method1().method2()
```

method1() returns a reference to the this object and so on. Using this named parameter idiom can be implemented.

What's named parameter idiom -it's similar to Verilog/system verilog module ports. Consider the following constructor -
```
OpenFIle(filename, permission, buffered, createIfNotexist, blockSize, exclusiveAccess)
```

It's very inconvenient to remember the parameters in the correct order. Instead all the parameters can be converted into methods returning reference to the this object.