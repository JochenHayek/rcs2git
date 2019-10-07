# …

################################################################################

experimental=$HOME/git-servers/ber.jochen.hayek.name/johayek/experimental

rm -fr "${experimental}"

mkdir -p "${experimental}/RCS"

cp   --arch ~/Computers/Programming/Languages/Perl/JHgen_diary_frame.pl     "${experimental}/"
cp   --arch ~/Computers/Programming/Languages/Perl/RCS/JHgen_diary_frame.pl "${experimental}/RCS/"

cd     "${experimental}"

git init .

~/git-servers/github.com/JochenHayek/rcs2git/rcs2git -authors_file=$HOME/etc/users.txt JHgen_diary_frame.pl

################################################################################

experimental=$HOME/git-servers/ber.jochen.hayek.name/johayek/experimental

rm -fr "${experimental}"

mkdir -p "${experimental}/RCS"

cp   --arch ~/Computers/Programming/Languages/Perl/JHgen_diary_frame.pl     "${experimental}/JHgen_diary_frame.pl"
cp   --arch ~/Computers/Programming/Languages/Perl/RCS/JHgen_diary_frame.pl "${experimental}/RCS/JHgen_diary_frame.pl,v"

cd     "${experimental}"

git init .

~/git-servers/github.com/knuta/rcs2git/rcs2git
