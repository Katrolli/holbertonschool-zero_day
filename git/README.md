# Git Essentials

Git is the most commonly used version control system. Git tracks the changes you make to files, so you have a record of what has been done, and you can revert to specific versions should you ever need to. Git also makes collaboration easier, allowing changes by multiple people to all be merged into one source. 
So regardless of whether you write code that only you will see, or work as part of a team, Git will be useful for you. You can watch this short [video](https://www.youtube.com/watch?v=2ReR1YJrNOM) for a basic introduction.

## Setup

**How to setup git on your sandbox**

- Your Identity

The first thing you should do when you install Git is to set your user name and email address. This is important because every Git commit uses this information, and it’s immutably baked into the commits you start creating:
```
$ git config --global user.name "Marc Aurel"

$ git config --global user.email marcaurel@email.com
```

- Your default branch name

By default Git will create a branch called *master* when you create a new repository with ```git init```. From Git version 2.28 onwards, you can set a different name for the initial branch.

To set **main** as the default branch name do:
```
$ git config --global init.defaultBranch main
```

- Adding a new SSH key to your GitHub account

Git allows you to work using a secure shell connection (SSH) using your terminal. In order to do so you will need to [generate a key](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent) and [adding](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account) that key to your account.

### Repositories

A Git repository allows performing various operations on it to create different versions of a project. These operations include the addition of files, creating new repositories, committing an action, deleting a repository, etc. These modifications will result in the creation of different versions of a project. You can think of a repository as a place where the files of your projects are stored.

- Creating a repository

First, log into your Github account and follow these steps :

1) In the upper-right corner of the page, use the + drop-down menu, and select **New repository**.
![Image](https://docs.github.com/assets/cb-11427/images/help/repository/repo-create.png)


2) Type a short, memorable name for your repository. For example, "home sweet home".


3) Optionally, add a description of your repository. For example, "My first repository on GitHub."
![image](https://docs.github.com/assets/cb-26377/images/help/repository/create-repository-desc.png)

4) Choose a repository visibility.

![image](https://docs.github.com/assets/cb-20877/images/help/repository/create-repository-public-private.png)

5) (Optional) Select *Initialize* this repository with a README.
![image](https://docs.github.com/assets/cb-49938/images/help/repository/initialize-with-readme.png)

6) Click *Create* repository.
![image](https://docs.github.com/assets/cb-19887/images/help/repository/create-repository-button.png)

- Basic commands needed

```
git add file_name
git add . 
```
The git add command adds a change in the working directory to the staging area. It tells Git that you want to include updates to a particular file in the next commit
```
git commit -m "Meaningful message"
```
Create a new commit containing the current contents of the index and the given log message describing the changes
```
git push
```
The git push command is used to upload *local* repository content to a *remote* repository. Pushing is how you transfer commits from your local repository to a remote repo.
```
git pull
```
The git pull command is used to fetch and download content from a remote repository and immediately update the local repository to match that content. Merging remote upstream changes into your local repository is a common task in Git-based collaboration work flows.

### Branching and merging
- Understanding branching

Branching in Git is used as a form of creating an identical copy of the current files and materials currently stored in your repository. Let's take a simple example that Team A and Team B need to update different files on the same *main* branch. In order to avoid conflict and confusion both of these teams would create new branches(branch a and branch b) so they can update and test their code without changing anything in the source material.


- Understanding merging

Merging basically merges the updated files of different branches to other branches. In the above example, suppose that Team A and Team B have updated and successfully tested their code and are ready to update the final 'main' branch. They would merge their individual branches with the main branch, thus updating the final product.

- Merging conflicts

Merge conflicts occur when competing changes are made to the same line of a file, or when one person edits a file and another person deletes the same file. 

To resolve a merge conflict caused by competing line changes, you must choose which changes to incorporate from the different branches in a new commit.

For example, if you and another person both edited the file **styleguide.md** on the same lines in different branches of the same Git repository, you'll get a merge conflict error when you try to merge these branches. You must resolve this merge conflict with a new commit before you can merge these branches.

- Resolving merge conflicts using the terminal

1) In the terminal, ```cd``` into the repository that has the conflict


2) Generate a list of the files affected by the merge conflict. In this example, the file **styleguide.md** has a merge conflict.
```
$ git status
> # On branch branch-b
> # You have unmerged paths.
> #   (fix conflicts and run "git commit")
> #
> # Unmerged paths:
> #   (use "git add ..." to mark resolution)
> #
> # both modified:      styleguide.md
> #
> no changes added to commit (use "git add" and/or "git commit -a")
```

3) Open a text editor of your choice and navigate to the conflicted file

4) To see the beginning of the merge conflict in your file, search the file for the conflict marker ```<<<<<<<```. When you open the file in your text editor, you'll see the changes from the HEAD or base branch after the line ```<<<<<<< HEAD```. Next, you'll see ```=======```, which divides your changes from the changes in the other branch, followed by ```>>>>>>> BRANCH-NAME```.

5) Decide if you want to keep only your branch's changes, keep only the other branch's changes, or make a brand new change, which may incorporate changes from both branches. Delete the conflict markers ```<<<<<<<```, ```=======```, ```>>>>>>>``` and make the changes you want in the final merge. In this example, both changes are incorporated into the final merge.

6) Add , commit and push changes.


