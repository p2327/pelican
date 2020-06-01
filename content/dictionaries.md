title: Counting with dictionaries in Python
slug: pythondictionaries
category: python
date: 2020-06-01
modified: 2020-06-01


There's various way to count dictionaries in Python.

Let's start with an intuitive example:
```python
colors = ['red'
         ,'green'
         ,'blue'
         ,'green'
         ,'blue'
         ,'green'
         ,'blue'
         ,'red'
         ]

d = {}
for color in colors:
    if color not in d:
        d[color] = 0
    d[color] += 1
```

Here we iterate over our colors, initialise them as keys in our dictionary with value 0 and 
add 1 each team we encounter a specific colour. Intuitive, but slow and not beautiful.

How can we do better? Using [get](https://docs.python.org/3/library/stdtypes.html#dict).
`get` takes two arguments, a key and a *default value*, and returns the key if it exists in the dictionary otherwise the default:
```python
d = {}
for color in colors:
    d[color] = d.get(color, 0) + 1
```
Much cleaner!

Is there a more modern way? Yes, using `defaultdict`.
```python
from collections import defaultdict

d = defaultdict(int)
for color in colors:
    d[color] += 1
```
What is happening here? [Default dictionaries](https://docs.python.org/3.8/library/collections.html#collections.defaultdict) use a *default_factory* argument which gets called (with no arguments) to provide a default value for a given key. In other words, when a key is encountered for the first time an entry is created using the factory function.


Note that in this instance we'll end up with a default dictionary object which is not the same as a Python dictionary and might require converting back to that type in your program, so use responsibly!