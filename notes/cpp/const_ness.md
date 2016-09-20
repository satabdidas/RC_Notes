# Const correctness

## Const overloading
Pair of functions. For instance,
```
class List {
public:
        int& operator [] (int id);
        const int& operator [] (int id) const;
};
```

## Logical state of an object vs Physical state of an object in the context of const

The logical state defines the state that is user visible. Some of that state may be a member variable of the class and some may be even calculated on the fly. For instance area of an rectangle calculated on the basis of height and width. All three belong to the logical state.

The physical state are the bits in the object.

A member function should be const if it doesn't change the logical state of an object but changes the physical stateo of an object. For instance a lookup table. It may keep a cache for it most recently searched object. Hence every search doesn't change the logical state but changes the physical state. Hence the search should be const. And the cache should be ```mutable```.
