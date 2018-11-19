# Tmux

`tmux` or `tmux new` start a new unamed session

`tmux attach` attach to most recent session

`tmux attach -t [<session_name>]` attach to named session

`tmux kill-server` kill tmux server, along with all sessions

`tmux kill-session -t [<session_name>]` kill named session

`tmux new -s [<session_name>]` start a new named session

`tmux ls` list sessions



`CTRL + b` to enter commands:

`"` split panes horizontally

`%` split panes vertically

`?` list shortcuts

`:` prompt

`,` name window

`&` kill window

`+` break pane into window (e.g. to select text by mouse to copy)

`-` restore pane from window

`[SPACE BAR]` toggle between layouts

`b + [ARROW KEY]` move to another pane

`c` create winder

`d` detach from session

`n` next window

`o` swap panes

`p` previous window

`q` show pane numbers

`t` big clock

`w` list windows

`x` kill current pane

