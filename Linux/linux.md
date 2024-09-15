`root@hostname:/#currentDirectory~`  This is the command line Interface. This is how your `cli` looks like.

`Commands` are executable files.
---
# Linux Commands

    mkdir folder
`mkdir` is used to create a new directory named `folder` in the current directory.

---
    touch file.extension
`touch` is used to create a new file named `file.extension` in the current directory.

---
    which git
The `which git` command locates the `git` executable in directories listed in your `PATH` environment variable. It returns the full path to the executable if found. If `git` is not installed or not in the `PATH`, it returns nothing.

---
    git -v
    /usr/bin/git -v
`Both` gives the same result.

---
    ls
`ls` is used to list all the visible files and directories in the current directory.

---
    ls -a
`ls -a` is used to list all the files and directories which are visible hidden or visible.

---
    ls -l
The `ls -l` command lists files and directories in the current directory with detailed information. It shows file permissions, owner, group, size, and modification date. This provides a more comprehensive view of file attributes compared to a basic `ls` command.

---
    ls -al
The `ls -al` command lists all files and directories, including hidden ones, in the current directory with detailed information. It shows file permissions, ownership, size, modification date, and includes entries like `.` and `..`. This provides a complete and detailed view of the contents.

---
    ls -R
`ls -R` is used to files and folders which are in subdirectories.

---
    open .
`open` is used to open the given directory in the GUI.

---
    cd <realtive path of directory>
`cd` is used to change the directory.

---
    cd ..
`cd ..` is used to go into previous directory or one directory backwards.

---
    cd
only `cd` is used to go directly to the `Home` directory.

---

**Process:-** Any Instance of a  running command is known as Process.
---
    echo $PATH
The `echo $PATH` command displays the directories listed in your `PATH` environment variable. These directories are where the system looks for executable files. This helps you understand where commands are searched for and verify if certain executables are accessible.

---
    cat .bashrc
`cat` is used to see the content of the file in the terminal.

---
    pwd
`pwd` reffered to `print working directory` and is used to show the working directory.

---
    cat > hello
The `cat > hello` command creates a new file named `hello` or overwrites an existing file with that name. It allows you to enter text directly into the file from the terminal. To finish and save the file, you need to press `Ctrl+D`.

---
    cat one.txt two.txt > three.txt
The command `cat one.txt two.txt > three.txt` reads the contents of `one.txt` and `two.txt`, merging them together. It then redirects this combined content into a new file named `three.txt`. If `three.txt` already exists, it will be overwritten with the new content; if not, it will be created. Essentially, this command combines two files into one, updating or creating the destination file.

---
    cat one.txt two.txt
    The command `cat one.txt two.txt` displays the contents of `one.txt` followed immediately by the contents of `two.txt` in the terminal. It does not modify or create any files; it simply outputs the combined contents to the screen. This command is useful for viewing the contents of multiple files in sequence.

---
    echo "Hello, world!"
The `echo "Hello, world!"` command outputs the text "Hello, world!" to the terminal. It is commonly used to display messages or the values of variables.

---
    echo "Hello, world!" > file.txt
The command `echo "Hello, world!" > file.txt` writes the text "Hello, world!" to a file named `file.txt`. If `file.txt` already exists, it will be overwritten; if not, a new file will be created with the specified content.

---
    man echo
The command `man echo` displays the manual page for the `echo` command. It provides detailed information about its usage, options, and syntax. This includes descriptions of how to use `echo` to output text or variables, and any special flags or formatting options. The manual page serves as a reference guide for understanding and using the `echo` command effectively. This command is useful for accessing built-in documentation directly from the terminal.

---
    cat file.txt | tr a-z A-Z > upper.txt
The command `cat file.txt | tr a-z A-Z > upper.txt` converts all lowercase letters in `file.txt` to uppercase and saves the result to `upper.txt`. The `tr` command is used here to perform the character transformation, while `cat` reads the file and `>` redirects the output.


Use `\` after a command if you want to write more commands in next line.
---
