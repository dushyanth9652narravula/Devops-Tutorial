# Variables

- Variables are placeholders or temporary stoarge for data. They actually be in memory as they are temporary. These are used to refer some data when that data or value is used repeteadly in the script. To declare a variable in the bash script we use the following syntax

  **Syntax** : `VARIABLENAME=Value`

  **Ex** : `URL="https://www.tooplate.com/zip-templates/2103_central.zip"`

- We need to remember one thing  while declaring variables that we shouldn't add spaces before and after the `=` sign. These things we generally do in other programming languages. It is not mandatory to declare variables in capital letters in bash scripting but it would be readable if we declare them in capital letters.

- **Note** : If you are trying to access the variable which is not declared then it prints an empty space.

- Sample Bash Script that contains variables are:

  ```bash

  #!/bin/bash

  # Declaring the Variables

  SVC="httpd"
  PACKAGE="wget unzip httpd"
  TEMPDIR="/tmp/web"
  ARTIFACT="2098_health"
  URL="https://www.tooplate.com/zip-templates/2098_health.zip"

  echo "############################"
  echo "Installing the Services"
  echo "###########################"

  sudo yum install $PACKAGE  -y > /dev/null

  echo "###########################"
  echo "Starting and Enabling the Services"
  echo "###########################"

  sudo systemctl start $SVC
  sudo systemctl enable $SVC

  echo "##########################"
  echo "Downloading the Artifact Code"
  echo "#########################"

  mkdir -p  $TEMPDIR

  cd $TEMPDIR

  sudo wget $URL > /dev/null

  unzip $ARTIFACT.zip > /dev/null

  cp -r $ARTIFACT/* /var/www/html/

  echo "#####################################"
  echo "Clean the temp files"

  cd ..

  rm -rf $TEMPDIR

  sudo systemctl restart $SVC

  sudo systemctl status $SVC
  ls -l /var/www/html/
  ```
## Command Line Arguments

- Generally in linux we pass arguments to commands such we pass source and destination path to `cp` and `mv` commands. Similar to that we can pass arguments to scripts also. Through command line arguments, users can able to pass arguments to scripts instead of fixing the values in the script. Command line arguments actually ensures dynamic values or data to scritps.

- To access the arguments in the script we use dollar sign followed by the position of the command. For example `$1` indicates the argument positioned at 1.

- Argument positioning starts from 0 and goes on any value. `$0` refers the command name itself. Such cp, mv etc. When you are executing the scripts then script path is 0th argument (`$0`).

- **Ex** : `./vars_websetup.sh https://www.tooplate.com/zip-templates/2103_central.zip 2103_central`

- The above example has 3 arguments. `$0` refers to `./vars_websetup.sh` , $1 refers to `https://www.tooplate.com/zip-templates/2103_central.zip` and `$2` refers to `2013_central`. 

- But if you have more than 10 arguments then argument positioned at 11 is refered by the ${10}. Like 12th argument is ${11} etc.

- Sample for the command line arguments is :

  ```bash

  #!/bin/bash

  # Declaring the Variables

  SVC="httpd"
  PACKAGE="wget unzip httpd"
  TEMPDIR="/tmp/web"
  #ARTIFACT="2098_health"
  #URL="https://www.tooplate.com/zip-templates/2098_health.zip"

  echo "############################"
  echo "Installing the Services"
  echo "###########################"

  sudo yum install $PACKAGE  -y > /dev/null

  echo "###########################"
  echo "Starting and Enabling the Services"
  echo "###########################"

  sudo systemctl start $SVC
  sudo systemctl enable $SVC

  echo "##########################"
  echo "Downloading the Artifact Code"
  echo "#########################"

  mkdir -p  $TEMPDIR

  cd $TEMPDIR

  sudo wget $1 > /dev/null

  unzip $2.zip > /dev/null

  cp -r $2/* /var/www/html/

  echo "#####################################"
  echo "Clean the temp files"

  cd ..

  rm -rf $TEMPDIR

  sudo systemctl restart $SVC

  sudo systemctl status $SVC
  ls -l /var/www/html/
  ```

## System Variables

- **$#** - It gives how many arguments are passed to bash script. 

- **$@** - It returns all the arguments passed to bash script.

- **$?** - It returns the exit status of most recently run process. If the process executed successfully then it returns 0. Otherwise it returns a non-zero number.

- **$$** - It returns the process ID of the current script.

- **$USER** - It returns the username of the user running the current script.

- **$HOSTNAME** - It returns the hostname of the machine that is running the current script on.

- **$SECONDS** - It returns the no of seconds since the script started running.

- **$RANDOM** - It returns number when it was refered.

- **$LINENO** - Returns the current line number in the Bash Script.

## Quotes

- Bash Scripting supports both type of quotes. First one is single quotes `' '` and second one is double quotes `" "`. Generally in most of the programming langauges they look similar. But in bash scripting, they are different. 

- **Single Quotes** : Single Quotes are used for literals only. Everything inside the single quote are treated as literals. No variable expansion, no command substitution happens. No special treatment for `$`, `\` or any special charecters.

  **Ex** : For example if you have a variable called `SKILL='DevOps'` and you are trying to print it using `echo 'I know $SKILL'`, it results this output `I know $SKILL`. So we can say everything inside single quote is an literal they don't have any special treatment. Because bash treates single quotes as strong quotes and they protect all charecters inside from being interpreted.

- **Double Quotes** : Double Quotes in bash are considerd as explansion mode. Variables ($var), command substitution and arthimetic are expnaded inside.

  **Ex** : `echo "I know $SKILL"` -> `I know Devops`. 

## Command Substituiton

- Command Substitution is method to store the output of a command in a variable. To do this we have two ways. First way is using back ticks **`<command>`** and second way is using `$(<command>)`.

- **Ex** : **UP=`uptime`** or `UP=$(uptime)` and run this command `echo $UP` ->  `22:48:22 up 2:13, 3 users, load average: 0.01, 0.02, 0.00`

## Exporting Variables

- Generally variables that we have created are temporary and they gets deleted once we closed the terminal. And variables created in one terminal doesn't accessible to other terminals opened under the parent terminal. Suppose we looged in as root user and we created a variable called `$SEASON=WINTER`. Now if you this variable in a script, then it just prints an empty space. Because when you run a script then it open a new bash shell under the root user and this variable `SEASON` created under the root user is not accessible for bash shell where our script is getting executed.

- Inorder to make the variable accessible for child process (or bash sessions), then we need to export that variable by using `export` command. The syntax for exporting a variable is `export <variable name>`.

  **Ex** : `export SEASON`

- But this `SEASON` variable gets deleted when we have logged out from the root user (as we have created that varaible under root user).

- If you want to make that variable permenent for an user then you need to place that variable under `.bashrc` file of that user which is located under home directory of that user. That means when you login as an user, then run `ls -a` then you can see the `.bashrc` file (This .bashrc file is an hidden file) .

- If you want to make this variable accessible for all user in the system (globally) then you need to add this export command in `/etc/profile` file. So you append this `export SEASON=Winter` at end of either `.bashrc` file of an user or `/etc/profile` file.But if write in both files then variable present in `.bashrc` file overwrittes the `/etc/profile` file if both files have different values for same variable.
