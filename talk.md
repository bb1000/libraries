
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


~~~
>>> now = datetime.datetime(2026, 4, 13, 9, 15)
>>> now
datetime.datetime(2026, 4, 13, 9, 15)
>>> print(now)
2026-04-13 09:15:00

~~~
