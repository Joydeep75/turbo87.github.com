---
layout: post

date: 2012-10-05 15:01:52
title: Downloading the XCSoar source code

category: xcsoar
tags: [xcsoar, git, code]
---
There are plenty of ways to get the source code of the [XCSoar](http://www.xcsoar.org/) glide computer. You can either download the pre-packaged source code as an archive or clone the repository including all the history using [git](http://git-scm.com/).

Downloading the archive version of the source code is easy, but not recommended if you want to contribute to the XCSoar source code at a later time. To download the source code for any previously released version of XCSoar you have to visit e.g. <http://download.xcsoar.org/releases/6.4.1/source/> and download the `.tar.bz2` archive from that server.

To download the source code for the current development version you will have to visit <http://git.xcsoar.org/cgit/master/xcsoar.git/>, click on `commit` in the upper tab bar and then choose between `xcsoar-master.zip`, `xcsoar-master.tar.gz` and `xcsoar-master.tar.bz2`. This is the direct link to the browser-based representation of our git repository. If you choose any other commit there, you will also be able to download the source code in that current state too.

If you want to participate in the development of the XCSoar glide computer you should clone the git repository including the entire history. Only then will you be able to create new commits and publish them. On Ubuntu 12.04 the `git` command line utility is not pre-installed so you will have to do that manually using:

    sudo apt-get install git

After `git` is installed you can clone the repository using the following command:

    git clone git://git.xcsoar.org/xcsoar/master/xcsoar.git

Now you have the whole recorded history of XCSoar development on your machine and are ready to contribute. Before you create any new commits however you should tell git who you are:

    git config --global user.name "John Doe"
    git config --global user.email "john.doe@xcsoar.org"

Have fun developing!
