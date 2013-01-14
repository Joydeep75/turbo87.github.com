---
layout: post

date: 2012-10-05 18:24:56
title: Compiling XCSoar for Windows

category: xcsoar
tags: [xcsoar, windows, mingw, wine]
---
Cross-compiling XCSoar on Ubuntu for Windows is possible, but before that you should be able to compile for Ubuntu itself. Once you've followed the instructions for that you can continue here.

If you want to compile XCSoar for Windows you will need a different toolchain and compiler than before: `g++-mingw-w64`. This compiler can be installed through `apt-get` like most other tools too:

    sudo apt-get install gcc-mingw-w64 g++-mingw-w64

Trying to compile XCSoar for Windows now through `make TARGET=PC` will still not work though because the `msgfmt` tool is missing. We can change this by installing the `gettext` package:

    sudo apt-get install gettext

Now that everything is in place we can cross-compile XCSoar for Windows:

    make TARGET=PC

To run it inside of Ubuntu you will need the `wine` emulator:

    sudo apt-get install wine
    wine output/PC/bin/XCSoar.exe

Unfortunately installing the `wine` package on a 64bit Ubuntu wants to uninstall the `gettext` package again and I haven't found a solution for that yet.
