# Directory Structure and Basic Commands of Linux

## Directory Structure of Linux

- If you look at the prompt of the virtual machine you logged in, you can see `[vagrant@vbox:~$]` which indicates that you logged in as varant user, `vbox` is the localhost name, `~` respresents you are in home directory of vagrant user and `$` indicats that it is normal user shell.

- If you logged in as root user using `sudo -i`, we can see prompt as `[root@vbox:~#]` which indicates that you logged in as root user, `vbox` is the localhost name, `~` indicates you are in root directory (`/root` which is home directory of root) and `#` indicates it is root user shell.

- The basic Directory structure of linux is :

  1. **Root Directory** - `/` : Root directory is the top most directory in linux which contains all other files and directories of the system.

  2. **Home Directories** : `/home` is the home directory in linux which contains all the users present in the operating system. `/home/username` contians all the personal files and directories of that user. `/root` contains all the files and directories related to root user. Suppose you are in different directory and you wanna comeback to home directory of that user directly then you just need to enter  `cd` command on command prompt.

  3. **User Executables** : User executable directories are `/bin`, `/usr/sbin`, `/usr/local/sbin`. These directories contains essential executable programs such as `ls`, `cp`, `mv` for system boot and other basic operations.

  4. **System Executables** : System executables are `/sbin`,`/usr/sbin`,`/usr/local/sbin`. These directories contains the system executable files such as `fsck`, `reboot`.

  5. **Other MountPoints** : Mountpoint directories are `/mnt` and `/media`. `/mnt` contians the temporary mount points for the devices such as USB drivers or external devices. `/media` automatically mounts the removable media.

  6. **Configuration** : `/etc` contains is the home directory for all the configuration files. It contains system wide configuration files such as `/etc/passwd` , `/etc/hosts` etc.

  7. **Temporary Files** : `/tmp` contains all the temporary files. These files are automatically gets removed when the system gets rebooted. 

  8. **Boot Loaders** : `/boot` contains the files for booting up the system such as Kernal Files etc.

  9. **Server Data** : `/var` and `/svar` contains all the server data. `/var` contains the data which changes frequently such as logs (`/var/logs`) , mails, temporary files etc whereas `/srv` contians system services such as web server etc.

  10. **System Information** : `/proc` and `/sys` contains all the system information.

  11. **Shared Libraries** : `/lib`, `/usr/lib`, `/usr/local/lib` are the shared libraries for root and users.

- From the directory structure of linux, we can say that every command we are running is a file. Since everything is file (and that files are text files) in linux, it becomes so easy to conifgure the changes in linux when compared to other operating systems. To configure settings in other operating systems, we actually need to go to settings tab and we need to go to some other tabs in that settings tab to configure settings which is difficult for automation.


## Basic Commands of Linux

- The basic structure of commands in linux is : `command options arguments`

  **Ex** : `ls -l /home/vagrant` displays all the files directories belongs to vagrant user. Here `ls` is command, `-l` is an option for `ls` command and `/home/varant` is argumet to `ls` command (in our terms it could be input to `ls` command).

- There are actually 5 basic commands in linux. Those are :

  **whoami** : It display the username looged in currently. The syntax is just `whoami`.

  **pwd** : It display the path of current directory. The syntax s just `pwd`.

  **ls** : It actually displays the list of files and directories present in current directory. The basic syntax is just `ls`. But `ls` has other options also.

  **cat** : It is used to content present in a file. The basic syntax is `cat <filename>` or `cat <absolute path of filename>`.`cat` stands for concatenate. It is a command-line utility in Unix/Linux used to: Read, concatenate, and write file contents to standard output (your terminal).

  **cd** : It is used to change the directory. The basic syntax is `cd <path>`. Path can be absolute or realtive.

## File Commands

- **mkdir** : The `mkdir` command is used to make or create directory. The basic syntax is `mkdir <directory name>`.

  **Ex** : `mkdir dev` -> It creates the dev directory in current directory. If you want to create multiple directories at a time then you use this syntax `mkdir <directory1_name> <directory2_name>` which means you need to provide the directories as arguments. Here you can provide path where you want to create directory instead of just directory name.

- **touch** : `touch` command is used to create the files in linux. The syntax is `touch <filename>`. 

  **Ex** : `touch testfile1.txt` -> it creates testfile1 in current directory. If you wanna create file in another directory you just need to provide the path of that directory instead of filename. If you wanna create multiple files with same name but numbering is different such as testfile1, testfile2, .. then you need to use this syntax which is `touch testfile{0..10}.txt`

- **cp** :  cp command is used to copy files to the given directory. The syntax is `cp <path1> <path2>`.

  **Ex** : `cp testfile1.txt dev` -> It copies testfile1.txt to the dev directory. If you want to copy a directory to another directory then you need to use option `-r`. So syntax is `cp -r dev ops` -> it copies dev directory to ops directory. cp command is used to copy contents from one file to another file also.

- **mv** : `mv` command is used to move one file or directory to another directory. The syntax is `mv <path1> <path2>`.

  **Ex** : `mv dev backupdir` -> It moves dev directory to backupdir. mv command can be used to rename a file or directory. But the file with that new name should not exist in that directory. If that new name exists then it will do move operation instead of rename operation. `mv ops operations` -> It renames ops directory to operations directory.

- **rm** : `rm` command is used to remove the files and directories in linux. The syntax is rm `<file or directory name>` .

  **Ex** : `rm testfile1.txt` -> it removes testfile1.txt from the current directory. If you want to remove the entire directory ten you need to use option `-r`. `rm -r dev` which remove entire dev directory. If you want to all the files or directories in the current directory then we need to `*` symbol.`rm -r *` -> removes all the files and directories presnt in the current directory. But beware while using `*` it will remove all the files or directories present in the current directory.

- **Note** : If you want any help regarding the commnad then we can use ``--help`` option. For example ``cp --help`` gives all te documentation of the ``cp`` command. Here we can observe in linux we use single hypen `-` for single word options and double hypen `--` for multi word options.


