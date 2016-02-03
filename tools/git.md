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

### Alias: ```gpk```

```bash
alias gpk='git count-objects -vH && echo "" && git repack -a -d -f --depth=250 --window=250 && echo "" && git count-objects -vH'
```
