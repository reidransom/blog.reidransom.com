---
layout: post
title:  "My New Favorite Thing: GruntJS"
date:   2013-10-15 21:00:00
tags:   reidransom software rsync gruntjs javascript build deploy
ogimage: /post-assets/grunt-logo.png
---

I've been using GruntJS for a few months and I'm really liking it.  This is a brief story about why I started using it and why I'm sticking with it.

### Backstory

<img class="right" src="{{ site.url }}/post-assets/grunt-logo.svg" alt="The GruntJS Logo" />

Back in April when I started developing my app [Sync Hard](https://synchardapp.com/) I was using this awesome build tool [CodeKit](http://incident57.com/codekit/) and writing my own python scripts for deployment.  This worked well for a bit until I tried to do some development on my laptop and realized that it was going to be a pain to keep my preferences in sync.

At that point I looked into using [Grunt](http://gruntjs.com/) but it seemed like overkill so I dismissed it in favor of implementing the build process in python myself.  After all, the only stuff I was doing was some `less` compilation and string replacements, no biggie right?  Well, it was fine at first but after adding tests and a companion marketing site, my simple python build/deploy script quickly got out of hand.  It saw me thru the 1.0 release and then I immediately went back to the Grunt website and started reading up.

### Reasoning

The learning curve is a little steeper than CodeKit obviously but there are a bunch of reasons why I'm liking Grunt better.

#### Gruntfile Config

Everything is configured on a per-project basis in one plain-text [Gruntfile](http://gruntjs.com/getting-started#an-example-gruntfile).

This lets you keep your config together with your project and lets you easily maintain it with version control.

Starting development on a new machine is as simple as:

	$ git clone project
	$ cd project
	$ npm install

That'll make sure you have everything you need.

#### Grunt Plugins

All the implementation stuff is kept separate from your config as grunt plugin modules.

The collection of [grunt plugins](http://gruntjs.com/getting-started) is vast.  There are the official grunt plugins which are named like `grunt-contrib-plugin` which give you a solid foundation of well-maintained plugins for basic functionality.  There are also a ton of third-party plugins named like `grunt-plugin`.  These give you the flexibility to do just about anything else you could need.

If you still can't find what you're looking for, well you must be very picky, but you're not out of luck.  [Creating your own grunt plugin](http://gruntjs.com/creating-plugins) is very straightforward.

#### Grunt CLI

The Grunt CLI is awesome for a couple reasons.

You can install it globally with:

	$ npm install -g grunt-cli

Keep in mind this literally only installs the Grunt command-line interface, not Grunt itself.

Like the plugins, Grunt is meant to be installed on a local/per-project basis.  This allows you to do things like keep `project-a` on it's own local Grunt v0.3 install and `project-b` on it's own local Grunt v0.4 install.

Also, when you run `grunt -h` you get all the grunt usage info along with a listing of the tasks available in your current project.

Sweet, right?  They thought of everything.

### Conclusion

All my projects from now are getting Gruntfiles.  I will be resting assured that if I table a project and come back to it in six months, I'll be able to open that file up and immediately be reminded of exactly how to test, build, and deploy.

In an upcoming post, I'll talk about my experience writing my first grunt plugin - [grunt-synchard](https://github.com/reidransom/grunt-synchard#readme).