# Introduction to Linux

- Linux is an Open Source Unix based Operating System build on top of linux kernal and some GNU Utilities. This linux kernal is developed by a finnish student called Linus Tolvards in 1991. Linux operating system is packaged as Linux dstribution which contains Linux Kernal, System Software and some other supporting libraries which are offered by GNU Project. Several Linux distributions uses title called "Linux" but free software foundation uses it as "GNU/Unix". Famous linux distributions in the market are RPM and Debian.

## History of Linux

- In earlier days, computers are enomorous and having different operating systems for different usecases making it difficult to run different applications and also making software incompatible. And these computers are expensive and inaccessible to public.

- To overcome this problem Bell labs developed Unix in 1969, a simpler and more efficient Operating System using C language not assenbly langauge. Unix has a recycable Kernal and its source code is Open.

- Initially Linux was adopted by many government bodies, financial institutions, universities etc and used it as mainframes and minicomputers.

- During 1980's, many companies such as IBM and HP created their own Unix Distributions and starts selling them which leads to framentation. In 1983, Richard Stallman developed a GNU (GNU's Not Unix) Project with a goal of to make Unix should be available for free. So to make Unix Freely available he created a GPL which is called as General Public License. The GPL ensures that software should be remained free to use, modify and distribute. By late 1980's all the components of GNU project is ready but kernal is not ready yet.

- In 1991, a finnesh student called Linus Tolvards developed the Linux Kernal as Unix alternative for his personal Usecase.Initially named “Freax,” it became “Linux.” He used the GNU C compiler and initially restricted commercial use. In 1992, Torvalds released the Linux kernel under the GNU General Public License, integrating GNU tools and making it free and open-source.

- Today Linux is simply Linux Kernal + GNU Utilities. Linux is just Kernal which is the important component of System and System itself is basically GNU System with Linux added. So when you speaking about this entire operating system you need to say it as "GNU/Linux". (GNU utilities are GNU C compilers, Bash Shell, and other software such as file system required for OS).

## Architecture of Linux

- Linux is majorly consists of 4 layers. Those are :

  **Hardware Layer** : This Layer consists of hardware components such as CPU, RAM, ROM, Mother Board etc.

  **Kernal** : On top of hardware layer we have linux kernal. This linux kernal is intermediatary between user and hardware components. This kernal atually manages the system resources such as RAM, ROM, I/O devices etc.

  **Shell** : This is the command line interface for user to interact with OS.

  **Applications** : On top of this layer many applications are installed.

- Linux distributions we have today are combination of linux kernal + GNU Utilities + Some Customized applications created by some organizations for specific usecases.

## Core Principles of Linux

- **Everything is a File**

  1. In Linux, almost everything (devices, directories, processes, etc.) is treated as a file.

  2. This unifying abstraction simplifies interactions with hardware and software components.

  **Ex** :

  3. `/dev` contains device files for hardware like disks and terminals.

  4. `/proc` provides process and system information as files.

- **Small, Simple and Modular Programs**

  1. Linux utilities and commands are designed to do one task and do it well.

  2. Programs are kept small and focused, promoting modularity and composability.

  **Ex** : Instead of a monolithic tool, Linux offers separate utilities like grep, awk, sed, and cat for text processing. Monolithic simply implies only single code base used for all the tasks. Non- Monolothic means seperate files are there for respective tasks which is actually linux.

- **Text is the Universal Interface**

  1. Text-based communication is preferred for input, output, and configuration.

  2. Files, logs, and settings are typically stored as plain text, making them easy to read, edit, and process.

  **Ex** : Configuration files like /etc/passwd are simple text files.

- **Open Source Collaboration**

  1. Linux is developed under the principles of open-source software.

  2. The source code is freely available, encouraging transparency, collaboration, and community contributions.

  3. Ensures security through peer review and rapid bug fixing.

- **Security and User Permissions**

  1. Security is a core principle, with strict access control mechanisms.

  2. Files and resources are assigned ownership and permissions (read, write, execute) for three categories: owner, group, and others.

  3. Principle of least privilege ensures that users and processes have only the permissions they need.

- **Interoperability and Composability**

  1. Linux tools are designed to work together, allowing users to combine them to perform complex tasks.

  2. The output of one program can be used as the input for another via pipes (|).

  **Ex** : cat file.txt | grep “search” | sort | uniq

- **Flexibility and Customization**

  1. Linux is highly customizable, from the kernel to the user interface.

  2. Users can build and modify their systems to suit specific needs, choosing components like window managers, shells, and tools.

- **Portability**

  1. Linux is designed to run on a wide range of hardware architectures, from embedded systems to supercomputers.

  2. Code written for Linux is highly portable across different platforms.

- **Community Over Corporation**

  1. Linux prioritizes the needs of its community of users and developers over corporate interests.

  2. Development is driven by collaboration and meritocracy


## Advantages of Linux

- Open Source

- Community Support

- Heavily Customizable

- Most Servers runs on Linux

- Devops most tools implements on Linux only

- Automation

- Secure

## Different Distributions of Linux

- **Popular Desktop Linux OS**

  1. Ubuntu Linux
  2. Linux Mint
  3. Arch Linux
  4. Fedora
  5. Debian
  6. OpenSue

- **Popular Server Linux OS**

  1. Red Hat Enterprise Linux
  2. Ubuntu Server
  3. Centos
  4. SUSE Enterprise Linux

- In todays IT Industry, people are using only two popular linux distors those are RPM (Red Hat Package Manager) and debian. The basic difference between these two are :

  **RPM** : RPM stands for Red Hat Package Manager and it use `.rpm` files for pacakage management. Its package management tools are `dnf`, `yum`, and `rpm`. It is basically derived from Red Hat Enterprise Linux. Some of the RPM distros are RHEL and CentOs, Fedora, OpenSUSE.

  **Debian** : Debian uses `.dpg` packages for package management and its package management tools are `apt`, `apt-get` and `dpkg`. It is basically derived from debian. Some of the debian distros are Ubuntu Server, Debian, Linux Mint, Kali Linux etc.