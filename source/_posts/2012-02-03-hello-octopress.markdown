---
layout: post
title: "Hello octopress"
date: 2012-02-03 16:22
comments: true
categories: 
---

I'm starting with a clean slate and moving to [Octopress](http://octopress.org/).

Haskell source code highlighting appears to work out of the box:

``` haskell Expression evaluator, compiler and interpreter
data Expr
  = Val Int
  | Add Expr Expr
  deriving (Show)

eval :: Expr -> Int
eval (Val n)   = n
eval (Add x y) = eval x + eval y

type Code = [Op]
data Op
  = PUSH Int
  | ADD
  deriving (Show)

comp :: Expr -> Code
comp (Val n)   = [PUSH n]
comp (Add x y) = comp x ++ comp y ++ [ADD]

exec :: Code -> Int
exec = exec' []
  where
    exec' [result] []                = result
    exec' stack (PUSH n : cs)        = exec' (n : stack) cs
    exec' (a : b : stack) (ADD : cs) = exec' (a + b : stack) cs
```

as does Scala:

``` scala
import scala.collection.mutable

def countWords(text: String) = {
  val counts = mutable.Map[String, Int]()
  for (word <- text.split("[ ,!.]+")) {
    val lowerWord = word.toLowerCase
    val oldCount = counts.getOrElse(lowerWord, 0)
    counts(lowerWord) = oldCount + 1
  }   
  counts
}   
    
val text = "See Spot run. Run, Spot. Run!"

countWords(text) foreach println
```
