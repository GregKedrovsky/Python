# Intro & Overview

## Contents
- [Numbers](#numbers)
- [Text](#text)
  - [Escape Character: `\`](#escape-character-)
  - [Multi-Line Strings](#multi-line-strings)
  - [Concatenate Strings](#concatenate-strings)
  - [Indexing Strings](#indexing-strings)
  - [Slicing Strings](#slicing-strings)
- [Lists](#lists)

## 

## Numbers

The operators `+`, `-`, `*` and `/` can be used to perform arithmetic; parentheses (`()`) can be used for grouping. 

The integer numbers (e.g. 2, 4, 20) have type `int`, the ones with a fractional part (e.g. 5.0, 1.6) have type `float`. 
- **Division** alwas returns a float.
- You can force **floor division** and get an integer using the `//` operator.
- To calculate a **remainder**, use the `%`
- Calculate **powers** with `**`.

```
>>> 17 / 3          # classic division returns a float
5.666666666666667
>>> 17 // 3         # floor division discards the fractional part
5
>>> 17 % 3          # the % operator returns the remainder of the division
2
>>> 
>>> 5 ** 2          # 5 squared
25
>>> 2 ** 7          # 2 to the power of 7
128
```

**NOTE:** In interactive mode, the last printed expression is assigned to the variable `_` (underline).
- This means that when you are using Python as a desk calculator, it is somewhat easier to continue calculations.
- This variable should be treated as read-only by the user. 
- Don’t explicitly assign a value to it (you would create an independent local variable with the same name masking the built-in variable with its magic behavior).
- Example:

```
>>> tax = 12.5 / 100
>>> price = 100.50
>>> price * tax
12.5625
>>> price + _
113.0625
>>> round(_, 2)
113.06
```

## Text 

Text is also referred to as "strings" and represented by the type `str`.
- Numbers can be strings (type `str`) also.
- Strings are usually enclosed in quotes ('single' or "double" are treated the same).
- Strings are immutable. You cannot change them. If you need to change a string, you need to create a new one.
- The built-in function `len()` will tell you the length of a string (e.g., `len("greg")` is 4).

### Escape Character: `\`
- In order to print an otherwise special character (like a quote), you need to *escape* it with the backslash (`\`).
- Example:
```
>>> doesn\'t'        # use \' to escape the single quote...
"doesn't"
>>> "doesn't"        # ...or use double quotes instead
"doesn't"
```

If you don’t want characters prefaced by `\` to be interpreted as special characters, you can use raw strings by adding an `r` before the first quote:
```
>>> print('C:\some\name')    # here \n means newline!
C:\some
ame
>>> print(r'C:\some\name')   # note the r before the quote
C:\some\name
```

### Multi-Line Strings
- For multi-line (block) strings, use triple-quotes (single or double). Example:
```
print("""\
Usage: thingy [OPTIONS]
     -h                        Display this usage message
     -H hostname               Hostname to connect to
""")
```

### Concatenate Strings
- Strings can be concatenated (glued together) with the `+` operator, and repeated with `*`.

### Indexing Strings
- Strings can be indexed (subscripted), with the first character having index 0. There is no separate character type; a character is simply a string of size one:
```
>>> word = 'Python'
>>> word[0]  # character in position 0
'P'
>>> word[5]  # character in position 5
'n'
```
- Indices may also be negative numbers, to start counting from the right:
```
>>> word[-1]  # last character
'n'
>>> word[-2]  # second-last character
'o'
>>> word[-6]
'P'
```

### Slicing Strings
- Slicing allows you to obtain a substring.
- Think of the indices as pointing between characters, with the left edge of the first character numbered 0 (or `:`). Then the right edge of the last character of a string of n characters has index n (or `:`)
- Example:
```
 +---+---+---+---+---+---+
 | P | y | t | h | o | n |
 +---+---+---+---+---+---+
 0   1   2   3   4   5   6
-6  -5  -4  -3  -2  -1
```
- The first row of numbers gives the position of the indices 0...6 in the string.
- The second row gives the corresponding negative indices.

![image](https://github.com/user-attachments/assets/575c8d54-ca9b-4df3-8437-ce1135321595)

## Lists

A *list* is a compound data type--a data type used to group values of the same type together.
- Although lists ***may*** contain items of different types, they usually contain items of the same data type.
- Lists are written as comma-separated values (items) between square brackets (you can nest: lists of lists).
- You can get the length of a list with the `len()` function.

```
>>> int_list = [1, 2, 3, 4]
>>> int_list
[1, 2, 3, 4]
>>> len(int_list)
4
```

### Index & Slice
Like all other built-in sequence types (like strings), lists can be *indexed* and *sliced*: 
- Indexed items are returned as their current type (int, str, etc.).
  - Reference the index to replace the item at that index: `list1[0] = new_value`
- Sliced items are returned as a new list.

### Append
Add new items to the end of the list with `list.append()`
```
>>> countdown = [10, 9, 8, 7, 6, 5, 4, 3, 2]
>>> countdown.append(1)
>>> countdown
[10, 9, 8, 7, 6, 5, 4, 3, 2]
```

### Reference
Assigning an existing list to a variable does not copy the list.
- The list is the same object. Each variable that references that list points to the same object (the same address in memory).
```
>>> rgb = ["Red", "Green", "Blue"]
>>> rgba = rgb
>>> id(rgb) == id(rgba)            # they reference the same object
```



