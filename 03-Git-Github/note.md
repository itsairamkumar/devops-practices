# Git and Github Note
## Day 1

### Setting up personal info

Before working with Git, you should set your username and email address. Git uses this information to identify who made each commit, so it's an important first step.

So, the first thing we need to do is tell Git who we are by setting our name and email address.

git bash par jake kahin par bhi wahan ek command run karna he
jaise ki

$ git config --global user.name "A Sairam Kumar Patro" then hit enter
$ git config --global user.email "itsairamkumar@gmail.com then hit enter

aap yahan email par jo bhi mail address dal sakte ho aisa nahi he ki sirf wohi git bala mail dalna he.

agar check karna he konsa name and email set kiya gaya he so simply use this command

    - git config : Checks the username for the current repository. If it's not set locally, Git may show the effective value from a higher level.

    Example : $ git config user.name
              $ git config user.email


    - git config --global : Checks the username stored in your global Git configuration.
    Example : $ git config --global user.name
              $ git config --global user.email
