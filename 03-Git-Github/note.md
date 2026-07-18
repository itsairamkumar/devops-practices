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
