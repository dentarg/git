git
===

### Change commit messages of past commits

    git rebase -i <commit before the first you want to edit>

Replace "pick" with "reword" for the commits you want to edit the message of. `$EDITOR` will open automatically until there's no more commit messages to edit.

src: [Change old commit message on Git](http://stackoverflow.com/questions/1884474/change-old-commit-message-on-git), [Change commit messages of past Git commits](http://makandracards.com/makandra/868-change-commit-messages-of-past-git-commits)

### Open pull request from command line (with [`hub`](http://hub.github.com/))

    git co -b newstuff
    git ci -m 'Add new stuff'
    git push -u origin newstuff
    hub pull-request
    
#### Convert existing issue to a pull request:

    hub pull-request -i <issue number>

Note: You need to be the creator of the issue.

src: [How do you attach a new pull request to an existing issue on github?](http://stackoverflow.com/questions/4528869/how-do-you-attach-a-new-pull-request-to-an-existing-issue-on-github)
    
### Merge pull request from command line (with `hub`)

    git co master
    hub merge https://github.com/user/zambezi/pull/11
    git push

src: [man hub](http://hub.github.com/hub.1.html)

### Undo last commit and keep the changes

    git reset --soft HEAD^

src: [Git Delete Last Commit](http://nakkaya.com/2009/09/24/git-delete-last-commit/)

### Delete the last commit (does NOT keep the changes)

    git reset --hard HEAD^
    
src: [Git Delete Last Commit](http://nakkaya.com/2009/09/24/git-delete-last-commit/)

### Reset master to origin/master

    git co master

    # optional backup
    git branch previous_master

    git reset --hard origin/master

src: [How to reset master to origin/master?](http://superuser.com/questions/273172/how-to-reset-master-to-origin-master)

### Selective `git stash`

> You can use git stash save --keep-index when you want to make two or more commits out of the changes in the work tree, and you want to test each change
before committing:

    # ... hack hack hack ...
    $ git add --patch foo            # add just first part to the index
    $ git stash save --keep-index    # save all other changes to the stash
    $ edit/build/test first part
    $ git commit -m 'First part'     # commit fully tested change
    $ git stash pop                  # prepare to work on all other changes
    # ... repeat above five steps until one commit remains ...
    $ edit/build/test remaining parts
    $ git commit foo -m 'Remaining parts'

src: [`git-stash(1)`](http://git-scm.com/docs/git-stash)

### Tracking Branches

    git co -t origin/<new_branch>

Example:

    $ git branch -a
    * master
      remotes/origin/coolbranch
      remotes/origin/master
    $ git co -t origin/coolbranch
    $ git branch -a
      master
    * coolbranch
      remotes/origin/coolbranch
      remotes/origin/master

src: [Tracking Branches](http://git-scm.com/book/en/Git-Branching-Remote-Branches#Tracking-Branches), [`git-checkout(1)`](http://git-scm.com/docs/git-checkout)

### Remove remote branch

    git push origin :branchname
    
src: [push and delete remote branches](http://gitready.com/beginner/2009/02/02/push-and-delete-branches.html)

### Remove stale tracking branches

    git remote prune origin
    
`--dry-run` is handy if you're unsure what's going to happen:
    
    git remote prune --dry-run origin

src: [How do you Remove an Invalid Remote Branch Reference from Git?](http://stackoverflow.com/questions/1072171/how-do-you-remove-an-invalid-remote-branch-reference-from-git)
