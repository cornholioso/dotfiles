# About
This repository contains everything needed to bootstrap and configure new Mac computer. It is opinionated and based on my own work flows. It is highly recommended that you fork this and customize it for your own purposes. Included here are:

* dotfiles
* ~/bin/ scripts
* Configuration files
* Scripting templates and utilities
* Bootstrap scripts to automate the process of provisioning a new computer or VM.

**Disclaimer:**  *I am not a professional or trained programmer and I bear no responsibility whatsoever if any of these scripts wipes your computer, destroys your data, burns your toast, crashes your car, or otherwise causes mayhem and destruction.  USE AT YOUR OWN RISK.*

The files are organized into three subdirectories.

```
dotfiles/
  ├── bin/
  ├── bootstrap/
  │   ├── boostrap-linux.sh
  │   ├── config-linux.sh
  │   ├── config-macOS.sh
  │   ├── config/
  │   └── plugins/
  ├── config/
  │   ├── bash/
  │   └── shell/
  ├── scripting/
  └── test/
```

* **bin/** - The scripts in `bin/` are symlinked into `~/bin/` to allow them to be executed by your user.  These symlinks are specified in `~/dotfiles/bootstrap/config/symlinks.yaml`
* **bootstrap/** - Scripts and utilities to bootstrap a new computer.  There is a script for linux, a script for macOS, and an initial bootstrap script for linux servers.
* bootstrap/**config/** - Contains YAML files which are the manifest for the list of packages to be installed or symlinks to be created.
* bootstrap/**plugins** - Plugin scripts that extend the usage of the install scripts for mac/linux
* **config/** - Contains the elements needed to configure your environment and specific apps.
* config/**bash/** - Files in this directory are *sourced* by `.bash_profile`.
* config/**shell/** - Files here are symlinked to your local environment. Ahem, dotfiles.
* **scripting/** - This directory contains bash scripting utilities and templates which I re-use often.
* **test/** - Unit tests written using [BATS](https://github.com/sstephenson/bats)

**IMPORTANT:** Unless you want to use my defaults, make sure you do the following:

* Edit all the config YAML files in `bootstrap/config/` to reflect your preferences before running the install script.
* Review the files in `config/` to configure your own aliases, preferences, etc.

### Private Files
Sometimes there are files which contain private information. These might be API keys, local directory structures, or anything else you want to keep hidden. I keep these in a separate private repository which has a folder structure very similar to this one. To configure your own private files edit the following files to reflect your setup

* Both bootstrap install scripts have a variable for the location of a private install script.  If that script is found, it will be run.
* Edit `config/shell/bash_profile` to add the location of your private plugins

## Cloning this repo to a new computer
The first step needed to use these dotfiles is to clone this repo into the `$HOME` directory.  To make this easy, I [created a gist](https://gist.github.com/natelandau/b3e1dfba7491137f0a0f5e25721fffc2) which can easily be run with the following command:

```
curl -SL https://gist.githubusercontent.com/natelandau/b3e1dfba7491137f0a0f5e25721fffc2/raw/d98763695a0ddef1de9db2383f43149005423f20/bootstrapNewMac | bash
```

This gist creates a script `~/bootstrap.sh` in your home directory which completes the following tasks

1. Creates a new public SSH key if needed
2. Copies your public key to your clipboard
3. Opens Github to allow you to add this public key to your 'known keys'
4. Clones this dotfiles repo to your home directory

See, easy. Now you're ready to run `~/dotfiles/bootstrap/config-macOS M.sh` and get your new computer working.

## A Note on Code Reuse
Many of the scripts, configuration files, and other information herein were created by me over many years without ever having the intention to make them public. As a novice programmer, I have Googled, GitHubbed, and StackExchanged a path to solve my own scripting needs.  Quite often I lift a function whole-cloth from a GitHub repo don't keep track of it's original location. I have done my best within these files to recreate my footsteps and give credit to the original creators of the code when possible. Unfortunately, I fear that I missed as many as I found. My goal of making this repository public is not to take credit for the wonderful code written by others. If you recognize something that I didn't credit, please let me know.