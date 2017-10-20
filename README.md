# git Flow Class

### Before we start
* Does anyone have any particularly horrible git-tastrophes that they'd like to share?

* Any burning questions?

* Git is a free and open source distributed version control system designed to handle everything from small to very large projects with speed and efficiency(LOCAL)

* GitHub is a web-based Git repository hosting service.

* [Setting your OSX Keychain](https://help.github.com/articles/caching-your-github-password-in-git/)

* [Setting up autocomplete for git commands](https://github.com/bobthecow/git-flow-completion/wiki/Install-Bash-git-completion)

* [Setting up hub](https://github.com/github/hub)

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
11. go to GitHub! (hub browse)
12. create a pull request(make sure its going to the right place)
13. hit the 'submit pull request' button
14. contact partner to review pull request
15. partner merges pull request
16. git checkout master, git pull origin master, and repeat the process

## Other very common commands I use

* `git init and hub create`

* `git stash`

* `git stash pop`

* `git status`

* `git diff`

* `hub browse`

* `git fetch`

* `git log`

* `git remote -v`

* `git remote add "name" "url"`

## Git Workflow, according to GitHub

When working on a team, it’s important to have a workflow. The details of the workflow will vary from team to team and company to company, but it's important that you have a workflow.

Below is GitHub's workflow. Most teams will do something similar. Step 6 can vary.

1. Anything in the master branch is deployable
2. To work on something new, create a descriptively named branch off of master (ie: new-oauth2-scopes)
3. Commit to that branch locally and regularly push your work to the same named branch on the server
4. When you need feedback or help, or you think the branch is ready for merging, open a pull request
5. After someone else has reviewed and signed off on the feature, you can merge it into master
6. Once it is merged and pushed to ‘master’, you can and should deploy immediately

It's useful to think of branches like Ruby methods: they should be small, have descriptive names and implement a single feature. Use branches for the small features that you can implement quickly.

When your feature is complete, don't just merge it into master—submit a pull request and let someone from your team review your code.

## Github and Code Reviews

Having your code reviewed gives you confidence that your code is clear, that it runs on someone else's machine, and that it's not accidently causing an error somewhere else in the application. It's also an opportunity to allow a mentor to review the code you're writing and give you advice.

Reviewing a teammate's code allows you to be familiar with parts of the codebase that you may not have touched. It also provides context for how the code your writing in your branch fits into the larger app.

Tools for conducting a code review:

* Line comments on Github
* Discussion in Github Issues and Waffle.io

__WIP Pull Request:__ A pull request isn’t the final word. You can always add to it based on feedback, so it can be a useful collaboration tool for code that's still "under development." Many teams will call this a "WIP" PR and sometimes will mark it with a special label (to make sure it doesn't accidentally get merged).

## Activity: Conflict Resolution

In pairs assign one person the role of `Person 1` and the other `Person 2`.

1. Person 1: Create a repo on Github with a README. Add Person 2 as a Collaborator.

1. Extra Challenge(optional): Add 2 issues to your github issues, one for Person 1, the other for Person 2.

1. Both: checkout a unique branch.

  Example:
  
  `git checkout -b person_1_changes_stuff`
  
  `git checkout -b person_2_changes_things`

1. Both: Make changes to the same line in the README in both repos.

1. Person 1: Push your branch and open a PR.

1. Person 2: Merge the PR 
  * If doing the extra challenge: close the issue assigned to Person 1 via a commit message.
  * [halp?](https://help.github.com/articles/closing-issues-via-commit-messages/)

1. Person 2: Push your branch and open a PR.
  * Notice that we can’t merge it automatically
  * We need to fix it locally first

1. Person 2: checkout the master branch.

1. Person 2: Pull from master on Github.

1. Person 2: Checkout the branch you have an open PR for.

1. Person 2: Merge master into your current branch.
  * This should throw an error
  CONFLICT (content): Merge conflict in readme.md
   Automatic merge failed; fix conflicts and then commit the result.

1. Person 2: Open the file it says the conflict occurs in. You can see it if you run git status

1. Person 2: You see something that looks like this:

```git
<<<<<<< HEAD
Person 2 adds a line!
=======
Person 1 Adds a line!
>>>>>>> master
```
1. Person 2: Update the line to look the way you want it to look
  * Remove the `<<<< HEAD`, `=======`, and `>>>> master` lines

1. Person 2: running git status tells you how to mark the conflict as resolved
  * After resolving and running git status you will see a `Changes to be committed` message.

1. Person 2: Commit the resolved changes

1. Person 2: Push the changes to your branch on Github

1. Reload the pull request
  * It should now be able to be merged in automatically
  * You should also see the commit that merged the two changes
  * If doing the extra challenge: Person 1: Merge the PR and close the issue via your commit message.
  [halp?](https://help.github.com/articles/closing-issues-via-commit-messages/)

## Other Git Commands
  
* git stash
  * git stash is used to save the state of your working directory as well as your index directory.  
  * It also reverts you back to a clean directory at your HEAD commit.

* git stash apply
  * git stash apply allows you to revert to a previous stash by either specicfying ie. git stash apply stash@{2}, which will take you back to the specified stash.  
  * Or, simply typing git stash apply will revert to your most recent stash.

* git shortlog
  * ths outputs a summary of the log read from standard input, without reference to the current repository.  Lists all commits by all authors in individualized lists

* git commit --amend
  * --amend allows you to combine staged changes with the previous instead of committing it as an entirely new snapshot.

* git reset --hard
  * This resets the index and the working tree.  Any changes to tracked files since the last commit are discarded.

* git reset --soft
  * This does not touch the index or working tree but resets the head to the latest commit and leaves all files unstaged.

* Setting your git config to use a certain text editor
  * `git config --global core.editor "sublime —wait"`

