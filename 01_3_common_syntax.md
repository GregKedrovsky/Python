# Common Syntax Structures

## Contents
- [Assignment Statements](
- [Console Input](
- [Iteration Keywords](
- [Selection](
- [Repetition](
- [Traversal](
- [Function Definition](
- [Function Call](
- [Class Definition](
- [Object Instantiation](
- [Method Invocation](
- [Exception Handling](
- [Prevent Module Execution on Import](

## Assignment Statements
```
var = exp                # assigns exp to var variable
var1, var2 = exp1, exp2  # assigns exp to var in sequence
list1[index] = value     # assign value to index in list
dict1[key] = value       # assign value to key in dictionary
```

## Console Input
```
var = input( [prompt] )            # Python 3
var = input( "Type something: " )
var = raw_input( [prompt] )        # Python 2
```

## Iteration Keywords
```
pass      # does nothing; placeholder for future statements
continue  # stop current iteration & return to the top to continue with next iteration
break     # jumps out of enclosing loop (for || while)
```

## Selection: if
```
if (boolean_exp):      #  or
if not(boolean_exp):
  stmt...
elif (boolean_exp):    # zero or more elif (else if) stmts
  stmt...
else:                  # else is optional
  stmt...
```

### Example: 
```
>>> x = int(input("Please enter an integer: "))
Please enter an integer: 42
>>> if x < 0:
...     x = 0
...     print('Negative changed to zero')
... elif x == 0:
...     print('Zero')
... elif x == 1:
...     print('Single')
... else:
...     print('More')
...
More
```

## Repetition: while
```
while (boolean_exp):
  stmt...
```

## Traversal: for
```
for var in traversable_object:  # iterates over each item in the sequence
  stmt...
```

### Example: 
```
>>> words = ['Greg', 'Jackie', 'Shawn', 'Dave', 'Will']
>>> for name in words:
...     print(name, len(name))
... 
Greg 4
Jackie 6
Shawn 5
Dave 4
Will 4
```

### The [range()](https://docs.python.org/3.12/library/stdtypes.html#range) Function:

If you do need a sequence of numbers, use the built-in `range()` function.
- Syntax: `range(start, stop[, step])`
- The given endpoint (the "stop" value) is ***never*** part of the sequence.
- `range()` returns an *[iterable](https://docs.python.org/3.12/glossary.html#term-iterable)*: an object capable of returning its members one at a time.
  - An iterable is ***not*** a list. It is its own object (even though it behaves like a list).
  - An iterable is an object that returns the successive items of the desired sequence when you iterate over it, but it doesn’t really make the list, thus saving space.
- Examples: 
```
>>> for i in range(3): print(i)
... 
0
1
2
>>> list(range(10))
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
>>> list(range(1, 11))
[1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
>>> list(range(0, 30, 5))
[0, 5, 10, 15, 20, 25]
>>> list(range(0, 10, 3))
[0, 3, 6, 9]
>>> list(range(0, -10, -1))
[0, -1, -2, -3, -4, -5, -6, -7, -8, -9]
>>> list(range(0))
[]
>>> list(range(1, 0))
[]
```

## Functions
- Usually ***functions*** return values and ***procedures*** do not.
- However, in Python even functions without a return statement do return a value, albeit a rather boring one: `None` (it’s a built-in name).
  - Writing the value `None` is normally suppressed by the interpreter if it would be the only value written.
- The `return` statement returns with a value from a function.
  - `return` without an expression argument returns `None`.
  - Falling off the end of a function also returns `None` (i.e., you don't need to end every function with `return`, although you could.

### Definition:
```
def function_name( parameters ):
  stmt...
```

Example: (function with a return value of `None`)
```
>>> def fib(n):    # write Fibonacci series less than n
...   """Print a Fibonacci series less than n."""
...   a, b = 0, 1
...   while a < n:
...     print(a, end=' ')
...     a, b = b, a+b
...   print()
...
```

Example: (function that returns a list)
```
>>> def fib2(n):  # return Fibonacci series up to n
...    """Return a list containing the Fibonacci series up to n."""
...    result = []
...    a, b = 0, 1
...    while a < n:
...        result.append(a)    # see below
...        a, b = b, a+b
...    return result
...
>>> f100 = fib2(100)    # call it
>>> f100                # write the result
[0, 1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89]
```

### Call: 
```
function_name( arguments )
```

Example (continued from above): 
```
# Call the function we just defined:
>>> fib(2000)
0 1 1 2 3 5 8 13 21 34 55 89 144 233 377 610 987 1597
```

### Lambda Expressions
- These are small functions that crecate in-line without a `def` statement.
- General Syntas: `lambda parameter1, parameter2, ... paramenterN : expression using the paramenters`
- Examples:
```
f = (lambda x, y, z : x + y + z)   # f(2, 3, 4) returns 9
f = (lambda x : x ** 2             # f(4) returns 16
```

## Classes

### Definition:
```
class Class_name [ (super_class ]:
  [ class variables ]
  def method_name( self, parameters ):
    stmt...
```

### Object Instantiation:
```
obj_ref = Class_name( arguments )
```

### Method Invocation: 
```
obj_ref.method_name( arguments )
```

### Document (Doc) Strings
- These are coded as strings at the ***top*** of **module** files, **function** statements, and **class** statements.
- The `help()` function (e.g., `help(YourFunction)`) will display the DocStrings like a man page.

**Top of Module Files:**
```
"""
Program: name.py
Author: FirstName LastName
Last Date Modified: mm/dd/yyyy

Give a purpose statment on its own line, then the following...

1. CONSTANTS
2. Inputs
3. Computations
4. Outputs
"""
```

**Top of Function Definitions:**
```
def func(parameters):
  """
  First line: short concise summary of the object's purpose.

  Describe the object's calling conventions, side effects, etc.
  """
```

**Top of Class Defintions:**
```
Class Whatever
  """
  First line: short concise summary of the object's purpose.

  Describe the object's calling conventions, side effects, etc.
  """
```

## Exception Handling
```
try:
  stmt...
except [exception_type][, var]:
  stmt...
```

## Prevent Module Execution on Import
```
if __name__ == "__main__": [run whatever statements]
```
- If the file is run as a top-level program, `__name__` is set to `__main__` when it starts.
  - So you can ***use this for self-testing code***.
- If the file is imported as a module, `__name__` is set to the module's name (as known by it clients).
  - So the module will never be `__main__` and the if statement above prevents module execution on import.
 
