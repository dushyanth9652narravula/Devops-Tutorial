# Git Branching

- Branches in Git is similar to branch of a tree. Similar to tree branch is attached to central part of the tree, a branch in git is a way to developing new features or modification of the software without effecting the main project code. We can say branches create anothor line of development in the project. The primary or default branch in the git is the master branch. As soon as we have created the branches all the commits that we have made in the current branch gets copied to new branch and we starts working on the same code present in main branch in new branch.

## Need of the Branches in Git

- As we know , git branches create a anothor line of development that is entirely different or isolated from the main stable master branch. Suppose you have created a new feature and you send the link of new feature to the client. But your client is too busy to check the new feature. Meantime, you started working on new feature on same code and after few days your client responded that he/she didn't like the new feature and wants to remove that feature. Since your development moving in straight line, it becomes a problem to cut the feature which is in the middle of the line. But we can do that one by rollbacking to previous commit where new feature is started, but we might lost the code of second new feature also. Instead of following a straight line in development what if we create a branch from the middle fo the line and create new feature in that line then if client doesn't like this new feature we can just cut that branch easily without effecting the original stable code. If client likes that code we can merge that the main stable code. This is what the purpose of git branches.

## Operations on Git Branches

- **Creating a new branch** : This is the first step in the process, you can start at default branch or create a new branch for development. To create a new branch we use the following syntax.

  **Syntax** : `git branch <branchname>`

- **Merging a branch** : An already running branch can merge with any other branch in your git repository. Merging a branch can help when you are done with that branch and you wanna integrate it into anothor branch.

  **Syntax** : `git merge <branchname>`

- **Switching the branches** : To switch to other branches we can use the following syntax

  **Syntax** : `git checkout <branchname>` or `git switch <branchname>`

  We can directly switch to a new branch which not even existed in repository by using this syntax.

  **Syntax** : `git checkout -b <banchname>` or `git switch -c <branchname>` 

  It actually creates and switch to the created branch.

- **Deleting a branch** : To delete a branch we actually use the following syntax.

  **Syntax** : `git branch -d <branchname>`

- **Renaming a branch** : To rename a branch, we can use the following syntax

  **Syntax** : `git branch -m <branchname>` -> Renames the current branch to new name. `git branch -m <oldname> <newname>` renames a particular branch.

- **Note** : `git branch` gives all the branches present in your repository and also highlights your current branch. And the command above for deleting the branch delete branch locally only. To delete branch in remote repository also we need to use `git push <repositoryname> --delete <branch name>`. To know branching more use this [link](https://www.toolsqa.com/git/branch-in-git/)

