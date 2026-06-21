# Command cheat-sheet


## Basics 

- pwd: print current dir
- cd: come on...
  - ~ is the home directory
  - \- is the previous directory
- clear: clear terminal
- ls: list
  - -a all, including hidden (starting with .)
  - -s size
  - -h human-readable size
  - -l list in long format (permissions, owner, group, size, mod time, name)
    - note on permissions: 
      - \- is a normal file, d is directory, l is a link
      - rwx for owner/group/everybody else
- file \<file\>: tells information about a file
- type \<cmd\>: gives info on a command, where to find it for example
- which \<executable\>: exact location of an executable

Finding help:
    - help \<built-in\>: reference page for shell builtins (like cd)
    - \<command\> --help: many programs offer a help page
    - man \<command>\: many programs offer a manual page (uses less to display)
    - a lot of documentation can be found in /usr/share/doc 

## less:

- less \<name\>
- page up / b: back
- page down / space: forward
- G: end of file
- 1G: beginning of file
- h: help
- q: quit

## GIT:

- add \<file\> : stage changes for commit
- commit -m "\<message\>" : commit to the repository
- push : update remote repository from your local 

## ln:

- create symbolic link
- ...

## Manipulating files

- Wildcards (https://linuxcommand.org/lc3_lts0050.php):
  - \* match any character
  - ? match a single character
  - [chars] match any character in the set
  - examples:
    - g* match all filenames beginning with g
    - Data??? match all filenames beginning with Data and 3 characters
    - [[:upper]]* match only uppercase files
    - *.[![:lower:]] match any file that does not have extension in lower case

- cp: copy
  - cp file1 file2
  - cp file1 dir1 (creates file1 inside dir1)
  - cp -i (interactive, asks before overwritting)
- mv: move or rename
- rm: remove 
  - rm file1 file2 file3
  - \-r dir1 recursive remove inside the directory
  - \-i interactive
  - useful trick: construct the command but using ls first. Make sure it won't remove anything you don't want removed.


  