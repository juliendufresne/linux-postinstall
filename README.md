# Linux Post Install

Scripts to automatically setup your linux distribution (software, tools, 
options) after a fresh install

## Install

Paste the following directly in your terminal.
It will run the scripts in a clean way

```sh
declare file="$(mktemp)"
wget --quiet -O "$file" https://raw.githubusercontent.com/juliendufresne/linux-postinstall/master/bootstrap && /usr/bin/env bash "$file"
rm "$file"
```

If you don't have wget, you can use curl:

```sh
declare file="$(mktemp)"
curl -sSL --output "$file" https://raw.githubusercontent.com/juliendufresne/linux-postinstall/master/bootstrap && /usr/bin/env bash "$file"
rm "$file"
```

## How it works?

This project relies on git branches to select the right distribution/release
version.
Each branch contains:

- a config.default file (see below).
- some scripts to install/remove software
- an `all` script that wrap all that. This script is called by the bootstrap
file directly.


## Requirements

I try to rely on the least possible things. If a requirement is not met,
scripts will tell you.
The strict minimum is to have a terminal and bash 4+ installed (tested with
bash 5.0.3)

## Configuration

Chances are that you don't have the same taste as me in terms of software or
what to do once you install your operating system.
The configuration file allows to control what this script should install,
remove or keep as is.

Configuration file should be located in `${XDG_CONFIG_HOME}/linux-postinstall/config`
(in most cases XDG_CONFIG_HOME corresponds to `$HOME/.config`)
Don't worry, if the file does not exist, the script will create it for you and
give you the opportunity to edit it.

For a preview of what a config file looks like, select a branch corresponding
to a linux distribution and open the config.default file.

## Contribution

Contributions are more than welcome.
Simply create a pull request or open an issue.
