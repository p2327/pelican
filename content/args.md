title: *args and **kwargs in Python
slug: argskwargs
category: python
date: 2020-05-20
modified: 2020-05-20



Today we are looking at `*args*` and `**kwargs*`. In Python this special syntax used in function definitions indicates it is possible to pass a variable number of arguments to the function.

- `*args*` is used to pass a *non-keyworded*, variable-length argument list
- `**kwargs*` is used to pass a keyworded, variable-length argument list.

What does this mean? Let's look at some examples:


```python
def test_var_args(an_arg, *args):
    print("standard argument:", an_arg)
    for index, argument in enumerate(args):
        print(f"variable argument {index}:", argument)

def test_var_kwargs(an_arg, **kwargs):
    print("standard argument:", an_arg)
    for argument in kwargs.values():
        print("variable argument:", argument)
```

If we run the above functions in a repl, we get:
```
>>> test_var_args(1, [1, 2, 3], "a string", 7.0, "words")
standard argument: 1
variable argument 0: [1, 2, 3]
variable argument 1: a string
variable argument 2: 7.0
variable argument 3: words

>>> test_var_kwargs(1, a=[1, 2, 3], b="a string", c=7.0, d="words") 
standard argument: 1
variable argument: [1, 2, 3]
variable argument: a string
variable argument: 7.0
variable argument: words
```

What we are doing is using the *unpacking operators*, `*` and `**`. A single asterisk unpacks iterables, while double asteriks unpack dictionaries (Python's key-value pair data structure).
