---
layout: post
title: "Introducing Todoly.net"
tags: [programming, ruby, rails, projects, todoly]
author_name: John Duff
author_uri: http://twitter.com/johnduff
---

So, I’ve been really slacking with the blogging lately, I haven’t even
been posting my learnings which is a 10 minute process at most.
Hopefully I can get back in the habit, no promises though. Okay, so what
have I been up to the last little while? Well, I’ve been working on a
little side project app that I recently put up and wanted to talk about
a little bit.

What is it?
-----------

Well from the post title you can probably guess it is called
[Todoly](http://todoly.net) and can by found at
[todoly.net](http://todoly.net). [Todoly](http://todoly.net) is a really
simple todo list application with very few features and is happy that
way. I can hear you now, “Why did you bother writing another todo list
app, have you not heard of X, Y or Z?”. Because I wanted to dammit,
that’s why.

Background
----------

More than just wanting to write something I did have a few specific
goals that writing [Todoly](http://todoly.net) has helped me to achieve.

1.  Build something using Rails 3.
2.  Try out my [Rails App
    Template](http://github.com/jduff/rails-templates) and expand on
    what is included in it.
3.  Actually finish something and get it deployed publicly.

[Todoly](http://todoly.net) has done all these things for me and more.
I’ve been able to play around with some of the cool new things in Rails
3 like the new [query
interface](http://m.onkey.org/2010/1/22/active-record-query-interface),
[unobtrusive
javascript](http://railscasts.com/episodes/205-unobtrusive-javascript),
[responders](http://weblog.rubyonrails.org/2009/8/31/three-reasons-love-responder)
and much, much more. I’ve found a number of bugs in my [app
template](http://github.com/jduff/rails-templates) and have a few ideas
on things I can add to make it more complete. Last, but not least, I got
to try out deploying an app to [Heroku](http://http://heroku.com/)
(which was amazingly simple) and have it running in the wild.

This last point was really important to me and was the main reason for
choosing a simple todo list application. I’ve worked on a number of side
projects over the years but never actually released a working
application because I got bored with the project, had another idea or
life distract me or whatnot. I’ve released lots of bits and pieces to my
[github account](http://github.com/jduff) but it feels very different
being able to finish a project and put it out there.

What’s under the hood?
----------------------

[Todoly](http://todoly.net) is a pretty straight forward Rails 3
application running locally under MySQL and under PostgreSQL on
[Heroku](http://heroku.com) in production. I used a number of gems and
open source projects include, but not limited to:

-   [jQuery](http://http://jquery.com/)
-   [Devise](http://github.com/plataformatec/devise) for authentication.
-   [Simple Form](http://github.com/plataformatec/simple_form) to
    simplify HTML form development.
-   [CanCan](http://github.com/ryanb/cancan) for authorization.
-   [HTML 5 boilerplate](http://github.com/paulirish/html5-boilerplate)
    (actually [my own fork](http://github.com/jduff/html5-boilerplate)
    that I made for Rails apps)

Did I mention that the source for the whole project is up on GitHub so
you can [check it out yourself](http://github.com/jduff/todoly) if you
want. This has already led to some cool stuff, like a friend of mine
taking the idea for the app and implementing the same features in
[Node.js](http://http://nodejs.org/). You can take a look at that on
GitHub as well, [right here](http://github.com/glongman/node-todo).

Why is Todoly better than X, Y or Z?
------------------------------------

In all honesty it probably isn’t any better than the other, countless,
todo list applications out there. I have been using it regularly for a
little while though and like it for a number of reasons.

The main reason I like it is the interface is really simple. It’s all
about adding tasks and completing them, so that’s what the interface
helps you to do. I added a cool little feature that lets you focus on a
groups of tasks by selecting the tag you’re interested in. I find this
to be all I really need to keep track of what I need to do.

Since I have the code and can push a new release whenever I want if
there is ever something I need from the application I can just add it.
Since the project is open source you can [fork
it](http://http://github.com/jduff/todoly) and do the same. I’ll gladly
pull in new features and bug fixes and release them to the main
[Todoly.net](http://todoly.net) website as well.

Where to now?
-------------

I have a number of features I would like to add to the application such
as task reordering, making a better homepage and making some tweaks to
clean up the UI a little more. I probably wont get to those until it
becomes a problem with my everyday use.

Until then I’m going to start working on a native iPhone application
that talks to [Todoly](http://todoly.net). I fixed up the styling the
other day so that it works pretty well in Safari on the iPhone but going
with the same premise for the [Todoly](http://todoly.net) web
application, I want to actually finish and release an iPhone app. I’ve
already started and the source will also go up on GitHub once I make a
little more progress. I’m also going to try and make it so you can point
the iPhone application to a different url for it’s data, so if you want
to run your own [Todoly](http://todoly.net) somewhere else or run
[glongmans version](http://github.com/glongman/node-todo) it should
“Just Work” ™ with those backends.

I’m also curious about making a Rails app an Oauth2 provider so I might
build this into [Todoly](http://todoly.net) to start playing around with
that. There doesn’t seem to be a whole lot of up to date information on
doing this so it would be nice to get a good example or even extract a
gem out of the work.

Anyways, that’s all I have to say about [Todoly](http://todoly.net) at
the moment. Please check it out and let me know what you think, either
in the comments here or by sending me an email at jduff@todoly.net.
