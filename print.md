# Print

The print() function writes the value of the argument(s) it is given.

## Contents:
- [Basic Usage](#basic-usage)
- [Print to a File](#print-to-a-file)
- [Print File Text](#print-file-text)

## Basic Usage: 
```
print(objects, sep=' ', end='\n', file=sys.stdout, flush=False)
```
Print `objects` (comma separated if multipe) to the text stream file, separated by `sep` and followed by `end`. 
- Defaults for `end`, `file`, and `flush` are given above.
- If you do not include them, they default to the value shown above.

```
>>> x,y,z = 'first', 'second', 'third'
>>> print(x,y,z, sep=',')
first,second,third
```

## Print to a File: 
```
>>> x,y,z = 'first', 'second', 'third'
>>> print(x,y,z, file=open('data.txt', 'w')

```

## Print File Text
```
print( open('data.txt').read() )
