# Conditional Comparisons in Bash/Shell

It seems that we can perform different kinds of comparisons in bash and shell in variables fashsions -
* Single brackets [ ... ]
* Double brackets [[ ... ]]
* Double parathesises (( ... ))

- Single brackets
  - Shell constructs; supported by POSIX
  - They will provide consistency/support for all UNIX based systems
  - Conditonal evaluations
  - Can compare strings, integers, and file system checks
- Double brackets
  - Bash constructs for conditoinal evaluations
  - Will fail in a script if `#!/bin/sh` doesn't point to `#!/bin/bash`. E.g. Debian
  - Superset of Single brackets with better multiple conditions support and string comparisons
- Double parathesises
  - Bash constructs for arithmetic operations
  - Evaluates expressions as C arithmetic
  - Does more than just conditional evaluations
  - More powerful than single brackets in conditional evaluations in strings comparisons
  - The comparison doesn't have weird and/or syntax like the single brackets for conditional comparisons
  - In shell, you would use `let`, `expr`, and `declare`
  - Usage: http://faculty.salina.k-state.edu/tim/unix_sg/bash/math.html

## Multiple conditions in one if statement
- Single brackets
```
# Short-circuiting by evaluating the exit codes of each condition
# && is and; || is or
if [ <condition> ] && [ <condition> ]; then
    ...
fi

# Native and supported by shell's conditional evalution
# -a is and; -o is or
if [ <condition> -a <condition ];
    ...
fi
```

- Double brackets
```
# Short-circuiting by evaluating the exit codes of each condition
# && is and; || is or
if [[ <condition> ]] && [[ <condition> ]]; then
    ...
fi

# Evaluations inside the brackets supported by bash :)
if [[ <condition> && <condition> ]]; then
    ...
fi
```

- Double Parathesises
```
if (( <condition> )) && (( <condition> )); then
    ...
fi
```

## Useful code snippets
- Single Brackets
  - Integer comparison: `if [ "$foo" -eq 0 ]`
    - Other integer comparison operations: -ne, -gt, -ge, -lt, -le
  - String comparison: `if [ "$foo" = "bar" ]`
    - Can be done with == as well, != for not equal
    - `if [ -z "$foo" ]` to check if the string is empty (-n for not empty)
  - File System comparision: `if [ -f "$foo" ] # true if file exists and is a regular file`
    - To check if directory, use -d. There are more! 
- Double Brackets
  - Integer comparisons are pretty much the same as single brackets
  - String comparisons are pretty much the same as single brackets as well, but you can do `if [[ "$foo" =~ "bar" ]]` to determine if the variable contains another string
- Combine Double Brackets with Double Parathesises!
  - `if [[ $(( n % 4 )) == 0 ]]` to check if modulo of n is 0
  - `$(( ... ))` is forcing the expression to return its value instead of true/false

Reference:
- http://stackoverflow.com/questions/12765340/difference-in-bash-between-if-statements-with-parenthesis-and-square-brackets
- http://www.tldp.org/LDP/abs/html/comparison-ops.html
