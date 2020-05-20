title: Purescript
slug: ps1
category: purescript
date: 2020-05-13
modified: 2020-05-13


Recently I started learning [Purescript](https://try.purescript.org/?session=4500d0d8-e031-d39d-293e-96552663338c)

In this series of posts we'll write simple programs to familiarise ourselves with Purescript's syntax while looking at functional programming concept and patterns. We'll use the exercises in [Exercism](https://exercism.io/my/tracks/purescript).

As a first program we'll write the classic `"Hello, World!"`.

Here's two implementations, full code on [Github]().

```purescript
-- | Using case expressions
helloWorld :: Maybe String -> String
helloWorld name = case name of
    Just name -> "Hello, " <> name <> "!"
    Nothing -> "Hello, World!"

-- | Using fromMaybe
helloWorld' :: Maybe String -> String
helloWorld' name = "Hello, " <> fromMaybe "World!" name
```

Let's talk a bit more about case expressions and `Maybe` values.

*TODO*

One feature of Purescript are `newtypes`, so that we can be sure our code is type-safe by using types to give extra meaning to an existing primitive type.
```purescript
newtype Name = Name String
```



*TODO*