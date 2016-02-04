# Git

#### Delete Branch

```bash
git push origin --delete <branchName>
```

#### Branch Authors

```bash
git for-each-ref --format='%(committerdate)%09%(authorname)%09%(refname)' | sort -k5n -k2M -k3n -k4n | grep remotes | awk -F "\t" '{ printf "%-32s %-27s %s\n", $1, $2, $3 }'
```

#### Merged Remote Branches

```bash
for branch in `git branch -r --merged | grep -v HEAD`; do echo -e `git show --format="%ci %cr %an" $branch | head -n 1` \\t$branch; done | sort -r
```

#### Unmerged Remote Branches

```bash
for branch in `git branch -r --no-merged | grep -v HEAD`; do echo -e `git show --format="%ci %cr %an" $branch | head -n 1` \\t$branch; done | sort -r
```

### Alias: `gpk`

```bash
alias gpk='git count-objects -vH && echo "" && git repack -a -d -f --depth=250 --window=250 && echo "" && git count-objects -vH'
```

### `git gc --aggressive`

> While git generally tries to re-use delta information (because it's a good idea, and it doesn't waste CPU time re-finding all the good deltas we found earlier), sometimes you want to say "let's start all over, with a blank slate, and ignore all the previous delta information, and try to generate a new set of deltas".

> ~ [Linus](http://markmail.org/message/gv4uua6ffsuhhjyt)


## [Git Compression of Blobs and Packfiles](https://gist.github.com/matthewmccullough/2695758)

Many users of Git are [curious about](http://programmers.stackexchange.com/questions/148434/why-do-git-mercurial-repositories-use-less-space/148498#148498) the lack of delta compression at the object (blob) level when commits are first written. This efficiency is saved until the pack file is written. Loose objects are written in compressed, but non-delta format at the time of each commit.

A simple run though of a commit sequence with only the smallest change to the image (in uncompressed TIFF format to amplify the observable behavior) aids the understanding of this deferred and different approach efficiency.


### The command sequence:

Create the repo:

```sh
$ git init test6
Initialized empty Git repository in /Users/torsday/Documents/Temp/Scratch/test6/.git/
[master (root-commit) 05e9c3e] First-commit
 0 files changed
 create mode 100644 README

$ du -c
72	./.git/hooks
8	./.git/info
8	./.git/logs/refs/heads
8	./.git/logs/refs
16	./.git/logs
8	./.git/objects/05
8	./.git/objects/54
8	./.git/objects/e6
0	./.git/objects/info
0	./.git/objects/pack
24	./.git/objects
8	./.git/refs/heads
0	./.git/refs/tags
8	./.git/refs
0	./.git/rr-cache
168	./.git
168	.
168	total
```

There's only a total of 168kb for the entire repo and working directory.

Now copy in the white image:

```sh
$ cp ../completely-white.tiff .
```

And show how large that image is (5294kb) in an uncompressed TIFF format:

```sh
$ ls -al
total 10344
drwxr-xr-x   5     170 .
drwxrwxr-x   6     204 ..
drwxr-xr-x  15     510 .git
-rw-r--r--   1       0 README
-rw-r--r--   1 5294996 completely-white.tiff
```

And show the size of the entire repo and working copy:

```sh
$ du -c
72	./.git/hooks
8	./.git/info
8	./.git/logs/refs/heads
8	./.git/logs/refs
16	./.git/logs
8	./.git/objects/05
8	./.git/objects/54
8	./.git/objects/e6
0	./.git/objects/info
0	./.git/objects/pack
24	./.git/objects
8	./.git/refs/heads
0	./.git/refs/tags
8	./.git/refs
0	./.git/rr-cache
168	./.git
10512	.
10512	total
```

Now add that file to the staging area and commit it.

```sh
$ git add .
$ git commit -m"White image added"
[master f93724b] White image added
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 completely-white.tiff

$ du -c
72	./.git/hooks
8	./.git/info
8	./.git/logs/refs/heads
8	./.git/logs/refs
16	./.git/logs
8	./.git/objects/05
8	./.git/objects/54
8	./.git/objects/87
56	./.git/objects/90
8	./.git/objects/e6
8	./.git/objects/f9
0	./.git/objects/info
0	./.git/objects/pack
96	./.git/objects
8	./.git/refs/heads
0	./.git/refs/tags
8	./.git/refs
0	./.git/rr-cache
240	./.git
10584	.
10584	total
```

The file is compressed when saved to its blob in the objects/90 directory and thus is only 56kb in size.

Make minor edits to the image:

```sh
$ open completely-white.tiff -a Pixelmator

$ git status
# On branch master
# Changes not staged for commit:
#   (use "git add <file>..." to update what will be committed)
#   (use "git checkout -- <file>..." to discard changes in working directory)
#
#	modified:   completely-white.tiff
#
no changes added to commit (use "git add" and/or "git commit -a")

$ git add .
$ git commit -m"Dot added to white image"
[master 3015c4a] Dot added to white image
 1 file changed, 0 insertions(+), 0 deletions(-)
```

Now, after the second minor alteration, we can see there is an equally sized 56kb directory called 31 that contains the blob for the modified image.

```sh
$ du -c
72	./.git/hooks
8	./.git/info
8	./.git/logs/refs/heads
8	./.git/logs/refs
16	./.git/logs
8	./.git/objects/05
8	./.git/objects/30
56	./.git/objects/31
8	./.git/objects/47
8	./.git/objects/54
8	./.git/objects/87
56	./.git/objects/90
8	./.git/objects/e6
8	./.git/objects/f9
0	./.git/objects/info
0	./.git/objects/pack
168	./.git/objects
8	./.git/refs/heads
0	./.git/refs/tags
8	./.git/refs
0	./.git/rr-cache
312	./.git
10656	.
10656	total
```

Lastly, we will compress the history into a single packfile instead of loose objects:

```sh
$ git gc --aggressive
Counting objects: 9, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (7/7), done.
Writing objects: 100% (9/9), done.
Total 9 (delta 1), reused 0 (delta 0)
$ du -c
72	./.git/hooks
16	./.git/info
8	./.git/logs/refs/heads
8	./.git/logs/refs
16	./.git/logs
8	./.git/objects/info
32	./.git/objects/pack
40	./.git/objects
0	./.git/refs/heads
0	./.git/refs/tags
0	./.git/refs
0	./.git/rr-cache
192	./.git
10536	.
10536	total
```

And you can see that the combined packfile is only 40kb instead of 168kb when stored separately in two unique blobs in separate object directories.

### References
* [Git Internal References](http://git-scm.com/book/en/Git-Internals-Git-References)
* [Packfiles](http://git-scm.com/book/en/Git-Internals-Packfiles)
* [StackOverflow question on Git Efficiency](http://programmers.stackexchange.com/questions/148434/why-do-git-mercurial-repositories-use-less-space/148498#148498)
