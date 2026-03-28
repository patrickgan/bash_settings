# bash_settings
My personal bash/terminal settings

### .bashrc modifications
Save this to `.bash_functions`
```
#!/usr/bin/bash

parse_git_branch() {
    git branch 2> /dev/null | sed -e '/^[^*]/d' -e 's/* \(.*\)/(\1)/'
}
```
Add the following to the top of `.bashrc` or equivalent file.
```
# Include bash functions
if [ -f ~/.bash_functions ]; then
    . ~/.bash_functions
fi
```

Add the following to your prompt, also typically somewhere in `.bashrc`.
```
PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[91m\]$(parse_git_branch)\[\033[00m\]\$ '
```

I use NVM, so I go ahead and install that via curl, as per installation instructions on https://github.com/nvm-sh/nvm.

### .bash_aliases
I add these lines to my `.bash_aliases` file. Don't do this if you have scripts that rely on Python 2.
```
alias ipython='ipython3'
alias python='python3'
```

### Tmux
These are my tmux settings. Add these to `.tmux.conf`.
```
set -g mouse on
set -g xterm-keys on

bind-key -T prefix C-b source-file ~/.tmux.conf \; display "Loaded ~/.tmux.conf"
```

### Vim
Edit `.vimrc`.
```
set mouse=a
set tabstop=4
set shiftwidth=4
set expandtab
set number
```
