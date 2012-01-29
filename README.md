Use cases
=========
I wrote deploydots because when I researched how best to manage my dotfiles under a git repository, 
I came up with lots of solutions which either weren't reusable or clean to me with a sensible layout.

The way I use deploydots is I have a git repository, under ~/dotfiles which holds all of my dot files.
Then I run deploydots to create symlinks for all the files in ~.

Dependencies
============
ruby

Installing
==========
```deploydots``` is available as a gem at https://rubygems.org/gems/deploydots

To install it using gem, issue the following command: ```gem install deploydots```

Setup
=====
Create a directory ~/dotfiles where everything in this directory will be put under git.

~/dotfiles/README.md wont be symlinked to ~ if it exists.
I reserve this filename so that you could store notes to the user about your dotfiles and how to install them, (git clone to ~ and run deploydots)

Organize ~/dotfiles as described below.

Explaining ~/dotfiles directory layout and decisions
====================================================
All direct descendants of ~/dotfiles will be prepended with a '.' so that you don't have to type ls -a to view folders under this directory.
This also allows you to store files under ~/.git/ easily.

Only the direct descendants of ~/dotfiles get prepended with a '.'.
All other descendant files get symlinked with the name stored under ~/dotfiles.

Folders will get created instead of symlinked as to not pollute the ~/dotfiles folder by applications that write new files to those folders.

Example directory run through
=============================

~/dotfiles/vimrc is a file, when running deploydots, since it is an immediate descendant, it gets symlinked to ~/.vimrc.

~/dotfiles/tagurit/urls is a file, since this isn't a direct descendant of ~/dotfiles, it get's symlinked to ~/.tagurit/urls

Similarly for folders.

~/dotfiles/weechat is a folder, and a direct descendant of ~/dotfiles which will get created as ~/.weechat

~/dotfiles/urlwatch/cache is a folder and will get created as ~/.urlwatch/cache
