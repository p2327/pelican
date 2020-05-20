title: Purescript
slug: ps1
category: purescript
date: 2020-04-13
modified: 2020-04-13


Today I have started working on a web app using the science questions dataset from the Allen AI Institute - grab it [here](https://allenai.org/data?tag=Aristo).

We'll be using Python/Flask for the backend and Purescript for the frontend.

Purescript is a functional programming (FP) language first appeared in 2013. For a gentle introduction to FP I recommend [this Gitbook](https://drboolean.gitbooks.io/mostly-adequate-guide-old/content/ch1.html#a-brief-encounter), this short [video course](https://egghead.io/courses/functional-programming-concepts-in-purescript) and this [blog](https://mmhaskell.com/purescript). 

The official language book is also [excellent](https://github.com/purescript-contrib/purescript-book) and the [online playground](http://try.purescript.org/) is a fantastic resource to try the language out.

Here's a short script:

```purescript
module Main where

import Prelude
import Control.Monad.Eff.Console (log)
import TryPureScript

addMe :: Int -> Int -> Int
addMe = \a -> \b -> a + b

main = render =<< withConsole do
  log $ show $ addMe 5 5
```

More on this project soon.