---
title: Ad Hoc Polymorphism
subtitle: >
  Some work-in-progress thoughts on polymorphism via mixins vs. via traits/protocols/etc.
tags:
  - JavaScript
  - TypeScript
  - Rust
  - Haskell
  - Swift

---

There are three basic strategies for supplying shared behavior to data types in modern programming languages:

- inheritance
- delegation
- ad hoc polymorphism

Inheritance is the most common of these, native to C++, Java, C#, JavaScript, Python, Ruby, PHP, and many others. All the languages which support it also trivially support delegation. The weird one here is “ad hoc polymorphism”: the name for Rust’s traits, Swift’s protocols, and Haskell’s type classes.[^others] The received wisdom for many years has been to “prefer composition over inheritance.” Following that advice, makes both delegation and ad hoc polymorphism are generally more attractive than inheritance.[^inheritance-alternative]

However, there is another variant in the space of inheritance which often stands in for both delegation and ad hoc polymorphism: *multiple inheritance* (often under the name of “mixins”).

[^others]: There are other languages which have ad hoc polymorphism, but these three are the most prominent and mainstream.

[^inheritance-alternative]: Perhaps the most interesting alternative approach to any of these I’ve run across is in Jon Goodwin’s [Cone](https://cone.jondgoodwin.com), which has [a bunch of interesting ideas about inheritance](https://pling.jondgoodwin.com/categories/inheritance/).