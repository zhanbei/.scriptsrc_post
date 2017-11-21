# Posted Scripts for .\*rc Scripts

<!-- > Created by Fisher at 14:49 on 2017-03-21. -->

Posted .scriptrc_post (e.g., .bashrc_post, .vimrc_post) that will be loaded after .scriptrc (e.g., .bashrc, .vimrc) to Set up some common configurations for common conditions, e.g., .vimrc, .bashrc.

## Installation(Git Clone)

Clone this repository directly to home directory.

```bash
cd ~
git clone https://github.com/zhanbei/.scriptsrc_post.git
```

## Enable Posted .bashrc Scripts for Your Bash Terminal

Add line: `source ~/.scriptsrc_post/.bashrc_post` to your `~/.bashrc` to enable posted scripts for .bashrc.

### Configure Modules to be Loaded([.bashrc_post](.bashrc_post))

You may comment lines in `~/.scriptsrc_post/.bashrc_post` file to configure modules to be loaded.

```bash
source ~/.scriptsrc_post/.bashrc_basic
source ~/.scriptsrc_post/.bashrc_git
```

### Posted .bashrc for Basic Usage About Bash([.bashrc_basic](.bashrc_basic))

```bash
# Simplify commands.
# Now you can use cd1 to change to parent folder.
alias ..="cd ../";
alias ...="cd ../../";
alias ....="cd ../../../";
alias .....="cd ../../../../";
alias ......="cd ../../../../../";
alias cd1="cd ..";
alias cd2="cd ../..";
alias cd3="cd ../../..";
alias cd4="cd ../../../..";
alias cd5="cd ../../../../..";

# For frequently used commands.
alias c="clear";
alias r="reset";
alias q="exit";

# Hint for important operations. 
# You will got hints for what you have just done:)
alias rm="rm -v";
alias cp="cp -v";
```

### Posted .bashrc for Git([.bashrc_git](.bashrc_git))

```bash
# Display git branch in bash prompt.
# @see https://gist.github.com/justintv/168835
# It may be displayed unexpectedly or cause some error, so try it out by yourself; (it's fun :).
export PS1="\[\e]0;\u@\h \w\a\]${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\] \[\033[01;34m\]\w\[\033[01;31m\]\$(__git_ps1 '(%s)')\[\033[01;34m\] \$ \[\033[00m\]"
```

## Enable Posted .vimrc Scripts for Your Vim Editor

Add line: `so ~/.scriptsrc_post/.vimrc_post` to your `~/.vimrc` to enable posted .vimrc scripts.

### Configure Modules to be Loaded([.vimrc_post](.vimrc_post))

You may comment lines in `~/.scriptsrc_post/.vimrc_post` file to configure modules to be loaded.

```vim
so ~/.scriptsrc_post/.vimrc_basic
so ~/.scriptsrc_post/.vimrc_cpp
```

### Posted .vimrc for Basic Usage About Vim([.vimrc_basic](.vimrc_basic))


```vim
" Using 'jk', 'JK', and 'Jk' to escape ignoring cases.
inoremap jk <esc>
inoremap Jk <esc>
inoremap JK <esc>

" Show lines number by default.
set number

" Settings for programming.
set autoindent
syntax on
filetype on
filetype plugin on
filetype indent on
```

### Posted .vimrc for C++([.vimrc_cpp](.vimrc_cpp))

```vim
" Auto indent in C/C++.
set cindent
```
