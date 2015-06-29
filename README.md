# rcs2git
Converts a tree of RCS-tracked files to a git repository.

This script will:
 - Convert all rcs-tracked files, preserving history
 - Do an initial commit of all untracked files, with the message "Adding previously untracked file"

_Please note that the conversion happens in-place. Make sure you're working on a copy!_

## Example usage

```bash
# Make a copy of the folder
cp -a folder folder-copy
# Enter the folder and copy it
(cd folder-copy && git init && rcs2git)
# Create a third directory with a clean checkout, to get rid of RCS files
mkdir folder-git
cp -a folder-copy/.git folder-git
(cd folder-git && git reset --hard)
# Sanity check
diff -ur folder folder-git
```
