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
pass      # placeholder for future statements
continue  # stop current iteration & return to the top
break     # jumps out of enclosing loop
```

## Selection
```
if (boolean_exp):      #  or
if not(boolean_exp):
  stmt...
elif (boolean_exp): 
  stmt...
else:
  stmt...
```

## Repetition
```
while (boolean_exp):
  stmt...
```

## Traversal
```
for var in traversable_object:
  stmt...
```

## Functions

### Definition:
```
def function_name( parameters ):
  stmt...
```

### Call: 
```
function_name( arguments )
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
 
