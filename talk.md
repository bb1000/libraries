
# Libraries


---

* The builtins
* The standard library
* Third-party libraries (PyPI)

## The builtins

* functions, types, and constants that are always available e.g.
    - functions: print, len
    - types: int, float, str, list, set, dict, tuple
    - constants: True, False, None

---

## The standard library

a minimal tour of commonly used modules

* General reference : https://docs.python.org/3/library/index.html
* A wide collection of modules and packages that come with Python
* Libraries that are not builtin but are always available via the `import` statement


Examples:

- `math` for mathematical functions
- `datetime` for date and time manipulation
- `os` for operating system interfaces
- `sys` for system-specific parameters and functions
- `json` for JSON encoding and decoding
- `re` for regular expressions

---

### The math module

* Provides mathematical elmentary functions and constants

~~~
>>> import math
>>> dir(math)
[...'acos', 'acosh', 'asin', 'asinh', 'atan', 'atan2', 'atanh', 'cbrt', 'ceil', 'comb', 'copysign', 'cos', 'cosh', 'degrees', 'dist', 'e', 'erf', 'erfc', 'exp', 'exp2', 'expm1', 'fabs', 'factorial', 'floor', 'fma', 'fmod', 'frexp', 'fsum', 'gamma', 'gcd', 'hypot', 'inf', 'isclose', 'isfinite', 'isinf', 'isnan', 'isqrt', 'lcm', 'ldexp', 'lgamma', 'log', 'log10', 'log1p', 'log2', 'modf', 'nan', 'nextafter', 'perm', 'pi', 'pow', 'prod', 'radians', 'remainder', 'sin', 'sinh', 'sqrt', 'sumprod', 'tan', 'tanh', 'tau', 'trunc', 'ulp']

~~~

~~~
>>> import math
>>> math.pi
3.141592653589793
>>> math.sqrt(81)
9.0

~~~

---

### datetime

* Provides datatypes for manipulating dates and times

~~~
>>> import datetime
>>> dir(datetime)
[..., 'date', 'datetime', 'datetime_CAPI', 'time', 'timedelta', 'timezone', 'tzinfo']

~~~

* note that the `datetime` module has a `datetime` datatype : `datetime` (confusing)


~~~
>>> now = datetime.datetime(2026, 4, 13, 9, 15)
>>> now
datetime.datetime(2026, 4, 13, 9, 15)
>>> print(now)
2026-04-13 09:15:00

~~~

---

### os

* Various operating system features

~~~
>>> import os
>>> os.getenv("USER") # get current working directory
'olav'
>>> os.getenv("HOME") # get home directory
'/home/olav'
>>> os.makedirs("a/b/c", exist_ok=True)

~~~
~~~bash
$ tree a
a
└── b
    └── c

3 directories, 0 files
0
~~~

`os.path` is a subpackage related to file path manipulation, but it is
preferred to use the more modern `pathlib` module instead for this.

---

### sys

* System-specific parameters and functions
* `sys.argv` is a list of command-line arguments passed to the script
* `sys.stdin` for standard input (normally keyboard)
* `sys.stdout` for standard output (normally terminal)

---

### collections

* High-performance container datatypes

~~~
>>> import collections

~~~

#### namedtuple

* `namedtuple` tuple-like datatype with named fields

c.f normal tuple vs. namedtuple

~~~
>>> book = ("Automate the Boring Stuff with Python", "Al Sweigart", 2015)
>>> book[1]
'Al Sweigart'

~~~
~~~
>>> Book = collections.namedtuple("Book", "title author year")
>>> book = Book("Automate the Boring Stuff with Python", "Al Sweigart", 2015)
>>> book.author
'Al Sweigart'

~~~


#### Counter

* simplifies counting of objects

~~~
>>> collections.Counter('ABBA')
Counter({'A': 2, 'B': 2})
>>> collections.Counter('hello hello'.split())
Counter({'hello': 2})

~~~

#### defaultdict

* simplifies handling of missing keys in dictionaries
* provides a default value for missing keys

~~~
>>> normaldict = {}
>>> normaldict.get('key')

~~~

~~~
>>> defaultdict = collections.defaultdict(list)
>>> defaultdict['key'].append('value')
>>> defaultdict
defaultdict(<class 'list'>, {'key': ['value']})

~~~

---

### functools

* Higher-order functions and operations on functions

#### partial

* Creates a new function with some arguments fixed

~~~
>>> import functools
>>> print1 = functools.partial(print, sep='\n')
>>> print1("Hello", "World")
Hello
World

~~~

#### cache

* Save results of previous called that can be recalled with same arguments
<!--
~~~
>>> def slow_function(x):
...     pass

~~~
-->

~~~
>>> slow_function = functools.cache(slow_function)
>>> slow_function(10) # takes a long time
>>> slow_function(10) # returns immediately with cached result

~~~

---

### argparse

* Parse command-line arguments insted of handling  `sys.argv` directly
* Automatic help generation

In script:

~~~
#hello.py
import argparse
parser = argparse.ArgumentParser(description="A simple script")
parser.add_argument("name", help="Your name")
parser.add_argument("--age", type=int, help="Your age")
args = parser.parse_args()
print(args)
~~~

In terminal:
~~~bash
$ python hello.py -h
usage: hello.py [-h] [--age AGE] name
$ python hello.py Alice --age 30
Namespace(name='Alice', age=30)

~~~

### csv
~~~
>>> import csv

~~~
* Handling of tabular data in CSV (comma-separated-values) format 

prices.csv
~~~
item,price_per_item,number_of_items
apple,0.5,1
banana,0.3,2
orange,0.7,4
~~~

~~~
>>> for line in csv.reader(open("prices.csv")):
...     print(line)
['item', 'price_per_item', 'number_of_items']
['apple', '0.5', '1']
['banana', '0.3', '2']
['orange', '0.7', '4']

~~~

~~~
>>> for line in csv.DictReader(open("prices.csv")):
...     print(line)
{'item': 'apple', 'price_per_item': '0.5', 'number_of_items': '1'}
{'item': 'banana', 'price_per_item': '0.3', 'number_of_items': '2'}
{'item': 'orange', 'price_per_item': '0.7', 'number_of_items': '4'}

~~~

