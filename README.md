# Git & Heroku Cheatsheet

## Git

```
# Basic Usage
git init # if you didn't fork before from another repo and you don't have a repo yet, creates a repo in github
git status
git diff
git add .
git commit -m "mensagem" -m "descrição"
git remote add origin git@github.com:gustborges/repo-name.git #sets the origin if you don't have it (create the repo first with git init)
git remote -v # check remote repository
git push origin master
git push -u origin master # sets origin master as default upstream so after it you can use just "git push"

# Branches
git checkout -b new-css # creates a branch with new-css name. if you are branching from another branch, it will assume the files from that branch
git push -u origin new-css # pushes branch, you should go to github and make a pull request
git checkout master # or gco master
git diff new-css # compares changes to other branch
(master) git merge new-css # merges the branch new-css to master
(new-css) git merge master # you can also go to the branch and "git merge master" to update the branch. if there's a conflict , you can open the editor and choose the right version
git merge --abort # aborts merge
git branch # see all branches
git branch -d new-css # deletes branch
git pull origin master # updates local using the repository

# Undoing
git reset filename.rb # unstages a file (the opposite of git add)
git reset # unstages all files that weren't committed yet
git reset HEAD~1 # unstages and uncommit last commit
git log # see commits and pick the hash you want to uncommit
git reset uenegdkdkdndh # goes back to the version before that commit
git reset uenegdkdkdndh --hard # same thing but discards changes instead of just unstaging and uncommitting
git revert # use the same way git reset. it commits a new change that undoes the previous activities

# Change last commit (without editing message)
git add file.html.erb
git add -p #use a tool to analyze and add each file
git rm file #remove a file from the staging area
git commit --amend --no-edit
git commit --amend # than you can edit the message as well

# Stash
git stash
git stash save "blabla" # name stashes for easy reference
git stash branch <optional branch name> # start a new branch from a stash
git checkout <stash name> -- <filename> # get a single file from stash
git stash list
git stash show stash@{0} # show the contents
git stash apply # apply the last stash
git stash apply stash@{0}
git stash --include-untracked # keep untracked files
git stash -all # keep all files in the stash including ignored (be careful)
git stash pop # remove the last stash and apply changes (stash apply + stash drop)
git stash drop stash@{n}
git stash clear #clears all stashes

# Check history
git log
heroku releases

More on https://ohshitgit.com
Stash, reflog and rebase - https://www.youtube.com/watch?v=0inyaj2jBXA--
```

## Heroku

```
# Install on OS X
brew tap heroku/brew && brew install heroku

# Help commands
heroku
Usage: heroku COMMAND [--app APP] [command-specific-options]
Primary help topics, type "heroku help TOPIC" for more details:
  addons     # manage addon resources
  apps       # manage apps (create, destroy)
  auth       # authentication (login, logout)
  config     # manage app config vars
  domains    # manage custom domains
  logs       # display logs for an app
  ps         # manage dynos (dynos, workers)
  releases   # manage app releases
  run        # run one-off commands (console, rake)
  sharing    # manage collaborators on an app

heroku login -i # if you have 2FA enabled do not use -i flag
heroku create $YOUR_APP_NAME --region eu
git remote -v # check if the remote was added
git push heroku master
heroku open         # open in your browser
heroku logs --tail  # show the app logs and keep listening
heroku run <command>         # Syntax
heroku run rails db:migrate  # Run pending migrations in prod
heroku run rails c           # Run the production console
```
