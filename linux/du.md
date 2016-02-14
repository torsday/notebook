# Du

The du (i.e., disk usage) command reports the sizes of directory trees inclusive of all of their contents and the sizes of individual files. This makes it useful for tracking down space hogs, i.e., directories and files that consume large or excessive amounts of space on a hard disk drive (HDD) or other storage media.

# Options

```
-c, --total            produce a grand total
-h, --human-readable   print sizes in human readable format (e.g., 1K 234M 2G)
```

# ```find```

```bash
find [-H] [-L] [-P] [-D debugopts] [-Olevel] [starting-point...] [expression]
```

## show empty directories

```bash
find . -type d -empty -print
```

## delete empty directories

```bash
find . -type d -empty -delete
```
