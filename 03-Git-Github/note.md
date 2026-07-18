# Git and Github Note
## Day 1

### 1. Setting up personal info
---
Before working with Git, you should set your username and email address. Git uses this information to identify who made each commit, so it's an important first step.

So, the first thing we need to do is tell Git who we are by setting our name and email address.

Open Git Bash and run the following commands from anywhere:

> $ git config --global user.name "A Sairam Kumar Patro"

Press Enter.

Then run:

> $ git config --global user.email "itsairamkumar@gmail.com"

Press Enter again.

Note: You can use any valid email address you want. It doesn't have to be the same email address you use for your GitHub account. However, if you want your commits to appear as linked to your GitHub profile, it's recommended to use the email associated with your GitHub account.

Now, if you want to verify which username and email are currently configured, simply run:

    - git config : Checks the username for the current repository. If it's not set locally, Git may show the effective value from a higher level.

    Example : $ git config user.name
              $ git config user.email


    - git config --global : Checks the username stored in your global Git configuration.
    Example : $ git config --global user.name
              $ git config --global user.email

### 2. Git Basic Commands
---
There are several Linux commands you can use to create a file, such as cat, touch, vi, nano, and echo.

In this example, I'll use the nano command to create a file.

> $ nano test.txt

**How do we create a local Git repository?**

To create a local Git repository, we use the 'git init' command.

The word init stands for initialize. When you run git init, Git initializes the current folder as a Git repository, allowing Git to start tracking changes in that project.

> $ git init

Whenever you run the git init command, Git creates a hidden folder named .git inside your project directory.

This .git folder contains all the information Git needs to manage and track your project, such as commit history, branches, configuration, and other repository data.

Since the .git folder is hidden by default, you won't see it in File Explorer. To view hidden files and folders in Windows, follow these steps:

1. Open File Explorer.
2. Click the View tab (or View > Show in Windows 11).
3. Enable the Hidden items checkbox.

Once you've enabled hidden items, you'll be able to see the .git folder inside your project directory.

Here's a polished, technically accurate version for your tutorial:

The second way to view hidden files is by using the `ls -al` command.

>$ ls -al


This command displays **all files and folders**, including hidden ones (such as the `.git` directory).

- git status

    The `git status` command shows the current state of your repository. It tells you which files are:

    * Untracked (new files Git isn't tracking yet)
    * Modified (files that have been changed)
    * Staged (files ready to be committed)

    >$ git status

- git add

    The `git add` command adds a specific file to the staging area. Only the file you specify will be staged.

    > $ git add note.md

- git add .

    The `git add .` command stages all new and modified files in the current directory and its subdirectories.

    > $ git add .

- git commit

    The `git commit` command saves the changes that are currently in the staging area. You can think of a commit as taking a snapshot of your project at that point in time.

    > $ git commit -m "Add a meaningful commit message"

    For example:
    >$ git commit -m "Create README file"

- git log

    The git log command displays the commit history of your Git repository. It shows detailed information about every commit, including:

        - Who made the commit (Author)
        - When the commit was made (Date)
        - The unique commit ID (Hash)
        - The commit message    

    >$ git log