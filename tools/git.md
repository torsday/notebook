# Git



## Commands

### [`count-objects`](https://git-scm.com/docs/git-count-objects)

Count unpacked number of objects and their disk consumption

```sh
git count-objects -vH
# -v  verbose
# -H  human readable
```

* **count:** the number of loose objects
* **size:** disk space consumed by loose objects, in KiB (unless -H is specified)
* **in-pack:** the number of in-pack objects
* **size-pack:** disk space consumed by the packs, in KiB (unless -H is specified)
* **prune-packable:** the number of loose objects that are also present in the packs. These objects could be pruned using git prune-packed.
* **garbage:** the number of files in object database that are neither valid loose objects nor valid packs
* **size-garbage:** disk space consumed by garbage files, in KiB (unless -H is specified)


### [`gc`](https://git-scm.com/docs/git-gc)

Cleanup unnecessary files and optimize the local repository.

> Users are encouraged to run this task on a regular basis within each repository to maintain good disk space utilization and good operating performance.


#### options

```sh
--aggressive
```

Usually git gc runs very quickly while providing good disk space utilization and performance. This option will cause git gc to more aggressively optimize the repository at the expense of taking much more time. **The effects of this optimization are persistent, so this option only needs to be used occasionally**; every few hundred changesets or so.

## Actions

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

### Alias: ```gpk```

```bash
alias gpk='git count-objects -vH && echo "" && git repack -a -d -f --depth=250 --window=250 && echo "" && git count-objects -vH'
```

## Topics

### [Re: Git and GCC](https://gcc.gnu.org/ml/gcc/2007-12/msg00165.html)

    From: Linus Torvalds <torvalds at linux-foundation dot org>
    To: Daniel Berlin <dberlin at dberlin dot org>
    Date: Wed, 5 Dec 2007 22:09:12 -0800 (PST)
    Subject: Re: Git and GCC


On Thu, 6 Dec 2007, Daniel Berlin wrote:
>
> Actually, it turns out that git-gc --aggressive does this dumb thing
> to pack files sometimes regardless of whether you converted from an
> SVN repo or not.

Absolutely. `git --aggressive` is mostly dumb. It's really only useful for the case of "I know I have a *really* bad pack, and I want to throw away all the bad packing decisions I have done".

To explain this, it's worth explaining (you are probably aware of it, but let me go through the basics anyway) how git delta-chains work, and how they are so different from most other systems.

In other SCM's, a delta-chain is generally fixed. It might be "forwards" or "backwards", and it might evolve a bit as you work with the repository, but generally it's a chain of changes to a single file represented as some kind of single SCM entity. In CVS, it's obviously the \*,v file, and a lot of other systems do rather similar things.

Git also does delta-chains, but it does them a lot more "loosely". There is no fixed entity. Delta's are generated against any random other version that git deems to be a good delta candidate (with various fairly successful heursitics), and there are absolutely no hard grouping rules.

This is generally a very good thing. It's good for various conceptual reasons (ie git internally never really even needs to care about the whole revision chain - it doesn't really think in terms of deltas at all), but it's also great because getting rid of the inflexible delta rules means that git doesn't have any problems at all with merging two files together, for example - there simply are no arbitrary \*,v "revision files" that have some hidden meaning.

It also means that the choice of deltas is a much more open-ended question. If you limit the delta chain to just one file, you really don't have a lot of choices on what to do about deltas, but in git, it really can be a totally different issue.

And this is where the really badly named "--aggressive" comes in. While git generally tries to re-use delta information (because it's a good idea, and it doesn't waste CPU time re-finding all the good deltas we found earlier), sometimes you want to say "let's start all over, with a blank slate, and ignore all the previous delta information, and try to generate a new set of deltas".

So **`--aggressive` is not really about being aggressive, but about wasting CPU time re-doing a decision we already did earlier!**

*Sometimes* that is a good thing. Some import tools in particular could generate really horribly bad deltas. Anything that uses "git fast-import", for example, likely doesn't have much of a great delta layout, so it might be worth saying "I want to start from a clean slate".

But almost always, in other cases, it's actually a really bad thing to do. It's going to waste CPU time, and especially if you had actually done a good job at deltaing earlier, the end result isn't going to re-use all those *good* deltas you already found, so you'll actually end up with a much worse end result too!

I'll send a patch to Junio to just remove the `git gc --aggressive` documentation. It can be useful, but it generally is useful only when you really understand at a very deep level what it's doing, and that documentation doesn't help you do that.

Generally, doing incremental `git gc` is the right approach, and better than doing `git gc --aggressive`. It's going to re-use old deltas, and when those old deltas can't be found (the reason for doing incremental GC in the first place!) it's going to create new ones.

On the other hand, it's definitely true that an "initial import of a long and involved history" is a point where it can be worth spending a lot of time finding the *really*good* deltas. Then, every user ever after (as long as they don't use `git gc --aggressive` to undo it!) will get the  advantage of that one-time event. So especially for big projects with a long history, it's probably worth doing some extra work, telling the delta finding code to go wild.

So the equivalent of `git gc --aggressive` - but done *properly* - is to do (overnight) something like

	git repack -a -d --depth=250 --window=250

where that depth thing is just about how deep the delta chains can be (make them longer for old history - it's worth the space overhead), and the window thing is about how big an object window we want each delta candidate to scan.

And here, you might well want to add the "-f" flag (which is the "drop all old deltas", since you now are actually trying to make sure that this one actually finds good candidates.

And then it's going to take forever and a day (ie a "do it overnight" thing). But the end result is that everybody downstream from that repository will get much better packs, without having to spend any effort on it themselves.

~ Linus
