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
  - -l list in long format:
    permissions, owner, group, size, mod time, name
    - note on permissions: 
      - \- is a normal file, d is directory, l is a link
      - rwx for owner/group/everybody else
      See here: https://linuxcommand.org/images/file_permissions.png
      - see chmod below

- file \<file\>: tells information about a file
- type \<cmd\>: gives info on a command, where to find it for example
- which \<executable\>: exact location of an executable
- du \<file, directory\>: display size, -h for human readable
- grep: search
    - grep [options] pattern [file]
    - examples: 
      grep 'someregexpattern' ./* 
      grep -E '^\#\#' cheat-sheet.md
- echo (see below)
- printenv : prints all environment variables (e.g. $USER)
- export \<var\>="something" : sets an environment variable (use echo $var to print)


## Finding help

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

Passwords are no longer accepted. Setup an SSH key:
https://dev.to/gervaisamoah/add-a-new-ssh-key-for-github-on-your-new-computer-54l1 

- add \<file\> : stage changes for commit
- commit -m "\<message\>" : commit to the repository
- push : update remote repository from your local 

## ln:

- create symbolic link
- ...

## Permissions

- Reference: https://linuxcommand.org/lc3_lts0090.php
- chmod \<permission\> \<file\>
    rwx rwx rwx = 111 111 111
    rw- rw- rw- = 110 110 110
    rwx --- --- = 111 000 000

    rwx = 111 in binary = 7
    rw- = 110 in binary = 6
    r-x = 101 in binary = 5
    r-- = 100 in binary = 4

    Example:
    chmod 600 file1: read write permission to owner, no one else can touch it
    Common codes:
    777 - free for all
    755 - only owner may write, anyone can read execute
    700 - owner has full rights, no one else can do anything
    666 - all users may read and write the file
    644 - owner may ready and write, others may only read
    600 - only owner may write, others can't do anything
- chown \<user\> \<file\> : change the owner (must be called as superuser)
- chgp \<group\> \<file\> : change the group ownership (must be owner of file or dir)

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

- echo: a shell built in that prints its arguments 
  - if the argument expends into something, echo will show us that.
  - see the expansion chapter below
  - example:
    - echo c : c
    - echo c* : cheat-sheet.md
    - echo ~ : /home/pedro
    - echo -e : escapes characters, e.g. echo -e "one\ntwo\three"
    - echo $(($((5**2)) * 3)) : 75
    - echo Front-{A,B,C}-Back: Front-A-Back ... Front-C-Back
    - echo Front-{0..5}-Back: Front-0-Back ... Front-5-Back
    - echo a{A{1,2},B{3,4}}b : aA1b aA2b aB3b aB4b
  - the above can be very useful for creating files or directories:
    - create a file with all the possible license plates in Portugal:
      echo {A..Z}{A..Z}-{0..9}{0..9}-{A..Z}{A..Z} > all_plates.txt
    - create a file with all letters in each line:
      echo {A..Z} | tr ' ' '\n' > all_letters.txt

## Redirection

- \> output to create file
- \>\> output to append file
- \< input to command
- \| pipelines the output of one command to another.
    example: 
     ll /s* | less : search all files or directors in / starting with s and display the output with less
     cat unsorted_list_with_dupes.txt | sort | uniq | pr | lpr

## Expansion 

  - pathname expansion: see the echo examples 
  - tilde expansion: ~ is home
  - arithmetic expansion: see the echo instructions above
  - parameter expansion: printenv and export, e.g.
    - export HANDSOME="pedro"
    - echo $HANDSOME
  - command substitution: similar to pathname expansion, e.g. 
    - ls -sh $(which ruby)
    - file $(ls /usr/bin/* | grep bin/zip)
  - double quotes: supress word-splitting, pathname, tilde, and brace expansion (keep parameter, arithmetic and command expansions)
  - single quotes: supress ALL expansions
  

## TAR (tape archive record)

- tar -xvzf files.tar.gz - C my_files: 
  - x: extract (opposite of collect)
  - v: verbose output
  - z: decompress using gzip
  - f: file immediately after 
  - -C: directory with a name of choice

## Job control

- ps : list processes
- jobs : lists own processes, ran by the user (simpler)

- \<program\> + ctrl-z : start a program and suspend
- bg : place a job in background execution
- fg : place a job in foreground execution

- \<program\> & : start a program and send to background
  - ctrl+z

- kill \<process_number\> or %\<job_number\>: kill a process
  example: kill %1 or kill 1234
  - can send OS signals to the process, example:
    - SIGHUP : hang-up, sent when terminal is closed, the program listens 
    - SIGINT : interrupt the process (ctrl-c), the program listens
    - SIGTERM : termination, the default signal sent by kill, the program listens
    - SIGKILL : kill, immediate termination by the kernel (program doesn't listen to this)
    


