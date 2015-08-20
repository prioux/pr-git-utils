## Four command line GIT utilities: *pr_blame*, *pr_log*, *pr_csdiff*, *pr_hist*

Three of these programs are terminal wrappers around standard GIT
utilities that colorize and reformat somewhat their outputs:

* *pr_blame* can show a file's content with lines colored by
  author, or by date (where a rainbow is used to categorize the age
  of each line, from dark blue being old code and bright red being
  recent code).

* *pr_log* can show the GIT log where each log entry is colorized
  such that each author has his/her own color. For each entry a
  list of modified files can also be shown color coded for Modified,
  Added, Deleted.

* *pr_csdiff* is a wrapper around GIT diff, but delegating the report creation to
  the *csdiff* utility (available at http://github.com/prioux/csdiff).
  It allows comparing files and entire directory subtrees using
  side-by-side, colorized diff.

The fourth utility ties them all together:

* *pr_hist* is an interactive tool to explore a GIT project; with
  single keystroke on a simple command prompt, one can move about the
  project, and launch the other three utilities and more. Easy to
  use, with a built-in help.

#### Screenshots

* *pr_blame* Here we see the output of `git-pr_blame -Ca somefile.rb | less -R`, where lines
  are color-coded by author names.

![Blame By Authors](https://raw.githubusercontent.com/prioux/pr-git-utils/master/screenshots/pr_blame_authors.png)

* *pr_blame* Here is the same file, seen through `git-pr_blame -Cr somefile.rb | less -R`, and the
  lines are now color-coded by age.

![Blame By Age](https://raw.githubusercontent.com/prioux/pr-git-utils/master/screenshots/pr_blame_age.png)

* *pr_log* Browsing the logs of a project using `git-pr_log -v . | less -R`.
  Notice that log entries are colored by author, and within
  each entry, a list of files is shown, with their modifications
  activity also color-coded.

![Log](https://raw.githubusercontent.com/prioux/pr-git-utils/master/screenshots/pr_log.png)

* *pr_csdiff* In this screenshot, the user is comparing the changes between two
  particular revisions, but only within a subdirectory of the project. The command
  was something like `git-pr_csdiff -ra22ca:ff28ae -C3 helpers | less -R`.

![Diff](https://raw.githubusercontent.com/prioux/pr-git-utils/master/screenshots/pr_csdiff.png)

* *pr_hist* This one's an interactive tool; the screenshot shows (part of) what the user
  obtained after typing `h` (for help) and `l` (for log) at the particular commit `23c61c`.

![Hist](https://raw.githubusercontent.com/prioux/pr-git-utils/master/screenshots/pr_hist.png)

#### Installation

Just copy the scripts to your favorite `bin` directory; you do have
a `$HOME/bin` configured in your $PATH, I hope?

The file `bash_aliases.md` contains a few examples on how to add
useful bash shortcuts to these commands, so you won't have to
remember all their options. It contains a nice cheatsheet for those
shortcuts.

#### Note about the first invocation of *pr_blame* and *pr_log*

These two programs will create, when first run, a file called
`$HOME/.pr_tools_prefs.pl` ; this file is a place where you can
configure your own preferences for coloring things in these utilities.
The two programs will not work until you edit this preference file
and remove three lines near the top (follow the instructions in
it). Below that is a `Perl` hash table were you can put your favorite
colors for your GIT authors. The programs will work fine any without specific
colors assigned for the authors, but then they will choose the colors
themselves, and so they might change from day to day.

These two programs are also invoked by *pr_hist*, so this configuration
step (and the accompanying message) might happen to you while using
it too.

#### History

These were all old wrapper scripts, written probably around 2006
(for subversion!) by Pierre Rioux and privately maintained (and
upgraded to support GIT) until their release on GitHub in August
2015.

The code stinks a bit, but it's quite stable and has been working
flawlessly on Mac OS X and Linux platforms ever since it was created.

