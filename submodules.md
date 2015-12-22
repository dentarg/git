# [Git Submodules](http://git-scm.com/docs/git-submodule)

## Add

```shell
$ git submodule add \
>     --name easy-rsa \
>     --branch release/2.x \
>     git@github.com:OpenVPN/easy-rsa.git \
>     openvpn/easy-rsa
Cloning into 'openvpn/easy-rsa'...
remote: Counting objects: 442, done.
remote: Total 442 (delta 0), reused 0 (delta 0), pack-reused 442
Receiving objects: 100% (442/442), 167.03 KiB | 0 bytes/s, done.
Resolving deltas: 100% (160/160), done.
Checking connectivity... done.
```

```diff
$ git diff --cached
diff --git a/.gitmodules b/.gitmodules
new file mode 100644
index 0000000..2844c0e
--- /dev/null
+++ b/.gitmodules
@@ -0,0 +1,4 @@
+[submodule "easy-rsa"]
+       path = openvpn/easy-rsa
+       url = git@github.com:OpenVPN/easy-rsa.git
+       branch = release/2.x
diff --git a/openvpn/easy-rsa b/openvpn/easy-rsa
new file mode 160000
index 0000000..987f3cf
--- /dev/null
+++ b/openvpn/easy-rsa
@@ -0,0 +1 @@
+Subproject commit 987f3cf9fa5ddb4da3d4ed5c150ae18ec40dfa29
```

## Status
