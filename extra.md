# tmux
# tmux source-file ~/.tmux.conf
bind r source-file ~/.tmux.conf

# change leader
unbind C-b
set-option -g prefix Delete
bind-key Delete send-prefix

# Start windows and panes at 1, not 0
set -g base-index 1
setw -g pane-base-index 1

# split panes using | and -
bind | split-window -h
bind - split-window -v
unbind '"'
unbind %

# nice to have 
set -g mouse on
set -g default-terminal "tmux-256color"

# vim navigation panes
bind-key h select-pane -L
bind-key j select-pane -D
bind-key k select-pane -U
bind-key l select-pane -R

# Configure the catppuccin plugin
set -g @catppuccin_flavor "mocha"
set -g @catppuccin_window_status_style "rounded"

# Load catppuccin
run ~/.config/tmux/plugins/catppuccin/tmux/catppuccin.tmux

# Make the status line pretty and add some modules
set -g status-right-length 100
set -g status-left-length 100
set -g status-right "#{E:@catppuccin_status_application}"
set -ag status-right "#{E:@catppuccin_status_session}"
set -ag status-right "#{E:@catppuccin_status_uptime}"


