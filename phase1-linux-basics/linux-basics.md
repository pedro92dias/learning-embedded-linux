# Linux knowledge

## Structure

  The standard containing all explanations and rules:
  https://www.pathname.com/fhs/
  https://refspecs.linuxfoundation.org/FHS_3.0/fhs-3.0.pdf

  - / root directory where the file system begins
  - /boot where Linux kernel and bootloader files reside
    - vmlinuz is the kernel
    - there's bootloader executables like EFI there too
  - /etc configuration files for the system
    - /etc/passwd file with info for each user, where accounts are defined
    - /etc/fstab file containing table of devices mounted at boot, including disk drives. See /media. This is for hard-drives. Other storage devices are removable and usually do not stay mounted all the time.
    - /etc/hosts file lists host names and IP addresses known to the system
    - /etc/init.d directory containing scripts that start system services at boot time
  - /bin contains essential system programs
  - /sbin contains system administration programs, for superuser
  - /usr/bin contains user programs
  - /usr/sbin contains user programs for system administration
  - /usr
    - /usr/share/... X11 window system files, dictionaries, documentation, manual pages
    - /usr/local to install software or other files that are not part of the distro
  - /var files that change while the system is running
    - /var/logs
    - /var/spool holds temporary files to be used
  - /lib shared libraries, like DLLs
  - /home only place where users can write
  - /home/\<name\> is usually the user directory and where Linux logs in to (also ~)
  - /root superuser home directory
  - /tmp temporary folder for programs to use
  - /dev contains devices. In Linux devices are treated as files (one can read from and write to them). E.g. /dev/fd0 is the first floppy disk drive, /dev/sda is the first hard drive. All the devices that the kernel understands are represented here.
    - see devices below
  - /proc contains "little peepholes into the kernel". It's a virtual directory containing entries that correspond all processes running in the system, e.g. /proc/cpuinfo contains all CPU information the kernel knows about.
  - /media contains mount points. Different physical storage devices in Linux are attached to the file system tree using mount points. Mounting is attaching the device to the device tree. See /etc/fstab
  - /lost+found contains corrupt files
  - /sys contains system and device controls, e.g. cpu frequency, power settings...


## Special devices

- /dev/null : data sink, everything is removed when written to this file
  example: mplayer &> /dev/null gets rid of all output
- /dev/zero : always returns \0
  example: dd if=/dev/zero of=disk.img bs=1k count=2048
- /dev/random : returns random bytes
  example: xxd /dev/random
- /dev/urandom : pseudo random, used when a true source of randomness doesn't exist


## Tasks

- Process: instance of a running program
  - several processes can run at the same time
  - a process has open files, allocated memory, stack, PID, parent, priority, state...
  - see Job Control in cheat-sheet.md


## Types of files

Almost everything in Unix is a file: directories, symbolic links, peripherals, devices, pipes, sockets

  - When running ll, the first letter represents the file
    - \- is a normal file
    - d is directory
    - l is a link
    - c is a character device
    - s is a socket
    - b is a block device

  - links:
    - hard links:
      - points to the a files physical data block (inode)
      - removing the original file has no effect on hard link contents - the inode still exists and the hard link still accesses it
      - contents are only removed when there are no more hard links to the inode
      - by default ln creates a hard link

    - soft link:
      - points to the path of a file, like a desktop shortcut
      - removing the original file makes the soft link dangling

    SOFT LINK                 HARD LINK

    +------+    +------+    +------+   +------+
    | Orig |<---| Soft |    | Orig |   | Hard |
    +------+    +------+    +------+   +------+
      |                       |          |
      v                       v          |
    (Data)                  (Data)<------+


## Shells
  - Tools to execute user commands
  - Can be scripted
  - sh the Unix traditional and basic shell
  - bash is the most famous and popular (bourne again shell)


## Some important scripts

The following are read by login shells:
  - /etc/profile: global configuration script for all users
  - ~/.bash_profile: personal user startup file
  - ~/.bash_login: if previous not found, bash attempts this
  - ~/.profile: if previous not found, bash attempts this

The following are read by non-login shells:
  - /etc/bash.bashrc : global configuration for all users
  - ~/.bashrc : user personal startup file
    - The user can add any start-up scripts here
    - Can define aliases, default env vars, prompt, etc.


Non-login shells inherit the environment from their parent process (usually a login shell).

## Bash scripts

- Reference: https://linuxcommand.org/lc3_writing_shell_scripts.php#contents
- (see examples in the folder)
- Positional parameters, control flow, errors and signals, etc...
