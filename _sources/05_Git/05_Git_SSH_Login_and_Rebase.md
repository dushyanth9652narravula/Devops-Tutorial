# Git SSH Login and Rebase

## Git SSH Login

- Till now we have configured the github or remote repository using https requests which requires username and password to login. But these usernames and passwords can be easily hacked. To make our login more secure, we can use the `git ssh` login.

- To login by using ssh first we need to create a ssh key-pair by using `ssh-keygen.exe` which creates an `.ssh` folder in our home directory. This folder contains two keys one is public key `id_rsa.pub` and anothor one is private key. 

- Now we need to copy the content in the public key and then got to your github account settings there you can see `SSH and GPG Keys` section. Once you moved to that section you need to create an ssh key and then paste the public key content in that key.

- Now when you adding the remote repsoitory details using `git remote add` command, you can provide the ssh url instead of https url. Then git automatically matchs the public key with the private key present in our directory and then it connect the local repository with remote repository.

- Generally whenever you run `ssh-keygen.exe` command, it actually creates two keys in that user's home directory and when you are trying to connect the remote server using ssh then it searches for private key in your home directory and then it matches that private key with public key provided. If both are matched it allows us to login otherwise request gets rejected.

## Git Rebase

- `git rebase` command is used to integrate changes from one branch to anothor branch similar to `git merge`. But `git rebase` command doesn't create an new commit like merge. It actually takes all the commits from current branch and apply all these  commits to the tip of the specified branch to make a linear project history. But we need to be careful before applying `git rebase`. There might be some problems will occur if we apply `git rebase` command.

- Suppose you and your friend is developing two features individually. And your feature needs to be integrate first and then your friend feature. But your friend done that feature very quickly and integrated with the main branch. But you didn't that your friend already integrated feature2 with main branch, so you intgrated the feature1 with main branch using `rebase` command. Later you came to know that your friend already integrated feature2 to main branch, which prone to errors now. So before applying the `git rebase` command, we actually need to fetch the changes from the remote repository firstby using  `git fetch <repository name>` which results a commit pointer called `fetch_head`. Now compare the difference in local head and fetch head by using `git log HEAD..Fetch_Head` . If there is any difference between your local and remote repository then take respective action based on those changes whether we need to pull the changes or delete the complete commits etc.

- If you want to apply `git rebase` command first be in the particular branch from where you want to take the commits and apply them to anothor branch. Now i want to apply commits from feature branch to main branch then i will execute these commands.

  `git checkout feature` and then `git rebase main`. This will take all the commits from feature branch and apply those commits at the tip of the main branch.

  General syntax of git rebase is `git rebase <branchname>`