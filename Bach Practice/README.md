# Read Me File

# Bash Command Line Tutorials :

> ## The Command Line :

### What The Command Line ?

- The command line, or terminal, is a text-based interface to the operating system, I can type commands in this interface, And I can type these commands by my keyboard and feedback will be displayed under my command as a text,I can running a programme from these command line.

### how does The Command Line work ?

- Presents us with a prompt, After that we entered a command .
- Then you will see output from running the command.
- Presents us with a prompt again.

### how do I get to one ?

- If you're on a Mac then you'll find the program Terminal under Applications -> Utilities. An easy way to get to it is the key combination 'command + space' which will bring up Spotlight, then start typing Terminal and it will soon show up.
- If on Linux then you will probably find it in Applications -> System or Applications -> Utilities. Alternatively you may be able to 'right-click' on the desktop and there may be an option 'Open in terminal'.
- If you are on Windows and intend to remotely log into another machine then you will need an SSH client. A rather good one is Putty (free) .

> ## Basic Navigation

- Relative path : A file or directory location relative to where we currently are in the file system.
- Absolute path : A file or directory location in relation to the root of the file system.
- `pwd` : Print Working Directory shows the current directory.
- `ls` : List the contents of a directory, It will just do a plain listing of our current location.
- `cd` : Change Directories, It will move to another directory, If you run the command cd without any arguments then it will always take you back to your home directory.
- `tilde` : This is a shortcut for your home directory.
- `dot` : This is a reference to your current directory.
- `dotdot` : This is a reference to the parent directory.

> ## More About Files :

- Everything is actually a file.
- In Windows systems and others, the extension is important and the system uses it to determine what type of file it is.
- file [path] :

  - file.exe : an executable file, or program.
  - file.txt : a plain text file.
  - file.png : file.gif, file.jpg ==> an image.

- `file` : obtain information about what type of file a file or directory is.
- `ls -a` : List the contents of a directory, including hidden files.

- Everything is a file under Linux ==> Even directories.
- Linux is an extensionless system ==> Files can have any extension they like or none at all.
- Linux is case sensitive ==> Beware of silly typos.

> ## Manual Pages

- Manual pages are a group of pages that explain every command available on your system with full functions.
- You can invoke the manual pages with the following command :
  - `man` command : Look up the manual page for a particular command.
  - `man -k` search term : Do a keyword search for all manual pages containing the given search term
  - `term>` : Within a manual page, perform a search for 'term'
  - `n` : After performing a search within a manual page, select the next found item.
- The man pages are your friend :
  Instead of trying to remember everything, instead remember you can easily look stuff up in the man pages.

> ## File Manipulation :

- No undo :
  The Linux command line does not have an undo feature. Perform destructive actions carefully.
- Command line options :
  Most commands have many useful command line options. Make sure you skim the man page for new commands so you are familiar with what they can do and what is available.

- `mkdir` :It is short for Make Directory to (create a directory / file).
- `rmdir` to remove a directory ,it is short for Delete directory.
- `touch` : Create a blank file.
- `cp` Copy - ie. Copy a file or directory.
- `mv` : Move - ie. Move a file or directory (can also be used to rename).
- `rm` Remove - ie. Delete a file.
- `-p` which tells (`mkdir`) to make master directories as needed.
- (-v) which makes (`mkdir`) tell us what to do.

> ## Cheat Sheet
  - A quick reference for the main points covered in this tutorial : 
    - [Cheat Sheet](https://ryanstutorials.net/linuxtutorial/cheatsheet.php)
