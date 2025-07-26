# Sudo Command in Linux

- The Sudo command in Linux and Unix - Like Operating System allows a user to execute commands with elevated privilages. Sudo stands for superuser do. When you prepend sudo to a command, you are requesting the system to execute that command as a superuser, provided you have the necessary permissions.

- Generally all users maynot able to run all the tasks in the Linux System. Some are restricted to the root user Only. But if a user want to perform that restricted tasks then that user needs to have some privilages. If that user have necessary privilages then that user can run all the tasks on behalf of root user by using `sudo` command.

- To give all the permissions to an User we need to include that User name in `sudoers` file located in `/etc` directory. But if you see the `sudoers` file doesn't have write permission for any kind of user even root user also. So edit that file we need to use another command `visudo`. 

  **Syntax** : `visudo` -> It will open `sudoers` file in vim editor.

- After opening `sudoers` file in vim editor then we need to add the following line below this line `Allow root to run any anywhere`

  `<username>    ALL=(ALL)    ALL`. 

  **Ex** : `vagrant  ALL=(ALL) ALL` -> Align this line with root line listed in that file. After editing the file just save and exit.

  Now try to change the password of any other user using `sudo` command. Since only root user have previlage to change the password of any other user using `passwd` command. Since vagrant user have all the privilages to run any tasks, so vagrant can change password of root user using `sudo` command`.

  **Ex** : `sudo passwd ansible` -> It will asks first the password of vagrant user then it will redirect to set the password of ansible user.

  If you donot want to enter your own password then edit the sudoers file like this.

  `vagrant ALL=(ALL)   NOPASSWD: ALL`

  **Note** : If you edit the sudoers file like above then linux won't asks passwd of the vagrant (or any user having sudo permissions) for `sudo` command only. If you are switching from vagrant to ansible user then linux asks for the password of ansible to switch from vagrant to ansible. Suppose if you want to change the password of any user (if you forgotten password of that user) then just switch to root user ans set the password of that user.

- But editing the sudoers file is not an optimal way to give the privilages of the root user to the normal user. Because if you made any errors in that file then we cannot able to run sudo command. But if you made any errors in the sudo file then linux will prompt hat errors in the console and then you just hit `e` on the keyboard to edit the the `sudoers` file, so that we can remove errors in that file.

- Inorder to overcome this issuse just create a file in `/etc/sudoers.d` directory. Suppose lets create a file called ansible in `/etc/sudoers.d` to give root user privilages to `ansible` user. So just open the created file in `vim` editor. And write the content same as you written in the `sudoers` file. `ansible ALL=(ALL) NOPASSWD: ALL`. This will automatically give the all root privilages to the ansible user. (Here you can name the file as you wish. But keep the file name as username might give more readability.) Similarly you can assign root privilages to the group also. Here iam assigning the root privilages to group `devops`.

- Now lets create a `devops` file in `/etc/sudoers.d` directory. Then we need to write the following thing in the created file. 

  **Syntax** : `%<group-name>   ALL=(ALL)   NOPASSWD: ALL`

  **EX** : `%devops ALL=(ALL)  NOPASSWD: ALL`

- This is how we can give the root privilages to normal users or groups.



  