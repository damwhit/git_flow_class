# git Flow Class

### Before we start
* Does anyone have any particularly horrible git-tastrophes that they'd like to share?

* Any burning questions?

* [Setting your OSX Keychain](https://help.github.com/articles/caching-your-github-password-in-git/)

* [Setting up autocomplete for git commands](https://github.com/bobthecow/git-flow-completion/wiki/Install-Bash-git-completion)
  * `alias bash='sublime ~/.bash_profile'`
  
## Git Flow
1. git checkout -b <branch_name> (this creates a new branch and checks out to that same branch)
2. do work
3. commit (add, commit)
4. git checkout master
5. git pull origin master
6. git checkout <branch_name>
7. git merge master
8. fix conflicts! (tells you on command line where to look in editor)
9. run tests if applicable
10. git push origin <branch_name>
11. go to GitHub!
12. create a pull request(make sure its going to the right place)
13. hit the 'submit pull request' button
14. contact partner to review pull request
15. partner merges pull request
16. git checkout master, git pull origin master, and repeat the process

## Some more useful commands

* `git diff`
  * shows all of the additions and deletions in your working directory

* `git remote -v`
  * check all remotes associated with local repo

* `git remote add <name(ie. origin or upstream)> <url>`
  * add another remote repo to your local repository
  
* `git stash`
  * saves the state of your working directory.  
  * It also reverts you back to a clean directory at your HEAD commit.

* `git stash pop`
  * gives you back changes from your last stash
  
* `git stash apply`
  * allows you to revert to a previous stash by either specicfying ie. git stash apply stash@{2}, which will take you back to the specified stash.  
  * Or, simply typing git stash apply will revert to your most recent stash.

* `git reset --hard`
  * This resets the index and the working tree.  Any changes to tracked files since the last commit are discarded.

* `git reset`
  * This does not touch the index or working tree but resets the head to the latest commit and leaves all files unstaged.

* Setting your git config to use a certain text editor
  * `git config --global core.editor "sublime —wait"`

## Git Workflow, according to GitHub

It's useful to think of branches like JavaScript functions: they should be small, have descriptive names and implement a single feature. Use branches for the small features that you can implement quickly.

## Activity: Conflict Resolution

In pairs assign one person the role of `Person 1` and the other `Person 2`.

1. Person 1: Create a repo on Github with a README. Add Person 2 as a Collaborator.

2. Extra Challenge(optional): Add 2 issues to your github issues, one for Person 1, the other for Person 2.

3. Both: checkout a unique branch.

  Example:
  
  `git checkout -b person1-update-readme`
  
  `git checkout -b person2-update-readme`

4. Both: Make changes to the same line in the README in both repos.

5. Person 1: Push your branch and open a PR.

6. Person 2: Merge the PR 
  * If doing the extra challenge: close the issue assigned to Person 1 via a commit message.
  * [halp?](https://help.github.com/articles/closing-issues-via-commit-messages/)

7. Person 2: Push your branch and open a PR.
  * Notice that we can’t merge it automatically
  * We need to fix it locally first

8. Person 2: checkout the master branch.

9. Person 2: Pull from master on Github.

10. Person 2: Checkout the branch you have an open PR for.

11. Person 2: Merge master into your current branch.
  * This should throw an error
  CONFLICT (content): Merge conflict in readme.md
   Automatic merge failed; fix conflicts and then commit the result.

12. Person 2: Open the file it says the conflict occurs in. You can see it if you run git status

13. Person 2: You see something that looks like this:

```git
<<<<<<< HEAD
Person 2 adds a line!
=======
Person 1 Adds a line!
>>>>>>> master
```
14. Person 2: Update the line to look the way you want it to look
  * Remove the `<<<< HEAD`, `=======`, and `>>>> master` lines

15. Person 2: running git status tells you how to mark the conflict as resolved
  * After resolving and running git status you will see a `Changes to be committed` message.

16. Person 2: Commit the resolved changes

17. Person 2: Push the changes to your branch on Github

18. Reload the pull request
  * It should now be able to be merged in automatically
  * You should also see the commit that merged the two changes
  * If doing the extra challenge: Person 1: Merge the PR and close the issue via your commit message.
  [halp?](https://help.github.com/articles/closing-issues-via-commit-messages/)
  * If not: Person 1: Just merge the PR
