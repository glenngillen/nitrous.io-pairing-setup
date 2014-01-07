# Nitrous.io pairing setup

**STILL VERY MUCH A WORK IN PROGRESS**

Scripts, configs, and other things to make syncing files and pairing via Nitrous.io easier

## Prerequisites

* A [Nitrous.io](http://nitrous.io/) account
* A Nitrous.io [box](https://www.nitrous.io/app#/boxes)

## Installation

You'll need to install `unison`:

```term
brew install unison
```

Clone this repo:

```term
git clone https://github.com/glenngillen/nitrous.io-pairing-setup.git
```

And then make sure the `bin/nitrous-watch` file is accessible in your `$PATH`. I've got `$HOME/bin` in my path so I symlinked the file in:

```term
ln -s /full/path/to/nitrous.io-pairing-setup/bin/nitrous-watch $HOME/bin/nitrous-watch
```

### Configure you're editor

You'll need to configure your editor or IDE of choice to do both of the following:

* Save changes regularly so that your pair can see them
* Read any changes from disk automatically

#### Vi(m)

I use vim, so I've provided the config settings I've added to [`.vimrc`](https://github.com/glenngillen/nitrous.io-pairing-setup/blob/master/.vimrc) to make that happen.

You'll also need to setup [vundle](https://github.com/gmarik/vundle), and then run `:BundleInstall` within vim to install the `vim-auto-save` package.

### Configure SSH

To reduce the overhead associated with establishing an SSH connection (which is how unison will keep files in sync) you'll need to enable SSH connection multiplexing so that any existing ssh connection can be reused. Add the settings in [.ssh/config](https://github.com/glenngillen/nitrous.io-pairing-setup/blob/master/.ssh/config) into `$HOME/.ssh/config`.

## Usage

TBD.

[![Analytics](https://ga-beacon.appspot.com/UA-46840117-1/nitrous.io-pairing-setup/readme?pixel)](https://github.com/igrigorik/ga-beacon)
