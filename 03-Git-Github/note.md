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

    - In Git, options like -m, -u, -b, and -d are called flags. Flags modify the behavior of a command and make it more powerful. For example, -m lets you add a commit message, -u sets the upstream branch, -b creates a new branch, and -d deletes a branch.

- git log

    The git log command displays the commit history of your Git repository. It shows detailed information about every commit, including:

        - Who made the commit (Author)
        - When the commit was made (Date)
        - The unique commit ID (Hash)
        - The commit message    

    >$ git log

#### Simple Definition of Staging area.

The staging area is a temporary place where Git stores the changes you've selected before creating a commit.

When you run the git add command, the selected file is moved to the staging area. This tells Git that you want to include this file in the next commit. Once you run the git commit command, Git permanently saves the staged changes in the repository.

    Example :
    Suppose your project contains five files:

        - readme.md
        - index.html
        - style.css

    Let's say you made changes only to README.md and index.html.

    Now, if you run:

    >$ git add readme.md
    Only the README.md file will be added to the staging area.

    Then, if you run:
    >$ git add index.html
    The index.html file will also be added to the staging area.

    At this point, both README.md and style.css are in the staging area and are ready to be committed. The remaining files are not staged because they were never added.

    Finally when you run:
    >$ git commit -m "Update readme and index"

    Git will create a commit containing only the files that are currently in the staging area.

    1. What happens when we run git commit?

        Whenever you run the git commit command, Git creates a snapshot of the staged changes. This snapshot represents the state of your project at that point in time.

        Each commit is assigned a unique identifier called a commit hash. Git generates this hash using the SHA-1 (Secure Hash Algorithm 1) hashing algorithm. This hash uniquely identifies every commit in your repository.

    2. Where are Git commits stored?

        Git stores all commits inside the .git directory. More specifically, commit objects are stored in the .git/objects folder. This folder contains the commits, blobs (file contents), trees (directory structures), and other Git objects that make up your repository.

- git commit -a
The -a flag stands for all tracked files.

>$ git commit -a -m "Modified f2 file"

Git will:

1. Automatically stage all modified and deleted tracked files.
2. Create a commit with the message "Update project".

- git commit -amend
The --amend option allows you to modify the most recent commit.
You can use it to:

    - Change the last commit message.
    - Add files you forgot to include in the last commit.
    - Update the last commit without creating a new one.

- git commit -s
It adds a Signed-off-by line to the end of your commit message.

    If your Git username and email are:

    - Name: A Sairam Kumar Patro
    - Email: itsairamkumar@gmail.com

    Then the commit message will look like this:

    Add login page

    > Signed-off-by: A Sairam Kumar Patro <itsairamkumar@gmail.com>

Why do we use -s?
 * The -s flag is commonly used in open-source projects. By signing off a commit, you're indicating that you have the right to submit the code and agree to the project's contribution requirements (such as a Developer Certificate of Origin, or DCO).

- git commit --allow-empty
It is used to create a commit even when there are no changes to commit.

What does it do?
 * Normally, Git won't let you create a commit if there are no staged changes. With --allow-empty, Git creates an empty commit—a commit that doesn't contain any file changes but is still recorded in the commit history.

Why is it useful?
 * Empty commits are commonly used to:
 
    - Trigger CI/CD pipelines (GitHub Actions, Jenkins, GitLab CI, etc.).
    - Mark an important milestone in the project's history.
    - Test Git hooks or automation.
    - Start a repository with an initial commit before adding files (less common).
