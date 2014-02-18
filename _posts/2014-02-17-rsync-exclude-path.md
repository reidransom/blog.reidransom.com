---
layout: post
title: rsync exclude path
date: 2014-02-14
---

I just spent way too much time trying to figure out how to exclude a folder from rsync without excluding all other folders with the same name.

Assume I have the following folder structure:

	.
	├── .git
	├── app.js
	├── build
	│   ├── public
	│   │   ├── file1.js
	│   │   └── file2.css
	│   └── views
	│       └── file3.html
	├── package.json
	├── public
	│   ├── file1.js
	│   └── file2.css
	└── views
	    └── file3.html

So my source js, css, and html files are in the public and views folders and my compiled js, css, and html files are in build/public and build/views.  If you want to exclude the source files and the .git folder you might try a command like this:

	$ rsync --exclude=.git --exclude=public --exclude=views ./ user@example.com:webapp/

That command actually excludes build/public and build/views as well as public and views.  The next thing I tried was:

	$ rsync --exclude=.git --exclude=./public --exclude=./views ./ user@example.com:webapp/

But that doesn't work at all.  You actually have to specify those folders like this:

	$ rsync --exclude=.git --exclude=/public --exclude=/views ./ user@example.com:webapp/

Even though that looks like your excluding files from the root of your filesystem, rsync interprets the leading slash as meaning the root of your source folder.
