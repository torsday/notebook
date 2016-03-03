# Git

## Basics

```sh
git init
git clone <repo_url>
git checkout <pre-existing-branch-name>
git checkout -b <new_branch_name>
```

## Commands

### adding a remote

```sh
git add remote <name> <url>
```

### [`count-objects`](https://git-scm.com/docs/git-count-objects)

Count unpacked number of objects and their disk consumption

```sh
git count-objects -vH
# -v  verbose
# -H  human readable
```

-   **count:** the number of loose objects
-   **size:** disk space consumed by loose objects, in KiB (unless -H is specified)
-   **in-pack:** the number of in-pack objects
-   **size-pack:** disk space consumed by the packs, in KiB (unless -H is specified)
-   **prune-packable:** the number of loose objects that are also present in the packs. These objects could be pruned using git prune-packed.
-   **garbage:** the number of files in object database that are neither valid loose objects nor valid packs
-   **size-garbage:** disk space consumed by garbage files, in KiB (unless -H is specified)

### [`gc`](https://git-scm.com/docs/git-gc)

Cleanup unnecessary files and optimize the local repository.

> Users are encouraged to run this task on a regular basis within each repository to maintain good disk space utilization and good operating performance.

#### options

```sh
--aggressive
```

Usually git gc runs very quickly while providing good disk space utilization and performance. This option will cause git gc to more aggressively optimize the repository at the expense of taking much more time. **The effects of this optimization are persistent, so this option only needs to be used occasionally**; every few hundred changesets or so.

### [`reflog`](https://git-scm.com/docs/git-reflog)

Reference logs, or "reflogs", record when the tips of branches and other references were updated in the local repository.

### `repack`

```sh
git repack -a -d -f --depth=250 --window=250
```

**Object window**: when repacking git compares each object (every version of every file, every directory tree object, every commit message, every tag...) against a certain number of other similar-ish objects to find one that creates the smallest delta - roughly speaking, the smallest patch that can create this object from that base object.

**Delta chain**: When, in order to re-create object A, you first have to check out object B and apply a delta to it, but in order to create B you need object C, which requires D...

Up to a point, increasing both `depth` and `window` can give you smaller packs. However, there are tradeoffs. For `window`, a higher setting means that `git repack` will compare each object with more objects while it is running, resulting in (potentially significantly) longer running time for `git repack`. However, once the pack is generated, `window` has no effect on further operations (outside of other repacks, anyway). depth, on the other hand, has less impact on the run time of `git repack` itself (although it still affects it somewhat), but the deeper your delta trees get, the longer it takes to re-build an old object from the sequence of base objects required to create the file. That means longer times for things like `checkout` when you're referencing older commits, so it can have a significant impact on the perceived efficiency of git if you do a lot of digging through your history. And, since git doesn't create deltas only against older objects, you can on occasion find a recent object that is slow to extract because it's a number of levels down the tree - it's not as common as with older objects, but it does happen.

> I personally use `window=1024` and `depth=256` on all my repos except for a couple of clones of very large projects (e.g. Linux kernel).

#### References

-   [StackOverflow: How to use `git repack -a -d --depth=250 --window=250`](https://stackoverflow.com/questions/14842127/how-to-use-git-repack-a-d-depth-250-window-250)

## Actions

### `git rebase -i <hash>`

Rewrite history.

### Delete Branch

```bash
git push origin --delete <branchName>
```

### Branch Authors

```bash
git for-each-ref --format='%(committerdate)%09%(authorname)%09%(refname)' | sort -k5n -k2M -k3n -k4n | grep remotes | awk -F "\t" '{ printf "%-32s %-27s %s\n", $1, $2, $3 }'
```

### Merged Remote Branches

```bash
for branch in `git branch -r --merged | grep -v HEAD`; do echo -e `git show --format="%ci %cr %an" $branch | head -n 1` \\t$branch; done | sort -r
```

### Unmerged Remote Branches

```bash
for branch in `git branch -r --no-merged | grep -v HEAD`; do echo -e `git show --format="%ci %cr %an" $branch | head -n 1` \\t$branch; done | sort -r
```

## Aliases

### ```gpk```

```bash
alias gpk='git count-objects -vH && echo "" && git repack -a -d -f --depth=250 --window=250 && echo "" && git count-objects -vH'
```

## Topics

### [Re: Git and GCC](https://gcc.gnu.org/ml/gcc/2007-12/msg00165.html)

> From: Linus Torvalds <torvalds at linux-foundation dot org>
> To: Daniel Berlin <dberlin at dberlin dot org>
> Date: Wed, 5 Dec 2007 22:09:12 -0800 (PST)
> Subject: Re: Git and GCC

> On Thu, 6 Dec 2007, Daniel Berlin wrote:
> \>
> \> Actually, it turns out that git-gc --aggressive does this dumb thing
> \> to pack files sometimes regardless of whether you converted from an
> \> SVN repo or not.

> Absolutely. `git --aggressive` is mostly dumb. It's really only useful for the case of "I know I have a *really* bad pack, and I want to throw away all the bad packing decisions I have done".

> To explain this, it's worth explaining (you are probably aware of it, but let me go through the basics anyway) how git delta-chains work, and how they are so different from most other systems.

> In other SCM's, a delta-chain is generally fixed. It might be "forwards" or "backwards", and it might evolve a bit as you work with the repository, but generally it's a chain of changes to a single file represented as some kind of single SCM entity. In CVS, it's obviously the \*,v file, and a lot of other systems do rather similar things.

> Git also does delta-chains, but it does them a lot more "loosely". There is no fixed entity. Delta's are generated against any random other version that git deems to be a good delta candidate (with various fairly successful heursitics), and there are absolutely no hard grouping rules.

> This is generally a very good thing. It's good for various conceptual reasons (ie git internally never really even needs to care about the whole revision chain - it doesn't really think in terms of deltas at all), but it's also great because getting rid of the inflexible delta rules means that git doesn't have any problems at all with merging two files together, for example - there simply are no arbitrary \*,v "revision files" that have some hidden meaning.

> It also means that the choice of deltas is a much more open-ended question. If you limit the delta chain to just one file, you really don't have a lot of choices on what to do about deltas, but in git, it really can be a totally different issue.

> And this is where the really badly named "--aggressive" comes in. While git generally tries to re-use delta information (because it's a good idea, and it doesn't waste CPU time re-finding all the good deltas we found earlier), sometimes you want to say "let's start all over, with a blank slate, and ignore all the previous delta information, and try to generate a new set of deltas".

> So **`--aggressive` is not really about being aggressive, but about wasting CPU time re-doing a decision we already did earlier!**

> *Sometimes* that is a good thing. Some import tools in particular could generate really horribly bad deltas. Anything that uses "git fast-import", for example, likely doesn't have much of a great delta layout, so it might be worth saying "I want to start from a clean slate".

> But almost always, in other cases, it's actually a really bad thing to do. It's going to waste CPU time, and especially if you had actually done a good job at deltaing earlier, the end result isn't going to re-use all those *good* deltas you already found, so you'll actually end up with a much worse end result too!

> I'll send a patch to Junio to just remove the `git gc --aggressive` documentation. It can be useful, but it generally is useful only when you really understand at a very deep level what it's doing, and that documentation doesn't help you do that.

> Generally, doing incremental `git gc` is the right approach, and better than doing `git gc --aggressive`. It's going to re-use old deltas, and when those old deltas can't be found (the reason for doing incremental GC in the first place!) it's going to create new ones.

> On the other hand, it's definitely true that an "initial import of a long and involved history" is a point where it can be worth spending a lot of time finding the *really*good* deltas. Then, every user ever after (as long as they don't use `git gc --aggressive` to undo it!) will get the  advantage of that one-time event. So especially for big projects with a long history, it's probably worth doing some extra work, telling the delta finding code to go wild.

> So the equivalent of `git gc --aggressive` - but done *properly* - is to do (overnight) something like

>   `git repack -a -d --depth=250 --window=250`

> where that depth thing is just about how deep the delta chains can be (make them longer for old history - it's worth the space overhead), and the window thing is about how big an object window we want each delta candidate to scan.

> And here, you might well want to add the "-f" flag (which is the "drop all old deltas", since you now are actually trying to make sure that this one actually finds good candidates.

> And then it's going to take forever and a day (ie a "do it overnight" thing). But the end result is that everybody downstream from that repository will get much better packs, without having to spend any effort on it themselves.

> ~ Linus

---

## Under the hood

<http://wildlyinaccurate.com/a-hackers-guide-to-git>

-   At its core, a repository is a key-value store.

    -   Each key is a SHA1 hash, and each value is an object of one of the following types:

        1.  **Blobs**: a bunch of bytes, usually a file.
        2.  **Tree objects**: like directories; nodes are either blobs or other tree objects.
        3.  **Commit objects**: point to a tree object with some extra metadata.
        4.  **Tag objects**: point to a commit object with some extra metadata.
        5.  **References**: pointers to any other object (usually commit or tag objects).

    -   `.git/objects` contains all the objects, and `.git/refs` contains all the references.

    -   Git represents your project directory as a tree object, with files as blobs and directories as trees.

    -   A commit is just a pointer to a tree object that represents the state of your project at commit time.

        -   Commit metadata also includes: a hash of its parent commit, author info, and the commit message.

    -   References are just pointers to other objects.

        -   A branch is a reference pointing to a commit.
        -   HEAD is a reference that points to the tip of the current branch, but it may point directly to a commit (so-called "detached" `HEAD`).

    -   Tags are pointers to commits.

        -   A lightweight tag just points to a commit and no more.
        -   An annotated tag includes some metadata, with a tag message, author, and timestamp.

-   When you merge, you move the branch pointer of the current branch ahead ('upstream') to tip of the branch
 you're merging.

-   When you rebase, you copy your working commits over ('upstream') to the tip of the branch you've rebased on.

    -   Note that these copied commits are true copies, and have new hashes.

---

## References

-   [Git Flow](https://github.com/nvie/gitflow)
