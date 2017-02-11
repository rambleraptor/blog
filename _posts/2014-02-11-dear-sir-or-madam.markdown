---
layout: post
title: "Dear sir or madam: the bookmarklet you didn't know you needed"
category: posts
tags:
  - life
  - tech
---

Do you sometimes feel the internet is holding you hostage? Don't you wish the internet would _look_ like it's holding you hostage? Worry no more! [Dear-sir-or-madam](https://github.com/notwaldorf/dear-sir-or-madam) is a bookmarklet that makes web pages look like they're ransom notes. For example, like this:

![screenshot](http://i.imgur.com/Hbcj9jE.png)

## How to use
Bookmark this by dragging it to your bookmark bar: <a href="javascript:var i,s,ss=['//ajax.googleapis.com/ajax/libs/jquery/1.11.0/jquery.min.js','//rawgit.com/notwaldorf/dear-sir-or-madam/master/ransom-it.js'];for(i=0;i!=ss.length;i++){s=document.createElement('script');s.src=ss[i];document.body.appendChild(s);}void(0);">ransomify!</a>.
Then go to a non-https webpage, and hit that bookmark. Then, wait a bit. Then, BAM. Ransomified.

## Disclaimers? Disclaimers!
This doesn't work with https websites at the moment (or possibly forever). Also, I wrote most of it in bed, at 7am, after insufficient levels of caffeine, so you can count on this being top drawer code. It's not the fastest it can be, but it's definitely not the n^2 abomination I wrote in the first iteration either.
