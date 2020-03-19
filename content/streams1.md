title: Streams
slug: streams
category: programming
date: 2020-03-19
modified: 2020-03-19


Today we are looking at streams, a way to represent sequential data *implicitly*. What is a stream? A stream is a lazily computed linked list.

Let's design a class to achieve this lazy evaluation: 

```python
class Stream:
        """
        A lazily computed linked list.
        """
        class empty:
            def __repr__(self):
                return 'Stream.empty'
        empty = empty()

        def __init__(self, first, compute_rest=lambda: empty):
            assert callable(compute_rest), 'compute_rest must be callable.'
            self.first = first
            self._compute_rest = compute_rest

        @property
        def rest(self):
            """
            Return the rest of the stream, 
            computing it if necessary.
            """
            if self._compute_rest is not None:
                self._rest = self._compute_rest()
                self._compute_rest = None
            return self._rest
        def __repr__(self):
            return 'Stream({0}, <...>)'.format(repr(self.first))
```


We will use this to build a small program that calculates prime numbers.


*TODO*