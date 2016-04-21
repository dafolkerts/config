# config

This repository tracks a personal xubuntu linux system configuration.  It uses a bare git repository in the .myconfig directory in the users $HOME directory.  It also sets up a bash alias "config" that is used instead of "git" to work with this repository.

## To migrate this setup to a new system

Create 'config' alias and then restart bash:

  $ echo "alias config='/usr/bin/git --git-dir=$HOME/.myconfig/ --work-tree=$HOME'" >> $HOME/.bashrc
  
Make the repository ignore it's own folder:

  $ echo ".myconfig" >> .gitignore
  
Clone into bare repository:

  $ git clone --bare <git-repo-url> $HOME/.myconfig
  
Checkout content from repository to $HOME:

  $ git checkout
  
If an error occurs saying that some files will be overwritten (.bashrc for instance), backup and/or remove files.
Set the flag 'showUntrackedFiles' to 'no':

  $ config config --local status.showUntrackedFiles no
  
From now on use 'config' instead of 'git' when interacting with this repository:

  $ config status
  $ config add .bashrc
  $ config commit -m "Add .bashrc"
  $ config remote -v
  $ config pull origin master
  $ config push origin master
  etc.

.SSD-OPT has some tips about optimizing the linux system for use with solid state drives

.SYSTEM_SETUP records changes made to the system during setup (files altered, programs installed, etc.)
