# Squash

**A tool to merge files of similar content.**

I store all my notes in simple text files, and those files in a Dropbox directory. This has the benefit of not being tied to a single app, small memory footprint, and redundant backup with a version control system, git in my case.

I created squash to merge files of similar content into single ones, in the interest of keeping the number of files in check, and the content tight.

## Installation

1.  Clone the repo wherever you like

    ```bash
    git clone git@github.com:torsday/squash.git
    ```

1.  Append the repo directory to your path, making sure squash has executable permissions

    ```bash
    export PATH="$PATH:~/code/squash"
    ```

1.  done

## Use

Within a directory with many `.md` files run

```bash
squash term1 term2 term3
```

This will collect files with the arguments, deleting them, but not before combining them in a single file titled after the first term. Within the file itself, it uses that same first term as the H1 header, creates an index of all squashed files, and adds an additional # onto any header declarations, downgrading their header status.

## Example

### directory

```bash
% ls | grep -i regular
Regular Expression - Date.md
Regular Expression - Email Address.md
Regular Expression - Phone Number.md
Regular Expression - Web Address.md
Regular Expression - Zip Code.md
Regular System Updates..md
```

### the command

```bash
$ squash "Regular Expression" regex
files to squash
  Regular Expression - Date.md
  Regular Expression - Email Address.md
  Regular Expression - Phone Number.md
  Regular Expression - Web Address.md
  Regular Expression - Zip Code.md
--------------------------------
New File: Regular Expression 2015-02-18 20:32:47.md
```

*posted February 16th, 2015*
