## Introduction

Git Watcher is a multi-platform desktop app written in pure HTML and Javascript using node-webkit.

It shows diff information about local staged/unstaged files and allows you to commit changes. UI is updated in real-time by detecting file changes and git index changes. Submodules also inform changes to their parent module.

It also organizes repository submodules in tabs, so that you can work easily with them without the need of having multiple git gui instances or shells.

In my opinion, the native git gui app is awful and lacks a lot of features. This app aims to outstand it :)

## Features

* **Real-time** multiple file diff information with line numbers and **syntax highlighting**
* Allows you to work with **submodules organized in tabs**.
* Allows you to **open files** by clicking on its name or lines numbers. You can even use your preferred editor!
* Shows current **branch information**: upstream branch and ahead/behind commit count.
* Menu bar with configuration options and utilities.
* System Tray support

## Screenshots
![Overview 1](http://gitw.zedplan.com/screenshots/gitw1.png)
![Overview 2](http://gitw.zedplan.com/screenshots/gitw2.png)
![Overview 3](http://gitw.zedplan.com/screenshots/gitw3.png)

## TODO

I'm working on the following features
(your help will be much appreciated!)

* Amend commit (Really hard to do without a proper API!)
* Correctly show unmerged paths info. Alert when staging an unmerged file. Allow to checkout local/remote version.
* Browse local recent branches.
* Better syntax highlighting.
* More configuration options.
* Git stash/pop.
* Shortcuts.
* Render images in diff.
* Git log: show errors/warnings.

## Download

Please consider downloading the proper build according to your distribution. 
See __Troubleshooting__ if you cannot run the app.

* Linux x64 - __Old dists__: Ubuntu 12.04, 12.10 or derivative distributions
    * [v0.3.13](http://gitw.zedplan.com/gitw-linux-x64-v0.3.13.tar.gz)
    * [v0.3.12](http://gitw.zedplan.com/gitw-linux-x64-v0.3.12.tar.gz)
* Linux x64 - __New dists__: Ubuntu 13.04+, Gentoo, Arch, Fedora 18+
    * [v0.3.13](http://gitw.zedplan.com/gitw-linux-x64-v0.3.13-new-dist.tar.gz)
    * [v0.3.12](http://gitw.zedplan.com/gitw-linux-x64-v0.3.12-new-dist.tar.gz)

## How to run the app

Just extract file contents and execute `./gitw`.

You can also:
* `sudo npm link`. A link to the app will be created in `/usr/local/bin`, so you can run the app using `gitw` command. If it's a valid Git repository, the current working directory is used by default.
* Create a desktop shortcut :P

## Or build it yourself!

Please read [node-webkit wiki](https://github.com/rogerwang/node-webkit/wiki) for details on how to run apps.

Requirements:
* [NodeJS >= 0.10](http://nodejs.org/download/)
* [node-webkit](https://github.com/rogerwang/node-webkit#downloads). Download and extract its contents in `/opt/node-webkit`.


Then:
* Clone repo and run `npm install` or just run `npm install gitw`.
* Install *nw-gyp*: `npm install -g nw-gyp`.
* Rebuild *git-utils* and *mmmagic* dependencies based on the node-webkit version you are running. Eg: `cd node_modules/git-utils && nw-gyp rebuild --target=0.8.4`. Do the same for *mmmagic*.
* Run the app! `/opt/node-webkit/nw /path/to/gitw`.

Also, you will find a helper script `./build.sh` that creates a distributable package for Linux. It asumes you have node-webkit installed on `/opt/node-webkit`.

## Troubleshooting

* [The solution of lacking libudev.so.0](https://github.com/rogerwang/node-webkit/wiki/The-solution-of-lacking-libudev.so.0)
* __ENOSPC error__: You may run into that error when browsing large repositories. You need to increase the maximum number of watches for inotify: `echo fs.inotify.max_user_watches=65536 | sudo tee -a /etc/sysctl.conf && sudo sysctl -p`. That should be enough.
