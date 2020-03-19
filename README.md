# ic
A shell-like environment for quickly writing simple C programs. 

## Building and installing
You need to have the `meson` build system installed. 

### Building
In the root directory of the project, run:

    meson build/ --prefix=<install-prefix>

`<install-prefix>` is where parent of the bin directory where the program will 
be installed. If you don't want to install the program or you want to use
meson's default setting you can omit the `--prefix` options

### Installing
In the root directory of the project, run:

    ninja -C build/ install

## How does it work?
The user will be greeted by a prompt:

    int main(int argc, char **argv) >>

This prompt tells you the currently selected function. By default you start
in the main() function. Every line written by the user will be added to the end
of the current function.

There are some commands that let you create/delete/change functions, add macros and
headers and other C stuff. Every one of them starts with `#`. To get a complete
list, run the `#help` command.

Once you are done writing, compile and execute your program with the `#run` 
command.

## Using other compilers
The `-x` option lets you choose you the compiler command line that `ic` will
use during its operation. Alternatively, you can set it wit the `#cc` command
(**Note: not yet implemented as of v2.0.0**).

The command line has a peculiar format: you can ass any option, but `{0}` will be
the substituted with the input file and `{1}` with for the output file.

You can find the default compiler command by running `ic --help`.

Example: `gcc -x c -o {1} {0}`

## Should you be using ic?
1. Do you need a quick prototyping tool? You can use ic.
2. Are you learning to program in C and you are trying out the language's features?
   You can use ic.
3. Do you want to test is sprintf() adds a \0 or you want to see how many bytes
   are and int without creating useless test.c files around? You can use ic.

1. You need to write a program that spans multiple files? Use a serious IDE
2. You need to use advanced features of the C language (Preprocessor stuff and
   other)? Use a serious IDE.
3. You want to easily edit what you have written? Use a text editor, not a shell.

# Features not yet included and limitations (as of v2.0.0)
Missing:
- Syntax checking is not available. I want to avoid recompiling the program for
  every line or writing a C parser from scratch;
- The `#cc` command is not yet implemented;
- A way to export the working workspace is missing (maybe a `#export` command
  will be added).

Limitations:
- ic requires the `#run` command to do stuff, making it not very interactive.
  That is more a compiler limitation more than a ic limitation: it would
  require a interactive compiling/injection system similar to gdb.
