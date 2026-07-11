# learning-embedded-linux
Notes, experiments and projects, as I build embedded Linux skills.

Coming from an electrical engineering background and bare-metal work experience, I thought it was career relevant to learn more about Linux and build additional skills as an embedded engineer. One of my ideas is also to rediscover the passion for creating and learning a new topic - this is something I've neglected for a while.

_My goals are roughly:_

- Phase 1: Linux as a system. I've already used it a lot before but forgot everything in the meantime. First I want to get re-acquainted with Linux as an OS, get comfortable and agile, start building up the basics and setup a good workspace for starting later with a Raspberry-Pi.
  - use the terminal
  - common commands, shell, file system fundamentals, navigate, permissions...
  - bash scripting
  - processes and internals
  - networking and using SSH/SCP
  - install a toolchain, compile a simple hello-world, transfer to the Pi

  References:
  - https://linuxcommand.org/index.php : good for command line basics and the bash scripting part
  - https://bootlin.com/blog/command-line/ : overlaps a bit with linuxcommand but adds a bit

- Phase 2: Linux and hardware. To be detailed
  - some ideas:
    * Course 1 — Embedded Linux System Development
      https://bootlin.com/training/embedded-linux/
      Free slides: https://bootlin.com/doc/training/embedded-linux/embedded-linux-slides.pdf
      Free labs: https://bootlin.com/doc/training/embedded-linux/embedded-linux-bbb-labs.pdf
      What it covers: Cross-compilation toolchains, U-Boot bootloader, kernel configuration and build, root filesystem from scratch, filesystems, open-source component integration, application development and debugging on embedded hardware. Everything you need to understand before touching a kernel module. It assumes Linux command line knowledge and nothing else. This is where to start.
    * Course 2 — Linux Kernel and Driver Development
      https://bootlin.com/training/kernel/
      Free slides: https://bootlin.com/doc/training/linux-kernel/linux-kernel-slides.pdf
      Free labs (BeagleBone Black): https://bootlin.com/doc/training/linux-kernel/linux-kernel-bbb-labs.pdf
      What it covers: Kernel architecture, how userspace talks to the kernel, writing two complete device drivers from scratch (an I2C device and a serial port controller), Device Tree, memory management, locking, interrupt handling, debugging. Writing a driver for an I2C device from scratch — embedded world but in linux. The interrupt handling and memory management sections will feel familiar conceptually, just in a new context.


- Phase 3: Yocto

- Phase 4: A project?

While doing this, I intend to keep notes and cheat-sheets for future use. I always found my memory to be a weakness - so I had to become good at documenting :)

pedro.d.amaral@gmail.com
