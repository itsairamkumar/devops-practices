# 1) Goal of Day 2

## Topic: File Viewing, Editing Basics, Permissions Intro, Users & Groups Intro
Today’s goal is to learn how to view file contents in Linux, do basic file editing, understand permissions, and get an introduction to users and groups.

## File Viewing / Editing
- `cat`
- `head`
- `tail`
- `less`
- `echo`
- `>` vs `>>`
- `nano` ya `vi` basics

## Permissions Intro
- Linux permissions ka format samajhna
- `r`, `w`, `x`
- owner / group / others
- `chmod` ka basic use

## Users / Groups Intro
- current user kaise check karte hain
- `whoami`
- `id`
- `groups`
- `hostname`

# 2) Why it is important

In DevOps, these are things you will deal with regularly in Linux:

- Viewing logs
- Opening and editing configuration files
- Checking application environment files
- Troubleshooting permission-related issues
- Understanding the root cause of “permission denied” errors
- Working with user and group context in tools like Jenkins, Docker, EC2, and Ansible

If you do not understand how to view files, edit them, and manage permissions in Linux, it will create confusion later when working with real DevOps tools and workflows.

For example:

- Jenkins pipeline scripts may fail and you may not understand why
- Docker volume and configuration issues will be harder to troubleshoot
- You may struggle while working with Nginx or Apache configuration files
- SSH keys, deployment scripts, and automation tasks may throw permission errors

That is why Day 2 is highly practical and very important.

## Part A - Viewing File Content
    - 1. Cat : It displays the entire contents of a file at once.
            
            Example : cat /d/DevOps/01-Linux/Day-01_Linux-Basics_FileSystem_Navigation_File-Operations/day1_note.md

        When to use?
        - To view a small file
        - To quickly verify the file content

    - 2. head : Displays the beginning of a file. By default, it usually shows the first 10 lines.

            Example : head /d/DevOps/01-Linux/Day-01_Linux-Basics_FileSystem_Navigation_File-Operations/day1_note.md
        
        head -n 5 : Displays the number of lines specified after -n.

            Example : head -n 1 /d/DevOps/01-Linux/Day-01_Linux-Basics_FileSystem_Navigation_File-Operations/day1_note.md

            head -n 5 /d/DevOps/01-Linux/Day-01_Linux-Basics_FileSystem_Navigation_File-Operations/day1_note.md

        A real use of head is to quickly view the beginning of a large log file.

    - 3. tail : Displays the end of a file. By default, it usually shows the last 10 lines.
    
            Example : tail /d/DevOps/01-Linux/Day-01_Linux-Basics_FileSystem_Navigation_File-Operations/day1_note.md
        
        tail -n 5 : Displays the number of lines specified after -n.

            Example : tail -n 1 /d/DevOps/01-Linux/Day-01_Linux-Basics_FileSystem_Navigation_File-Operations/day1_note.md

            tail -n 5 /d/DevOps/01-Linux/Day-01_Linux-Basics_FileSystem_Navigation_File-Operations/day1_note.md

        A real use of tail is to view the latest portion of log files, which is very useful for checking recent entries.

    - 4. less : less is used to view a large file page by page by scrolling through it.

        Example : less /d/DevOps/01-Linux/Day-01_Linux-Basics_FileSystem_Navigation_File-Operations/day1_note.md

        less command basic controls are

            - Space → next page
            - b → previous page
            - /word → search
            - q → quit

        Real uses of less include opening large files and inspecting log files or configuration files conveniently.

## Part B - Adding or Overwriting Content in a File

    - 5. echo : It is used to print text to the terminal.

            Example : echo "Drop your message"

    - 6. > vs >> : This is very important

## Part C - Basic Editor use

    - 7. nano
    - 8. vi / vim basics