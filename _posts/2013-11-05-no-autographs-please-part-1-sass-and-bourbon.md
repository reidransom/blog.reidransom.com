---
layout: post
title:  "No Autographs Please: Part 1 “Sass and Bourbon”"
date:   2013-11-05 23:30:00
tags:   reidransom electricpond
---

I recently volunteered my web development skills for my wife, who has been working hard lately taking care of our kids and keeping up with schoolwork.  She's also been leading up this reunion committee for a whole bunch of people she used to work with as characters at Disney World in Florida.  They've all reconnected on Facebook and will be meeting up in Orlando in September 2014.  So they needed a website including info for the event and a way to purchase tickets.

Since I've been honing my front-end web development skills lately, and I'm such a nice guy, I jumped at the opportunity.  Since the deadline wasn't too pressing I decided to use the project as an opportunity to learn as much as I could and do everything super-professionally.

The first thing I wanted to learn more of was Sass.  I had used LESS and Bootstrap on a couple previous projects and kinda wasn't feeling it.

I remember trying to do a circular gradient in LESS without having to type out vendor prefixes.  (In a world with css pre-processors, I refuse to type vendor prefixes.)  Anyway I forget the specifics but it was a pain and I gave up in the end and typed them out anyway.  I heard someone talking about Bourbon on a podcast and how one of their goals was to figure out all that vendor stuff for you.  It sounded appealing so I decided to jump the LESS/Bootstrap ship and get on the Sass/Bourbon train.

The LESS website is nicer.  Sass is more powerful.  Moving on :)

One thing I liked about Bourbon is it seems to get out of the way much better than Bootstrap.  Going in I felt like the two would be providing similar functionality but looking back I'm thinking that's not really the case at all.  Bourbon's website says it's "A simple and lightweight mixin library for Sass." and that's pretty accurate.  Infact I installed it on day one, used it to get my initial structure done, then completely forgot it was there for the rest of the project.  Actually now I'm realizing I should have used it more than I did.  Well there you go, Bourbon gets the job done and gets out of your way... completely.  Also, I like bourbon.

I've tried out a bunch of different grid frameworks in the past but definitley like Neat the best for one glaring, shiny, reason - everything happens in Sass.  Meaning, you don't have to crud up your HTML with annoying classnames like `row2` or whatever.  Grids are display logic and it belongs in your CSS (in my humble opinion).

The one negative thing I'll say about Bourbon is that they seem to *really* want you to use it with Ruby/Rails for no apparent reason.  In fact a big selling point for me over Compass was that Bourbon was written in pure Sass.  Yet for some reason the Bourbon install instructions assume you're rolling with Rails 3.1+.  Alternatively they say you can install it as a Ruby gem.  This gives you the handy `bourbon` command for running `bourbon install` to generate your scss or `bourbon update` to get the latest scss.  Anyway, since I lean JavaScript over Ruby, I used Bower instead:

    bower install bourbon --save
    bower install neat --save

Incase you're curious, [here's a link to the finished website](https://electricpond.com/nap/).

In future posts I'll do a deep dive on GruntJS and talk about how I got to know Backbone.js by implementing a simple shopping cart.
