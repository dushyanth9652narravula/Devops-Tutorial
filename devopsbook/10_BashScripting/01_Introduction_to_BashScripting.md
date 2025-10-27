# Introduction to Bash Scripting

- In Software Industry, System Administrators (in operations team) main tasks are maintaining the system up all the time,checking the system health and scaling the environment whenever required.

- If you see their work, they have to do these repeatedly in their day to day life which means they have to open the linux terminal and execute the linux commands related to their work. So everytime they have to run eacha nd every command in the terminal. It would be tedious for them to run same commands everyday.

- So to overcome this, we have a scripting language called bash scripting. Bash Scrpiting is a scripting langauge in which we acutally create a file with an extension of `.sh` and keep all the linux commands which we execute repeatedly in our day to day life. Once we have created this file, we just need to execute this file in the linux then all the commands in that file gets executed automatically. So Bash Scripting simply automates the day to day tasks performing in linux environment.

- Generally there are different types of shell scripting in linux. Since we are executing our commands in bash shell, we call it as bash scripting.

## Sample Bash Script File

- Bash Script file starts with a shebang character `#!` followed by a path. This path is an interpreter path which is required to execute the commands written in the script file. If you are writing the python code then you need to give the path of python interpreter. If you are writing the linux commands then we need to give the path of bash shell which is `/bin/bash`.

- Sample bash script is :

  ```bash

  #!/bin/bash

  ### Sample Bash Script File ###

  echo "Welcome to Bash Script"
  echo

  echo "#######################"

  echo "System Uptime Information"
  
  uptime

  echo

  echo "#######################"

  echo "Memory Information"

  free -m

  ```