---
layout: post
title: "Cat-DNS: a DNS server that resolves everything to cats"
category: posts
tags:
  - life
  - tech
---
The internet needs more cats. DNS servers are the authority on all things internet. Therefore, the best DNS server is the one that resolves everything to cats. Guess what kind of DNS server this is (Hint: it's the cat kind).

## Making it go

First, get the [code](https://github.com/notwaldorf/cat-dns), and the npm packages you need (the instructions are with the code). To run, start the server as a privileged process. This is because to be a DNS server, you need to be a UDP server on port 53. This is a small numbered port, which means it needs superpowers. This is how your run it:

<code>
sudo node cat-dns.js
</code>

You also need to somehow set your DNS server to be localhost. On a Mac, I do this by creating a new (wi-fi) interface (called Cats), in my Network preferences, and setting its DNS server to `127.0.0.1`. You could do this on your normal interface, but this makes switching back and forth easier.

## Warnings
While you're playing with this, pretty much nothing on your computer that requires the internet works. Except for your browser. And then that's mostly cats. So being able to deactivate this easily is kind of key (I know. You might think "Why would I ever want to deactivate cats?", but trust me on this one). I also recommend killing all the things that need to call the mothership (google hangouts, twitter feeds, dropbox, iMessage), because they will not like your sassy cat answers, and will slow everything down.

## You are ready
Go in your browser to `www.google.com` and wait a bit. You should see a cat. Go to a different website. Another cat. Congratulations. Your internet is now all cats.

## Wait, what?
Do not panic. While I recommend you don't look at the source because it's gross, if you do look at the source, you'll notice all it does is resolve any hostname to `54.197.244.191`, which is a magical place on the internet that has cats. My friend [@eigma](https://github.com/cpatulea/cats) made it, and is hosting it, so please try not to kill all the cat bandwith at once. You could also resolve everything to localhost, and serve your own for now cats on an http server on port 80. But then you'd have to store your own cats locally, and that is animal cruelty. Thankfully, for now, while that magical static IP exists, you don't have to.
That's it, that's all.

## I NEED TO KNOW MORE
Here's the little [summary](http://notwaldorf.github.io/posts/oops-cat-dns/) I wrote originally about how DNS servers work. Basically, cat-dns ends up doing this:

* gruesomely parse the query from the client. I used [this](http://www.zytrax.com/books/dns/ch15/) as a reference on what each of the fields in the message sections are, because the spec itself is very dry. This was the worst part, because the message sections are sequences of bits that don't add up to bytes on any sane boundary, so you have to work with bit arrays, which is nobody's idea of fun. Anyway, a spec is a spec.
* assemble the DNS answer. The answer is mostly the same for each query -- the only thing that changes is the content of the query (i.e. the hostname you requested). And you copy that from the query, so it's not a big deal.
* always returns `54.197.244.191` as the resolved IP, unless you're requesting `imgur.com`. Then it gives you an actual IP for imgur that I got from `nslookup`. Imgur stores our cats, so we need to be able to get to them. :)
