---
layout: post
title: Use Mercurial for dotfiles
date: 2013-11-06
---

You use source control to keep track of dotfiles in your home directory, right?

Well instead of using `git`/`.gitignore` like this:

    *
    !.vimrc
    !.zshrc

and ending up with git info in your fancy zsh shell prompt (even though your only in your home folder) that looks like this:

    ~ git:(master) $

Roll with mercurial for your dotfiles instead so your `.hgignore` looks like this:

    syntax: glob
    *

and your home folder shell prompt will be nice and clean like this:

    ~ $

Any files you explicitly add to your mercurial repo with `hg add <filename>` will add the file to your repo even if `.hgignore` says to ignore it.