# Simple Shell project 0x16.c - hsh -

This is a simple UNIX command interpreter project(Alx) based on bash and Sh.

## Overview

**hsh** is a sh-compatible command language interpreter that executes commands read from the standard input or from a file.

### How to Invoke

Usage: **hsh** 
hsh is started with the standard input connected to the terminal. To start, compile all .c located in this repository by using this command: 
```
gcc -Wall -Werror -Wextra -pedantic -std=gnu89 *.c -o hsh
./hsh
```

**hsh** is allowed to be invoked interactively and non-interactively. If **hsh** is invoked with standard input not connected to a terminal, it reads and executes received commands in order.

Example:
```
$ echo "echo 'Alx'" | ./hsh
'Alx'
$
```

When invoked with standard input connected to a terminal (determined by isatty), the interactive mode is opened. **hsh** Will be using the following prompt `^-^ `.

Example:
```
$./hsh
^-^
```

When a command line argument is invoked, **hsh** will take that first argument as a file from which to read commands.

Example:
```
$ cat text
echo 'works'
$ ./hsh text
'works'
$
```

### Environment

Whwn invoked, **hsh** receives and copies the environment of the parent process in which it was executed. This environment is an array of *name-value* strings describing variables in the format *NAME=VALUE*. A few key environmental variables are:

#### HOME
The home directory of the current user and the default directory argument for the **cd** builtin command.

```
$ echo "echo $HOME" | ./hsh
/home/vagrant
```

#### PWD
The current working directory as set by the **cd** command.

```
$ echo "echo $PWD" | ./hsh
/home/vagrant/simple_shell
```

#### OLDPWD
The previous working directory as set by the **cd** command.

```
$ echo "echo $OLDPWD" | ./hsh
/home/vagrant/test_suite
```

#### PATH
A colon-separated list of directories in which the shell looks for commands. A null directory name in the path (represented by any of two adjacent colons, an initial colon, or a trailing colon) indicates the current directory.

```
