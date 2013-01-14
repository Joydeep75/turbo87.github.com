---
layout: post

date: 2012-10-05 17:14:52
title: Compiling XCSoar with ccache

category: xcsoar
tags: [xcsoar, ccache]
---
To speed up the compilation of XCSoar we can use [ccache](http://ccache.samba.org/) to cache the object files for us. All we have to do is install ccache and add `USE_CCACHE=y` to the make command line:

    sudo apt-get install ccache
    make TARGET=UNIX USE_CCACHE=y

If you want to take advantage of all the processors and cores in your machine you can also add the `-j` parameter including the number of threads that `make` should use to compile the application:

    make TARGET=UNIX USE_CCACHE=y -j4
