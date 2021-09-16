# Aiko-H
Simplistic programming language concept.

_______________
AIKO:H concept.
---------------
- Mostly whitespace insensitive.
- The language uses a single colon as a shorthand for `()`.
- Square, circular or brace brackets can be used `()[]{}` to contain code blocks.
- Text chars are converted to unicode values in integer operations.
- Integers should be but are not required to be 64 bit.
- Supports multiple comparison, so `||` and `&&` works as usual.
  Aliases for logical operators [reserved words]:
  ```
  equals    =
  not       !
  and       &&
  or        ||
  is        ==
  ```
- If and for loops also use the colon to describe brackets.
  - Disadvantage is no nested brackets visually or going up in the nest.
  - `(a(b))` is the same as `:a:b`. Brackets are fine as an alternative as shown.
- If is aliased with `?` question mark.
- Two datatypes, int and string [Think of string as a group of ints].
  - number arrays are just strings, they behave as strings of multiple numbers.
    That in mind, `"hello world"` can be thought of as a string or a group of numbers.
    - `array = "ab";` is the same as `array = [61, 62];`
    - Strings are as big as the farthest non-null value's position.
      Padding is needed at the end in some scenarios where you'd want some null space.

- Examples:
  - ```
    while: a == b && c == d [ #Do something. ]
    while: a is b and c is d [ #Do something. ]
    #Both of the above are the same.
    ```

  - ```
    if: a / 2 : + 2 [ #Do something. ]
     ?: a / 2 : + 2 [ #Do something. ]
    if (a / 2) + 2) [ #Do something. ]
    if [a / 2] + 2] [ #Do something. ]
    if (a / 2) + 2) { #Do something. }
    #Are all equivalent to (a / 2) + 2)
    ```

  - ```
    for: a = 0; a < 100 [ #Do something. ]
    for: a = 0; a < 100 ( #Do something. )
    for: a = 0; a < 100 { #Do something. }
    #Bracket styles for code blocks are interchangable.
    #The for loop is implicitly incrementing a++.
    ```

  - ```
    array = "ab";
    array = [61, 62];
    array = {61, 62}
    #Etc...

    #To get the length:
    length = len: array;

    #to access and set a value:
    value = get: array, 0;      #Pull array value at position 0.
    set: array, 1, value;       #Push value into array at position 1.
    ```

  - `"a"` is an int.\
    `61` is an int.\
    `"ab"` is a string.\
    `[61, 62]` is a string.

- Core Functions:\
  `print: text_in`                Print a line of text.\
  `input: text_in`                Print a line of text and wait for input.\
  `sleep: time_in`                Sleep for however many milliseconds.\
  `rval: max_val`                 Obtain a random integer up to max_val.\
  `open: file_in`                 Open by filename.\
  `save: file_in, data_in`        Save a file by filename.\
  `get: var_in, position`         Get a number value from a string.\
  `set: var_in, position, val`    Set a number value in a string.\
  `len: var_in`                   Get the length of a variable or array.\
  `del: var_in, position = null`  Removes a variable. If position is set and the var is a string [an array], then remove the member.

________________
Example Program.
----------------
```
#High level AIKO concept program.

#Wrapper functions.
fun print: text_in [
  python: "print(str(" + text_in + "))";   #Python is a built in function for a transpiler,
                                            #Not a language feature, just a lazy shortcut.
]

fun input: text_in [
  python: "input(str(" + text_in + "))";
]

user = input: "Your name? ";
if: user != "" [
  print: "Hello " + user + ".";
]
else [
  print "No name."
]
```
________________
Design issues.
----------------
- Variable scoping not defined, though expect something conventional.
- The `:a:b` syntax is not very useful.
- `null` behaviour isn't properly defined, nor is it given a datatype.
- Not object oriented, if that's what you're into.
