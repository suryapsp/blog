---
title: "MUPL(Made Up Programming Language)"
date: 2023-08-07T12:46:12+05:30
---

MUPL(Made Up Programming Language) is a simple programming language interpreter implemented in Racket.

## Features
MUPL supports the following features for now.

```racket
variable
addition
integer
ifgreater
functions
pair
null
closures
lexical scope
```

## Syntax

```racket
(var  (string))                        ;; a variable, e.g., (var "foo")
(int  (num))                           ;; a constant number, e.g., (int 17)
(add  (e1 e2))                         ;; add two expressions
(ifgreater (e1 e2 e3 e4))              ;; if e1 > e2 then e3 else e4
(fun  (nameopt formal body))           ;; a recursive(?) 1-argument function
(call (funexp actual))                 ;; function call
(mlet (var e body))                    ;; a local binding (let var = e in body) 
(apair (e1 e2))                        ;; make a new pair
(fst  (e))                             ;; get first part of a pair
(snd  (e))                             ;; get second part of a pair
(aunit ())                             ;; unit value
(isaunit (e))                          ;; evaluate to 1 if e is unit else 0
(closure (env fun))                    ;;closures
```
## Source Code
The [Source Code](https://raw.githubusercontent.com/suryapsp/mupl/master/src/mupl.rkt) of MUPL is easy to understand if you have some idea about racket or any lisp like programming language.



