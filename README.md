# learning-embedded-linux
Notes, experiments and projects, as I build embedded Linux skills.

Coming from an electrical engineering background and bare-metal work experience, I thought it was career relevant to learn more about Linux and build additional skills as an embedded engineer. One of my ideas is also to rediscover the passion for creating and learning a new topic - this is something I've neglected for a while.

_My goals are roughly:_

- Phase 1: Linux as a system. I've already used it a lot before but forgot everything in the meantime. First I want to get re-acquainted with Linux as an OS, get comfortable and agile, start building up the basics and setup a good workspace for starting later with a Raspberry-Pi or other board.
  - use the terminal
  - common commands, shell, file system fundamentals, navigate, permissions...
  - bash scripting
  - processes and internals, threads, system calls, etc...
  - networking and using SSH/SCP
  - install a toolchain, compile a simple hello-world, transfer to the Pi
  - revisit git, makefiles, libraries, etc... just the basic tools.

  References:
  - https://linuxcommand.org/index.php : good for command line basics and the bash scripting part
  - https://bootlin.com/blog/command-line/ : overlaps a bit with linuxcommand but adds about processes and job control. Also a bit about compiling a simple app.
  - https://www.baeldung.com/linux/process-vs-thread#differences-between-process-and-thread : a bit about processes and threads
  - https://zah.uni-heidelberg.de/it-guide/ssh-tutorial-linux : SSH reference
  - https://refspecs.linuxfoundation.org/FHS_3.0/fhs-3.0.pdf : Linux file system

- Phase 2: Linux and hardware.
  - Here I thought of taking a more structured approach. There's so many courses online but I found that bootlin was consistentyl mentioned as one of the best, so I chose the Embedded Linux training by Bootlin.
    - I got a Beaglebone Black to work through the labs
    - Topics to cover:
      - architecture of embedded linux
      - cross-compilation and toolchains
      - understand the boot process, setup and use u-boot
      - configure, build and install a linux kernel
      - create a root filesystem from scratch
      - create file systems for block storage devices
      - select, cross-compile and integrate open-source software libaries and applications
      - understand the main open-source licenses
      - use Linux build system to build a complete embedded platform
      - develop and debug application in a linux system

  References:
    - Course: https://bootlin.com/training/embedded-linux/
    - Slides: https://bootlin.com/doc/training/embedded-linux/embedded-linux-slides.pdf
    - How toolchains are built: https://crosstool-ng.github.io/docs/toolchain-construction/
    - Crosscore-ng: https://github.com/crosstool-ng/crosstool-ng
    -

--------------------------------------------------------------------------------

From here, work in progress:

  * Course 2 — Linux Kernel and Driver Development
    https://bootlin.com/training/kernel/
    Free slides: https://bootlin.com/doc/training/linux-kernel/linux-kernel-slides.pdf
    Free labs (BeagleBone Black): https://bootlin.com/doc/training/linux-kernel/linux-kernel-bbb-labs.pdf
    What it covers: Kernel architecture, how userspace talks to the kernel, writing two complete device drivers from scratch (an I2C device and a serial port controller), Device Tree, memory management, locking, interrupt handling, debugging. Writing a driver for an I2C device from scratch — embedded world but in linux. The interrupt handling and memory management sections will feel familiar conceptually, just in a new context.


- Phase 3: Yocto

- Phase 4: A project?

While doing this, I intend to keep notes and cheat-sheets for future use. I always found my memory to be a weakness - so I had to become good at documenting :)

pedro.d.amaral@gmail.com
