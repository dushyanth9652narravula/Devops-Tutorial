# Git

## Introduction to Version Control System

- Suppose you are working in a team where you all together developing an application and some of the members in the team are working on same code. At a moment you made some changes to the code and save it. And when your teammate opened the same code file and starts executing the code and he faced so many issues with this new code. Now your teammate wants to go back to previous code which is working better. But he doesn't know what changes you have made in that code.

- Now your teammate ask you to remove all the changes you made to that code file to get back the previous code file. Suppose you have made a lot of changes to that code and you forgot the some of the changes you made. Now its become difficult for you to get back the previous code by removing the changes. In these case people generally version the code written by all developers (in this case teammates.)

- In Versioning, what we actually do is there is an original file at start. Here we have wriiten some code for some features of the application and we save it in the same file. Now we actually create one more file with same name but ending with the timestamp (it is date and time at which we made changes to that file.) which is treated as backup. Now you teammate has changes the original file by adding some more features and save it in the same file. Now he will create one more file with same name but appending the timestamp at end. If you want to go back to the previous code, yo just need to copy the code form the backup file to original file so that you get back into the previous changes. This is the basic idea of the versioning.

- The main drawback in this versioning is we might end up creating a lot of backup files in our system as we made changes to the application continuously. So it would be tedious for to go back to previous changes quickly, as we need to find the file first to where we want to rollback and then we have to copy the content from that file to original file to get the previous code.

- To overcome these drawbacks, we have so many version control systems available in market which uses different methods for versioning the data. One of the most popular one is `Git`.

- These version control systems manage the multiple versions of Documents, programs and websites etc. They actually keep track history of collection of files. This version control software keeps track of every modification in a special kind of database.

## Types of Version Control System

- There are actually three types of version control systems. Those are :

  1. Localized Version Control System
  2. Centralized Version Control System
  3. Distributed Version Control System

- **Localized Version Control System** : In Localized VCS, we actually have a version control system locally and it uses a certain kind of database to version all our modifications to that program, document or website etc. Here we have a local repository which contains all the versions of our documents or whatever we are versioning. Here is how Localized VCS Works :

<img src = "./_static/Local_VCS.png" alt = "Localized Version Control System" width = 1000 height = 500>


- **Centralized Version Control System** : In Centralized VCS, we actually have a server which mantians the original copy of our data and each workstation (Our own computer) has a working copy of the fileand we can make changes in that working copy and once we made changes that we have made then we can push the changes to the server. This server maintains all the versions of the file (Code or Document or Website). 

<img src = "./_static/Centralized_VCS.PNG" alt = "Centralized Version Control System" width = 1000 height = 500>


- But there are some drawbacks with the both version controlling system. In Localized VCS , If our local system fails then we donot have backup for the data we are versioning and we lost our Documents, Code or Websites and its history. In Centralized VCS also, if the server stops working or fails then we donot have any backup of the history of modifications we have made till now. But we atleast have the current copy in our system.

- To overcome these issues we have distributed version control system.

- **Distributed Version Control System** : In distributed VCS, we have both local repository and remote repository. In this kind of version control system we acutally tracks the modifications in our local system and also in remote system. Once we made changes to files in our local system and this VCS maintains tracks of all these changes then we actually push these changes to the remote system which also has a copy of history of modifications we made. So even our local or remote system fails still we have a copy of the current file and history of changes. A best example of Distributed Version Control System is `Git`.

<img src = "./_static/Distributed_VCS.png" alt = "Continuous Integration Process" width = 1000 height = 500>


## Git

- Git is a distributed version control system. It is created by linus tolvards who has created the linux kernal.

- Git supports for non - linear development and it is fully distributed and can able to handle large projects. It is simple to use and provides simple commands to version our data. It also provides many cloud based remote repositories such as Github, Bigbucket, codecommit by aws etc. 

- Since it is supported by many cloud based remote repositories, so we can make a copy of local repositories in many ways as backup and these backups can be useful in case of system failures.


  