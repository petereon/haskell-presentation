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
- Lazy evaluation
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
- No assignments (kinda)
- No statements
- No loops

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

Can only ever call `readConfig` in another function that deals with `IO a`

### Maybe Monad

```hs
safeDivision :: Float -> Float -> Maybe Float
safeDivision _ 0 = Nothing
safeDivision a b = Just (a `div` b)
```

### Currying

```hs
divide4By = safeDivision 4
divide4By 2 -- Just 2
```

---

## Lazy Evaluation

Expression only evaluates when the result is required.

```diff
+ Deals with infinite data-structures
+ Allows for compiler-level optimizations
- Can make profiling hard
```

### Example (lazy evaluation makes debugging a living hell)

#### Haskell

```hs
add a b = a + a
add 10 (3/0) -- 20
```

#### Python

```python
add = lambda a, b: a + a
add(10, (3/0)) # ZeroDivisionError: division by zero
```

---

## Immutability

> "An object is immutable when its state doesn't change after it has been initialized" 🤓

- No in-place value changing
- Always deep-copying (sort of)

```haskell
replaceAtIndex [] _ _ = []
replaceAtIndex (x:xs) 0 newVal = newVal:xs
replaceAtIndex (x:xs) n newVal = x:replaceAtIndex xs (n-1) newVal

relaceAtIndex [1,2,3] 2 5 -- [1,2,5]
```

---

## Algebraic Type System
### Characteristics

- Strong
- Allows polymorphism
- Allows algebraic types
  - Unions (`String | Int`)
  - Tuples (`(String, Int)`)
  - Unit (`()`), Void (`Void`)
- Automatic type inference

Fun side effects:

```haskell
absurd :: Void -> a
```

---

## Algebraic Type System
### Provability

- Category Theory
- Curry-Howard correspondence (mapping between type system and FOL) --> Provable programs

Proof assistants:
  - Coq
  - Lean
  - Agda


`lean` example:
```lean
theorem p1 : (P -> Q) -> (¬ Q -> ¬ P) :=
begin
    assume pq,
    assume nq,
    assume p,
    apply nq,
    apply pq,
    exact p,
end
```

---

## Pattern Matching

- Destructuring on steroids
- Easy recursion
- Exhaustiveness checking

### Destructuring Maybe

```haskell
printIfHasValue:: Maybe String -> IO ()
printIfHasValue (Just x) = print x
printIfHasValue Nothing = return ()
```

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
  - Elm compiler
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
