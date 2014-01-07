# Nitrous.io pairing setup

**STILL VERY MUCH A WORK IN PROGRESS**

Scripts, configs, and other things to make syncing files and pairing via Nitrous.io easier

## Prerequisites

* A [Nitrous.io](http://nitrous.io/) account
* A Nitrous.io [box](https://www.nitrous.io/app#/boxes)

## Installation

You'll need to install `unison`:

```sh
$ brew install unison
```

Clone this repo:

```sh
$ git clone https://github.com/glenngillen/nitrous.io-pairing-setup.git
```

Copy the unison profile settings into your `$HOME` directory:

```sh
$ cp -r /full/path/to/nitrous.io-pairing-setup/.unison $HOME/
```

And then make sure the `bin/nitrous-watch` file is accessible in your `$PATH`. I've got `$HOME/bin` in my path so I symlinked the file in:

```sh
$ ln -s /full/path/to/nitrous.io-pairing-setup/bin/nitrous-watch $HOME/bin/nitrous-watch
```

### Configure your editor

You'll need to configure your editor or IDE of choice to do both of the following:

* Save changes regularly so that your pair can see them
* Read any changes from disk automatically

#### Vi(m)

I use vim, so I've provided the config settings I've added to [`.vimrc`](https://github.com/glenngillen/nitrous.io-pairing-setup/blob/master/.vimrc) to make that happen.

You'll also need to setup [vundle](https://github.com/gmarik/vundle), and then run `:BundleInstall` within vim to install the `vim-auto-save` package.

### Configure SSH

To reduce the overhead associated with establishing an SSH connection (which is how unison will keep files in sync) you'll need to enable SSH connection multiplexing so that any existing ssh connection can be reused. Add the settings in [.ssh/config](https://github.com/glenngillen/nitrous.io-pairing-setup/blob/master/.ssh/config) into `$HOME/.ssh/config`.

## Usage

Once everything is setup, go into the directory that your app lives in and run `nitrous-watch`, you'll be prompted for the SSH URI for the box associated with this app:

```sh
$ cd my-app
$ nitrous-watch
Specify the SSH URI to the Nitrous.io box for this app (e.g., ssh://action@usw1.actionbox.io:12353):
ssh://action@usw1.actionbox.io:12353
Nitrous.io box is ssh://action@usw1.actionbox.io:12353
Warning: No archive files were found for these roots, whose canonical names are:
        /Users/jessie-example/dev/my-app
        //go-dev-65376//home/action/workspace
        This can happen either
        because this is the first time you have synchronized these roots,
        or because you have upgraded Unison to a new version with a different
        archive format.

        Update detection may take a while on this run if the replicas are
        large.

        ...
```

The initial sync will probably throw up a heap of noise as it moves the app up into your workspace on your Nitrous.io box. The SSH URI for the app is saved into a `.nitrousio` file within the app working directory on your machine, so you won't be prompted for it a 2nd time.

This also means there is a 1:1 mapping between apps and Nitrous.io boxes, trying to reuse a box for a different app will have undesirable consequences. This is by design as it's part of the app-centric development workflow I try to maintain.

[![Analytics](https://ga-beacon.appspot.com/UA-46840117-1/nitrous.io-pairing-setup/readme?pixel)](https://github.com/igrigorik/ga-beacon)
