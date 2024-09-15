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
    cp file.txt copied_file.txt
The command `cp file.txt copied_file.txt` copies the contents of `file.txt` into a new file named `copied_file.txt`. If `copied_file.txt` already exists, it will be overwritten with the contents of `file.txt`.

---
    mv file.txt folderName
The command `mv file.txt folderName` moves the file `file.txt` into the directory `folderName`. If `folderName` is a valid directory, the file will be relocated there. If `folderName` is not a directory, the command will rename `file.txt` to `folderName`.

---
    mv file.txt newFile.txt
The command `mv file.txt newFile.txt` renames the file `file.txt` to `newFile.txt` in the same directory. If `newFile.txt` already exists, it will be overwritten with the contents of `file.txt`.

---
    mv name.txt ../newName.txt
The command `mv name.txt ../newName.txt` moves the file `name.txt` from the current directory to the parent directory. It renames the file to `newName.txt` in the process. If a file named `newName.txt` already exists in the parent directory, it will be replaced.

---
    rm file.txt
The command `rm file.txt` deletes the file `file.txt` from the current directory. Once removed, the file cannot be easily recovered unless restored from a backup.

---
    cp -R test random
The command `cp -R test random` recursively copies the directory `test` and all of its contents into a new directory named `random`. If `random` does not exist, it will be created. If `random` already exists, `test` will be copied inside it as a subdirectory.

---
    mv test renamedTest
The command `mv test renamedTest` renames the directory `test` to `renamedTest` in the same location. If a directory named `renamedTest` already exists, the `test` directory will be moved inside it. If `renamedTest` does not exist, it will replace the name of `test` with `renamedTest`.

---
    rm -R renamedTest
The command `rm -R renamedTest` recursively deletes the directory `renamedTest` and all of its contents, including subdirectories and files. This operation is irreversible and will permanently remove the directory and everything inside it. Use caution, as the deleted data cannot be easily recovered.

---
    rm -rf renamed
The command `rm -rf renamed` forcefully and recursively deletes the directory `renamed` along with all of its contents, including subdirectories and files. The `-f` flag bypasses prompts and warnings, while the `-r` flag ensures that all nested files and directories are removed. This action is irreversible and will permanently erase all specified data.

---

`sudo` refers `Super User Do`. When we need to do some administrative action then we need to use `sudo`.
---
    df
The command `df` displays information about the disk space usage of all mounted file systems. It shows the total size, used space, available space, and the percentage of space used for each file system. By default, the output includes file systems mounted on local disks. You can use options like `-h` to format the output in a human-readable form with units like GB and MB. This command helps monitor disk usage and manage storage efficiently.

---
    du
The command `du` (disk usage) estimates and displays the amount of disk space used by files and directories. By default, it provides a summary of space usage for the current directory and its subdirectories in kilobytes. Options like `-h` can be used to format the output in a human-readable form, showing sizes in KB, MB, or GB. The `-s` option summarizes the total usage for each specified directory, while `-a` includes individual files in the output. This command is useful for tracking space consumption and managing disk storage.

---
    head file.txt
The command `head file.txt` displays the first 10 lines of the file `file.txt` by default. It is useful for quickly viewing the beginning of a file to check its contents or format. You can specify a different number of lines to show by using the `-n` option, e.g., `head -n 20 file.txt` for the first 20 lines. The command helps in previewing large files without opening the entire document. It is often used in combination with other commands in Unix-like systems for efficient file processing.

---
    tail file.txt
The command `tail file.txt` displays the last 10 lines of the file `file.txt` by default. It is useful for viewing the end of a file, which is particularly helpful for checking logs or recent additions. You can specify a different number of lines to display by using the `-n` option, such as `tail -n 20 file.txt` for the last 20 lines. Additionally, the `-f` option can be used to follow the file in real-time, showing new lines as they are added, which is useful for monitoring log files. This command is commonly used in system administration and debugging tasks.

---
    diff total.txt two.txt
The command `diff total.txt two.txt` compares the contents of the files `total.txt` and `two.txt` line by line. It outputs the differences between the two files, highlighting what has been added, removed, or changed. The output format typically includes lines prefixed with `<` or `>` to indicate which file each line is from. This command is useful for identifying changes between file versions, such as in source code or configuration files. Options like `-u` can be used for a unified format, which provides a more readable view of the differences.

---
    locate "*.txt"
The command `locate "*.txt"` searches for files with the `.txt` extension across the system based on the database maintained by the `locate` command. It returns a list of file paths that match the search pattern, providing a quick way to find all text files. The `locate` command relies on an index that is updated periodically by the system, which means the results might not include files created or moved since the last update. For real-time file searches, consider using `find` instead. The `locate` command is efficient and faster for large-scale searches compared to other methods.

---
    find random
The command `find random` searches for files and directories within the directory named `random` and its subdirectories. By default, it lists all files and directories found in `random` without applying any filters. The command can be customized with various options and expressions to search for specific file types, names, or attributes, such as `find random -name "*.txt"` to find all text files. It’s highly versatile and useful for locating files based on criteria like size, modification time, or permissions. The `find` command is powerful for complex search tasks and is widely used in Unix-like operating systems.

---