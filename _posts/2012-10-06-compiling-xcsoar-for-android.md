---
layout: post

date: 2012-10-06 17:03:42
title: Compiling XCSoar for Android

category: xcsoar
tags: [xcsoar, android, ndk]
---
If you want to compile XCSoar for Android you will first need to download the official Software Development Kit and the Native Development Kit from Google:

- <http://developer.android.com/sdk/index.html>
- <http://developer.android.com/tools/sdk/ndk/index.html>

Extract the downloaded archives and move the folders (`android-sdk-linux` and e.g. `android-ndk-r8b`) into the `opt` folder of your home directory. The resulting folder structure should look like:

    /home/turbo/opt/android-sdk-linux/
                   /android-ndk-r8b/

Now rename the `android-sdk-linux` folder to `android-sdk-linux_x86`. To actually use the SDK and NDK you will need Java. In case you haven't installed it yet you can do so by executing the following command in the `Terminal`:

    sudo apt-get install default-jre default-jdk

After installing Java you will have to install at least one Android Platform SDK using the Android SDK Manager:

    ~/android-sdk-linux_x86/tools/android

In the dialog that opens wait until *Android 4.0* appears in the list, choose and download it.

If you try to compile it now by executing `make TARGET=ANDROID` you might notice that a few other tools are still missing: `ant` and `oggenc`. You can install those through the following `apt-get` command:

    sudo apt-get install ant vorbis-tools

In case you are using a 64bit machine you might experience a problem when you try to run the Android cross-compiler. The cross-compiler is a 32bit version of the compiler and the build script might complain that the necessary compiler is "not found", which is obviously wrong since the file is there and accessible. The problem is rather that the supporting 32bit libraries are missing, which can be fixed through the following command:

    sudo apt-get install ia32-libs

Now that we have installed all the necessary tools to build the Android version of XCSoar we can start to build it by executing this:

    make TARGET=ANDROID
