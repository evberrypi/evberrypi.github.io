---
layout: post
title:  "My Config Files"
image: ''
date:   2017-03-20 00:06:31
tags:
- untagged
description: ''
categories: code linux 
comments: true
---

 I find myself frequently working on systems that are not mine. Some of the tools that I have spent the most time learning are the ones that I have gotten massively efficient on. For example, my (beloved) code editor *Vim* is ubiquitous on most systems I use, but will never be set up in the way I need as it is currently default installed in these ubiquitious locations.

So to rectify that -- here are my config files!

### Vimrc

```
map <C-n> :NERDTreeToggle<CR>
set encoding=utf-8
set fileencoding=utf-8
set number
set nocompatible
execute pathogen#infect()
call pathogen#helptags()

set rtp+=/usr/local/lib/python2.7/dist-packages/powerline/bindings/vim/

" Always show statusline
set laststatus=2


set term=xterm-256color
set termencoding=utf-8
set guifont=Ubuntu\ Mono\ derivative\ Powerline:10
" set guifont=Ubuntu\ Mono
let g:Powerline_symbols = 'fancy'


" Use 256 colours (Use this setting only if your terminal supports 256 colours)
set t_Co=256
noremap <c-q> <Esc>:q<CR>
inoremap <c-s> <Esc>:w<CR>

```

### TMUX.CONF

```
unbind C-b
set-option -g prefix C-a
bind-key C-a send-prefix

# Easy config reload
bind-key R source-file ~/.tmux.conf \; display-message "tmux.conf reloaded."

# vi is good
setw -g mode-keys vi

# mouse behavior
set -g mouse on

set-option -g default-terminal screen-256color


bind-key : command-prompt
bind-key r refresh-client
bind-key L clear-history
bind-key enter next-layout


bind -n S-Left  previous-window
bind -n S-Right next-window

# use vim-like keys for splits and windows
bind-key v split-window -h -c "#{pane_current_path}"
bind-key s split-window -v -c "#{pane_current_path}"
bind-key h select-pane -L
bind-key j select-pane -D
bind-key k select-pane -U
bind-key l select-pane -R


# Status Bar
set-option -g status-interval 1
set-option -g status-left ''
set-option -g status-right '%l:%M%p'
set-window-option -g window-status-current-fg magenta
set-option -g status-fg default

# Status Bar solarized-dark (default)
set-option -g status-bg black
set-option -g pane-active-border-fg black
set-option -g pane-border-fg black

# Status Bar solarized-light
if-shell "[ \"$COLORFGBG\" = \"11;15\" ]" "set-option -g status-bg white"
if-shell "[ \"$COLORFGBG\" = \"11;15\" ]" "set-option -g pane-active-border-fg white"
if-shell "[ \"$COLORFGBG\" = \"11;15\" ]" "set-option -g pane-border-fg white"

# Set window notifications
setw -g monitor-activity on
set -g visual-activity on

# get powerline to work
#source /usr/local/lib/python3.5/dist-packages/powerline/bindings/tmux/powerline.conf
set-option -g default-terminal "screen-256color"

```

ZSHRC (because whynot -- pretty colors are cool)

```
# If you come from bash you might have to change your $PATH.
# export PATH=$HOME/bin:/usr/local/bin:$PATH

# Path to your oh-my-zsh installation.
  export ZSH=/home/ev/.oh-my-zsh
# Press ctl s in vim
stty -ixon
if [ -z $TMUX ]; then; tmux -u; fi
# Set name of the theme to load. Optionally, if you set this to "random"
# it'll load a random theme each time that oh-my-zsh is loaded.
# See https://github.com/robbyrussell/oh-my-zsh/wiki/Themes
ZSH_THEME="awesomepanda"

# Uncomment the following line to use case-sensitive completion.
# CASE_SENSITIVE="true"

# Uncomment the following line to use hyphen-insensitive completion. Case
# sensitive completion must be off. _ and - will be interchangeable.
# HYPHEN_INSENSITIVE="true"

# Uncomment the following line to disable bi-weekly auto-update checks.
# DISABLE_AUTO_UPDATE="true"

# Uncomment the following line to change how often to auto-update (in days).
# export UPDATE_ZSH_DAYS=13

# Uncomment the following line to disable colors in ls.
# DISABLE_LS_COLORS="true"

# Uncomment the following line to disable auto-setting terminal title.
# DISABLE_AUTO_TITLE="true"

# Uncomment the following line to enable command auto-correction.
 ENABLE_CORRECTION="true"

# Uncomment the following line to display red dots whilst waiting for completion.
# COMPLETION_WAITING_DOTS="true"

# Uncomment the following line if you want to disable marking untracked files
# under VCS as dirty. This makes repository status check for large repositories
# much, much faster.
# DISABLE_UNTRACKED_FILES_DIRTY="true"

# Uncomment the following line if you want to change the command execution time
# stamp shown in the history command output.
# The optional three formats: "mm/dd/yyyy"|"dd.mm.yyyy"|"yyyy-mm-dd"
# HIST_STAMPS="mm/dd/yyyy"

# Would you like to use another custom folder than $ZSH/custom?
# ZSH_CUSTOM=/path/to/new-custom-folder

# Which plugins would you like to load? (plugins can be found in ~/.oh-my-zsh/plugins/*)
# Custom plugins may be added to ~/.oh-my-zsh/custom/plugins/
# Example format: plugins=(rails git textmate ruby lighthouse)
# Add wisely, as too many plugins slow down shell startup.
plugins=(git)

source $ZSH/oh-my-zsh.sh

# User configuration

# export MANPATH="/usr/local/man:$MANPATH"

# You may need to manually set your language environment
# export LANG=en_US.UTF-8

# Preferred editor for local and remote sessions
 if [[ -n $SSH_CONNECTION ]]; then
   export EDITOR='vim'
# else
#   export EDITOR='mvim'
# fi

# Compilation flags
# export ARCHFLAGS="-arch x86_64"

# ssh
# export SSH_KEY_PATH="~/.ssh/rsa_id"

# Set personal aliases, overriding those provided by oh-my-zsh libs,
# plugins, and themes. Aliases can be placed here, though oh-my-zsh
# users are encouraged to define aliases within the ZSH_CUSTOM folder.
# For a full list of active aliases, run `alias`.
#
# Example aliases
alias note="vim ~/Downloads/note.md"
alias code="vim ~/Downloads/code.md"
# alias zshconfig="mate ~/.zshrc"
# alias ohmyzsh="mate ~/.oh-my-zsh"

#change the colors, duke, the colors!
export TERM=xterm-256color

#get powerline to work
#export PATH=/usr/local/bin:/usr/bin:/bin:/usr/local/games:/usr/games:/home/ev/.vimpkg/bin
#if [[ -r /usr/local/lib/python2.7/dist-packages/powerline/bindings/zsh/powerline.zsh ]]; then
#    source /usr/local/lib/python2.7/dist-packages/powerline/bindings/zsh/powerline.zsh
#fi


```

