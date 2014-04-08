---
layout: post
title: OS X ZFS on Startup
date: 2014-04-07
---

### Motivation

So I've been running [OpenZFS on OS X](https://openzfsonosx.org/) and it's been great so far.  One caveat being that I need to run `sudo zpool import -f tank` after every startup to mount the ZFS filesystem.  Since I'm using this on servers, I need this to run on startup without requiring a user to login.

Here's what I did:

### OS X: Launch on Startup (pre-login)

Put this all up in your `/Library/LaunchDaemons/com.reidransom.startup.plist`:

    <?xml version="1.0" encoding="UTF-8"?>
    <!DOCTYPE plist PUBLIC "-//Apple Computer//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
    <plist version="1.0">
    <dict>
        <key>Label</key>
            <string>com.reidransom.startup</string>
        <key>ProgramArguments</key>
            <array>
                <string>/usr/local/bin/mystartup</string>
            </array>
        <key>RunAtLoad</key>
            <true></true>
        <key>StartInterval</key>
            <integer>1</integer>
    </dict>
    </plist>

Then put something like this in `/usr/local/bin/mystartup`:

    #!/bin/bash
    zpool import -f tank

Then the next time you need something on startup you could just append it to `/usr/local/bin/mystartup`.

Finally, permissions should look something like this:

    -rw-r--r--  root  wheel  /Library/LaunchDaemons/com.reidransom.startup.plist
    -rwxr-xr-x  reid  wheel  /usr/local/bin/mystartup
