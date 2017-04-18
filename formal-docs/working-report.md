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

# Week 4, 5, 6..: 9th Feb - 7th March

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

# 8th March - April 1

- Add loop and break constructs ([7519e864](https://github.com/polybuildr/balloon-lang/commit/7519e8646548a698847e27d97345c447a395efa7))
  
  Involved refactoring the `interpret_statement` logic to return `StatementEffect`
- Add function-like `println` as a statement ([cf56b6e8](https://github.com/polybuildr/balloon-lang/commit/cf56b6e842a7f6a888717e6685fb2a6c9bcc897a))
- Add inbuilt functions, make `println` one ([f878272d](https://github.com/polybuildr/balloon-lang/commit/f878272d240a676266e2f12f3558d0c2705507f8))
- Complain when if/else branches exit with different variable types ([beaf0130](https://github.com/polybuildr/balloon-lang/commit/beaf01303cc457dc4a1551cdd0ef22c3e7543f2f))
- Improved error printing
    - [194bc9c1](https://github.com/polybuildr/balloon-lang/commit/194bc9c1cfabbb0602510eebc6570cd195c26ed6), [d75c72e0](https://github.com/polybuildr/balloon-lang/commit/d75c72e02f1dd99cc5b96c5f3b9e5157d067357b), [00bac476](https://github.com/polybuildr/balloon-lang/commit/00bac47637ec349858bc79adb79a5a164f77fb6a) and others
    - Print better error messages with human-readable information and snippet of source causing error
- Typecheck number of function arguments ([239a365c](https://github.com/polybuildr/balloon-lang/commit/239a365c3174e92686f084faae4fb2a93c5755bb))
  
  Also account for variadic functions like `println`
- Support for user-written functions as closures ([69346dcd](https://github.com/polybuildr/balloon-lang/commit/69346dcdd176e7b472236a41270c6d85d0522c25, [bbcd3d7e](https://github.com/polybuildr/balloon-lang/commit/bbcd3d7eb2924be8e3a584a6af70daa9e229495b))
  
  Involved first possible occurrence of `null` - avoided that.
  
  Also add tests for curried add ([c3091fc3](https://github.com/polybuildr/balloon-lang/commit/c3091fc3edefbee86207bcc89e9ca160f2c68c84)) and Y combinator ([53887b89](https://github.com/polybuildr/balloon-lang/commit/53887b89fc70a501c8f69f0f0402db7f1c00f164))

# April 2nd - April 18th
- Significantly large refactoring, testing and minor changes
  
  [440009](https://github.com/polybuildr/balloon-lang/commit/440009809e2f9a7a018c48e6310657581c663792), [2f7b86d](https://github.com/polybuildr/balloon-lang/commit/2f7b86d4d062192b7fe893791975df6ae99c0355), [0f2c4bcc](https://github.com/polybuildr/balloon-lang/commit/0f2c4bccf4b989302ecf012004d17c1b3af092a5), [c13cca85](https://github.com/polybuildr/balloon-lang/commit/c13cca85c3ce7fb812918968de0043b179574b78) and others
    - Add more tests for interpreter and typechecker
    - Run tests on Travis CI ([a8c248d5](https://github.com/polybuildr/balloon-lang/commit/a8c248d5efc7efe4c76959f67fe944330a50a276))
- Add strings and string concatenation ([7980837](https://github.com/polybuildr/balloon-lang/commit/79808378dcb4a581fe0d2a48cc99046fee9716d5))
- Another set of refactoring commits
- Add support for tuples (basically, immutable lists) ([76cb3b5b](https://github.com/polybuildr/balloon-lang/commit/76cb3b5b16a1c237812221761d6cce5fcde476a8))
- Add a basic http server using Rust's TcpListener and TcpStream ([9e7bdefa3](https://github.com/polybuildr/balloon-lang/commit/9e7bdefa313c1f9697215de920fa9f28ce79dca1))
- Add a stack trace-like thing in error messages ([642bfb00](https://github.com/polybuildr/balloon-lang/commit/642bfb0087e46589cc9248e146d9c0b26d71f099))
- Implement member access by index for tuples ([696a794](https://github.com/polybuildr/balloon-lang/commit/696a794eb93945fbc659a723e5c402cfd125326e))
  
  Also did a sorely needed refactor of grammar - allowing for expressions like `expr(x)[0](y)[1]`
- Typecheck function bodies with parameter types from call sites ([19f63718](https://github.com/polybuildr/balloon-lang/commit/19f6371851ccf131e918fb5983f4ad5482272bf6))
