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
    find .
The `find` command in Linux is used to search for files and directories within a specified directory hierarchy based on various criteria such as name, size, type, and modification time. It allows users to perform actions on the found items, such as deleting or moving them, making it a powerful tool for file management.

---
    find . -type d
The command `find . -type d` searches for all directories starting from the current directory (`.`). It uses the `-type d` option to filter the results, ensuring that only directories are listed. This command is useful for quickly identifying the structure of subdirectories within the current directory.

---
    find . -type f
`f` for files.

---
    find . -type f -name "two.txt"
The command `find . -type f -name "two.txt"` searches for a file named "two.txt" starting from the current directory (`.`). It uses the `-type f` option to ensure that only regular files are considered, excluding directories. This command is useful for locating a specific file within a directory tree.

---
    find . -type f -name "two*"
Files starts from `two`.

---
    find . -type f -name "*.txt"
`all txt files` inside the current directory.

---
    find . -type f -iname "*.txt"
The command `find . -type f -iname "*.txt"` searches for all files with a `.txt` extension in the current directory and its subdirectories, ignoring case sensitivity. This means it will match files like "example.txt", "Example.TXT", and "EXAMPLE.TxT".

---
    find . -type f -mmin -20
The command `find . -type f -mmin -20` searches for all regular files in the current directory and its subdirectories that were modified in the last 20 minutes. The `-mmin` option specifically looks for files based on their modification time. This command is useful for quickly identifying recently updated files for review or backup.

---
    find . -type f -mmin +15
The command `find . -type f -mmin +15` searches for all regular files in the current directory and its subdirectories that were modified more than 15 minutes ago. This is useful for identifying older files that may need attention or cleanup.

---
    find . -type f -mmin +2 -mmin -10
The command `find . -type f -mmin +2 -mmin -10` searches for all regular files in the current directory and its subdirectories that were modified between 2 and 10 minutes ago. This allows users to locate files that were recently updated, specifically within that time frame.

---
    find . -type f -mtime -10
The command `find . -type f -mtime -10` searches for all regular files in the current directory and its subdirectories that were modified within the last 10 days. This is useful for identifying recently updated files for review or backup.

---
    find . -type f maxdepth 1
The command `find . -type f -maxdepth 1` searches for all regular files in the current directory without descending into subdirectories. The `-maxdepth 1` option restricts the search to the top level, making it useful for quickly listing files in the current directory.

---
    find . -size +1k
The command `find . -size +1k` searches for all files in the current directory and its subdirectories that are larger than 1 kilobyte. This is useful for identifying larger files that may require attention or cleanup.

---
    find . -empty
The command `find . -empty` searches for all empty files and directories in the current directory and its subdirectories.

---
    find . -perm 777
The command `find . -perm 777` searches for all files and directories in the current directory and its subdirectories that have permissions set to read, write, and execute for all users. This is useful for identifying files with potentially insecure permissions that may need to be modified.

---
    find . -perm 770
The command `find . -perm 770` searches for all files and directories in the current directory and its subdirectories that have permissions set to read, write, and execute for the owner and group, but no permissions for others.

---
## File System Permissions

In Linux (including Ubuntu), file permissions determine the access levels for files and directories. There are three main types of permissions, each associated with a specific numeric value:

1. **Read (r)**: Allows viewing the contents of a file or listing a directory's contents.
   - **Numeric value**: 4

2. **Write (w)**: Allows modifying or deleting a file or adding/removing files in a directory.
   - **Numeric value**: 2

3. **Execute (x)**: Allows executing a file as a program or entering a directory.
   - **Numeric value**: 1

4. **No Permission**:  
    - **Numeric value**: 0
### Permission Types:
These permissions can be assigned to three categories of users:

1. **Owner**: The user who owns the file.
2. **Group**: A group of users that share certain permissions.
3. **Others**: All other users who are not the owner or part of the group.

### Numeric Representation:
Permissions can be represented as a three-digit octal number, where each digit corresponds to the permissions for owner, group, and others, respectively. Each digit is the sum of the permissions:
- **Read** = 4
- **Write** = 2
- **Execute** = 1

For example:
- `7` (4+2+1) means read, write, and execute permissions.
- `5` (4+0+1) means read and execute permissions, but no write permission.
- `0` means no permissions at all.

Thus, a permission setting of `770` would grant read, write, and execute permissions to the owner and group, but no permissions to others.

## What is sudo ? 
`sudo` (short for "superuser do") is a command-line utility in Unix-like operating systems, including Linux, that allows a permitted user to execute a command as the superuser (root) or another user, as specified by the security policy. 

### Key Features of `sudo`:
- **Privilege Escalation**: It allows users to perform administrative tasks that require elevated permissions without needing to log in as the root user.
- **Granular Control**: System administrators can configure which users can run specific commands as root or other users through the `/etc/sudoers` file.
- **Audit Trail**: `sudo` logs all commands executed with it, which can help with security auditing and monitoring.
- **Temporary Access**: Users can perform tasks with elevated privileges for a limited time, reducing the risk associated with maintaining a constant root session.

### Common Usage:
To use `sudo`, simply prefix the desired command with `sudo`, like this:
```bash
sudo apt update
```
This command would run `apt update` with root privileges, allowing it to modify system files as necessary.

---
    chmod u=rwx,g=rx,o=r upper.txt
The command `chmod u=rwx,g=rx,o=r upper.txt` modifies the permissions of the file `upper.txt`. It grants the owner (user) full permissions (read, write, and execute: `rwx`), the group read and execute permissions (`rx`), and allows others to have only read permissions (`r`). This setup enables the owner to fully manage the file while providing limited access to the group and read-only access to everyone else.

---
    chmod 777 uper.txt
The command `chmod 777 upper.txt` sets the permissions of the file `upper.txt` to allow read, write, and execute access for the owner, group, and others. This configuration grants full access to all users, making the file accessible for any operation.

---
    whoami
The command `whoami` displays the username of the currently logged-in user in the terminal.

---
    sudo chown root upper.txt
The command `sudo chown root upper.txt` changes the ownership of the file `upper.txt` to the user `root`. By using `sudo`, it executes the command with elevated privileges, allowing the user to modify file ownership even if they do not own the file. This is often used for administrative tasks where specific files need to be owned by the root user for security or access control purposes.

---

## What is root ?
In Linux and Unix-like operating systems, the "root" user is the superuser with unrestricted access to all system commands and files. This account has the highest level of privileges, allowing it to perform any administrative tasks, such as installing software, modifying system configurations, and managing user accounts. The root user's home directory is typically located at `/root`. Because of its powerful capabilities, operating as the root user carries significant risks, as mistakes can lead to system-wide issues or security vulnerabilities. Therefore, it's recommended to use the root account only when necessary and to rely on regular user accounts for everyday tasks.

---
    find . -type f -name "*.txt" -exec  rm -rf {} +
The command `find . -type f -name "*.txt" -exec rm -rf {} +` searches for all files with a `.txt` extension in the current directory and its subdirectories. It uses the `-type f` option to ensure only regular files are targeted. The `-exec` option allows the command to execute a specified action on each found file, in this case, removing them with `rm -rf`. The `{}` placeholder represents the files found, and the `+` at the end allows for more efficient execution by passing multiple files to the `rm` command at once. This command permanently deletes all matching text files, so it should be `used with caution`.

---
## What is grep ?
`grep` is a command-line utility in Unix and Linux used for searching plain-text data for lines that match a specified pattern. It stands for `"global regular expression print"` and supports regular expressions, allowing for flexible and powerful search capabilities. Users can search through files, standard input, or command output, making it a versatile tool for text processing. Common options include case sensitivity control, line numbering, and inverse matching. `grep` is widely used in scripts and command-line operations for data extraction and analysis, making it an essential tool for system administrators and developers.

---
    grep "Lav" names.txt
The command `grep "Lav" names.txt` searches for the string "Lav" within the file `names.txt`. It returns all lines from the file that contain the specified pattern, allowing users to quickly find relevant entries. This command is useful for filtering text data and locating specific information efficiently.

---
    grep -w "Lav" names.txt
The `-w` option in the command `grep -w "Lav" names.txt` restricts the search to whole words only, ensuring that only instances of "Lav" that appear as a standalone word are matched. This prevents partial matches, such as "Lavender" or "Laver", from being included in the results.

---
    grep -i "lav" names.txt
The `-i` option in the command `grep -i "lav" names.txt` makes the search case-insensitive, allowing it to match "Lav", "lav", "LAV", and any other variations regardless of case. This is useful for finding entries without worrying about the capitalization of the search term.

---
    grep -n "Lav" names.txt
The `-n` option in the command `grep -n "Lav" names.txt` displays the line numbers along with the matching lines in the output. This helps users quickly locate the position of each match within the file, making it easier to reference specific entries.

---
    grep -win "lav" names.txt
The command `grep -win "lav" names.txt` combines the `-w`, `-i`, and `-n` options to search for the whole word "lav" in a case-insensitive manner while displaying line numbers. This ensures that only exact matches as standalone words are returned, along with their corresponding line numbers in the file.

---
    grep -B 3 "lav" names.txt
The `-B 3` option in the command `grep -B 3 "lav" names.txt` instructs `grep` to display three lines of context before each matching line containing "lav". This is useful for providing additional context around the match, helping users understand the surrounding content.

---
    grep -win "Lav" ./*.txt
The pattern `./*.txt` in the command `grep -win "Lav" ./*.txt` specifies that `grep` should search for the term "Lav" in all text files (`*.txt`) located in the current directory (`./`). This allows for a convenient way to filter and search through multiple text files at once without needing to specify each file individually.

---
    grep -rwin "Lav" .
The `-r` option in the command `grep -rwin "Lav" .` enables recursive searching, allowing `grep` to search for the term "Lav" in all files within the current directory and its subdirectories. This is useful for locating matches across multiple files and directories without having to specify each one individually.

---
    grep -wirl "Lav" .
The `-l` option in the command `grep -wirl "Lav" .` instructs `grep` to list only the names of files that contain the whole word "Lav", rather than displaying the matching lines. This makes it easier to identify which files include the specified term, streamlining the search process.

---
    grep -wirc "lav" .
The `-c` option in the command `grep -wirc "lav" .` tells `grep` to count and display the number of lines that match the whole word "lav" across all files in the current directory and its subdirectories. This provides a quick summary of how many lines contain the specified term, rather than showing the actual matching lines.

---
    history
The `history` command displays a list of previously executed commands in the terminal, allowing users to view and reuse past commands easily.

---
    history | grep "ls"
The command `history | grep "ls"` searches the command history for all instances of commands that contain "ls". By piping the output of `history` into `grep`, users can quickly find specific usages of the `ls` command, which is commonly used for listing directory contents. This is helpful for reviewing past actions and recalling specific command options or arguments used.

---
    grep -P "<REGEX>" names.txt
The command `grep -P "<REGEX>" names.txt` uses the `-P` option to enable Perl-compatible regular expressions for pattern matching in the file `names.txt`. This allows for advanced regex features that are not available with basic or extended regex, providing more flexibility in search patterns. It is particularly useful for complex string matching, such as assertions or advanced character classes.

---
    grep -p "\w" companies.txt
The command `grep -P "\w" companies.txt` uses the `-P` option to enable Perl-compatible regular expressions and searches for lines in `companies.txt` that contain any word character (letters, digits, or underscores). This command effectively filters and displays lines that include at least one word character, making it useful for identifying relevant entries in the file.

---
    grep -p "\d{3}-\d{3}-\d{4}" companies.txt
The command `grep -P "\d{3}-\d{3}-\d{4}" companies.txt` uses the `-P` option to enable Perl-compatible regular expressions and searches for patterns in `companies.txt` that match the format of a US phone number (e.g., 123-456-7890). The pattern `\d{3}-\d{3}-\d{4}` specifies exactly three digits followed by a hyphen, another three digits, another hyphen, and four digits. This command is useful for extracting lines that contain valid phone number formats from the file.

---
    alias
The `alias` command in the terminal is used to create shortcuts for longer commands, allowing users to define custom command names or abbreviations. For example, by typing `alias ll='ls -la'`, users can simply use `ll` to list directory contents in a detailed format.

//TODO:

    //setting alias
    alias gpom = "git push origin main"


    //Shortcut in terminal
    Ctrl a
    ctrl e
    ctrl k
    ctrl u
    ctrl r
    tab
    up
    down


    //command
    history
    !2747
    !find
    clear
    git add .;git commit -m "message";git push origin main
    sort -r companies.txt
    sort  companies.txt
    sort -f companies.txt
    sort -n companies.txt
    jobs
    ping google.com
    wget
    brew install wget
    wget <url>
    wget  -o myfile.pdf <url>
    top
    kill <process_id>
    uname
    uname -o
    uname -m
    uname -r
    cat /etc/os-release
    zip files.zip companies.txt
    zip files2.zip companies.txt file.txt
    unzip files2.zip
    hostname
    hostname -i
    useradd User
    passwd User
    userdel Lav
    lscpu
    free
    free -h
    vmstat
    vmstat -S m
    id
    id -g
    id -G
    id -r
    getent group lav
    id User
    lsof
    nslookup google.com
    netstat
    ifconfig
    sed
    cut -c 1-2 companies.txt
    htop
    px aux


    //operators
    ping google.com & ping commclassroom.org
    echo "first" && echo "second"
    echo "first" || echo "second"
    rm -r !(surnames.txt)
    echo "hey" >> names.txt
    echo "hey" > names.txt
    echo "hey" && {echo "hi";echo "hi am goos"}

    //package manager
    apt-get
    snap
    rpm
    yum

