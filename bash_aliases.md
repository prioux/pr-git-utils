## Supplemental Bash Aliases And Functions

Here are some simple bash aliases and functions that you can add
to your shell initializations scripts; these will help you make the
most of the commands in this package by reducing many common
combinations of commands and options unto simpler commands.

Since by principle I don't like to include a pager inside my
command-line utilities, many of the aliases and functions below do
that by piping to a `less -R` command. Adjust to your own taste
if you use another pager, or have other options that you like
for `less` (my personal settings always invoke `less -MeqisR` !).

#### Shortcuts for *pr_csdiff*

```bash
function gdi  { git-pr_csdiff "$@" | less -R ; }
alias    gdic="gdi -C5 -b -W"
```

_Try it yourself_: run "gdi" on one of the files you're
currently editing in a git repository, then try to run
"gdic" on it afterwards.

#### Shortcuts for *pr_log*

```bash
function glo  { git-pr_log -P prefix "$@" | less -R ; }
```

_Try it yourself_: run "glo" on one of your files.


#### Shortcuts for *pr_blame*

```bash
function gblama { git-pr_blame -Ca "$@" | less -R ; }
function gblamr { git-pr_blame -Cr "$@" | less -R ; }
```

_Try it yourself_: run "gblama" on one of your files,
then run "gblamr" right after.

#### Shortcut for *pr_hist*

```bash
alias  gih='git-pr_hist'
```

No comments, it's pretty obvious what that one does.

#### Full cheatsheet

| Shortcut | Argument type? | Example          | Explanation |
|----------|----------------|------------------|-------------|
| gdi      | File or dir    | gdi file.txt     | Diff between your working file and HEAD |
| gdic     | File or dir    | gdic file.txt    | Same, but with collapse of unchanged lines and blank space ignored |
| glo      | File or dir    | glo file.txt     | Log the file |
| gblama   | File only      | gblama file.txt  | Annotate file lines by author |
| gblamr   | File only      | gblamr file.txt  | Annotate file lines by age |
| gih      | File or dir    | gih .            | Start interactive explorer |
