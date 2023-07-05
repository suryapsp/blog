---
title: "Currying in SML(Standard ML)"
date: 2023-07-05T18:42:01+05:30
---

## What is Currying?
Currying is a [closure idiom](https://en.wikipedia.org/wiki/Closure_(computer_programming)) named after a famous logician [Haskell Curry](https://en.wikipedia.org/wiki/Haskell_Curry). Currying means taking a function which takes in an argument and then return return the function which takes in an other argument and it keeps on going until it evaluates the whole program.

### Normal Way of Writing a Sum Function
```sml
fun sum (x, y, z) =
    x + y + z

val sixty = sum(20,20,20)
```
This is the normal way of writing a sum function also known as the tupled way of writing function.

### The Curried Way
```sml
fun sum x =
    fn y => 
        fn z => 
            x + y + z

val sixty = ((sum 20) 20) 20
```
This is a Curried function here sum takes in an argument x that returns an anonymous function which takes in an argument y that returns an anonymous function which takes in an argument z and this anonymous functions sums all the number.

(sum 20) return the closure fn y => fn z => x + y + z. Where x maps to 20.

Calling that Closure with 20 again returns a closure fn z => x + y + z. Where x maps to 20 and y also maps to 20.

Calling that closure with 20 again returns 60.

There is some syntactic sugar as well for Currying provided by SML(Standard ML) but I am not gonna cover that in this post because I wanna keep this post more abstract.

### Some Other Useful Resources
- [Currying by Dan Grossman (highly recommended)](https://youtu.be/mQztHT2OLCE)
- [Currying Wikipedia](https://en.wikipedia.org/wiki/Currying)