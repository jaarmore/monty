# The Monty language
Monty 0.98 is a scripting language that is first compiled into Monty byte codes (Just like Python). It relies on a unique stack, with specific instructions to manipulate it. The goal of this project is to create an interpreter for Monty ByteCodes files.

### Monty byte code files
Files containing Monty byte codes usually have the `.m` extension. Most of the industry uses this standard but it is not required by the specification of the language. There is not more than one instruction per line. There can be any number of spaces before or after the opcode and its argument:

```
vagrant@ubuntu:~/monty$ cat -e bytecodes/000.m
push 0$
push 1$
push 2$
  push 3$
                   pall    $
push 4$
    push 5    $
      push    6        $
pall$
vagrant@ubuntu:~/monty$
```
Monty byte code files can contain blank lines (empty or made of spaces only, and any additional text after the opcode or its required argument is not taken into account:
```
vagrant@ubuntu:~/monty$ cat -e bytecodes/001.m
push 0 Push 0 onto the stack$
push 1 Push 1 onto the stack$
$
push 2$
  push 3$
                   pall    $
$
$
                           $
push 4$
$
    push 5    $
      push    6        $
$
pall This is the end of our program. Monty is awesome!$
vagrant@ubuntu:~/monty$
```

### The monty program
Usage: `monty file`
where `file` is the path to the file containing Monty byte code
+ If the user does not give any file or more than one argument to your program, print the error message `USAGE: monty file`, followed by a new line, and exit with the status `EXIT_FAILURE`
+ If, for any reason, its not possible to open the file, print the error message `Error: Can't open file <file>`, followed by a new line, and exit with the status `EXIT_FAILURE`

## Compilation & Output
Your code will be compiled this way:
```
$ gcc -Wall -Werror -Wextra -pedantic *.c -o monty
```

## Requirements
+ Allowed editors: `vi, vim, emacs`
+ All your files will be compiled on `Ubuntu 14.04 LTS`
+ You are allowed to use the C standard library

### Author
**Jackson Moreno**