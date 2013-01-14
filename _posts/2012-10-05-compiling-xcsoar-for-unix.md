---
layout: post

date: 2012-10-05 16:49:20
title: Compiling XCSoar for Unix

category: xcsoar
tags: [xcsoar, unix, linux, sdl, boost, curl]
---
Once you've downloaded the [XCSoar](http://www.xcsoar.org/) source code on your machine you will probably want to compile it. This set of instructions has been written and tested on a freshly installed Ubuntu 12.04 but should be more or less valid on most other Linux-based environments too.

To compile the Unix version of XCSoar you will have to enter `make TARGET=UNIX` into your `Terminal` after entering the folder, in which you have downloaded the XCSoar source code. If you do this right now, you will probably notice that a few packages are still missing to build the application. The Unix and Android versions of XCSoar are depending on the [SDL library](http://www.libsdl.org/), but that apparently isn't installed by default on most Ubuntu distributions. The first step to successfully compiling XCSoar is installing the missing packages:

    sudo apt-get install libsdl1.2-dev libsdl-image1.2-dev libsdl-ttf2.0-dev

Unfortunately the `libsdl-ttf2.0-dev` package in the Ubuntu 12.04 repository is slightly broken because it misses a `.pc` file, that `pkg-config` needs to determine whether the package is installed or not. To fix this we will have to create the file ourselves. Depending on your platform you may have to replace `i386` by `x86_64` in the following paths.

    sudo cp /usr/lib/i386-linux-gnu/pkgconfig/SDL_image.pc /usr/lib/i386-linux-gnu/pkgconfig/SDL_ttf.pc
    sudo gedit /usr/lib/x86_64-linux-gnu/pkgconfig/SDL_ttf.pc

In the text editor that opens now you have to replace a few text blocks:

- "Name: SDL_image" to "Name: SDL_ttf"
- "Description: image loading library for Simple DirectMedia Layer" to "Description: ttf library for Simple DirectMedia Layer with FreeType 2 support"
- "Libs: -L${libdir} -lSDL_image" to "Libs: -L${libdir} -lSDL_ttf"

If you try to compile XCSoar now you should notice that the SDL-related errors are gone. Instead you might find the build script complaining that it can't find [`libcurl`](http://curl.haxx.se/). You can fix this by installing the `libcurl4-openssl-dev` package:

    sudo apt-get install libcurl4-openssl-dev

After installing the necessary libraries you will notice that the default Ubuntu distribution is missing some other things too that are needed to build XCSoar. One of them is actually the [GNU C++ compiler](http://gcc.gnu.org/) `g++`, that can be installed like this:

    sudo apt-get install g++

If you run `make TARGET=UNIX` now, the build process will start and compile and first couple of files. At some point it will probably stop again though, complaining that `boost/cstdint.hpp` can't be found. To fix this, the necessary [boost](http://www.boost.org/) libraries have to be installed:

    sudo apt-get install libboost-dev

This will install *all* boost libraries and not just the ones that XCSoar needs, but unless you have a very small disk or a bad internet connection this shouldn't be much of a problem.

The next problem you might encounter is a missing `xsltproc` tool, which can be fixed by just installing it through:

    sudo apt-get install xsltproc

The `xsltproc` tool is used to process the SVG image files that are making up a part of the XCSoar user interface. Since SVG files can't be used directly we need to convert them to PNG images first using the [`librsvg`](https://live.gnome.org/LibRsvg) library. Unfortunately that library isn't installed by default on Ubuntu either so you will have to execute the following command in the `Terminal`:

    sudo apt-get install librsvg2-bin

Now that we have the SVG to PNG converter installed, we notice that what we need are actually masked BMP images. These are created by the build script using [ImageMagick](http://www.imagemagick.org/) which also needs to be installed:

    sudo apt-get install imagemagick

Now you should have installed everything you need to build and run XCSoar:

    make TARGET=UNIX
    output/UNIX/bin/xcsoar
