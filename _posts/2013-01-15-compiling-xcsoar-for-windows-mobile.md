---
layout: post

date: 2013-01-15 00:17:20
title: Compiling XCSoar for Windows Mobile

category: xcsoar
tags: [xcsoar, windows, windows mobile, cegcc]
---
If you want to create a version of [XCSoar](http://www.xcsoar.org/) that runs on any of the ancient Windows Mobile devices you will need a cross-compiler. Fortunately the [CeGCC project](http://cegcc.sourceforge.net/) has ported the popular GNU compiler to create executables for that platform. Unfortunately though their latest release only uses gcc 4.4.0, which does not include all the nice things yet that the C++11 standard has to offer.

Since the CeGCC project is open-source there was a solution though. XCSoar core developer [Max Kellermann](http://max.kellermann.name/) took the time to merge a more recent version of gcc into the project. You will have to visit <http://max.kellermann.name/download/xcsoar/devel/cegcc/> and download the most recent version for your CPU architecture.

After you downloaded the file you will need to extract it to a good location on your harddrive. I usually choose `~/opt/` for that. In the end you should be able to see something like this:

    > ls ~/opt/mingw32ce/bin
    arm-mingw32ce-addr2line  arm-mingw32ce-gcc        arm-mingw32ce-ranlib
    arm-mingw32ce-ar         arm-mingw32ce-gcc-4.6.3  arm-mingw32ce-readelf
    arm-mingw32ce-as         arm-mingw32ce-gcov       arm-mingw32ce-size
    arm-mingw32ce-c++        arm-mingw32ce-gprof      arm-mingw32ce-strings
    arm-mingw32ce-c++filt    arm-mingw32ce-ld         arm-mingw32ce-strip
    arm-mingw32ce-cpp        arm-mingw32ce-ld.bfd     arm-mingw32ce-windmc
    arm-mingw32ce-dlltool    arm-mingw32ce-nm         arm-mingw32ce-windres
    arm-mingw32ce-elfedit    arm-mingw32ce-objcopy    libgcc_s_sjlj-1.dll
    arm-mingw32ce-g++        arm-mingw32ce-objdump

To be able to use these applications from the command line directly you will need to add the `bin` folder to your `PATH` variable. Open the `.profile` file in your user folder and attach the following line to it:

    PATH="/home/turbo/opt/mingw32ce/bin:$PATH"

after that close and save the file, and restart any command line windows you might have open.

Unfortunately the compiler seems to require different versions of `libmpfr` and `libgmp` than those installed by default on Ubuntu. To solve this problem we can use symlinks that link to the more recent versions. Follow these commands and then you should be read to compile:

    cd /usr/lib/i386-linux-gnu/
    sudo ln -s libmpfr.so.4 libmpfr.so.1
    sudo ln -s libgmp.so.10 libgmp.so.3
    
 Now that we have installed all the necessary tools to build the Windows Mobile version of XCSoar we can start to build it by executing for example this:

    make TARGET=WM5
    
Keep in mind that there are also a few other Windows Mobile targets: `PPC2000`, `PPC2003`, `PPC2003X`, `WM5` and `WM5X`
