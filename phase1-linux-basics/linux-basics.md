# Linux knowledge

## Structure

  The standard containing all explanations and rules: 
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
  - /proc contains "little peepholes into the kernel". It's a virtual directory containing entries that correspond all processes running in the system, e.g. /proc/cpuinfo contains all CPU information the kernel knows about.
  - /media contains mount points. Different physical storage devices in Linux are attached to the file system tree using mount points. Mounting is attaching the device to the device tree. See /etc/fstab. 

## Types of files

  - When running ll, the first letter represents the file
  - \- is a normal file
  - d is directory
  - l is a link
  - c is a character device
  - s is a socket
  - b is a block device

  