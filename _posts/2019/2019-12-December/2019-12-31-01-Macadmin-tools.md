---
title: "MacAdmin Tools"
date: '2019-12-31 18:30:59 +0530'
tags:
  - APPLE
permalink: "/blog/:title.html"
header:
  teaser: "/assets/images/blog-posts-images/03-tools.png"
published: true
---
## These are the tools that I use :

- [Packages - WhiteBox](http://s.sudre.free.fr/Software/Packages/about.html){:target="_blank"} - A free package creation tool. The gold standard of making your own custom installer packages

- [Suspicious Package](http://www.mothersruin.com/software/SuspiciousPackage/){:target="_blank"} - Another similar application for inspecting the contents of macOS packages

- [Pacifist](https://www.charlessoft.com/){:target="_blank"} - Similar app to inspect / create packages

- [LaunchControl](https://www.soma-zone.com/LaunchControl/){:target="_blank"} - To inspect launchd items

- [AutoPkg](https://github.com/autopkg/autopkg){:target="_blank"} - Automated third party package download and creation for deployment

- [AutoPkgr](https://github.com/lindegroup/autopkgr){:target="_blank"} - GUI for AutoPkg, with click-to-add functionality of additional components

- [AutoDMG](https://github.com/MagerValp/AutoDMG){:target="_blank"} - Create deployable system images from macOS installers

- [Atom IDE](https://atom.io/){:target="_blank"} - A free, open source IDE

- [Sublime Text IDE](https://www.sublimetext.com/){:target="_blank"} - A high performance, cross-platform IDE

- [SUS Inspector](https://github.com/hjuutilainen/sus-inspector/releases){:target="_blank"} - An app for viewing detailed information about Apple's Software Update Service

- [Pathology](https://apps.apple.com/us/app/pathology/id877848776?mt=12){:target="_blank"} - XPath debugger and visualizer

- [Log file navigator](http://lnav.org/features){:target="_blank"} - The  log  file navigator, lnav, is an enhanced log file viewer that takes advantage of any semantic information that can be gleaned from the files being viewed, such as timestamps and log levels.  Using this extra semantic information, lnav can do things like interleaving messages from different files, generate histograms of messages over time, and providing hotkeys for navigating through the file. It is hoped that these features will allow the user to quickly and efficiently zero in on problems.
  - You can do `brew install lnav`

- [bat](https://towardsdatascience.com/awesome-rust-powered-command-line-utilities-b5359c38692#1a8c){:target="_blank"} - bat is a cat clone with syntax highlighting and Git integration.
  - You can do `brew install bat`

- [htop](https://medium.com/better-programming/12-terminal-tips-and-tricks-using-macos-and-homebrew-4e89c2ccb2fb){:target="_blank"} - htop is an interactive system monitor, process viewer, and process manager for Unix, and it is said to be a successor to the Unix program top. It shows the updated list of processes running on your Mac and is ordered by the amount of CPU usage.
  - You can do `brew install htop`
  - To run, you'll have to `sudo htop`

- [launchd Package Creator](https://github.com/ryangball/launchd-package-creator){:target="_blank"} - A utility that allows you to easily create a .pkg containing a LaunchDaemon or LaunchAgent, and a target script of your choosing.

- [Outset](https://github.com/chilcote/outset){:target="_blank"} - Automatically process packages, profiles, and scripts during boot, login, or on demand.
  - Login/Logout Hooks Deprecated Technology. Instead, its recommended to use third-party tools such as Outset and Offset.
  - References :
    - [Daemons and Services Programming Guide - Login and Logout Scripts](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/BPSystemStartup/Chapters/CustomLogin.html){:target="_blank"}
    - [JamfNation - Login/Logout Hooks Deprecated Technology](https://www.jamf.com/jamf-nation/discussions/27703/login-logout-hooks-deprecated-technology){:target="_blank"}




## Useful links :

- <https://github.com/smashism/awesome-macadmin-tools>{:target="_blank"}
