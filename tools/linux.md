# Linux

- [Linux](#linux)
  - [find](#find)
  - [grep](#grep)
  - [rsync](#rsync)

---

## ```find```

```bash
find [-H] [-L] [-P] [-D debugopts] [-Olevel] [starting-point...] [expression]
```

#### show empty directories

```bash
find . -type d -empty -print
```

#### delete empty directories

```bash
find . -type d -empty -delete
```

---

## ```grep```

search for string in a dir of files

```bash
grep -r '<string>' '<path_to_somewhere>'
```


#### Finding all files containing a text string on Linux

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

### References

* [Man Page](http://linux.die.net/man/1/grep0)
* [StackOverflow: Finding all files containing a text string on Linux](https://stackoverflow.com/questions/16956810/finding-all-files-containing-a-text-string-on-linux)

---

## ```rsync```

A remote (and local) file-copying tool.

```bash
rsync [OPTION...] SRC... [DEST]
```

```bash
rsync -ripumtz --progress src/ dest/

# -r recurse into directories
# -i turns on the itemized format, which shows more information than the default format
# -p preserve permissions
# -u makes rsync transfer skip files which are newer in dest than in src
# -m prune empty directory chains from file-list
# -t preserve modification times
# -z turns on compression, which is useful when transferring easily-compressible files over slow links

# --progress shows a progress bar for each transfer, useful if you transfer big files

# -n dry run
```

### Use of `/` at the end of path:

- When using `/` at the end of source, rsync will copy the content of the last folder.
When not using `/` at the end of source, rsync will copy the last folder and the content of the folder.
- When using `/` at the end of destination, rsync will paste the data inside the last folder.
When not using `/` at the end of destination, rsync will create a folder with the last destination folder name and paste the data inside that folder.

### Complete Options

```
-v, --verbose               increase verbosity
-q, --quiet                 suppress non-error messages
    --no-motd               suppress daemon-mode MOTD (see caveat)
-c, --checksum              skip based on checksum, not mod-time & size
-a, --archive               archive mode; equals -rlptgoD (no -H,-A,-X)
    --no-OPTION             turn off an implied OPTION (e.g. --no-D)
-r, --recursive             recurse into directories
-R, --relative              use relative path names
    --no-implied-dirs       don't send implied dirs with --relative
-b, --backup                make backups (see --suffix & --backup-dir)
    --backup-dir=DIR        make backups into hierarchy based in DIR
    --suffix=SUFFIX         backup suffix (default ~ w/o --backup-dir)
-u, --update                skip files that are newer on the receiver
    --inplace               update destination files in-place
    --append                append data onto shorter files
    --append-verify         --append w/old data in file checksum
-d, --dirs                  transfer directories without recursing
-l, --links                 copy symlinks as symlinks
-L, --copy-links            transform symlink into referent file/dir
    --copy-unsafe-links     only "unsafe" symlinks are transformed
    --safe-links            ignore symlinks that point outside the tree
-k, --copy-dirlinks         transform symlink to dir into referent dir
-K, --keep-dirlinks         treat symlinked dir on receiver as dir
-H, --hard-links            preserve hard links
-p, --perms                 preserve permissions
-E, --executability         preserve executability
    --chmod=CHMOD           affect file and/or directory permissions
-A, --acls                  preserve ACLs (implies -p)
-X, --xattrs                preserve extended attributes
-o, --owner                 preserve owner (super-user only)
-g, --group                 preserve group
    --devices               preserve device files (super-user only)
    --specials              preserve special files
-D                          same as --devices --specials
-t, --times                 preserve modification times
-O, --omit-dir-times        omit directories from --times
    --super                 receiver attempts super-user activities
    --fake-super            store/recover privileged attrs using xattrs
-S, --sparse                handle sparse files efficiently
-n, --dry-run               perform a trial run with no changes made
-W, --whole-file            copy files whole (w/o delta-xfer algorithm)
-x, --one-file-system       don't cross filesystem boundaries
-B, --block-size=SIZE       force a fixed checksum block-size
-e, --rsh=COMMAND           specify the remote shell to use
    --rsync-path=PROGRAM    specify the rsync to run on remote machine
    --existing              skip creating new files on receiver
    --ignore-existing       skip updating files that exist on receiver
    --remove-source-files   sender removes synchronized files (non-dir)
    --del                   an alias for --delete-during
    --delete                delete extraneous files from dest dirs
    --delete-before         receiver deletes before transfer (default)
    --delete-during         receiver deletes during xfer, not before
    --delete-delay          find deletions during, delete after
    --delete-after          receiver deletes after transfer, not before
    --delete-excluded       also delete excluded files from dest dirs
    --ignore-errors         delete even if there are I/O errors
    --force                 force deletion of dirs even if not empty
    --max-delete=NUM        don't delete more than NUM files
    --max-size=SIZE         don't transfer any file larger than SIZE
    --min-size=SIZE         don't transfer any file smaller than SIZE
    --partial               keep partially transferred files
    --partial-dir=DIR       put a partially transferred file into DIR
    --delay-updates         put all updated files into place at end
-m, --prune-empty-dirs      prune empty directory chains from file-list
    --numeric-ids           don't map uid/gid values by user/group name
    --timeout=SECONDS       set I/O timeout in seconds
    --contimeout=SECONDS    set daemon connection timeout in seconds
-I, --ignore-times          don't skip files that match size and time
    --size-only             skip files that match in size
    --modify-window=NUM     compare mod-times with reduced accuracy
-T, --temp-dir=DIR          create temporary files in directory DIR
-y, --fuzzy                 find similar file for basis if no dest file
    --compare-dest=DIR      also compare received files relative to DIR
    --copy-dest=DIR         ... and include copies of unchanged files
    --link-dest=DIR         hardlink to files in DIR when unchanged
-z, --compress              compress file data during the transfer
    --compress-level=NUM    explicitly set compression level
    --skip-compress=LIST    skip compressing files with suffix in LIST
-C, --cvs-exclude           auto-ignore files in the same way CVS does
-f, --filter=RULE           add a file-filtering RULE
-F                          same as --filter='dir-merge /.rsync-filter'
                            repeated: --filter='- .rsync-filter'
    --exclude=PATTERN       exclude files matching PATTERN
    --exclude-from=FILE     read exclude patterns from FILE
    --include=PATTERN       don't exclude files matching PATTERN
    --include-from=FILE     read include patterns from FILE
    --files-from=FILE       read list of source-file names from FILE
-0, --from0                 all *from/filter files are delimited by 0s
-s, --protect-args          no space-splitting; wildcard chars only
    --address=ADDRESS       bind address for outgoing socket to daemon
    --port=PORT             specify double-colon alternate port number
    --sockopts=OPTIONS      specify custom TCP options
    --blocking-io           use blocking I/O for the remote shell
    --stats                 give some file-transfer stats
-8, --8-bit-output          leave high-bit chars unescaped in output
-h, --human-readable        output numbers in a human-readable format
    --progress              show progress during transfer
-P                          same as --partial --progress
-i, --itemize-changes       output a change-summary for all updates
    --out-format=FORMAT     output updates using the specified FORMAT
    --log-file=FILE         log what we're doing to the specified FILE
    --log-file-format=FMT   log updates using the specified FMT
    --password-file=FILE    read daemon-access password from FILE
    --list-only             list the files instead of copying them
    --bwlimit=KBPS          limit I/O bandwidth; KBytes per second
    --write-batch=FILE      write a batched update to FILE
    --only-write-batch=FILE like --write-batch but w/o updating dest
    --read-batch=FILE       read a batched update from FILE
    --protocol=NUM          force an older protocol version to be used
    --iconv=CONVERT_SPEC    request charset conversion of filenames
    --checksum-seed=NUM     set block/file checksum seed (advanced)
-4, --ipv4                  prefer IPv4
-6, --ipv6                  prefer IPv6
    --version               print version number
(-h) --help                  show this help (see below for -h comment)
```

### References

* [man page](http://linux.die.net/man/1/rsync)
* [To Slash or Not To Slash](http://qdosmsq.dunbar-it.co.uk/blog/2013/02/rsync-to-slash-or-not-to-slash/)