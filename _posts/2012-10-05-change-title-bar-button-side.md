---
layout: post

date: 2012-10-05 17:46:00
title: Change the title bar button side

category: ubuntu
tags: [ubuntu, title bar]
---
In the process of making Ubuntu look more like Mac OS X, Canonical decided that it would be a good idea to have the buttons in the title bar on the left side from now on. Once again, I don't agree... Fortunately there is once again a very easy solution:

    gconftool-2 --set "/apps/metacity/general/button_layout" --type string ":minimize,maximize,close"

Source: <http://www.ubuntugeek.com/quick-and-easy-title-bar-button-side-switching-in-ubuntu-10-04-lucid9-10-karmic.html>
