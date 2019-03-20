---
layout: post
title: "Project Idea: Fake Server"
tags: [programming, ruby, idea]
author_name: John
author_uri: http://twitter.com/johnduff
---

While working on the [Presence
assignments](http://jduff.github.com/2009/10/14/presence-3/) for the
[Stanford iPhoneU
course](http://www.stanford.edu/class/cs193p/cgi-bin/index.php) I
noticed that they did something really interesting to make interacting
with the [Twitter API](http://apiwiki.twitter.com/) a little bit easier.
They setup a server that responded to actions similar to Twitter with
some sample data. This really helped out so that when messing around
during development so that Twitter wasn’t annoyed with all the requests.

While working with this dummy server they set up I got thinking that
something like this might be useful when developing other API mashups. I
don’t think Stanford wants to set something like this up for all the
apis out there though, so what about a Gem that does something like
this?

What I’m thinking of is a very simple gem that basically runs a
[Sinatra](http://www.sinatrarb.com/) app which mimics a Twitter or
Google Maps or some other api. These ‘mock apis’ could be plugins that
could easily be pulled into the gem and run locally. I could see running
commands like ‘fakeserver install Twitter
git://github.com/jduff/fake-twitter.git’ and this would install a git
clone so that it can be kept up to date. Then you could run the fake
server with ‘fakeserver Twitter’ and then you’d have a local server that
mocked Twitters API.

I did a little bit of searching and still haven’t really come across
anything that does what I am thinking. There is this project,
[mock-server](http://github.com/djanowski/mock-server) that is kind of
like [FakeWeb](http://github.com/chrisk/fakeweb) but you define the
mocks by writing actions like you do with
[Sinatra](http://www.sinatrarb.com/). This is kind of what I’m thinking
of except it doesn’t run a server, but the general idea is pretty much
the same.

I’m not sure if there is another project that does what I am thinking of
but I might start working on something like this. If anyone has any
ideas or suggestions leave a comment and let me know.
