# Versioning in Git

- We know that Git is a distributed version control system which means we maintain both local repository and remote repository. Here remote reposiory might be Github, BigBucket or an other cloud platform. One important thing we need to remember that git won't version the directories, it will only version the files only.

- So before making any commits (changes), we actually need to tell the git whom we are, i mean git will recored all the details of person making a commit such as email address and username etc. So before making commits we need to provide these two details to Git. But the username and email we are providing doesn't need to match with the remote repository username and email. If they didn't match still our commit will be pushed into remote repository but we cannot see any github contribution on our profile. So see contributions on our profile, we need to provide the username and email that matches with our github account.

- To provide the user details such as username and mail, we will use `git config` command.

  **Syntax (For Email)** : `git config --global user.EMAIL "<your email>"`

  **Syntax (For Username)** : `git config --global user.NAME "<Your Username>"`

- Here `--global` option tell the git to use these details for every commit not only in current repository but also in every repository present in our system.

- So once we provided the details then we are ready to make any commits. So the first step is we need to create a local repository to track all the changes we have made. So to do this create a new folder or directory and open the terminal and go to this directory and run `git init` command.

  **Syntax** : `git init`

  `git init` command initializes a new local repository in our directory and create `.git` hidden file in our directory. This `.git` file is used to track all the changes we have made and some metadata of each commit etc.

- Once we have initialized the local repository, then we actually need to add the changes we have made to stagging area. Before adding the changes to stagging area lets see what does stagging area mean and how does our changes moves from working directory to local repository and then to remote repository.

  **Stagging Area** : Stagging Area is crucial part in git workflow which acts as an intermediatory directroy between working directory and local repository. Now lets see steps involved in this git workflow.

- **Git Worflow** : Git workflow mainly involves 4 basic steps. Those are :

  1. **Working Directory** : Working Directory is where we make changes to our project files. It is actually our project direcotry where we edit, create or delete files etc.

  2. **Stagging Area** : The Stagging Area (also know as index) is where we actually keeps all the changes we made before commiting them to local repository. That means we don't do a lot of changes in a single day. We actually progress our project day by day. So we actually need to commit all the chnages we have made in a day. So to commit these changes, we need to add them in stagging area first. It is just like clipborad where we actually store all the content that we wanna paste them later.

  3. **Local Repository** : Once we have added the changes to stagging area, then we are ready to make commits. The area where all the commits gets stored is local repository.

  4. **Remote Repository** : Once we commited all the changes in our local repository then we actually add all these changes to a cloud platform which is a remote repository. This will be act as a backup and also usd to share our work to public.

- So to add the changes to stagging area, we use `git add` command.

  **Syntax** : `git add <filename>`

  This will add the specific file to the stagging area. 

  **Syntax** : `git add .`

  This will add the all the files (or changes we made in current directory) in current directory to stagging area.

  Once we have added all these files the status all the areas are :

  **Working Directory** : Changes Made

  **Stagging Area** : Changes added

  **Local Repository** : Empty

  **Remote Repository** : Empty

- Till now we have added the changes to stagging area. At this point , if you came to know if you have done some mistakes in your code then you can unstage the changes in the stagging area by making it empty and rectify the mistakes and the changes again to stagging are by using `git add` command.

- Once we have added the changes to stagging area the next step is to add changes to local repository. To add the changes to local repository then we actually need to commit the changes. We commit the changes by using `git commit` command.

  **Syntax** : `git commit -m "<Some Message>"`

  This command actually add all the changes in stagging area to local repository and makes stagging area empty (that means it makes stagging area ready for next commit).

  Now status of all the steps is :

  **Working Directory** : Changed

  **Stagging Area** : Empty

  **Local Repository** : Changes added

  **Remote Repository** : Empty

  Once we commited the changes git stores some meta data i.e the authors name, authors email, timestamp when we made commit, commit message, A hash code (SHA). To get this info we need to use `git log` command. If you wanna see the sepecific commit then we need to use `git show <commit hashcode>` . It actually shows the commit message, Author and date, Files changed and actual changes made (atual differences). `git log --oneline` gives the short commit hashcode for each commit we have made.

- Until now, we have committed all the changes to local repository and know we need to make them available to all our teammates by adding them into remote repository. Before adding them into remote repository, we need to tell git which remote repository we are using by using `git remote` command.

  **Syntax** : `git remote add <repository name (by default origin)> < repository link>`

  Adds a remote repository with the name 'origin'. Specifies the URL of the remote repository(in this case, a Github Repository).The remote repository is a version of project hosted on internet. Naming it 'origin' is a convention that refers to primary remote repository. I mean by default git uses 'origin' as  repository name when we clone a repository. But we can provide our own name to repository. For example :

  `git remote add myrepository <repository link>`

  But we need to use the same name when we are pushing them.

  Once we add the remote repository to git, now we need to push the changes to remote repository by using `git push` command.

  **Syntax** : `git push <repository name (by default origin)> <branch name (by default main)>`

  In general the command is `git push origin main`

  So before pushing the changes we actually changes the branch from master to main by using this command `git branch -M main`.

  Now status of all the steps is :

  **Working Directory** : Changed

  **Stagging Area** : Empty

  **Local Repository** : Changes added

  **Remote Repository** : Changes added

