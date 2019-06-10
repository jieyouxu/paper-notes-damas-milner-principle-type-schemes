Notes on the paper [L. Damas, R. Milner - Principal type-schemes for functional programs](http://steshaw.org/hm/milner-damas.pdf) [Damas 1982]

---

## Introduction

- The paper is based on *polymorphic type discipline* of [ML](http://www.cs.unc.edu/~stotts/144/ML/).
- Aims to show that the *type assignment algorithm* in [Milner 1978]:
  - Finds the **most general type possible**, for every *expression* and *declaration*.

Finding the most general type possible allows:

- **Flexibility** (from polymoriphism), and
- **Robustness** (from semantic soundness), and
- **Detection of errors at compile time**.

An example is given for the `map` function in ML:

```ml
map f [x1; ...; xn] = [f(x1), ..., f(x_n)]
letrec map f xs =
	if null s then nil
	else cons(f (hd s)) (map f (tl s))
```

Or in Haskell, with the `ExistentialQuantification` type system extension,

```haskell
{-# LANGUAGE ExistentialQuantification #-}

-- An alias for empty lists
nil :: forall a . [a]
nil = []

-- `cons` is `(:)`
-- `tail` and `head` are replaced by equivalent pattern matching
map :: forall a b . (a -> b) -> [a] -> [b]
map f [] = []
map f (x:xs) = f x : map f xs
```

That is, the **type-scheme** (since objects are polymorphic) of `map` being

```haskell
map :: forall a b . (a -> b) -> [a] -> [b]
```

Is deduced by the type checker from the type-schemes of

```haskell
null :: forall a . [a] -> Bool
nil :: forall a . [a]
-- cons == (:)
cons :: forall a . a -> [a] -> [a]
head :: forall a . [a] -> a
tail :: forall a . [a] -> [a]
```

**Types** are build from:

- **Type constants**: `Bool`, ...
- **Type variables**: `a`, `b`, ...
- Using **type operators**, such as
  - *Function*`->`
  - *List* `[$]` of elements of type `$`.

A **type-scheme** is a **type** with (*optional*) **quantification** of **type variables** at the outermost.

*Recursion* and *condition* is omitted. Recursion can be introduced by the polymorphic *fixed-point combinator*

```haskell
fix :: forall a . (a -> a) -> a
```

## Language

Let there be a set `Id` of identifiers `x`, then the language `Exp` of expressions `e` is defined by the syntax

```haskell
e ::= x
	|		e e'
	|   \x -> e
	| 	let x = e in e'
```

The last clause extends λ-calculus.

## References

**[Damas 1982]** Damas, L. and Milner, R. 1982. Principal type-schemes for functional programs. *Proceedings of the 9th ACM SIGPLAN-SIGACT symposium on Principles of programming languages - POPL 82*(1982). DOI:http://dx.doi.org/10.1145/582153.582176.

**[Milner 1978]** Milner, R., 1978. A theory of type polymorphism in programming. *Journal of Computer and System Sciences*, 17(3), pp.348-375.

