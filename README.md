git
===

### Change commit messages of past commits

    git rebase -i <commit before the first you want to edit>

Replace "pick" with "reword" for the commits you want to edit the message of. `$EDITOR` will open automatically until there's no more commit messages to edit.

src: [Change old commit message on Git](http://stackoverflow.com/questions/1884474/change-old-commit-message-on-git), [Change commit messages of past Git commits](http://makandracards.com/makandra/868-change-commit-messages-of-past-git-commits)

### Change tag annotation message

    # Fixing tag named '1.0.1'
    git checkout 1.0.1               # Go to the associated commit
    git tag -d 1.0.1                 # Locally delete the tag
    git push origin :refs/tags/1.0.1 # Push this deletion up to GitHub

    # Create the tag, with a date derived from the current head
    GIT_COMMITTER_DATE="$(git show --format=%aD | head -1)" git tag -a 1.0.1 -m"v1.0.1"

    git push --tags                  # Send the fixed tags to GitHub

src: [How do I edit an existing tag message in git?](http://stackoverflow.com/a/29019547/525616), [Change date of git tag (or GitHub Release based on it)](http://stackoverflow.com/a/21741848/525616)

### Open commit from command line (with [`hub`](http://hub.github.com/))

    hub browse -- commit/46109ccf
    
src: [hub browse: improve support for opening a commit](https://github.com/github/hub/issues/516)

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

### Undo N last commits and keep the changes

N=3:

    git reset --soft HEAD~3

src: [Squash my last X commits together using Git](http://stackoverflow.com/questions/5189560/squash-my-last-x-commits-together-using-git/5201642#5201642)

### Delete the last commit (does NOT keep the changes)

    git reset --hard HEAD^

src: [Git Delete Last Commit](http://nakkaya.com/2009/09/24/git-delete-last-commit/)

### Start a git commit message with a hashmark (`#`)

    git commit --cleanup=whitespace

src: [Start a git commit message with a hashmark (`#`)](http://stackoverflow.com/questions/2788092/start-a-git-commit-message-with-a-hashmark)

### Patches

Create patch file for a commit

    $ git format-patch -1 c460a1a324571b30ef2a6f4373be053c1ead2066
    0001-Push-arbitrary-branch-to-origin-master.patch

Check if you can apply the patch

    $ git apply --check 0001-Push-arbitrary-branch-to-origin-master.patch

Apply the diff, but don't commit

    $ git apply 0001-Push-arbitrary-branch-to-origin-master.patch

Apply the diff and make a commit

    $ git am < 0001-Push-arbitrary-branch-to-origin-master.patch

If someone else wrote the patch

    $ git am --signoff < 0001-Push-arbitrary-branch-to-origin-master.patch

Can be handy to be able to ignore whitespace

    $ git apply --ignore-space-change --ignore-whitespace < 0001-Push-arbitrary-branch-to-origin-master.patch

src: [How to create and apply a patch with Git](https://ariejan.net/2009/10/26/how-to-create-and-apply-a-patch-with-git/), [git: patch does not apply](http://stackoverflow.com/questions/4770177/git-patch-does-not-apply)

### Push arbitrary branch to origin/master

    git push origin my-feature-branch:master

Useful when working with i.e. Heroku where the master branch gets deployed on push.

### Reset master to origin/master

    git co master

    # optional backup
    git branch previous_master

    git reset --hard origin/master

src: [How to reset master to origin/master?](http://superuser.com/questions/273172/how-to-reset-master-to-origin-master)

### Search in history

    git log -p -S search_string

src: [git-log(1) Manual Page](http://git-scm.com/docs/git-log)

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

### Remove remote tag

    git tag -d mytag
    git push origin :refs/tags/mytag

src: [How to: Delete a remote Git tag](https://nathanhoad.net/how-to-delete-a-remote-git-tag)

### Remove stale tracking branches

    git remote prune origin

`--dry-run` is handy if you're unsure what's going to happen:

    git remote prune --dry-run origin

src: [How do you Remove an Invalid Remote Branch Reference from Git?](http://stackoverflow.com/questions/1072171/how-do-you-remove-an-invalid-remote-branch-reference-from-git)
