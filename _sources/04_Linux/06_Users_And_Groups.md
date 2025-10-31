# Users and Groups in Linux

## Introduction

- Users and Groups are used to control the access to files and resources of the system.

- Users login to the system by supplying username and password.

- Every file in the system is owned by a particular user and associated with particular group.

- Every process has an owner and group affiliation and can only access the resources of its owner or group.

- Every user in the system has an unique User ID (UID) and unique Group ID (GID).

- Users name and UID are stored in `/etc/passwd`.

- User's password is stored in `/etc/shadow` in encrypted form.

- Users are assigned to home directory and programs automatically runs when they logged in. (`Usually that program is Shell`)

- Users cannot read, write or execute each other's files without permission.

## Types of User

- **Super User** : Super User or Root User is the most powerful User. He is the administrator user. Root user has the following things :

  1. **User ID (UID)** : 0
  2. **Group ID (GID)** : 0
  3. **Home Directory** : `/root`
  4. **Shell** : `/bin/bash`

- **System User** : System Users are the users created by the softwares or applications. For example, if you install Apache in our system then it will create an user called Apache. These kind of users are called system users. System users have the following things.

  1. **User ID** : 1 to 999
  2. **Group ID** : 1 to 999
  3. **Home Directory** : `/var/ftp`
  4. **Shell** : `/sbin/nologin`
  5. **Example** : ftp, sshd, apache, etc.

- **Normal User** : Normal Users are the users created by the root users. Those users are Rahul, Sai etc. Only root user has the permission to create or remove an user. Normal User has the following things.

  1. **User ID (UID)** : 1000 to 60000
  2. **Group ID (GID)** : 1000 to 60000
  3. **Home Directory** : `/home`
  4. **Shell** : `/bin/bash`
  5. **Example** : Sai, Shashank etc.

- Whenever you created an user in linux the following things will happen :

  1. A home directory gets created (Like `/home/vagrant`)
  2. A mail box is created (`/var/spool/mail`)
  3. Unique UID and GID are given to the user.

## Passwd File in Linux

- Passwd file is located in `/etc`  directory (whose path is `/etc/passwd`) which contains all the information of users present in the system.

- When you open the file using `head -2 /etc/passwd`, it shows the following information :

  `root : x : 0 : 0 : root : /root : /bin/bash`

  `vagrant : x : 1000 : 1000 : : /home/vagrant : /bin/bash`

  Now lets decode the information :

  1. **root or vagrant** : These are the usernames.

  2. **x** : These are the links to the passwd file `/etc/passwd`

  3. **0 or 1000** : This represents User ID (UID). "0" for root and "1000" for vagrant.

  4. **0 or 1000** : This represents Group ID (GID). "0" for root and "1000" for vagrant.

  5. **root or <space>** : This just reperesent comments of that user. For root user the comment is just `root` itself but vagrant doesn't have comments.

  6. **/root or /home/vagrant** : This represents the home directory of the user. `/root` for root user and `/home/vagrant` for agrant user.

  7. **/bin/bash** : Last item represents the shell program of that user.

- Overall passwd file contains this information :

  `Username : Link to passwd file : UID : GID : Comments : Home Directory : Shell Program`

## Group File

- Group file is located in `/etc` directory (whose path is `/etc/group`) which contains information of all groups present in linux which is in this format :

  `Group Name : link to Group passwd file : Group ID : Group Members`

  **Ex** : `root : x : 0 : `

## Addding and Deleting the User and Group

- To add an User we use a command called `useradd` which has the following syntax :

  **Syntax** : `useradd <username>`

  **Ex** : `useradd ansible` -> This will create an user called ansible.

  To check whether the user gets created or not, just check the `passwd` file in `etc` directory by using this command - `tail -1 /etc/passwd`.

  `ansible : x : 1001 : 1001 : : /home/ansible : /bin/bash`

  Whenever you created an user, a group also gets created with the same name of the user and assign that user to that group.

  `ansible : x : 1001 : `
  
  We have one more command to check whether an user gets created or not i.e `id` command.

  **Syntax** : `id <user>`

  **Ex** : `id ansible` -> It gives the output as `uid=1003(ansible) gid=1003(ansible) groups = 1003(ansible)`

- To create a group in linux, we have `groupadd` command.

  **Syntax** : `groupadd <groupname>`

  **Ex** : `groupadd devops`

  To check whether that group is created or not, just check the `etc/group` file by running this command `tail -1 /etc/group`. It will show the following :

  `devops : x : 1002 : `

- **usermod** : `usermod` command is used to change the properties of the existing user account. It allows administrators to change the user account settings such as home directory,  shell, group memberships etc.

  **Syntax** : `usermod [options] <username>

  The most common options we use with usermod are : 

  `-G` - This option will be used to add the group membership to an user which means it will assign an user to particular group. But by using the option `-G`, we might lose the previous group membership. Suppose user `ansible` has assigned with group `dev` and now you wanna assign this user to group `ops` also. If you use `-G` option for assigning `ansible` to `ops` then it first remove the membership with `dev` and create membership with `ops`. So you have only the final memebership. To overcome this we use option `-a` along with `-G` which actually add the users to the groups without deleting the previous memebrships.

  `-a` - This option just appends the user to supplementary groups mentioned by `-G` with removing the users from other groups.

  **Syntax** : `usermod -aG <groupnames> <username>`

  Here we can provide as many as groups we can, but we need to provide single username

  **Ex** : `usermod -aG devops,ops jenkins` -> It will add jenkins to devops and ops group.

- But we can assign groups to users bu just editing the `etc/group` file in vim editor. Just add these users in the `/etc/group` file to the groups you want to add.

- **passwd** : `passwd` command is used to set the password for an user.

  **Syntax** : `passwd <username>`

  **Ex** : `passwd ansible` -> After running this command, linux asks you to set the new password and then it asked you to retype the same password and then you see this output `passwd : All authentication tokens gets updated successfully`

  Generally root user can able to set all user password using `passwd <username>` but a normal user can able to reset his/her own passwd using `passwd <username>` command. They cannot able to change the other users password.

- **last** : `last` command is used to check the last looged in user in the system.

  **Syntax** : `last`

- **who** : `who` command return the current logged in user name.

  **Syntax** : `who`

- **lsof** : `lsof` command is used to check the list of files accessed by an user.

  **Syntax** : `lsof -u <username>`

- **userdel** : `userdel` command is used to delete the user from the system.

  **Syntax** : `userdel username`

  **Ex** : `userdel jenkins` -> It actually deletes the user jenkins from the system. But it doesn't remove the `home/jenkins` and mail spool from the system. Since it doesn't delete those files from the system then you cannot able to create the same user using `useradd` command as it returns user already exits. So to delete an user completely then we can use an option `-r` which removes all related files to that user. So the syntax for this is `userdel -r jenkins`.

- **groupdel** : `groupdel` command is used to delete the group from the system.

  **Syntax** : `groupdel <groupname>`

  **Ex** : `groupdel devops`



   