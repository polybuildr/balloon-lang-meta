# Week 1: 12th - 19th Jan

- Looked into Scala's type system
    - https://twitter.github.io/scala_school/type-basics.html
    - Part of https://twitter.github.io/scala_school/advanced-types.html
    - Went through some basic tutorials at https://www.tutorialspoint.com/scala/
- Read about subtype polymorphism, parametric polymorphism, covariance and contravariance (especially in function calls), and row polymorphism
- Looked at Typed Racket
- Looked at Racket's syntax extensions
- Read about Nim, a new (2008) "statically typed, imperative programming language that tries to give the programmer ultimate power without compromises on runtime efficiency." since an article said that it combines features of C/C++, Rust, Python and Go.
- Looked at sum types (tagged variants) and union types (Typescript's need to model existing JS libs)
- Looked at Jeremy Siek and Walid Taha's paper: Gradual Typing for Objects
- Looked at Sam Tobin-Hochstadt Matthias Felleisen's paper: The Design and Implementation of Typed Scheme
- Started reading the under-development book "Crafting Interpreters" (craftinginterpreters.com) by Bob Nystrom, a language designer and engineer currently working on Dart at Google. He has built several small languages: https://github.com/munificent
- [IRC] Joined a programming language design IRC channel which has many enthusiasts that have built their own programming languages, some of which are impressive
- Got a gentle introduction to Typeclasses in the Haskell context
- [IRC] Was pointed to a "Programming Languages Zoo" (https://github.com/andrejbauer/plzoo) with examples of tiny languages, each with different language features (functional, declarative, object-oriented, and procedural languages, for example)
- [IRC] Got an explanation for why normal subtyping makes type inference difficult
- [IRC] Was pointed to Google's Dart, since it seems to share many goals

# Week 2: 19th Jan - 24th Jan

- Looked at Dart language, since it shares many common goals
- Attempted to understand details of Jeremy Siek's paper on gradual typing for objects
- Learnt that there was a difference between optional and gradual typing
- A week long vacation started on the 24th

# Week 3: 1st Feb - 8th Feb

- Considered and decided some semantics of the language
    - Basic syntax (without OOP considerations)
    - Handling of immutability: asked certain questions on IRC channel and StackOverflow: have some tentative decisions
- Ran a basic analysis on jQuery's code to look for a particular assignment pattern
- Read (and understood more of) Siek's paper
- Found an LLVM Kaleidoscope tutorial in Rust for reference: https://github.com/jauhien/iron-kaleidoscope
- Reconsidered Rust vs C++ for implementation.
    - With some assurance of help with the trickier parts of Rust, will tentatively go with Rust.
- Found and read Siek's analysis of gradual typing in TypeScript
    - [Part 1](siek.blogspot.in/2012/10/is-typescript-gradually-typed-part-1.html), [Part 2](siek.blogspot.in/2012/10/is-typescript-gradually-typed-part-2.html)
    - Discusses type 1, type 2, and type 3 gradual typing
    - Raises some issues in TypeScript, a TypeScript team member responds
    - For type 3 typing, will need to look at a follow up paper by Siek on blaming

# Week 4, 5, 6..: 9th Feb - 7rd March

- Basic interpreter and REPL
    - 1174 lines of Rust (total work in commits: 2956++, 1091--)
    - variable declarations
    - arithmetic
    - 2 primitive types: `Number` (with subtypes `Integer`, `Float`), `Bool`
    - comparison operators, equality operators
    - logical operators `and`, `or`, and `not`
    - `if`/`else` statements

- Things read
    - ["Let's stop copying C"](https://eev.ee/blog/2016/12/01/lets-stop-copying-c/)

      Slightly questionable choices from C that other languages seem to continue making.

    - Next chapter of "Crafting Interpreters": [Representing Code](http://craftinginterpreters.com/representing-code.html)

- More experience on sum types and tagged variants when using Rust. Relevant since the new language will probably have these.
    - Combinators, early returns
    - Haskell's `liftM2`
- Explicit line terminators or not - that is the question
    - ambiguities in JS, Go
    - Dartlang issue discussing this
    - chose to have explicit terminators at least for now for simplicity's sake
- Integers and floats: problems with JS's `float64`
- Lua
    - Small, fast, "simple" language: can be intepreted or compiled
    - Entire distribution is just ~1.1MB, can be compiled on virtually any platform
    - Lua 5.3's change wrt integers, `number` type with two subtypes
