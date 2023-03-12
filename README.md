# tmux-basics
In tmux, `Ctrl + b` is the default prefix. A lot of commands in tmux will start with the prefix.

To start a tmux session:
```bash
tmux # start a unnamed session
tmux new -s <session_name> # start a session with a name
```
Once you have started a session, you are in a tmux window, where you can work on your projects.

To kill a session from terminal:
```bash
tmux kill-session -t <session_name>
```
## Split Window
You can split your window into multiple panes:
- Split Window Vertically: `prefix + %` 
- Split Window Horizontally: `Prefix + "`
You can switch between panes using `prefix + arrow_key`.
## Remove Pane
To remove a pane, type `exit` or `Ctrl + d`. `Ctrl + d` from the last pane will detach you from tmux
## Collections of Panes
A session can consist of multiple windows, each having a collection of panes. This way, you can use different windows for different projects within one tmux session.

To create a new window:
```bash
prefix + c
```
To switch between different sessions:
```bash
prefix + p # previous pane
prefix + n # next pane
```

To detach from current session:
```bash
prefix + d
```

To attach a tmux session:
```bash
tmux attach # bring back the most recent session
tmux ls # list all sessions
tmux attach -t <session_name> # resume a specific session
```

You can also list all sessions within the current session:
```bash
prefix + s
```

## Rename Session & Window
While you are working inside a session, rename your session or window via:
```bash
prefix + $ # rename session 
prefix + , # rename window
```

While you are from terminal:
```bash
tmux rename-session -t <old_name> <new_name>
```

## Zoom & Resize Panes
While you are working in one project (one window), and you want to focus on one pane. You can zoom the pane to take all the window using:
```bash
prefix + z
```
Use the same command again will zoom you back again.

You can also resize your pane:
```bash
prefix + : + "resize-pane -D" + <optional_size_number> # use D / U / R / L to indicate directions
```

## Custom tmux
You can change your tmux configurations via the config file `~/.tmux.conf`.

Once you changed the config file, you can `prefix + : + "source-file ~/.tmux.conf` to change the settings.

### Change Prefix
By default, the prefix is `Ctrl + b`. But you can change it in the config via:
```bash
unbind C-b
set-option -g prefix C-a # use ctrl+a as prefix
bind-key C-a send-prefix
```

### Change Theme
Some examples for changing colors of the status bar:
```bash
set -g status-bg blue
set -g status-fg white
```
Some additional resouces:
https://cassidy.codes/blog/2019-08-03-tmux-colour-theme/

### Copy & Paste in tmux
`prefix + [` will take you to scroll-back mode, and you can use up arrow to scroll back. `q` to exist the croll back mode.

To copy and paste, first go into scroll back mode, and do `prefix + : + "set-window-option mode-keys vi`. Then you can scroll to the starting place where you want to copy, and do `space + e + enter` to copy the text and do `prefix + ]` to paste.

### Mouse Mode
To start mouse mode:
```bash
prefix + : + "set mouse on"
```
Now you can click between panes to select the pane to work on or resize panes or scroll using your mouse.

You can also set some short cuts to start or end mouse mode in the config file:
```
bind m -g mouse on
bind M set -g mouse off
```
Now you can just do `prefix + m` to start mouse mode and `prefix + M` to end moust mode.

