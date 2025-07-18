# Semantic Versioning in Git

- Generally we see many softwares releases thier versions as `2.19.1` etc. , which means they are giving a particular name to thier software build upto certian time. Naming the product upto certian time is called as semantic versioning. Here we represent those in numbers instead of particular names.

- Naming format for semantic versioning is `Major . Minor . Patch` . So `patch` indicates some bug fixes are happend in present version. `Minor` indicates some small feature are gets updated. `Major` indicates majority of software gets updated which means prereqs gets updated etc. For example some software needs JDK11 as preq, now its gets updated a lot and needs JDK17 as preq. So we cannot use JDK11 for this new version.

- Once the developers are good with that specific version they made then they actually release those version to production level. To do semantic versioning, git provides tagging. 

- Tagging is a way to mark specific milestones in our project development which are typically used as release points. Git provides two types of tags. Those are :

 1. **Light Weight Tags** : Light Weight tag is a named pointer to specific commit (simlar to branch) but meant to be static. It stores just commit hash not any metadata such as taggers name, message or data etc. It is basically a bookmark to a commit. to create a lightweight tag we use the following syntax.

     **Syntax** : `git tag <tagname>` 

    It creates a tag for last commit we made. To apply tags to particular commit, we use `git tag <tagname> <commit Hash>`.

 2. **Annotated tags** : Annotated tags are stored as full git objects in git database. They contain additional metadata such as taggers name, email, date, and a tagging message etc. To create an annotated tag, we use the following syntax.

    **Syntax** : `git tag -a <tag name> -m "<Description about tag>"`

    It also creates a tag for last commit we made. To create annotated tags for particular commits we need to include commit hash also.

    **Syntax** : `git tag -a <tag name> -m "<Description about tag>" <Commit Hash>`

- To check the tags present in current repository we use `git tag` command. If we want to see what we have done at that particular tag we use `git show <tagname>`.

- To push the tags to remote repository, we use the following syntax.

  **Syntax** : `git push <repository name> <tagname>`

  This command pushes only single tag which is mentioned there. If you want to push all tags present in the local repository, we use `git push <repository name> --tags`

- To delete a particular tag we use `git tag -d <tagname>`. To push the deleted tags into remote repository we use `git push <repository name> --delete tag <tagname>`

- Once we create tags then we can release those versions by using the relases in git. Once you created tags then got to github and click on tags there you can see the tags created by you or your organization. Beside tags you can see an option called releases. Click on new release. There you need to select the tag you want to release and then add a little bit description of that release and click on publish release.