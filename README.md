# Python
> Trying to get all my notes housed in one place...

## Contents
- [Invoke the Interpreter](invoke-the-interpreter)
- [Argument Passing](#argument-passing)
- [Shebang](#shebang-additional-source)
- [Comments](#comments)
- [Numbers](#numbers)
- [Text](#text)
  - [Escape Character: `\`](#escape-character-)
  - [Multi-Line Strings](#multi-line-strings)
  - [Concatenate Strings](#concatenate-strings)
  - [Indexing Strings](#indexing-strings)
  - [Slicing Strings](#slicing-strings)

## 

## [Invoke the Interpreter](https://docs.python.org/3/tutorial/interpreter.html):

From the CLI: `python` (Kali: /usr/bin/python*) 
- This place you in Interactive Mode, gives you the version of Python used, etc.
- You'll be given the primary prompt: `>>>`
- When you enter a command that requires additional lines of code, you'll get the secondary prompt: `...`
- If you are given a blank `...`, you must hit ENTER: a blank line is used to end a multi-line command.

Or use the following command:

```
python -c command [arg] ...  # place command in "quotes" if it includes spaces

# Example:
python -c "for i in range(3): print(i)"  # prints: 0, 1, 2
```

## [Argument Passing](https://docs.python.org/3/tutorial/interpreter.html#argument-passing):

The script name and additional arguments thereafter are turned into a list of strings and assigned to the `argv` variable in the `sys` module.
- You can access this list by executing `import sys`.
- The length of the list is at least one: 
  - When no script and no arguments are given, `sys.argv[0]` is an empty string. 
  - When the script name is given, `sys.argv[0]` is the name of the script.

## [Shebang](https://docs.python.org/3/tutorial/appendix.html#tut-scripts) ([additional source](https://stackoverflow.com/questions/6908143/should-i-put-shebang-in-python-scripts-and-what-form-should-it-take))

You can make your Python script directly executable (i.e., you don't have to type `python [script name]`; you just type the script name) by including a shebang statement in the ***first line*** of your script.
- You add the **correct** shebang line to your script.
- You `chmod` your script so it's executable. Done.

**Correct usage** for (defaults to version 3.latest) Python 3 scripts is:
```
#!/usr/bin/env python3
```

**Correct usage** for (defaults to version 2.latest) Python 2 scripts is:
```
#!/usr/bin/env python2
```

The following should ***not*** be used (except for the rare case that you are writing code which is compatible with both Python 2.x and 3.x):
```
#!/usr/bin/env python
```
- The reason for these recommendations, given in [PEP 394](https://peps.python.org/pep-0394/), is that `python` can refer either to `python2` or `python3` on different systems.

Also, do ***not*** use:
```
#!/usr/local/bin/python
```
- Your machine might not be able to find this.
- Python may be installed at `/usr/bin/python` or `/bin/python` so the above #! will likely fail.
- `env` will always be found in `/usr/bin/`, and its job is to locate bins (like `python`) using PATH.
- No matter how `python` is installed, its path will be added to this variable, and `env` will find it (if not, python is not installed).

## Comments

Comments in Python start with the hash character (`#`) and extend to the end of the physical line.
- A comment may appear at the start of a line or following whitespace or code
- A comment cannot appear within a string literal.
  - A hash character within a string literal is just a hash character.
- Comments are often used to clarify code.

Examples:
```
# this is the first comment
spam = 1  # and this is the second comment
          # ... and now a third!
text = "# This is not a comment because it's inside quotes."
```

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





















