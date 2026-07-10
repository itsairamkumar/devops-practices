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

        > : It overwrites the file content, meaning the old content is removed and replaced with new content.

            Example : echo "Myself krishna" > notes.md

        >> : It appends content to a file, meaning the new content is added below the existing content.

            Example : echo "Myself krishna, how's your day?" >? notes.md
        
        > = replace
        >> = add below

## Part C - Basic Editor use

    - 7. nano : Nano is a text editor, similar to Notepad. If it is available on your system, it will be easy to use and access.

        Example : nano notes.txt

        Basic points to remember:
            Ctrl + O = Write Out / Save
            Then press Enter
            After that, press Ctrl + X to exit the file

    - 8. vi / vim basics : In the era of DevOps, you should know the basics of vi. It is a terminal-based text editor in Linux/Unix that is used to open, edit, save, and exit files.

        Example : vi notes.txt

        Basic vi workflow:
            Press i → enter Insert mode
            Type your text
            Press Esc → exit insert mode
            Type :wq → save and quit
            Type :q! → quit without saving

## Part D - Permissions intro

    - 9. ls -l : Command tells you what permissions are given to each file or directory, along with full details.

        Example : ls -l

        Output : -rw-r--r-- 1 Master 197121   5180 Jul 10 15:21  day2_note.md

            Permission Breakdown in `ls -l`
            In the output of `ls -l`, the **first character** shows the **file type**:

                * `-` = normal file
                * `d` = directory

            After that, the **next 9 characters** represent **permissions**.
            These 9 characters are divided into **3 groups of 3**:

                rw-   r--   r--

            These 3 groups represent:

                1. **Owner**
                2. **Group**
                3. **Others**

            Meaning of permission characters

                `r` = **read**
                `w` = **write**
                `x` = **execute**

            Example

                `rw-` = read + write
                `r--` = read only
                `---` = no permission
    - 10. chmod : The `chmod` command is used to **change file or directory permissions**.

        Example : chmod u+x notes.txt

        Meaning

            `u` = user / owner
            `+x` = add execute permission

        So, this command gives **execute permission to the owner** of `notes.txt`.

        Common Symbolic Examples

            chmod u+x notes.txt
            chmod g+w notes.txt
            chmod o-r notes.txt

        Meaning of symbols

            `u` = owner / user
            `g` = group
            `o` = others

        Explanation

            `chmod u+x script.sh` → add execute permission for the owner
            `chmod g+w notes.txt` → add write permission for the group
            `chmod o-r secret.txt` → remove read permission for others
        
        Numeric Permission – Intro Level
    
        In numeric format, each permission has a value:

            `7` = `rwx`
            `6` = `rw-`
            `5` = `r-x`
            `4` = `r--`
            `0` = no permission

        Examples

            chmod 045 notes.txt
            chmod 644 script.sh
        
        Basic

            * `045` → owner has **no permission**, group **read only** and others have **read + execute**
            * `644` → owner has **read + write**, group **read only** and others have **read only**

        The most commonly used permission sets in real Linux/DevOps work are 644, 755, 700, and sometimes 777.

            644 → for normal files
            755 → for scripts and executable files
            700 → for private files/directories
            777 → gives full permission to everyone, but should be avoided unless absolutely necessary
        
    11. whoami : It shows current logged-in user.
        
        Example : whoami
        Output : Master

    12. id : It shows the current user's user ID (UID), group ID (GID), and the groups the user belongs to.

        Example : id 
        Output : uid=197609(Master) gid=197121 groups=197121

    13. groups : It shows which groups the current user belongs to.

        Example : groups
        Output : If group mapping is available, the group name is shown. Otherwise, the system may show “cannot find name for group ID …” along with the GID.
    
    14. hostname : It shows the name of the machine/system.

        Example : hostname
        Output : DESKTOP-3VR7RHO

# 3) In DevOps why are users and groups important?

        - Jenkins runs under a specific user account.
        - Docker daemon permissions are important.
        - Application files may be owned by a different user.
        - SSH key permissions are very strict.
        - Deployment scripts may fail to run if the execute permission is missing.
        - A log file may not be readable if the required group permission is missing.
