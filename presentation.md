# Haskell

--> A deep dive nobody asked for

---

## What is Haskell?

- Functional programming language
- Est. 1990 
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

## Functions

- Functions in mathematical sense
- No side-effects (usually)
- Monads 🧠
- Currying 🍛

### IO Monad

```hs
readConfig :: IO String
readConfig = do
  contents <- readFile "config.yaml"
  return contents
```

Can only ever call `log` in another function that returns `IO ()`

### Maybe Monad

```hs
safeDivision :: Float -> Float -> Maybe Float
safeDivision _ 0 = Nothing
safeDivision a b = Just (a `div` b)
```

```hs
divide4By = safeDiv 4
divide4By 2 -- Just 2
```

---

## Lazy execution

Expression only evaluates when the result is required.

```diff
+ Deals with infinite data-structures
+ Allows for compiler-level optimizations
- Can make profiling hard
```

<!-- TODO: Needs a bit more content -->

---

## Immutability

> "An object is immutable when its state doesn't change after it has been initialized" 🤓

- No in-place value changing
- Always deep-copying (sort of)

Haskell:

```haskell
replaceAtIndex [] _ _ = []
replaceAtIndex (x:xs) 0 newVal = newVal:xs
replaceAtIndex (x:xs) n newVal = x:replaceAtIndex xs (n-1) newVal

relaceAtIndex [1,2,3] 2 5 -- [1,2,5]
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

## Provability

- Category theory
- Curry-Howard correspondence
- Provable programs
- Provers:
  - Coq
  - Lean
  - Agda

---

## Pattern Matching

- Easy destructuring
- Easy recursion
- Exhaustiveness checking

### Destructuring Maybe

```haskell
printIfHasValue:: Show a => Maybe a -> IO ()
printIfHasValue (Just x) = print x
printIfHasValue Nothing = return ()
```

---

## Loops

- No loops
- Not one
- Anywhere

---

## Recursion

- Only way to "loop"
- Tail-call optimization

```haskell
factorial :: Int -> Int
factorial 0 = 1
factorial n = n * factorial (n - 1)
```

---

## Performance

- Slow compilation 🐢
- LLVM compiled
- No runtime
- Garbage collected
- Ridiculously fast execution 🚀
    - Laziness
    - Immutability
    - Purity
    - Type system
- Optimization options

---

## Real-World Applications

- Not a lot of business-world applications
- Mostly used for research, compilers and parsers
- Notable usages:
  - Facebook spam filter
  - Hasura GraphQL engine
  - Cardano blockchain
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
