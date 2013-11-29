git
===

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

### Remove remote branch

    git push origin :branchname
    
src: [push and delete remote branches](http://gitready.com/beginner/2009/02/02/push-and-delete-branches.html)

### Remove stale tracking branches

    git remote prune origin
    
`--dry-run` is handy if you're unsure what's going to happen:
    
    git remote prune --dry-run origin

src: [How do you Remove an Invalid Remote Branch Reference from Git?](http://stackoverflow.com/questions/1072171/how-do-you-remove-an-invalid-remote-branch-reference-from-git)
