
# Haskell

--> A deep dive nobody asked for 


---

## What is Haskell?

- Functional programming language
- Turing complete
- General purpose (❓)
- Based on lambda calculus
- Influenced by ML (Standard ML, OCaml, F#, etc ...)

What sets it apart:

- Pure functions
- Immutability
- Lazy execution
- Algebraic type-system
- Pattern-matching

---

```
██╗    ██╗██╗  ██╗██╗   ██╗    ██╗  ██╗ █████╗ ███████╗██╗  ██╗███████╗██╗     ██╗   ██████╗ 
██║    ██║██║  ██║╚██╗ ██╔╝    ██║  ██║██╔══██╗██╔════╝██║ ██╔╝██╔════╝██║     ██║   ╚════██╗
██║ █╗ ██║███████║ ╚████╔╝     ███████║███████║███████╗█████╔╝ █████╗  ██║     ██║     ▄███╔╝
██║███╗██║██╔══██║  ╚██╔╝      ██╔══██║██╔══██║╚════██║██╔═██╗ ██╔══╝  ██║     ██║     ▀▀══╝ 
╚███╔███╔╝██║  ██║   ██║       ██║  ██║██║  ██║███████║██║  ██╗███████╗███████╗███████╗██╗   
 ╚══╝╚══╝ ╚═╝  ╚═╝   ╚═╝       ╚═╝  ╚═╝╚═╝  ╚═╝╚══════╝╚═╝  ╚═╝╚══════╝╚══════╝╚══════╝╚═╝   
```

### Benefits 📈

- High-level
- Safe
- Performant
- Productive
- Pathway to many abilities some consider to be unnatural

### Drawbacks 📉

- Performance
- Productivity

---

## Hello World

```hs
main = putStrLn "Hello, World!"
```
### Syntax

- Small amount of syntax
- Few keywords
- No variables (kinda 🤷)
- No statements
- No loops
- No assignments (kinda)

--> Everything is an expression

---

## Pure functions

- Functions in mathematical sense (functor)
- No side-effects (usually)
- Monads 🧠

### IO Monad

```hs
log :: String -> IO ()
log s = putStrLn s
```
Can only ever call `log` in another function that returns `IO ()`

### Maybe Monad

```hs
safeDiv :: Float -> Float -> Maybe Float
safeDiv _ 0 = Nothing
safeDiv a b = Just (a `div` b)
```

---

## Lazy execution

Expression only evaluates when the result is required.

- Deals with infinite data-structures
- Allows for optimizations
- Can make profiling hard


---

## Immutability

> "An object is immutable when its state doesn't change after it has been initialized" 🤓

- No in-place value changing
- Always deep-copying

Python:

```python
a = [1,2,3]
a[2] = 5
```

Haskell:

```haskell
let a = [1,2,3]
let a = take 2 a ++ [5]
```

---

## Algebraic type system

- Strong
- Allows polymorphism
- Allows algebraic types
    - Unions (`String | Int`)
    - Tuples (`(String, Int)`)
    - etc ...
- Automatic type inference

Fun side effects:

```haskell
absurd :: Void -> a
```

---

## Pattern Matching

- Easy destructuring
- Easy recursion

### Destructuring Maybe

```haskell
printIfHasValue:: Maybe a -> IO ()
printIfHasValue (Just x) = print x
printIfHasValue Nothing = print "x is Nothing"
```

---
## Recursion

- Only way to loop
- Tail-call optimization

```haskell
factorial :: Int -> Int
factorial 0 = 1
factorial n = n * factorial (n - 1)
```

---

## Real-World Applications

- Not a lot of business-world applications
- Mostly used for research, compilers and parsers
- Notable usages:
    - Facebook spam filter
    - Hasura GraphQL engine
    - GHC (Haskell compiler)

---

## Conclusion
- Fun 💪
- Useless 🥲

---

## Questions?

---

## Resources


[Haskell for Imperative Programmers](https://www.youtube.com/watch?v=Vgu82wiiZ90&list=PLe7Ei6viL6jGp1Rfu0dil1JH1SHk9bgDV)
- Video Series
- Easy going
- Includes exercises

[Category Theory for Programmers](https://bartoszmilewski.com/2014/10/28/category-theory-for-programmers-the-preface/)
- Website
- Category theory focused
- Very math heavy
- Includes exercises

[Learn You a Haskell for Great Good!](http://learnyouahaskell.com/)
- Book
- Easy going
- Inaccurate at times