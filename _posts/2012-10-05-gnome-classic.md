---
layout: post

date: 2012-10-05 14:22:11
title: Gnome Classic

category: ubuntu
tags: [ubuntu, gnome, panel]
---
The Unity desktop might feel like a good idea to some people, but I'm definitely not one of them. I need my task bar and I want to see what applications are currently running and what windows are open. Apple apparently first introduced this strange user interface, having a dock with all possible applications and and indicator below each application showing whether it is running or not. Windows 7 kinda imitated this behaviour but in a usable manner and it was also configurable, so that you could get the old behaviour back. I personally used the Windows 7 taskbar as a mix of windowbar and quick launch bar, without the grouping behaviour but with window labels instead. Fortunatly for me, Ubuntu is not as locked down as Mac OS X and enables you to use other desktop environments too, like the old-school Gnome Classic. Installing it is pretty easy and straight-forward:

    sudo apt-get install gnome-session-fallback indicator-applet-complete

After entering this into the `Terminal` application you will have to log off and on again, but during the login screen you will have to choose `Gnome Classic` instead of `Unity`. On Ubuntu 12.04 this choice can be accessed by clicking the small Ubuntu icon next to the selected user name.

Source: <http://wiki.ubuntuusers.de/GNOME3_Fallback-Modus>
