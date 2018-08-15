# Posted Scripts for .\*rc Scripts

<!-- > Created by Fisher at 14:49 on 2017-03-21. -->

Posted .scriptrc_post (e.g., .bashrc_post, .vimrc_post) that will be loaded after .scriptrc (e.g., .bashrc, .vimrc) to Set up some common configurations for common conditions, e.g., .vimrc, .bashrc.

## Installation( via Git Clone)

Clone [this repository](https://github.com/zhanbei/.scriptsrc_post.git) directly to home directory.

```bash
# cd to home directory.
cd ~
# Clone this repository directly to home directory.
git clone https://github.com/zhanbei/.scriptsrc_post.git
```

## Enable Posted .bashrc Scripts for Your Bash Terminal

Add line: `source ~/.scriptsrc_post/.bashrc_post` to your `~/.bashrc` to enable posted scripts for .bashrc.

### Configure Modules to be Loaded([.bashrc_post](.bashrc_post))

You may comment lines in `~/.scriptsrc_post/.bashrc_post` file to configure modules to be loaded.

```bash
source ~/.scriptsrc_post/.bashrc_basic
source ~/.scriptsrc_post/.bashrc_prompt
source ~/.scriptsrc_post/.bashrc_git
source ~/.scriptsrc_post/.bashrc_coding
source ~/.scriptsrc_post/.bashrc_proxy
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
# -i, --interactive     prompt before overwrite (overrides a previous -n option)
alias cp="cp -iv";
alias mv="mv -iv";

# Find with a maxdepth option.
alias find-with-maxdepth='find -maxdepth';

# save the bash history to ${HISTFILE}_whatever.
# @see https://stackoverflow.com/questions/8473121/execute-command-without-keeping-it-in-history
alias save-bash-history-to-whatever='export HISTFILE="${HISTFILE}_whatever"'

# Print every command being executed.
# @see https://stackoverflow.com/questions/2853803/how-to-echo-shell-commands-as-they-are-executed
alias set-on-xtrace='set -o xtrace'
# Stop printing every command being executed.
alias set-off-xtrace='set +o xtrace'
```

### Posted .bashrc for the Shell Prompt([.bashrc_prompt](.bashrc_prompt))

```bash
# Backing up the current PS1 and providing reset cmd in case for need.
export PS1BACKUP=$PS1
alias reset-ps1-to-origin="export PS1=\$PS1BACKUP"

# Removing the >>'$'<< sign and spaces around from original PS1. Substring matches the pattern >>' \$*'<< will be removed.
export PS1=${PS1/' \$'*/''}
# Removing any characters following with the last occurrence of ' \$*' in $PS1.
# export PS1=`echo $PS1 | sed 's/\(.*\)\\\$.*/\1/'`


# Posted .bashrc for shell prompt for git.
# Display git branch in bash prompt.
# It may be displayed unexpectedly or cause some error, so try it out by yourself; (it's fun :).
# @see https://gist.github.com/justintv/168835
# Appending >>'(GIT_BRANCH_NAME)'<< (Git branch name wrapped in parentheses/round-brackets) with a color of blue.
export PS1=$PS1'\[\033[01;31m\]$(__git_ps1 '"'"'(%s)'"'"')'


# Appending >>' $ '<< (a dollar sign with spaces around) with color being set as red.
export PS1=$PS1'\[\033[01;34m\] \$'

# Appending >>' '<< (a space) and set prompt color to white.
export PS1=$PS1'\[\033[00m\] '

# And finally the PS1 probably will be something like >>\[\e]0;\u@\h \w\a\]${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\] \[\033[01;34m\]\w\[\033[01;31m\]$(__git_ps1 '(%s)')\[\033[01;34m\] \$\[\033[00m\]<<
```

### Posted .bashrc for Git([.bashrc_git](.bashrc_git))

```bash
# Print out the history log in oneline with a prefix of '- ', of the current branch by default.
# @see https://git-scm.com/docs/pretty-formats
alias git-log-dash-oneline='git log --format="- %s"';
```

### Posted .bashrc for Programming([.bashrc_coding](.bashrc_coding))

```bash
# Count lines of codes of files of a specified format.
# @see https://stackoverflow.com/questions/1358540/how-to-count-all-the-lines-of-code-in-a-directory-recursively
function count-lines-of-code(){
	local p1=$1;
	local p2=$2;
	if [ -z "$1" ]; then
		(echo -e "\e[01;33mYou are not specifying the target folder, and the current directory \".\" will be used.\e[0m" >&2)
		(echo -e "\e[01;33mYou may use \"count-lines-of-code ./some-folder js\" to count code lines of all \"*.js\" files.\e[0m" >&2)
		p1='.';
	fi;
	if [ -z "$2" ]; then
		(echo -e "\e[01;33mYou are not specifying the file extensions, and all files like \"*.*\" are gonna be checked.\e[0m" >&2)
		p2='*';
	fi;
	find "${p1}" -name "*.${p2}" | xargs wc -l
}

# Total number of lines of codes of files of a specified format.
function count-lines-of-code-summary(){
	count-lines-of-code "$@" | tail -n1
}
```

### Posted .bashrc for Proxy([.bashrc_proxy](.bashrc_proxy))

```bash
# Enable proxy for the current terminal using the exported $SELECTED_HTTP_PROXY.
# The http proxy is used because many command do not support socks5 proxy well.
# Make sure your SELECTED_HTTP_PROXY has been correctly exported.
# export SELECTED_SOCKS5_PROXY='socks://127.0.0.1:1080';
# export SELECTED_HTTP_PROXY='http://127.0.0.1:1081';
alias using-proxy="export HTTP_PROXY=${SELECTED_HTTP_PROXY}; export HTTPS_PROXY=${SELECTED_HTTP_PROXY}; export HTTP_PROXY=${SELECTED_HTTP_PROXY}; export https_proxy=${SELECTED_HTTP_PROXY}; export no_proxy='127.0.0.1,localhost,*.loxal.me,';";
alias enable-proxy=using-proxy;
alias disable-proxy="export HTTP_PROXY=''; export https_proxy=''; export HTTP_PROXY=''; export HTTPS_PROXY='';";

# Use http proxy for git.
# @see https://stackoverflow.com/questions/128035/how-do-i-pull-from-a-git-repository-through-an-http-proxy
alias enable-git-proxy="git config --global http.proxy ${SELECTED_HTTP_PROXY}"
alias disable-git-proxy="git config --global --unset http.proxy"
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
" Using 'jk', 'JK', and 'Jk' to escape insert mode.
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

" Ignore case when searching by default and automatically switch to a case-sensitive search if you use any capital letters.
" @see https://stackoverflow.com/questions/2287440/how-to-do-case-insensitive-search-in-vim
set ignorecase
set smartcase
```

### Posted .vimrc for C++([.vimrc_cpp](.vimrc_cpp))

```vim
" Auto indent in C/C++.
set cindent
```
