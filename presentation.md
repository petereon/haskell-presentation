# Haskell (syntax guide)

A deep-dive nobody asked for.

---

```







██╗    ██╗██╗  ██╗██╗   ██╗    ██╗  ██╗ █████╗ ███████╗██╗  ██╗███████╗██╗     ██╗   ██████╗ 
██║    ██║██║  ██║╚██╗ ██╔╝    ██║  ██║██╔══██╗██╔════╝██║ ██╔╝██╔════╝██║     ██║   ╚════██╗
██║ █╗ ██║███████║ ╚████╔╝     ███████║███████║███████╗█████╔╝ █████╗  ██║     ██║     ▄███╔╝
██║███╗██║██╔══██║  ╚██╔╝      ██╔══██║██╔══██║╚════██║██╔═██╗ ██╔══╝  ██║     ██║     ▀▀══╝ 
╚███╔███╔╝██║  ██║   ██║       ██║  ██║██║  ██║███████║██║  ██╗███████╗███████╗███████╗██╗   
 ╚══╝╚══╝ ╚═╝  ╚═╝   ╚═╝       ╚═╝  ╚═╝╚═╝  ╚═╝╚══════╝╚═╝  ╚═╝╚══════╝╚══════╝╚══════╝╚═╝   
```

---

Benefits:

- High-level
- Safe
- Elegant
- Performant
- Gives arcane powers (?)

Drawbacks:

- Development productivity (at the beginning)

---

```hs
main = putStrLn "Hello, World!"
```
---

## Loops

Ha, sike

---

## Recursion


```hs
map :: (a -> b) -> [a] -> [b]
map _ [] = []
map fn (e: rest) = fn e : (map fn rest)
```

```hs
map (+ 2) [1, 2, 3, 4]
--- [3, 4, 5, 6]
```

---

## Pattern-matching

Count leaves:

```
     •
    / \
   /   \
  •     \
 / \     •
•   •   / \
       •   \
            •
           / \
          •   •
```

---

## Lazy evaluation

- Deals with infinite structures
- Allows for optimizations

```hs
sumUntilFive :: [Int] -> Int
sumUntilFive list = case head list of
    5 -> 5
    a -> a + sumUntilFive (tail list)

main = print $ sumUntilFive [1..]
```

---

## Purity

---
