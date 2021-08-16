> **Instructions**
> 
> 1. Answer these questions using Markdown format.   
> 2. **Test that your answers are correct!** There is **no excuse** for submitting an incorrect answer, since you can verify your answers by experimentation.    
> 3. After the title ("Using Git"), create a link to each section (Basics, Adding and Changing Things, Undoing Changes, etc.). One line per link.     
> 4. Delete these instructions.    
> 5. Check that your Markdown formatting is correct (points deducted if incorrect).  VS Code and IntelliJ have markdown previewers. See Sahanon's post on Discord for better VS Code Previewer.
> 
> There are 2 ways to display your answer as lines of *unformatted text* (for commands, not for text answers):
> - (best) put the lines between triple backquotes, as in the source for this file:    
    ```
    unformatted text
    ```
> - leave 4 spaces at start of the line. The text on the line must **not** "look like" a Markdown numbered or bulleted item (if it does, Markdown will format it as a nested list item).

## Using Git

> TODO: Create a table of contents here.  Create a clickable link to each part of this document or other file containing the questions and answers. Each link on a separate line.

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
   * Staging area -
   * Working copy -
   * master -
   * HEAD -

2. A git commit includes the author's name and email.  When you install git on a new machine (or in a new user account) you should perform these 2  git commands to tell git your name and email:
   ```
   # Git configuration commands for a new account


   ```
3. If you want to specify a **different** name and email for a single project (instead of the global values in Item 2 above), in the working directory of that repository enter:
    ```
    # Configuration commands for a single repository

    ``` 
4. There are 2 ways to create a local Git repository.  What are they?
   - todo: briefly describe first way
   - todo: briefly describe second way

5. When you create a git repository in a directory named "/project1" by entering `git init`, Git will create a "hidden" directory for the local repository.  Where is the directory for this local repository (write the full path of the repository)?



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


2. Write the command to add `test/test_a.py` to the staging area (but not any other files).


3. Write a command to list the files in the staging area.



4. You decide you **don't** want to commit `test/test_a.py` to git.  The command to remove `test/test_a.py` from the staging area is:


5. The command to commit everything in the staging area to the repository is:



6. You **never** want any files in the `out/` directory to be added to git. Describe 2 steps to configure the repo so git always ignores files in the `out/` directory:
   - step one
   - step two

7. What is the command to move `a.py`, `b.py`, and `c.py` from the `src` directory to the top-level directory of the project, so that they will also be moved in the git repository?


8. Commit this change with the message "moved src directory":


9. To add **all changed files** (but not untracked files) to the stagin area using a single command, enter:

    (After doing this you should use "git status" to verify you didn't add unintended files.)

10. To **delete** the file `c.py` from your working copy **and** the repository, enter these two commands:



## 3. Undoing Changes

1. To see the differences between your working copy of `a.py` and the `a.py` in the local repository (current version in the repo) enter:


2. If you decide you don't like the changes to `a.py`, what is the command to **replace** your working copy of `a.py` with the most recent (HEAD) version in the repository?    
   (This also works if you accidentally *delete* a file from your working copy.)


3. How do you "undo" a commit? Suppose you want to **discard** some commits and move both HEAD and "master" to an earlier commit (so you can continue working from that commit).  Suppose the commit graph looks like this:
   ```
   aaaaa ---> bbbbb ---> ccccc ---> ddddd [HEAD -> master]
   ``` 
   What are the commands to do this:
   - show all the commits and commit messages so you can find the one you want
   - move HEAD and master to the commit with id bbbbb


 

## 4. Branch and Merge

1. What is the command to create a new branch named `dev-foo`?

 

2. The command to display the name of your current branch is:



3. To list the names of **all** branches, including remote branches, enter:



4. To switch your working copy to the branch named `dev-foo` enter:


5. The steps to merge the work from `dev-foo` into the master branch are:
   - write a brief description, with git commands


6. Describe under what conditions a merge may fail.



## 5. Viewing Commits

1. To show the history of a repository in the terminal (command) window, using one line per commit is:
    ```
    git log --oneline --graph
    ```
    Some versions of git have an *alias* "log1" for this (`git log1`).

2. To show the history (as above) including all branches in the repository, use:


3. To list all the files in the current branch of the repository, enter:


## 6. Favorites

> TODO: Add at least 1 git usage task or situation that you'd like to remember, and the git command(s) to do it.


---
## Resources

> TODO: Add your own favorite Git resources

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
