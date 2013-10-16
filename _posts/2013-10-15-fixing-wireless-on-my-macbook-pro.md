---
layout: post
title:  "Fixing Wireless on My MacBook Pro"
date:   2013-08-21 22:00:00
tags:   reidransom osx
---

So recently I was trying to configure my MacBook Pro (early 2008) to dual boot OS X and Linux.  It was a huge pain - I never got Linux to boot, I only managed to hose my OS X wireless config completely.  Apparently I have the most [Linux-incompatible MacBook Pro ever](https://help.ubuntu.com/community/MacBookPro5-1_5-2/Oneiric).  After a ton of searching I finally found the answer:

    $ rm -rf /Library/Preferences/SystemConfiguration
    $ reboot

That's it!  You may want to back that sucker up instead of deleting it completely but I like to live life on the edge.