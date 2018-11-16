#Git Basics

`CTRL + a`
move text cursor to the beginning of the command line

`CTRL + e`
move text cursor to the end of the command line

`pwd`
print working directory

`cd [/location]`
change directory

`..`
up a directory

`ls`
list all files in current directory

`ls -a`
list all files in current directory, including hidden files

`ls -l`


`ls -la`


`touch [file_name]`
create a new file within the current path

`madir [directory_name]`
create a new directory within the current path

`mv [orignal_name] [new_name]`
`mv [original_name] [/new_location]`
move or rename file/directory

`cp [file_name]`
copy a file

`less [file_name]`
show a file

`CTRL + C`
kill current running task

`head`
see the first lines of a file/log

`tail`
see the last lines of a file/log
`tail -f [filename]`
see the last lines of a file/log updating in realtime

`cat`
concatenate given files to stdout

`echo`
print given text to stdout

`>`
`echo "insert this into a file" > [newfile.txt]`

`|`
`cat app.py | wc -l`

`wc`
word count

`CTRL + R`
reverse search commands

#Git
`git init` initialize git in a directory
`git status` check if there are any changes that have not been commited
`git clone` clone a repository into the current directory
`git pull` pull changes from a remote repository into the current directory
`git push` push changes from the current directory to a remote repository
`git branch [branch_name]` create a new branch
`git checkout [branch_name]` change to specific branch
`git diff` 
`git add -p .` 
`git commit -m "message` add message to the current commit
`git commit --amend`
`--no-edit`
`git log --all --decorate --oneline --graph`

#Vim
[vim-adventures.com]
[vimcommands.github.io]

`ESC`
to start typing in commands

`%s/[orignal_word]/[new_word]/g`
find and change all [orignal_word] to [new_word]`g` runs it for the entire file

`:[number]`
move to line number [number]

`/[pattern]`
search for [pattern] in the file

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

`~/.bashrc`
set up alias commnds within this file, for example: `alias gst = 'git status'`

`git config --global alias.co checkout`
set up an alias via the command line