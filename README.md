# pyinternals

A visualizer for Python object layout in CPython.

This package provides tools to directly inspecting Python objects through their C-level structure using `ctypes`.
This is a powerful approach for deep object introspection, especially when you need to examine the internal memory representation of Python objects like `int`, `float`, `str`, `list`, `dict` and custom classes.


## Features

- Inspect memory layout of Python objects.
- Visualize CPython object internals like `__dict__`, `__slots__`, methods, and more.
- Great for learning how CPython manages memory.

## Installation

Install via pip:

```bash
pip install pyinternals
```
## Examples

To inspect `int` we can use `inspect_int` or `inspect_obj` for brevity.

```python

>>> from pyinternals import inspect_int

>>> inspect_int(78)
```
```

#---> Int at 0x1005b5310:
----------------------------------------
Field           | Value
----------------------------------------
Reference count | 10
Type address    | 0x1004dfd50
Size            | 1

Digits (base 2^30):
  ob_digit[0]   | 78
----------------------------------------
```

To inspect dictionary objects we can use `inspect_dict` or `inspect_obj`

```python

>>> from pyinternals import inspect_dict
>>> inspect_dict({'x':12, 'y': 34})
````
```
---> Dict at 0x101bb6c00:
----------------------------------------
Field           | Value
----------------------------------------
Reference count | 2
Type address    | 0x1004eaac0
Used            | 2
Keys            | 0x101a915b0
Values **(combined)** | None

  Contents:
    'x': 12
    'y': 34
----------------------------------------

```
Comined above means keys and values are stored in the dict, The other option is split where keys of the dict are shared. see: [PEP 412 -- Key-Sharing Dictionary](https://www.python.org/dev/peps/pep-0412/)

## Learning materials

- CPython implementation : https://github.com/python/cpython
- Cpython Internals repository: https://github.com/zpoint/CPython-Internals