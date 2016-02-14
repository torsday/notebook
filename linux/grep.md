# ```grep```

search for string in a dir of files

```bash
grep -r '<string>' '<path_to_somewhere>'
```


## Finding all files containing a text string on Linux

```bash
grep -rnw '/path/to/somewhere/' -e "pattern"

# `-r` or `-R` is recursive
# `-n` is line numbe
# `-w` stands match the whole word
# `-l` (lower-case L) can be added to just give the file name of matching files.
```

`--exclude` or `--include` parameter could be used for greater efficiency:

```bash
grep --include=\*.{c,h} -rnw '/path/to/somewhere/' -e "pattern"
```

`--exclude` does the opposite:

```bash
grep --exclude=*.o -rnw '/path/to/somewhere/' -e "pattern"
```

Just like exclude file it's possible to exclude/include directories through `--exclude-dir` and `--include-dir` parameter; for example, the following shows how to integrate `--exclude-dir`:

```bash
grep --exclude-dir={dir1,dir2,*.dst} -rnw '/path/to/somewhere/' -e "pattern"
```

## References

* [Man Page](http://linux.die.net/man/1/grep0)
* [StackOverflow: Finding all files containing a text string on Linux](https://stackoverflow.com/questions/16956810/finding-all-files-containing-a-text-string-on-linux)
