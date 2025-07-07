# File Permissions

## Viewing File Permissions

- To view the file permissions of a file we just use `ls -l <filepath>`. 

  **Ex** : `ls -l devopsdir`

  It results the following output

  `drwxr-xr-x 2 root root 24 Jan 8 19:21 devopsdir`

  Now lets breakdown the what the output is representing

  1. **File Type and File Permissions** :

     - `drwxr-xr-x` represents both file type and file permissions. `d` represents the type of the file which means `devopsdir` is a directory.

     - The next three charecters after `d` represents the permissions of the owner of the file. Here it is `rwx`.
     - The next 3 charecters of the owners permissions are the permissions of the group this file belongs to. Here it is `r-x`.
     - The last 3 charecters are the permissions of the other users. Here it is `r-x`.

     - The charecters r, w, x, -, represents the following :

       **r** : permission to read a file or list the dictionary's contents.

       **w** : permission to write to a file or create and remove files from a directory.

       **x** : permission to execute a program or change into a directory and do a long listing of the directory.

       **-** : means no permission

  2. **Number of Hard Links** : The number after file permissions represents the no of hard links associated to that file or directory. Here devopsdir has 2 hard links.

  3. **User and Group** : The two words after the number of hard links represents the username and groupname that this file or directory belongs to. Here devopsdir user and group name is root itself.

  4. **File Size** : The number after the user and groupname is file or directory size. Here the devopsdir directory memory is 24 bytes.

  5. **Timestamp** : The timestamp in that output represents the last modification of that file or directory. Here devopsdi's last modification is at `Jan 8 19:21`.

  6. **Filename or Directory Name** : The last word in the output represents the file or directory name.



## Changing the Ownership and Groups of the File

- Only root can change the files owner and only file owner can change the files group. To change the onwership of the file we use `chown` command which means the change ownership.

  **Syntax** : `chown [options] Owner:Group <filepath>`

  **Ex** : `chown ansible:devops devopsdir` -> It changes the owner to ansible and group to devops for devopsdir directory. To check whether the ownership gets changed or not just use `ls -l` command.

  If you want to chnage the only owner of the file or directory use this syntax.

  **Syntax** : `chown [options] owner <filepath>`

  If you want to change only group of the file then we can use the following syntax

  **Syntax** : `chown [options] :Group <filepath>`

  If you want to change the ownership of all the files in the current directory then you you the following syntax

  **Syntax** : `chown -r owner:group <filepath>`

  We can change the group of a file or directory by using `chgrp` command.

  **Syntax** : `chgrp [options] Group <Filename or filepath>`

## Changing the permissions to the File or Directory Using Symbolic Method

- To change the permissions of a file, we use a command called `chmod` command -> Change Mode

  **Syntax** : `chmod [options] Mode <Filename or Filepath>

  In symbolic method mode includes :

  `u` : Owner

  `g` : Group

  `o` : Others

  `+` : grant

  `-` : remove

  `=` : set

  `r` : read

  `w` : write

  `x` : Execute

  For example if you want to give read, write permission to owner the you wite mode as `u+rw`. If you want execute permission to all then your mode is `ugo+x` or `a+x`. If you want to deny write and execute permission to other users then your mode is `o-wx`. Like this we write mode by using symbols.

  **Ex** : `chmod -r u=rwx devopsdir` -> It actually changes the permissions of all files owner in devopsdir to read , write and execute permissions.

  If you won't give any type such as owner, group or others then the permissions is applied to all.

  **Ex** : `chmod +x devopsdir` -> It gives execute permission to all (Owner, group, other users).

## Changing the file permissions by using Number Method

- In this method also we use `chmod` command to change the permissions of the file. But instead of symbols in mode we use numbers here. So the mode is :

  `r` : 4

  `w` : 3

  `x` : 1

  If you want to give read, write and execute permission to owner only then the mode is `700` (4+3+1). If you want to read and execute permission to all then we use `555` (4+1 = 5). If you want to deny write and execute permission to alll then the mode is `444`. 

  The only draw back here is, we actually need to change the permissions all (owner, group and other) at a time. We cannot change the permissions of them individually. If you want to change permissions like that the you have to symbolic method.

  **Ex** : `chmod -r 777 devopsdir` -> It gives all permissions of all (owner, group and other) to all files present in devopsdir.
