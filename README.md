# 0x16. C - Simple Shell

	*This is a group project of ALX software Engineering students.
	*It is a colloborative project done on a group of two. Here We were tasked to create a simple shell that mimics the Bash shell. Our shell shall be called hsh.

## Learning Objectives
	At the end of this project, you are expected to be able to explain to anyone, without the help of Google:

### General
	*Who designed and implemented the original Unix operating system
	*Who wrote the first version of the UNIX shell
	*Who invented the B programming language (the direct predecessor to the C programming language)
	*Who is Ken Thompson
	*How does a shell work
	*What is a pid and a ppid
	*How to manipulate the environment of the current process
	*What is the difference between a function and a system call
	*How to create processes
	*What are the three prototypes of main
	*How does the shell use the PATH to find the programs
	*How to execute another program with the execve system call
	*How to suspend the execution of a process until one of its children terminates
	*What is EOF / “end-of-file”?

## Using the Shell (file name is hsh)
	To Lauch hsh, compile all .c files in the repository and run the resulting executable.

	hsh can be invoked both interactively and non-interactively. If hsh is invoked with standard input not connected to a terminal, it reads and executes received commands in order.
	Requirements

	If hsh is launched with standard input connected to a terminal (determined by isatty(3)), an interactive shell is opened. When executing interactively, hsh displays the prompt $ when it is ready to read a command.

	Example:

	$./hsh
	$

	Alternatively, if command line arguments are supplied upon invocation, hsh treats the first argument as a file from which to read commands. 
	The supplied file should contain one command per line. hsh runs each of the commands contained in the file in order before exiting.

	Example:

	$ cat test
	echo 'hello'
	$ ./hsh test
	'hello'	
	$

	Upon invocation, hsh receives and copies the environment of the parent process in which it was executed. This environment is an array of name-value strings describing variables in the format NAME=VALUE.

	some of these environmental variables includes: Home, Pwd, OldPwd, PATH, 

### During Execution:

	After receiving a command, hsh tokenizes it into words using " " as a delimiter. The first word is considered the command and all remaining words are considered arguments to that command. 
	hsh then proceeds with the following actions:

	If the first character of the command is neither a slash (\) nor dot (.), the shell searches for it in the list of shell builtins. If there exists a builtin by that name, the builtin is invoked.
	If the first character of the command is none of a slash (\), dot (.), nor builtin, hsh searches each element of the PATH environmental variable for a directory containing an executable file by that name.
	If the first character of the command is a slash (\) or dot (.) or either of the above searches was successful, 
	the shell executes the named program with any remaining given arguments in a separate execution environment.

### On exit;

	*hsh returns the exit status of the last command executed, with zero indicating success and non-zero indicating failure.

	*If a command is not found, the return status is 127; if a command is found but is not executable, the return status is 126.

	*All builtins return zero on success and one or two on incorrect usage (indicated by a corresponding error message)
### Signals
	While running in interactive mode, hsh ignores the keyboard input Ctrl+c. Alternatively, an input of end-of-file (Ctrl+d) will exit the program.

	User hits Ctrl+d in the third line.


# General
	*Allowed editors: vi, vim, emacs
	*All your files will be compiled on Ubuntu 20.04 LTS using gcc, using the options -Wall -Werror -Wextra -pedantic -std=gnu89
	*All your files should end with a new line
	*A README.md file, at the root of the folder of the project is mandatory
	*Your code should use the Betty style. It will be checked using betty-style.pl and betty-doc.pl
	*Your shell should not have any memory leaks
	*No more than 5 functions per file
	*All your header files should be include guarded
	*Use system calls only when you need to (why?)
	*Write a README with the description of your project
	*You should have an AUTHORS file at the root of your repository, listing all individuals having contributed content to the repository. Format, see Docker

## More Info
	Output
	Unless specified otherwise, your program must have the exact same output as sh (/bin/sh) as well as the exact same error output.
	The only difference is when you print an error, the name of the program must be equivalent to your argv[0] (See below)
	Example of error with sh:

	List of allowed functions and system calls
	access (man 2 access)
	chdir (man 2 chdir)
	close (man 2 close)
	closedir (man 3 closedir)
	execve (man 2 execve)
	exit (man 3 exit)
	_exit (man 2 _exit)
	fflush (man 3 fflush)
	fork (man 2 fork)
	free (man 3 free)
	getcwd (man 3 getcwd)
	getline (man 3 getline)
	getpid (man 2 getpid)
	isatty (man 3 isatty)
	kill (man 2 kill)
	malloc (man 3 malloc)
	open (man 2 open)
	opendir (man 3 opendir)
	perror (man 3 perror)
	read (man 2 read)
	readdir (man 3 readdir)
	signal (man 2 signal)
	stat (__xstat) (man 2 stat)
	lstat (__lxstat) (man 2 lstat)
	fstat (__fxstat) (man 2 fstat)
	strtok (man 3 strtok)
	wait (man 2 wait)
	waitpid (man 2 waitpid)
	wait3 (man 2 wait3)
	wait4 (man 2 wait4)
	write (man 2 write)

### Compilation
	Your shell will be compiled this way:

	gcc -Wall -Werror -Wextra -pedantic -std=gnu89 *.c -o hsh

## Task 0: 

	*Write a beautiful code that passes the Betty checks

## Task 1: 

	Write a UNIX command line interpreter.

	Usage: simple_shell
	Your Shell should:

	*Display a prompt and wait for the user to type a command. A command line always ends with a new line.
	*The prompt is displayed again each time a command has been executed.
	*The command lines are simple, no semicolons, no pipes, no redirections or any other advanced features.
	*The command lines are made only of one word. No arguments will be passed to programs.
	*If an executable cannot be found, print an error message and display the prompt again.
	*Handle errors.
	You have to handle the “end of file” condition (Ctrl+D)
	*You don’t have to:

	use the PATH
	implement built-ins
	handle special characters : ", ', `, \, *, &, #
	be able to move the cursor
	handle commands with arguments
	execve will be the core part of your Shell, don’t forget to pass the environ to it…

## Task 2

	*Simple shell 0.1 +

	*Handle command lines with arguments

## Task 3:
	*Simple shell 0.2 +

	*Handle the PATH
	fork must not be called if the command doesn’t exist

## Task 4:
	Simple shell 0.3 +

	*Implement the exit built-in, that exits the shell
	Usage: exit
	*You don’t have to handle any argument to the built-in exit

## Task 5:
	Simple shell 0.4 +

	Implement the env built-in, that prints the current environment

## Task 6:
	Simple shell 0.1 +

	*Write your own getline function
	*Use a buffer to read many chars at once and call the least possible the read system call
	*You will need to use static variables
	*You are not allowed to use getline
	*You don’t have to:

	*be able to move the cursor

## Task 7:
	Simple shell 0.2 +

	*You are not allowed to use strtok

## Task 8:
	Simple shell 0.4 +

	*handle arguments for the built-in exit
	*Usage: exit status, where status is an integer used to exit the shell

## Task 9:
	Simple shell 1.0 +

	*Implement the setenv and unsetenv builtin commands

	setenv
	Initialize a new environment variable, or modify an existing one

	Command syntax: setenv VARIABLE VALUE
	Should print something on stderr on failure

	unsetenv
	Remove an environment variable
	Command syntax: unsetenv VARIABLE
	Should print something on stderr on failure

## Task 10:
	Simple shell 1.0 +

	Implement the builtin command cd:

	Changes the current directory of the process.

	*Command syntax: cd [DIRECTORY]
	*If no argument is given to cd the command must be interpreted like cd $HOME
	*You have to handle the command cd -
	*You have to update the environment variable PWD when you change directory
	man chdir, man getcwd

## Task 11:
	Simple shell 1.0 +

	*Handle the commands separator ;

## Task 12:
	Simple shell 1.0 +

	Handle the && and || shell logical operators

## Task 13:
	Simple shell 1.0 +

	*Implement the alias builtin command

	Usage: alias [name[='value'] ...]
	*alias: Prints a list of all aliases, one per line, in the form name='value'
	*alias name [name2 ...]: Prints the aliases name, name2, etc 1 per line, in the form name='value'
	*alias name='value' [...]: Defines an alias for each name whose value is given. If name is already an alias, replaces its value with value

## Task 14:
	Simple shell 1.0 +

	*Handle variables replacement
	*Handle the $? variable
	*Handle the $$ variable

## Task 15:
	Simple shell 1.0 +

	*Handle comments (#)

## Task 16:
	Simple shell 1.0 +

	*Usage: simple_shell [filename]
	*Your shell can take a file as a command line argument
	*The file contains all the commands that your shell should run before exiting
	*The file should contain one command per line
	*In this mode, the shell should not print a prompt and should not read from stdin
