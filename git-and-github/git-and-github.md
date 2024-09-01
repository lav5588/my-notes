`Git` is a software and `GitHub` is a service.

# Git
![image](image.png)
![alt text](image-1.png)

    git --version
`git --version` is used to check the version of git.

    git status
`git status` is used to check the status of the git repository.

    ls -la
`ls -la` is used to show all hidden and shown files and folders in the repository.

    git init
`git init` is used to initialize the git repository. After this git starts tracking changes into the repository.

![alt text](image-2.png)

    git add <file name which we want to track>
`git add` is used to add files in the tracking zone (staging area) of the repository. Sometimes we use `git add .`.  `.` specifies to put all the changed files in the tracking zone.

    git commit -m "some commit message"
`git commit` is used to commit changes to the files which are in staging area. `-m` is tag to write some message why we commit changes.

![alt text](image-3.png)

    git log
`git log` is used to log all the commits and details.

    git log --oneline
`git log --oneline` is used to show the logs of commits int one line each commit.
    
    git config --global user.name "Lav Kumar yadav"
`git config --global user.name "Lav Kumar yadav"` is used set the username globally to the git system. whenenver we change in any repository this username will be shared.
    
    git config --global user.email "lavkumar3000@gmail.com"
`git config --global user.name "lavkumar3000@gmail"` is used set the email globally to the git system. whenenver we change in any repository this email will be shared.

    git config --global core.editor "code --wait"
`git config --global core.editor "code --wait"` is used to set the code editor for git as VsCode. It opnes the vscode and wait for to close the editor.

![alt text](image-4.png)

    cat .gitconfig
If we run this cmd from `home directory` it will open the .gitconfig file.