# Python
> Trying to get all my notes housed in one place...

## [Invoke the Interpreter](https://docs.python.org/3/tutorial/interpreter.html):

From the CLI: `python` (Kali: /usr/bin/python*) 
- This place you in Interactive Mode, gives you the version of Python used, etc.
- You'll be given the primary prompt: `>>>`
- When you enter a command that requires additional lines of code, you'll get the secondary prompt: `...`

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
