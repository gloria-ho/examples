# Git

Git is a fast, scalable, dirstributed revision control system for tracking changes in computer files and coordinating work on those files among multiple people.


## Git Basics

`..` up one level from working directory


`|` piping
Example:
```
cat app.py | wc -l
```

`~/.bashrc`

set up alias commands within this file, for example: `alias gst='git status'`

`git config --global alias.co checkout` set up an alias via the command line


`cat` concatenate given files to stdout

`cd /[<location>]` change directory

`cd /[<location>]` change directory

`cp [<file_name>]` copy a file

`CTRL + a` move text cursor to the beginning of the command line

`CTRL + c` kill current running task

`CTRL + e` move text cursor to the end of the command line

`CTRL + r` reverse search commands

`echo` print given text to stdout


`>` insert into a file

Example:
```
echo "insert this into a file" > [<newfile.txt>]
```


`grep`

`[<command>] | grep "[<search_term>]"` after the command, search for any lines that contain the search_term


`head` see the first lines of a file/log

`less [<file_name>]` show a file

`ls` list all files in working directory

`ls -a` list all files in working directory, including hidden files

`ls -l`

`ls -la`

`mkdir [<directory_name>]` create a new directory within the working directory

```
mv [<orignial_name>] [<new_name>]
mv [<original_name>] /[<new_location>]
```
move or rename file/directory

`pwd` print working directory

`tail` see the last lines of a file/log

`tail -f [<filename>]` see the last lines of a file/log updating in realtime

`touch [<file_name>]` create a new file within the current path

`wc` word count


## [Git](https://git-scm.com/docs)

### [GitHub Cheat Sheet](https://services.github.com/on-demand/downloads/github-git-cheat-sheet.pdf)

### [Visual Git Cheat Sheet](http://ndpsoftware.com/git-cheatsheet.html)

[`git add [<filename>]`](https://git-scm.com/docs/git-add) add file contents to the index

[`git add -p .`](https://git-scm.com/docs/git-add) 

[`git branch`](https://git-scm.com/docs/git-branch) list branches

[`git branch [<branch_name>]`](https://git-scm.com/docs/git-branch) create a new branch

[`git branch -d [<branch_name>]`](https://git-scm.com/docs/git-branch#git-branch--d) delete the branch_name branch

[`git checkout [<branch_name>]`](https://git-scm.com/docs/git-checkout) switch branches or restore working tree files

[`git clean`](https://git-scm.com/docs/git-clean) remove untracked files from the working tree

[`git clone`](https://git-scm.com/docs/git-clone) clone a repository into the working directory

[`git commit -m "message`](https://git-scm.com/docs/git-commit) add message to the current commit

[`git commit --amend`](https://git-scm.com/docs/git-commit#git-commit---amend) replace the tip of the current branch by creating a new commit.

[`git commit --amend --no-edit`](https://git-scm.com/docs/git-commit#git-commit---no-edit) use the selected commit message without launching an editor

[`git diff`](https://git-scm.com/docs/git-diff) show the difference between commits, commit and workings tree, etc.

[`git fetch`](https://git-scm.com/docs/git-fetch) download objects and refs from another repository without merging

[`git grep [<search_pattern>]`](https://git-scm.com/docs/git-grep) print lines matching a pattern

[`git gui`](https://git-scm.com/docs/git-gui) a portable graphical interface to git

[`git init`](https://git-scm.com/docs/git-init) initialize a new repository in the working directory

[`git log'](https://git-scm.com/docs/git-log) show commit logs

[`git log --all --decorate --oneline --graph`](https://git-scm.com/docs/git-log#git-log---decorateshortfullautono) Print out log comments

[`git merge`](https://git-scm.com/docs/git-merge) join two or more development histories together

[`git pull`](https://git-scm.com/docs/git-pull) fetch from and integrate with another repository or local branch

[`git push`](https://git-scm.com/docs/git-push) update a remote repository with committed changes

[`git rebase`](https://git-scm.com/docs/git-rebase) reapply commits on top of another base tip

[`git reflog`](https://git-scm.com/docs/git-reflog) manage reflog information

[`git remote`](https://git-scm.com/docs/git-remote) manage set of tracked repositories

[`git remote --verbose`](https://git-scm.com/docs/git-remote#git-remote--verbose) show remote url after name **!This must be places between `remote` and `subcommand`**

[`git remote add origin [<url>]`](https://git-scm.com/docs/git-remote#git-remote-emaddem) add a remote repository origin from <url>

[`git remote remove origin`](https://git-scm.com/docs/git-remote#git-remote-emremoveem) all remote-tracking branched and configuartion settings for the remote are removed

[`git reset`](https://git-scm.com/docs/git-reset) reset current HEAD to the specified state

[`git revert`](https://git-scm.com/docs/git-revert) revert some existing commits

[`git rm`](https://git-scm.com/docs/git-rm) remove files from the working tree and from the index

[`git stash`](https://git-scm.com/docs/git-stash) record the state of the working directory and the index, but go back to a clean working directory.

[`git stash clear`](https://git-scm.com/docs/git-stash#git-stash-clear) remove all stash entries **!Entries may be impossible to recover**

[`git stash drop [-q|--quiet] [<stash>]]() remove a single stash entry from a list fo stash entries. When no stash is given, it removes the lastest one. i.e. `stash@{0}`, otherwise <stash> must be a valid stash log reference of the form `stash@{<revision>}`

[`git stash list [<options>]`](https://git-scm.com/docs/git-stash) list the stash entries that you currently

[`git status`](https://git-scm.com/docs/git-status) check if there are any changes that have not been commited



## [Vim](https://www.vim.org/)

[Learn VIM while playing a game](vim-adventures.com)
[Vim Commands](vimcommands.github.io)

`ESC` to start typing in commands

`%s/[<orignal_word>]/[<new_word>]/g` find and change all [orignal_word] to [new_word]`g` runs it for the entire file

`:[<number>]` move to line number [<number>]

`/[<pattern>]` search for [<pattern>] in the file

hitting `dd` will cuts (deletes and copies) line

hitting `yy` will copy

hitting `pp` will paste

hitting `da` cuts words between ""

hitting `u` will undo in order

`CTRL + v` visual block mode for deletion

`.vimrc` for additional configuration 

`:`
to start typing commands

`q!`
quit without saving


`x` or `x!` or `wq!`
quit with saving