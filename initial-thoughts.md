# Balloon: Initial thoughts

This is a working draft and is subject to major changes.

## Goals

Balloon is meant to be a scripting language, primarily meant for back-end web programming. It is meant to be familiar to developers who have worked with languages like JS, Python and PHP. It will also try to not surprise the developer and try to reduce accidental misinterpretation of code (WYSIWYG, no hidden magic).

- Gradually typed
    - opt-in static typing
    - opt-in to inferred static types (C++'s `auto`)
    - default dynamic typing

- Mutability
    - Provide mutable and immutable bindings _statically_ (whether a variable can be re-assigned)
    - Provide mutable and immutable values _dynamically_ (whether the value a variable points to can be mutated)

- Types
    - primitives: `bool`, `number` (`int64` or `float64`), `string` (ASCII bytes), `fn`
    - lists/arrays, maps/hashtables

## Under consideration
- Gradually typed
    - type inference

- Types
    - `[u]int[8|16|32|64]` and `float[32|64]`
    - union types: `string | number`
    - nullability vs default values (safety?)
    - Unicode strings, utf-8 strings

- Mutability
    - Provide mutable and immutable values _statically_ (whether the value a variable points to can be mutated)

- object oriented
    - `class`, `object`
    - inheritance? interfaces? mixins?

- Matching (`match`) and destructuring

## Non-goals
- Being an "original", "innovative" language
- Speed => will not spend much time optimizing, at least initially
x
