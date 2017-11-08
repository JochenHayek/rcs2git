# rcs2git
Converts a tree of RCS-tracked files to a git repository.

This script will:
 - Convert all rcs-tracked files listed on the command line (yes, only these ones!!), preserving history
 - *Abandoned* *feature*: Do an initial commit of all untracked files, with the message "Adding previously untracked file"
   (we do not support untracked files any more)

_Please note that the conversion happens in-place. Make sure you're working on a copy!_

It makes quite good sense to (RCS-wise) "ci -u" the files you want to get converted,
before you actually start our rcs2git.

I added this option to the command line:

  -authors_file=$HOME/etc/users.txt

Create your users.txt like this:

  perl -ne 'm/^date\s+(.*);\s+author\s+(?<author>.*);\s+state\s+(.*);/ && print "$+{author} = $+{author} <$+{author}\@DOMAIN>\n"' RCS/* | sort -u >> $HOME/etc/users.txt

CAVEAT: This version of rcs2git also considers RCS files (*below* RCS/) w/o a trailing ",v".

## Example usage

```bash
# Make a copy of the folder
cp -a folder folder-copy
# Enter the folder and copy it
(cd folder-copy && git init && rcs2git -authors_file=$HOME/etc/users.txt SOME_FILES)
# Create a third directory with a clean checkout, to get rid of RCS files
mkdir folder-git
cp -a folder-copy/.git folder-git
(cd folder-git && git reset --hard)
# Sanity check
diff -ur folder folder-git
```

# Alternatives
There are other RCS to Git converters out there, which may or may not work better for your use-case. These are the ones I know of:

 - https://github.com/Oblomov/rcs-fast-export
