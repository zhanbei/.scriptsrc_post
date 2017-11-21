# Posted Scripts for .\*rc Scripts

<!-- > Created by Fisher at 14:49 on 2017-03-21. -->

Posted .scriptrc_post (e.g., .bashrc_post, .vimrc_post) that will be loaded after .scriptrc (e.g., .bashrc, .vimrc) to Set up some common configurations for common conditions, e.g., .vimrc, .bashrc.

## Installation(Git Clone)

Clone this repository directly to home directory.

```bash
cd ~
git clone https://github.com/befisher/.scriptsrc_post.git
```

## Enable Posted .bashrc Scripts for Your Bash Terminal

Add line: `source ~/.scriptsrc_post/.bashrc_post` to your `~/.bashrc` to enable posted scripts for .bashrc.

You may update `~/.scriptsrc_post/.bashrc_post` file to configure modules to be loaded.

## Enable Posted .vimrc Scripts for Your Vim Editor

Add line: `so ~/.scriptsrc_post/.vimrc_post` to your `~/.vimrc` to enable posted .vimrc scripts.

You may update `~/.scriptsrc_post/.vimrc_post` file to configure modules to be loaded.



