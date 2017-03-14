+++
author = "Justin Zimmerman"
date = "2016-07-23T20:12:34-04:00"
description = "Switching from iTerm to Hyper terminal shells."
keywords = ["HyperTerm", "Hyper", "Terminal"]
tags = ["HyperTerm", "Hyper", "Terminal"]
title = "Switching from iTerm to Hyper Terminal"
topics = ["Hyper"]
type = "post"

+++

Recently [zeit.co](https://zeit.co/) released to the world a wonderful terminal built with JavaScript / HTML / CSS called [Hyper](https://hyper.is/). Even better yet, this terminal is fully customizable with open source plugins.

I'm not one to change my development environment constantly, but this electron app was simple to install on OSX and even easier to customize programmatically.

My hope is to demo how simple it is to get started with Hyper terminal, and show how I only added a few lines to the configuration file to have a terminal I enjoy to use.

### Installing Hyper Terminal

To install Hyper terminal on OSX simply install the .dmg file from Hyper's [website](https://hyper.is/#installation).

Once installed, use your editor of choice to open `~/.hyper.js`

While the default configuration is very good, I have a few recommended configurations.

### Configuring Hyper Terminal

Changing the theme is as simple as adding `hyper-solarized-dark` to the plugins array.

You can find many other plugins at the [awesome-hyper](https://github.com/bnb/awesome-hyper) github repository.

```
plugins: [
    'hyper-solarized-dark',
  ]
```

Save the configuration, and Hyper will automatically update for you.

I also enjoy using the `hyperlinks` plugin to open links with your browser, we can also add this to the plugins array.

```
plugins: [
    'hyper-solarized-dark',
    'hyperlinks'
  ]
```

Since I use ZSH with a Powerline font, I can simply update the fonts to include `Meslo LG L DZ for Powerline`.

```
// font family with optional fallbacks
fontFamily: '"Meslo LG L DZ for Powerline", Monaco, Menlo, "DejaVu Sans Mono", "Lucida Console", monospace',
```

We can also modify the default window size of Hyper terminal.

```
// size of window by pixels (width, height)
windowSize: [1000, 500]
```

With a few lines of code, we now have a fully customized terminal!

<script src="https://gist.github.com/jrzimmerman/36c6b919b520e7cc0da07f39c1a6f6a3.js"></script>
