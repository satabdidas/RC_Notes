# New concepts for me

1. Multiple return values
2. Naked return values
3. Variable declaration of the form
```
var blah, foo, bar bool
```
The type comes at the last.
4. Initiliazing variables
```
var i, j int = 1, 2
var blah, foo, bar = true, false, "a string!"
```
5. Short variable declaration
```:=``` cn be used only inside a function. Outside the ```var``` keyword has to be used.
6. Variables are initialized with 0, false or ""
7. Type conversion - T(v)
8. Type inference (kind of tricky to remember, hence writing it down)
```
i := 6
j := 4.5
k := 1.3 + 0.4i // complex type
```
9. Constants with ```const```. Can't be declared with := syntax

10. if statement - Something like this is feasible. Of course the variable v is visible only in the scope of if and else
```
if v := math.Pow(x, n); v < 3 {
   return v
}
```

11. Switch statements without expression are cool too!

12. defer and stack of defer are cooler



Confusions

1. Let p be a pointer to a struct

```
v1 = Vertex{1, 2}
p = &v1
p = &Vertex{1, 2}
```

p.X is valid
p is a pointer to a struct


2. What's the use of slice literals? How are the different from array literals?