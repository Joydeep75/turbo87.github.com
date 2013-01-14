---
layout: post

date: 2012-10-30 19:46:00
title: Change the title bar button side in Ubuntu 12.10

category: ubuntu
tags: [ubuntu, title bar]
---
The usual way to change the position of the title bar buttons has changed with Ubuntu 12.10. From now on the Windows-like arrangement can be activated like this:

    gsettings set org.gnome.desktop.wm.preferences button-layout 'menu:minimize,maximize,close'

Interestingly the chromium browser doesn't care about that setting. If you want the title bar buttons of that browser to be on the right place then you will have to execute the following command too:

    gconftool-2 --set "/apps/metacity/general/button_layout" --type string ":minimize,maximize,close"

Source: <http://www.matbra.com/en/2012/10/19/mudando-a-posicao-dos-botoes-do-menu-no-ubuntu-12-10/>
