# Rolling Back to Previous Changes and Commits

- Suppose we have added some content into a file and later we came to know that we have added that content into the wrong file and we have not added the changes to stagging area. So to get our changes back, we can run the `git checkout` command. 

  **Syntax** : `git checkout <filename>` -> It will remove the changes and gets back that file to previous state. This will happen if you not added it to stagging area.

- To check the changes we have made between previous commit and current state before adding them into stagging area, we can use `git diff` command. The `git diff` command shows the changes in already tracked files only. If you created any new file those changes doesn't show up in the output of `git diff` command.

- Unfortunately, you have added the changes to stagging area, but you want to remove the changes from the Stagging area then we just use the `git restore` command.

  **Syntax** : `git restore --staged <filename>` -> It actually removes the changes made on that file from stagging area but not from working directory. Once changes of that file is removed from the stagging area, we can easily remove that changes in working directory by using `git checkout <filename>` command. 

  But `git restore --staged .` command will remove all the current changes made in this repository from stagging area.

  Once you added the changes to stagging area, `git diff` command doesn't show the changes we made to tracked files. So to check the changes made to tracked files even after stagging, we actually need to us `git diff --cached` command. 

- Suppose you want to delete all the changes you made now without even tracking then you just run the following command.

  **Syntax** : `git restore .` -> It command will change our working directory to last commit.

- Suppose you commited the changes but you want to revert back to previous commit then we actually need to use the following syntax. Now if you want to see the changes made from previous commit to present commit we can use tje following syntax.

  **Syntax** : `gi diff <previous commit hash> .. <present commit hash>

- Suppose you have commited the changes but not yet pushed the changes into the remote repository then we can delete or revert back to previous commit by using the `git reset` command. `git reset` command has different options. Those are :

  **--soft** : `git reset --soft <commit hash>` actually delete the commits made after the commit hash from the commit history but doesn't make any changes in working directory and all the changes made after the proivided commit hash are gets stagged in stagging area. So only commits gets deleted in the commit history but all changes gets stagged in staging area.

  **--mixed** : `git reset --mixed <commit hash>` actually delete the commits made after the provided commit hash from the commit history but doesn't make any changes in working directory. But here the changes are not stagged but we can see the changes we made by using `git diff` command. To revert back to latest commit now, just run the `git checkout .` .

  **--hard** : `git reset --hard <commit hash>` actually deletes ll the commits made after the provied commit hash form the commit history and also changes the working directory so that it matches the working directory at that commit hash we have provided. So it actually rollbacks to commit hash.

- But we can use `git reset` command if you not push the changes to remote repository. If you push changes to remote repository and want to revert back to previous commits then we actually need to use `git revert` command. Because `git reset` command deletes the commit from the commit history and we run the `git push` at this instance then it throws an error called `you remote and local repository are not in same state. so changes not gets pushed`. So we need to run `git pull` to make both local and remote repository a same state. But if you run `git pull` then reverted changes gets back to working directory because we have already pushed those changes to remote repository. So inorder to revert back to previous commits in this scenarios we use `git revert <commit hash>`. It doesn't deletes the commits after the provided commit hash from commit history but makes anothor commit to gets the working directory to the provided commit hash state. 