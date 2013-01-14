---
layout: post

date: 2012-10-05 14:07:51
title: Using old-school scrollbars

category: ubuntu
tags: [ubuntu, scrollbars]
---
Some people may like the new dynamic scrollbars that Ubuntu is using by default now, I don't. Good thing that it is rather easy to go back to the old scrollbars:

    sudo apt-get remove --purge overlay-scrollbar liboverlay-scrollbar-*
    gsettings set org.gnome.desktop.interface ubuntu-overlay-scrollbars false

After entering this into the `Terminal` application you will have to log off and on again to reinitialize the session.

Source: <http://wiki.ubuntuusers.de/GNOME3_Fallback-Modus>
