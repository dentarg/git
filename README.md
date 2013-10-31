git
===

### Open pull request from command line (with [`hub`](http://hub.github.com/))

    git co -b newstuff
    git ci -m 'Add new stuff'
    git push -u origin newstuff
    hub pull-request
    
    
### Merge pull request from command line (with `hub`)

    git co master
    hub merge https://github.com/user/zambezi/pull/11
    git push

### Remove remote branch

    git push origin :branchname
    
src: [push and delete remote branches](http://gitready.com/beginner/2009/02/02/push-and-delete-branches.html)

### Remove stale tracking branches

    git remote prune origin
    
`--dry-run` is handy if you're unsure what's going to happen:
    
    git remote prune --dry-run origin

src: [How do you Remove an Invalid Remote Branch Reference from Git?](http://stackoverflow.com/questions/1072171/how-do-you-remove-an-invalid-remote-branch-reference-from-git)
