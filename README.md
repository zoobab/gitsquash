# Gitsquash
A shell script to squash git commits

# Why?
Because authors of git don't provide this basic feature built-in.

# Screenshot
This is an example with the `zoobab/versaloon` git repo:

```
zoobab@machine soft/versaloon [master] $ git log --oneline -n3
eace3a4 HK flag protest SVG test
c8ba1cb openwrt forum
0cab911 add VID and PID to openocd config

zoobab@machine soft/versaloon [master] $ gitsq 2 'squashing Honk-Kong protests and Openwrt forums'
---------------------------------
Will squash 2 commits
Commit message will be 'squashing Honk-Kong protests and Openwrt forums'
...validating input
...input looks good
...proceeding to squash
[master e5cd1b0] squashing Honk-Kong protests and Openwrt forums
 1 file changed, 2 insertions(+), 1 deletion(-)
...done

zoobab@machine  soft/versaloon [master] $ git log --oneline -n3
e5cd1b0 squashing Honk-Kong protests and Openwrt forums
0e7c7af add quotes around filename
0cab911 add VID and PID to openocd config
```

# Alternatives

I now use this configuration in my ```$HOME/.gitconfig``` explained in this blog post ```git squash, add a global “squash” alias from bash``` (https://medium.com/@crafttang/git-squash-d4daf8a9b731):

```
$ cat .gitconfig
[alias]
    squash = "!f(){ git reset --soft HEAD~${1} && git commit --edit -m\"$(git log --format=%B --reverse HEAD..HEAD@{1})\"; };f"
```

# Source

* Modified from https://stackoverflow.com/questions/7275508/is-there-a-way-to-squash-a-number-of-commits-non-interactively/44802383
* https://medium.com/@crafttang/git-squash-d4daf8a9b731
