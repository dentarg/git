Added submodules are locked to specific commit, and will continue to be until we do something:

```sh
$ git submodule status
 8ef28bceaa6a9eded47e640d26df4a6f3a80320c cookbooks/apt (v2.2.0-29-g8ef28bc)
 494290c8d9a042e52ba8b9ee7976b6c46f09906a cookbooks/sysctl (v0.3.3-4-g494290c)
 965ca2371e551d036a690775e17b32234c3bb5ec cookbooks/ulimit (v0.2.0-20-g965ca23)
```

## Update

```sh
$ git submodule update --remote cookbooks/apt
Submodule path 'cookbooks/apt': checked out 'ac1917c66a9d67fb4a0afeffaa92195b7385887e'
$ git st
On branch master
Your branch is up-to-date with 'origin/master'.

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

	modified:   cookbooks/apt (new commits)

no changes added to commit (use "git add" and/or "git commit -a")
$ git diff
diff --git a/cookbooks/apt b/cookbooks/apt
index 8ef28bc..ac1917c 160000
--- a/cookbooks/apt
+++ b/cookbooks/apt
@@ -1 +1 @@
-Subproject commit 8ef28bceaa6a9eded47e640d26df4a6f3a80320c
+Subproject commit ac1917c66a9d67fb4a0afeffaa92195b7385887e
$ git submodule status
+ac1917c66a9d67fb4a0afeffaa92195b7385887e cookbooks/apt (v2.2.0-38-gac1917c)
 494290c8d9a042e52ba8b9ee7976b6c46f09906a cookbooks/sysctl (v0.3.3-4-g494290c)
 965ca2371e551d036a690775e17b32234c3bb5ec cookbooks/ulimit (v0.2.0-20-g965ca23)
```

`git commit` and `git push` if you want to introduce the changes. 

`git submodule update --init` if you want to undo your changes (`git checkout` does nothing).

## Remove

````sh
$ git submodule deinit cookbooks/apt
Cleared directory 'cookbooks/apt'
Submodule 'cookbooks/apt' (https://github.com/opscode-cookbooks/apt.git) unregistered for path 'cookbooks/apt'
$ git st
On branch master
Your branch is up-to-date with 'origin/master'.

nothing to commit, working directory clean
$ git rm cookbooks/apt
rm 'cookbooks/apt'
$ git st
On branch master
Your branch is up-to-date with 'origin/master'.

Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

	modified:   .gitmodules
	deleted:    cookbooks/apt

$ git diff --cached
diff --git a/.gitmodules b/.gitmodules
index 5fbf575..39b18fb 100644
--- a/.gitmodules
+++ b/.gitmodules
@@ -1,9 +1,6 @@
 [submodule "cookbooks/sysctl"]
        path = cookbooks/sysctl
        url = https://github.com/onehealth-cookbooks/sysctl.git
-[submodule "cookbooks/apt"]
-       path = cookbooks/apt
-       url = https://github.com/opscode-cookbooks/apt.git
 [submodule "cookbooks/ulimit"]
        path = cookbooks/ulimit
        url = https://github.com/bmhatfield/chef-ulimit.git
diff --git a/cookbooks/apt b/cookbooks/apt
deleted file mode 160000
index 8ef28bc..0000000
--- a/cookbooks/apt
+++ /dev/null
@@ -1 +0,0 @@
-Subproject commit 8ef28bceaa6a9eded47e640d26df4a6f3a80320c
$ git submodule status
 494290c8d9a042e52ba8b9ee7976b6c46f09906a cookbooks/sysctl (v0.3.3-4-g494290c)
 965ca2371e551d036a690775e17b32234c3bb5ec cookbooks/ulimit (v0.2.0-20-g965ca23)
````

`git commit` and `git push` if you want to introduce the changes. 

`git reset`, `git checkout .` and `git submodule update --init` if you want to undo your changes.

Sources:

* http://git-scm.com/docs/git-submodule
* http://stackoverflow.com/questions/1260748/how-do-i-remove-a-git-submodule
