---
description: Friendliness • Safety • Productivity
---

# First Principles

## Friendliness / Human Factors

> People are part of the system. The design should match the user's experience, expectations, and mental models.
>
> ~Saltzer & Kaashoek, [Principles of Computer System Design](https://dl.acm.org/citation.cfm?id=1594884)

> The origin of "easy" implies "nearness". Something that is near can be easily touched or grabbed.
>
> — Rich Hickey, [Simple Made Easy](https://www.infoq.com/presentations/Simple-Made-Easy/)

> Any fool can write code that a computer can understand. Good programmers write code that humans can understand.
>
> — Martin Fowler, [Refactoring](https://martinfowler.com/books/refactoring.html)

Development tools should be helpful, friendly, robotic pair-programming assistants. You should be left with a sense of productivity, achievement, and confidence. Programming should be a joy. No one wants to get paged at 3am that the server has gone down, or spend a full day debugging some very deep Type Tetris.

Despite popular opinion, it can be done! Look at Elm, well loved and influential, and about 80% of the way to being Haskell. It is not uncommon to hear a desire for there to be an "Elm for the Back End".

### Invariants

### Principle of Least Astonishment

### Pave the Cow Paths

There are things that people do over and over again. This is signal that it's a desrable trait. Make those patterns as easy to express as possible. We have the advantage that we have both a black slate and essentially unbounded abstraction. We can build features directly into the toolchain.

### Make Good Practice Obvious

Without ruling with an iron fist, make the affordances of the language lead to the best 

### Orthogonality

Prefer composition to additional parameters. Infixity can be expressed as pipes.

### Metaphor

Data flow is a powerful metaphor

### Interactive Development

A helpful tool chain can make the difference between The compiler \(and other tools\) should be your friend, not your enemy! Interactive development in the style of Idris

### Ergonomics

### Learnable

### 

## Safety

> One of Haskell’s core tenets is making illegal states unrepresentable
>
> ~ Alexis King, [An Opinionated Guide to Haskell in 2018](https://lexi-lambda.github.io/blog/2018/02/10/an-opinionated-guide-to-haskell-in-2018/)

Haskell is great at eliminating huge classes of bugs without much boilerplate.

### Make Error States Unrepresentable

fjdskla

### Supervision

Safety goes beyond universals. There will be bugs: there may be an OS-level error, cosmic rays may flip a bit in your RAM chip, or there may be a successfully typechecked business-logic error.

## Productivity

The _meaning_ of code should be easy to comprehend. This is a rather wooly statement, so to clarify, it refers to 

### Consistency

This is something that Haskell 2010 is remarkably good at. The syntax is very clear and always used in a consistent way. For instance:

```haskell
class Functor f => Applicative f where
  -- ...

instance Applicative (Maybe a) where
  -- ...
  
foo :: Applicative f => a -> f a
foo x = -- ...
```

### Error Messages

Elm and Rust have some of the best error messages around. Imagine not only getting the line number and type error, but also an explication of why this situation typically happens, 

### Maintainability

Nothing kills productivity like a painful refactor, crufty code, &c

### Make It Right

> Don’t optimize your code at the first stage. First make it right, then \(if necessary\) make it fast \(while keeping it right\).
>
> — Joe Armstrong, [Making Reliable Distributed Systems in the Presence of Software Errors](https://erlang.org/download/armstrong_thesis_2003.pdf)

Step one in programming is getting your program to perform a task to spec. Haskell has a ton of performance headroom. It's far more performant than a garbage collected, lazy, high-level, functional language has any right to be.



