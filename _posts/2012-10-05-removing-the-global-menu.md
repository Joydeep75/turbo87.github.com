---
layout: post

date: 2012-10-05 14:03:17
title: Removing the global menu

category: ubuntu
tags: [ubuntu, menu, appmenu, global menu]
---
If you don't like the global menu that Ubuntu introduced with the switch to the Unity desktop, you can simply go back to the old menu-as-part-of-the-window behaviour by deinstalling a few packages:

    sudo apt-get remove --purge appmenu-gtk appmenu-gtk3 appmenu-qt firefox-globalmenu thunderbird-globalmenu lo-menubar

After entering this into the `Terminal` application you will have to log off and on again to reinitialize the session.

Source: <http://wiki.ubuntuusers.de/GNOME3_Fallback-Modus>
