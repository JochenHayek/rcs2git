# ...

forked on github.com
  from https://github.com/knuta/rcs2git
  to   https://github.com/JochenHayek/rcs2git

################################################################################

Q: what about a "missing" trailing ",v"?
A/1: the original version only deals with RCS files *with* a trailing ",v",

    so: rename the RCS file to end in ",v"!

A/2: my adapted version properly deals with a "missing" trailing ",v".

################################################################################

Q: what about "-authors_file=$HOME/etc/users.txt" ?
A: I liked the --authors-file=... I saw in the "vicinity", so I adapted it.

################################################################################

Q: which authors do I need in my "-authors_file=…" ?
A: extract the entries of all available RCS files:

    $ perl -ne 'm/^date\s+(.*);\s+author\s+(?<author>.*);\s+state\s+(.*);/ && print "$+{author} = $+{author} <$+{author}\@DOMAIN>\n"' RCS/* | sort -u >> ~/etc/users.txt

################################################################################
