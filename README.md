```

                       _____ _   _ _____    ____    _  _____ _____ ____     ___  _____ 
                      |_   _| | | | ____|  / ___|  / \|_   _| ____/ ___|   / _ \|  ___|
                        | | | |_| |  _|   | |  _  / _ \ | | |  _| \___ \  | | | | |_   
                        | | |  _  | |___  | |_| |/ ___ \| | | |___ ___) | | |_| |  _|  
                        |_| |_| |_|_____|  \____/_/   \_\_| |_____|____/   \___/|_|    

                                       ____  _   _ _____ _     _     
                                      / ___|| | | | ____| |   | |    
                                      \___ \| |_| |  _| | |   | |    
                                       ___) |  _  | |___| |___| |___ 
                                      |____/|_| |_|_____|_____|_____|
                                                                      
```

## HSH: The Holberton Shell
The gates of shell is a Holberton School project in the first trimester, helps student to understand the advanced
concepts behind the shell program include process, system call, bit manipulation, file managment, error handling ...

### Genreral

* Who designed and implemented the original Unix operating system
* Who wrote the first version of the UNIX shell
* Who invented the B programming language (the direct predecessor to the C programming language)
* Who is Ken Thompson
* How does a shell work
* What is a pid and a ppid
* How to manipulate the environment of the current process
* What is the difference between a function and a system call
* How to create processes
* What are the three prototypes of `main`
* How does the shell use the `PATH` to find the programs
* How to execute another program with the `execve` system call
* How to suspend the execution of a process until one of its children terminates
* What is `EOF` / “end-of-file”?

## Getting HSH
In order to install the shell and get benefits of it's features you need to clone the current project, and compile it.
You need to make sure that this shell tested and garantees work based on `gcc-4.8` and the `C90` standard.

## Features
* Display a prompt and wait for the user to type a command. A command line always ends with a new line.
* If an executable cannot be found, print an error message and display the prompt again.
* Handle errors.
* Hndling the “end of file” condition (Ctrl+D)
* Hanling the command line with arguments
* Handle the PATH
* Support the exit features and the exit status
* Handle the Ctrl-C to not terminate the shell
* Handling the command seperator `;`
* Handling `&&` and `||` logical operators
* Handle variable replacements `$?` and `$$`
* Handle the comments `#`
* Support the history feature
* Support the file input

## Builtins
* The exit builtin `exit [STATUS]`
* The change directory `cd [DIRECTORY] | [OPTION]`
* Display the environnment variables `env`
* Initialize a new environnment variables or created if not match `setenv [VARIABLE] [VALUE]`
* Remove an environnment variable `unsetenv [VARIABLE]`
* Support the aliases `alias [name [='value'] ...]`
* Display help `help [BUILTIN]`
* Display history `history`



## Author
Diego-Landony

## MANUAL

.TH HSH 1
.SH NAME
hsh \- Holberton Shell	
.SH SYNOPSIS
.B hsh
[command] [options ...]
.SH COPYRIGHT
hsh \- is a holberton school first trimester project
.SH DESCRIPTION
.B hsh
is a shell command interpreter that executes command read from the standard input or from file.
.B hsh
is intend to be a clone of the standard command interpreter of 
.B Unix
and 
.B Unix-like
system.
.SH OPTIONS
A  simple command is a sequence of optional variable assignments followed by blank-separated words and redirections, 
and terminated by a control operator.  The first word specifies the command to be
executed, and is passed as argument zero.  The remaining words are passed as arguments to the invoked command.
.PP
The return value of a simple command is its exit status, or 128+n if the command is terminated by signal n.
.SS
Piplines
A pipeline is a sequence of one or more commands separated by one of the control operators | or |&.  The format for a pipeline is:
.PP
[command [..ARGS]] [| - |&] [command2 [..ARGS]]
.PP
The standard output of command is connected via a pipe to the standard input of command2.  This connection is performed before any redirections specified by the command (see REDIRECTION below).   If
|&  is  used,  command's standard error, in addition to its standard output, is connected to command2's standard input through the pipe; it is shorthand for 2>&1 |.  This implicit redirection of the
standard error to the standard output is performed after any redirections specified by the command.
.SS Lists

A list is a sequence of one or more pipelines separated by one of the operators ;, &, &&, or ||, and optionally terminated by one of ;, &, or <newline>.
Of these list operators, && and || have equal precedence, followed by ; and &, which have equal precedence.
A sequence of one or more newlines may appear in a list instead of a semicolon to delimit commands.
.PP
If  a command is terminated by the control operator &, the shell executes the command in the background in a subshell.  The shell does not wait for the command to finish, and the return status is 0.
Commands separated by a ; are executed sequentially; the shell waits for each command to terminate in turn.  The return status is the exit status of the last command executed.
AND and OR lists are sequences of one or more pipelines separated by the && and || control operators, respectively.  AND and OR lists are executed with left associativity.  An AND list has the form
.PP
command1 && command2
.PP
command2 is executed if, and only if, command1 returns an exit status of zero.
.PP
An OR list has the form:
.PP
command1 || command2
.PP
command2 is executed if and only if command1 returns a non-zero exit status.  The return status of AND and OR lists is the exit status of the last command executed in the list.
.SH AUTHORS
Diego-Landony \- Holberton School Software Engineer Student
.SH VERSIONS
.B hsh
V1.0.0