## Using Git

[1. Basics](#1-basics)<br/>
[2. Adding and Changing Things](#2-adding-and-changing-things)  <br/> 
[3. Undoing Changes](#3-undoing-changes)<br/>
[4. Branch and Merge](#4-branch-and-merge)<br/>
[5. Viewing Commits](#5-viewing-commits)<br/>
[6. Favorites](#6-favorites)<br/>
[Resources](#resources)

### Note on Paths

In this file, directory paths are written with a forward slash as on MacOS, Linux, and the Windows-Bash shell: `/dir1/dir2/somefile`.    
For the MS Windows command prompt, when using the command substitute a backslash: `\dir1\dir2\somefile`.


## 1. Basics

1. When working with Git locally, what are these?  Describe each one in a sentence
   * Staging area - files and changes marked for commit, but not yet committed.
   * Working copy - the copy of files you see and can edit. The working copy may include files ‘tracked’ by git and untracked files.
   * master - a repository's primary branch.
   * HEAD - a label that refers to the commit your working copy is based on.

2. A git commit includes the author's name and email.  When you install git on a new machine (or in a new user account) you should perform these 2  git commands to tell git your name and email:
   ```
   git config –global user.name “[name]”
   git config –global user.email “[email address]”
   ```
3. If you want to specify a **different** name and email for a single project (instead of the global values in Item 2 above), in the working directory of that repository enter:
    ```
    git init [repository name]
    ``` 
4. There are 2 ways to create a local Git repository.  What are they?
   - Take a local directory that is currently not under version control, and turn it into a Git repository.
   - Clone an existing Git repository from elsewhere.

5. When you create a git repository in a directory named "/project1" by entering `git init`, Git will create a "hidden" directory for the local repository.  Where is the directory for this local repository (write the full path of the repository)?
   ```
   /project1/.git/
   ```


## 2. Adding and Changing Things

Suppose your working copy of a repository contains these files and directories:
```
README.md
out/
    a.exe
src/a.py
    b.py
    c.py
test/
    test_a.py
    ...
```     

1. What is the command to add README.md and *everything* in the `src` directory to the git staging area?
   ```
   git add src
   ```

2. Write the command to add `test/test_a.py` to the staging area (but not any other files).
   ```
   git add test/test_a.py
   ```

3. Write a command to list the files in the staging area.
   ```
   git status
   ```

4. You decide you **don't** want to commit `test/test_a.py` to git.  The command to remove `test/test_a.py` from the staging area is:
   ```
   git rm --cached test/test_a.py
   ```

5. The command to commit everything in the staging area to the repository is:
   ```
   git commit -m "[commit message]"
   ```

6. You **never** want any files in the `out/` directory to be added to git. Describe 2 steps to configure the repo so git always ignores files in the `out/` directory:
   - Create a file named `.gitignore` with the following written inside
     ```
     out/
     ```
   - Add the `.gitignore` file to the repo via the following commands:
     ```
     git add .gitignore
     git commit -m "added .gitignore"
     ```

7. What is the command to move `a.py`, `b.py`, and `c.py` from the `src` directory to the top-level directory of the project, so that they will also be moved in the git repository?
   ```
   git mv src/* .
   ```

8. Commit this change with the message "moved src directory":
   ```
   git commit -m "moved src directory"
   ```

9. To add **all changed files** (but not untracked files) to the staging area using a single command, enter:
   ```
   git add -A
   ```
    (After doing this you should use "git status" to verify you didn't add unintended files.)

10. To **delete** the file `c.py` from your working copy **and** the repository, enter these two commands:
   ```
   git rm c.py
   git commit -m "removed c.py"
   ```


## 3. Undoing Changes

1. To see the differences between your working copy of `a.py` and the `a.py` in the local repository (current version in the repo) enter:
   ```
   git diff a.py
   ```

2. If you decide you don't like the changes to `a.py`, what is the command to **replace** your working copy of `a.py` with the most recent (HEAD) version in the repository?    
   (This also works if you accidentally *delete* a file from your working copy.)
   ```
   git checkout -- a.py
   ```

3. How do you "undo" a commit? Suppose you want to **discard** some commits and move both HEAD and "master" to an earlier commit (so you can continue working from that commit).  Suppose the commit graph looks like this:
   ```
   aaaaa ---> bbbbb ---> ccccc ---> ddddd [HEAD -> master]
   ``` 
   What are the commands to do this:
   - Show all the commits and commit messages so you can find the one you want
     ```
     git log
     ```
   - Move HEAD and master to the commit with id bbbbb
     ```
     git reset --hard bbbbb
     ```
 

## 4. Branch and Merge

1. What is the command to create a new branch named `dev-foo`?
   ```
   git branch dev-foo
   ```

2. The command to display the name of your current branch is:
   ```
   git branch --show-current
   ```

3. To list the names of **all** branches, including remote branches, enter:
   ```
   git branch -a 
   ```

4. To switch your working copy to the branch named `dev-foo` enter:
   ```
   git checkout dev-foo
   ```

5. The steps to merge the work from `dev-foo` into the master branch are:
   - Switch to the `master` branch using `git checkout`, then start merging using `git merge`.
     ```
     git checkout master
     git merge dev-foo
     ``` 

6. Describe under what conditions a merge may fail.<br/>
   - When you changed the same part of the same file differently in the two branches you want to merge.
   - When s file has been deleted in one of the two branches you want to merge.


## 5. Viewing Commits

1. To show the history of a repository in the terminal (command) window, using one line per commit is:
    ```
    git log --oneline --graph
    ```
    Some versions of git have an *alias* "log1" for this (`git log1`).

2. To show the history (as above) including all branches in the repository, use:
   ```
   git log --oneline --graph --decorate
   ```

3. To list all the files in the current branch of the repository, enter:
   ```
   git ls-tree -r [current branch's name]
   ```


## 6. Favorites

> **Upload the local repository's changes to the remote repository**
> ```
> git push
> ```
> **Copy Changes from the remote repository**
> ```
> git pull
> ```


---
## Resources

> https://www.atlassian.com/git/tutorials
> https://git-scm.com/docs

Learn Git:

[Pro Git Online Book][ProGit] best source for Git. Ch. 2 & 3 contain the essentials. Free e-book download available.     
[Visual Git Reference](https://marklodato.github.io/visual-git-guide) one page with illustrations of git commands.

Try Git:

[Learn Git Interactive Tutorial][LearnGitInteractive] excellent visual tutorial.   
[Git Visualizer][VisualizeGit] execute Git commands and see the results as a graph.    

[ProGit]: https://www.git-scm.com/book/en/v2 "Pro Git online book on Git-scm.com"
[ProGitPdf]: https://progit2.s3.amazonaws.com/en/2016-03-22-f3531/progit-en.1084.pdf "Pro Git v.2 PDF on AWS. Longer, book format."
[LearnGitInteractive]: https://learngitbranching.js.org "Interactive graphical git tutorial"
[VisualizeGit]: http://git-school.github.io/visualizing-git/ "Online tools draws a graph of commits in a repo as you type"
