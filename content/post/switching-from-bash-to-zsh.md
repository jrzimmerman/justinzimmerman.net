+++
author = "Justin Zimmerman"
date = "2016-08-01T09:33:10-04:00"
description = "I recently switched from BASH (Bourne Again SHell) to ZSH after hearing about z shell's many benefits."
keywords = ["Bash", "ZSH"]
tags = ["Bash", "ZSH"]
title = "Switching From Bash to ZSH"
topics = ["Bash", "ZSH"]
type = "post"

+++

I recently switched from BASH (Bourne Again SHell) to ZSH after hearing about z shell's many benefits.

The main benefits for me were better autocompletion, and file globbing, and better autocorrection. I spent quite a few weekends doing research on whether to switch or not, and finally I bit the bullet.

## Installing ZSH with Homebrew

While this isn't necessary, it's incredibly straightforward to do. The default version of ZSH shipped with OSX is 5.0.2. The latest version of ZSH at the time of writing is 5.2.

### Download ZSH

```sh
brew update
brew install zsh
```

Once installation is completed, we need to insert the location into `/etc/shells`

```sh
 sudo vim /etc/shells
```

Insert the following line to the end of the file

```sh
/usr/local/bin/zsh
```

This is the file path that homebrew system linked ZSH to.

To set the default shell to ZSH

```sh
chsh -s /usr/local/bin/zsh
```

This might require a restart, but once completed verify zsh is your default shell by running

```sh
echo $SHELL
```

Now you have the latest ZSH running as default.

### Installing oh-my-zsh

The [oh-my-zsh](https://github.com/robbyrussell/oh-my-zsh) repository is a very large open source collection of zsh plugins and [themes](https://github.com/robbyrussell/oh-my-zsh/wiki/themes). While there are a few alternatives to oh-my-zsh, such as prezto. I wanted to be able get started right away.

To install oh-my-zsh run the following

```sh
sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
```

This will modify your `.zshrc` file

It comes with the "robbyrussell" theme as default, but I wanted something a bit more exciting like the "agnoster" theme as pictured below.

![agnoster theme](/img/agnoster.png)

To switch themes, open your .zshrc file and replace this line

```sh
ZSH_THEME="robbyrussell"
```

with

```sh
ZSH_THEME="agnoster"
```

This is also a great time to copy over your custom `.bash_profile` configs to the `.zshrc` file.

### Installing Powerline Fonts

The only problem is that the agnoster theme requires [Powerline fonts](https://github.com/powerline/fonts) to show the "pipeline" icons. Fortunately installing the fonts is very simple and comes with a script.

First, clone down the `powerline/fonts` repository into your github work folder

```sh
git clone https://github.com/powerline/fonts.git
```

Then `cd fonts` into the fonts repository and run

```sh
./install.sh
```

Once completed, this also might require a restart to show the new fonts available.

In your terminal (iTerm2 or HyperTerm) change the default font to one of the "for powerline" fonts. I chose `Meslo for Powerline`.

Once selected, you have successfully completed setting up ZSH with oh-my-zsh!

Congratulations on your awesome new terminal!
