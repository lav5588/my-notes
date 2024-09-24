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


---
## How to set aliases of commands ?
In Linux, when setting an alias, you need to use the correct syntax. Here’s how to define your alias properly:

### Making the Alias Permanent
If you want the alias to be available every time you open a terminal, add it to your shell configuration file:

1. For **bash**, open your `.bashrc` file:
   ```bash
   nano ~/.bashrc
   ```



3. Add the alias line at the bottom:
   ```bash
   alias gpom="git push origin main"
   ```
   Make sure there are no spaces around the `=` sign.

4. Save and close the file, then run:
   ```bash
   source ~/.bashrc   # For bash
   ```

---

## Shortcuts


1. **`Ctrl + A`**:  
   Moves the cursor to the beginning of the current line.

2. **`Ctrl + E`**:  
   Moves the cursor to the end of the current line.

3. **`Ctrl + K`**:  
   Deletes (cuts) everything from the cursor position to the end of the line.

4. **`Ctrl + U`**:  
   Deletes (cuts) everything from the cursor position to the beginning of the line.

5. **`Ctrl + R`**:  
   Searches the command history interactively. You can type a part of a previous command and the shell will search for it.

6. **`Tab`**:  
   Auto-completes commands, file names, and directories. If multiple options are available, pressing `Tab` twice shows a list of possible completions.

7. **`Up Arrow`**:  
   Navigates backward through the command history to view and edit previously entered commands.

8. **`Down Arrow`**:  
   Navigates forward through the command history, after using the up arrow.


---
## What is package managers ?
  ### Package Manager Overview:
A **package manager** is a tool that automates the process of installing, upgrading, configuring, and removing software packages from a system. It ensures that dependencies are handled properly and simplifies software management.

### 1. **apt-get**:
   - APT (Advanced Package Tool) is the package manager for Debian-based systems like Ubuntu. `apt-get` is a command-line tool used to install, update, and remove software packages from the system's repositories.
   - It manages `.deb` packages and resolves dependencies automatically.

### 2. **snap**:
   - Snap is a package management system designed by Canonical for universal, sandboxed application distribution across Linux distros. Applications are bundled with all their dependencies and run in isolation.
   - It's particularly useful for installing newer versions of software that may not be available in traditional package repositories.

### 3. **rpm**:
   - RPM (Red Hat Package Manager) is the package management system used by Red Hat-based distributions like Fedora and CentOS. It handles `.rpm` packages.
   - While it provides low-level package management, dependency resolution must be handled manually or with higher-level tools like `yum` or `dnf`.

### 4. **yum**:
   - YUM (Yellowdog Updater, Modified) is a high-level package manager for Red Hat-based systems that automates the process of installing, updating, and resolving dependencies for `.rpm` packages.
   - It has been largely replaced by `dnf` in more recent Fedora and CentOS versions, but is still widely used.

These package managers simplify software management and ensure a consistent system environment.

---
    history

The `history` command displays a list of previously executed commands in the terminal session, allowing you to view your command history. Each command is numbered, making it easy to recall and rerun commands using their corresponding number. This is useful for tracking command sequences or quickly repeating past commands.

---
    !2747

`!2747` runs the 2747th command from your shell history. The number corresponds to a specific command in your shell history. You can use the `history` command to view your past commands and find the corresponding number.

---
    !find

`!find` runs the most recent command that starts with `find` from your shell history. It's a shortcut for quickly repeating a previous `find` command without having to retype it.

---
    clear

`clear` clears the terminal screen, giving you a clean workspace. It does not affect running processes or commands, it only resets the visible display in the terminal.

---
    git add .;git commit -m "message";git push origin main

`git add .; git commit -m "message"; git push origin main` stages all changes in the current directory, commits them with the provided message, and then pushes the changes to the `main` branch on the remote repository. The `;` separates multiple commands in one line.

---
    sort -r companies.txt

`sort -r companies.txt` sorts the contents of the file `companies.txt` in reverse (descending) order. This only displays the sorted output and does not modify the file itself.

---
    sort  companies.txt

`sort companies.txt` sorts the file `companies.txt` in ascending order (the default behavior). The output is displayed in the terminal, and the file itself remains unchanged.

---
    sort -f companies.txt

`sort -f companies.txt` performs a case-insensitive sort of `companies.txt`. This option ignores case differences while sorting the lines in the file.

---
    sort -n companies.txt

`sort -n companies.txt` sorts `companies.txt` numerically, interpreting the file contents as numbers rather than text. Useful for files with numeric data.

---
    jobs

`jobs` lists all the background and suspended jobs running in the current terminal session. It shows job IDs and their current state (running, stopped, etc.).

---
    ping google.com

`ping google.com` sends ICMP echo requests to `google.com` to check its network connectivity and response time. It's useful for diagnosing network issues.

---
    wget

`wget` is a command-line utility for downloading files from the web. It supports HTTP, HTTPS, and FTP protocols.

---
    brew install wget

`brew install wget` installs the `wget` tool using Homebrew, a package manager for macOS and Linux. If `wget` is not already installed, this command downloads and installs it.

---
    wget <url>

`wget <url>` downloads the file located at the specified `<url>` and saves it to the current directory. By default, the file is saved with its original name.

---
    wget  -o myfile.pdf <url>

`wget -o myfile.pdf <url>` downloads the file from the specified `<url>` and saves it as `myfile.pdf`. The `-o` option allows you to specify a custom file name.

---
    top

`top` displays real-time system information including running processes, CPU usage, memory usage, and more. It provides a dynamic view of system resource consumption. Useful for monitoring system performance and diagnosing issues.

---
    kill <process_id>

`kill <process_id>` terminates a process by sending it a signal, usually to stop execution. The process ID (PID) must be specified to target the correct process. Commonly used to stop misbehaving or unresponsive programs.

---
    uname

`uname` prints basic system information, such as the operating system name. It is helpful for identifying the system type and version being used.

---
    uname -o

`uname -o` displays the operating system name specifically. It gives you a more detailed view of which OS is running.

---
    uname -m

`uname -m` outputs the machine hardware name, such as `x86_64`, which shows the architecture of your system (32-bit or 64-bit).

---
    uname -r

`uname -r` shows the kernel version running on your system, which can be useful for troubleshooting and ensuring compatibility with software.

---
    cat /etc/os-release

`cat /etc/os-release` prints detailed information about the operating system, including the distribution name, version, and release ID. This is a reliable way to identify Linux distributions.

---
    zip files.zip companies.txt

`zip files.zip companies.txt` compresses the file `companies.txt` into a ZIP archive named `files.zip`. This reduces the file size and makes it easier to share or store.

---
    zip files2.zip companies.txt file.txt

`zip files2.zip companies.txt file.txt` compresses multiple files (`companies.txt` and `file.txt`) into a single ZIP archive named `files2.zip`. Useful for bundling files together.

---
    unzip files2.zip

`unzip files2.zip` extracts the contents of `files2.zip`, restoring the original files. It's commonly used to decompress files for access and usage.

---
    hostname

`hostname` displays the name of the current host or system on the network. It provides a quick way to identify the machine you are working on, especially in a multi-system environment.

---
    hostname -i

`hostname -i` shows the IP address associated with the current hostname. This can help verify network settings or troubleshoot connectivity issues.

---
    useradd User

`useradd User` creates a new user account named "User" on the system. This command requires administrative privileges and is essential for managing user access.

---
    passwd User

`passwd User` sets or changes the password for the specified user account. It prompts for a new password and is used to secure user accounts.

---
    userdel Lav

`userdel Lav` removes the user account named "Lav" from the system. This command deletes the user and, optionally, their home directory if specified.

---
    lscpu

`lscpu` provides detailed information about the CPU architecture, including the number of CPUs, cores, threads, and CPU family. It is useful for understanding system capabilities.

---
    free

`free` displays the total amount of free and used memory in the system, including physical and swap memory. This is essential for monitoring system performance and resource usage.

---
    free -h

`free -h` shows the memory usage in a human-readable format, using appropriate size units (KB, MB, GB). It makes it easier to interpret memory statistics at a glance.

---
    vmstat

`vmstat` reports information about processes, memory, paging, block I/O, traps, and CPU activity. It provides a snapshot of system performance and is useful for performance monitoring.

---
    vmstat -S m

`vmstat -S m` displays memory statistics in megabytes instead of the default kilobytes. This option helps users analyze memory usage more intuitively, especially on systems with large amounts of memory.

---
    id

`id` displays the user ID (UID) and group ID (GID) of the current user, along with the groups they belong to. This command helps identify user permissions and roles within the system.

---
    id -g

`id -g` shows only the group ID (GID) of the current user. This is useful for quickly checking the primary group without additional details.

---
    id -G

`id -G` lists all the group IDs (GIDs) that the current user belongs to. This command provides insight into the user's group memberships and permissions.

---
    id -r

`id -r` displays the real user ID (UID) and group ID (GID) instead of any effective IDs, which can be helpful for understanding user privileges in various contexts.

---
    getent group lav

`getent group lav` retrieves information about the group named "lav" from the system's group database. It shows details like GID and group members, aiding in user management.

---
    id User

`id User` displays the UID and GID for the specified user "User," along with their group memberships. This is useful for checking the privileges and roles of other users.

---
    lsof

`lsof` lists open files and the corresponding processes using them. It provides valuable information for diagnosing issues related to file usage and system performance.

---
    nslookup google.com

`nslookup google.com` queries the DNS to retrieve the IP address associated with the domain "google.com." This command is helpful for network troubleshooting and verifying DNS resolution.

---
    netstat

`netstat` displays network connections, routing tables, interface statistics, and more. It is useful for monitoring network activity and diagnosing network issues.

---
    ifconfig

`ifconfig` shows the current network configuration for all active network interfaces. It provides details like IP addresses, subnet masks, and interface statuses, although it's being replaced by `ip` in many distributions.

---
    sed

`sed` is a stream editor used for parsing and transforming text in a pipeline. It allows for complex text manipulations such as substitutions, deletions, and insertions.

---
    cut -c 1-2 companies.txt

`cut -c 1-2 companies.txt` extracts the first two characters from each line of the file `companies.txt`. This command is useful for retrieving specific portions of text from a file.

---
    htop

`htop` is an interactive process viewer that provides a real-time view of system resources, running processes, and performance metrics. It offers a more user-friendly interface than `top`.

---
    ps aux

`ps aux` displays a snapshot of all running processes on the system, including their user, CPU usage, memory usage, and command line. This command is essential for monitoring system activity and troubleshooting processes.

---
    ping google.com & ping commclassroom.org

In the command `ping google.com & ping commclassroom.org`, the `&` operator runs the first `ping` command in the background while immediately starting the second `ping` command. This allows both commands to execute concurrently without waiting for each other to finish.

---
    echo "first" && echo "second"

The command `echo "first" && echo "second"` uses the `&&` operator to execute the second `echo` command only if the first one is successful. This is useful for chaining commands where the success of one command dictates whether the next should run.

---
    echo "first" || echo "second"

In `echo "first" || echo "second"`, the `||` operator runs the second `echo` command only if the first one fails. This operator is useful for providing alternative actions in case of errors in the preceding command.

---
    rm -r !(surnames.txt)

The command `rm -r !(surnames.txt)` uses the extended globbing feature to remove all files in the current directory except `surnames.txt`. This allows for selective file operations based on patterns.

---
    echo "hey" >> names.txt

In `echo "hey" >> names.txt`, the `>>` operator appends the string "hey" to the end of `names.txt`, preserving existing content. This is useful for adding information to a file without overwriting it.

---
    echo "hey" > names.txt

The command `echo "hey" > names.txt` uses the `>` operator to overwrite `names.txt` with the string "hey". This operator is useful when you want to replace the entire content of a file with new data.

---
    echo "hey" && {echo "hi";echo "hi am goos"}

In `echo "hey" && {echo "hi"; echo "hi am good"}`, the command runs the block of commands inside the braces only if the first `echo` command succeeds, effectively grouping related commands together for conditional execution. This is useful for executing multiple commands in a single logical block based on the success of a preceding command.

---