# Questions

## Default copy vs default reference

Python, PHP and JS all use references by default for assignments when the types involved are non-primitive.

```js
let A = {a: 5};
let B = A; // reference to the value that A was pointing to
B.a = 10;
A.a; // = 10
```

while C++, for example, uses copy by default.
```cpp
std::vector<int> v = {1, 2, 3};
std::vector<int> v2 = v; // copy of v
v[0] = 100;
v2[0]; // = 1
```

Both types have their gotchas.

TBH, web programmers are probably used to the default reference version. So maybe something like a `= copy` and `= deepcopy` would make assigning to a copy clearer, and the default should be left as copy by reference.

## Error handling: exceptions vs return values
...

## Multiple return values from functions
...

## Unicode support
- ICU/Boost::Locale
- String operations?
- utf8

## Conditionally assigning const variables

```js
const x;
if (cond) {
    x = 10;
} else {
    x = 20;
}
```

does not work. On the other hand,

```js
const x = cond ? 10 : 20;
```

works.

It should be possible to have complex to assign `const` variables. Rust has:

```rust
let x = if cond { 10 } else { 20 };
```

could be implemented as

```js
const x = if (cond) 10 else 20;
// and also,
const x = if (cond) {
    f1();
    f2();
    /* return ? */ 10;
} else {
    f3();
    /* return ? */ 20;
};
```

similar to how python has

```py
x = 10 if cond else 20
```

## Sum types and union types?

Ideally, would like to support both.
