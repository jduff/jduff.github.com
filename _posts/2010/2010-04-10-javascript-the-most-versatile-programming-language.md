---
layout: post
title: "JavaScript: The Most Versatile Programming Language"
tags: [programming, javascript]
author_name: John Duff
author_uri: http://twitter.com/johnduff
---

I’ve been spending quite a bit of time programming JavaScript lately,
not only using [jQuery](http://jquery.com/) and writing simple jQuery
plugins but also building some ‘classes’ to organize the larger
application code. As I’ve been going I’ve been trying to learn how to
really write javascript well, following best practices and using
[JavaScript programming
patterns](http://www.klauskomenda.com/code/javascript-programming-patterns/#module)
as much as possible. I’ve been blown away with how versatile JavaScript
really is.

You can see examples of just how powerful the language is by looking at
some of the popular JavaScript frameworks that are out there and just
how differently they do things.

Take this extremely simple piece of [jQuery](http://jquery.com/) code:

{% highlight javascript %}
  $('#my-div').addClass('awesome');
{% endhighlight %}

Have you ever thought about how this works? The first bit,
*$(’\#my-div’)*, is selecting your element from the DOM using jQuerys
CSS selector engine [Sizzle](http://github.com/jeresig/sizzle). What you
get back is a DOM element that is wrapped by a jQuery object. You can
then call any jQuery method or methods added by plugins on this object,
such as the *addClass* method. The method then manipulates the DOM
element or whatever the method is supposed to be doing (in this case
adding the class ‘awesome’).

Now lets contrast this with how the same thing would work with
[Prototype](http://www.prototypejs.org/).

{% highlight javascript %}
  $('my-div').addClassName('awesome');
{% endhighlight %}

This code looks very similar to how we did things with
[jQuery](http://jquery.com/) but underneath the behaviour is very
different. Again *$(’my-div’)* is selecting the element from the DOM but
with [Prototype](http://www.prototypejs.org/) you get back the actual
DOM element, not an object wrapped by something else. All the
[Prototype](http://www.prototypejs.org/) methods have been added
directly onto the objects that they are intended for (Array methods
added to the Array object, DOM methods added to DOM objects etc). When
you call *addClassName* it is being called on the DOM element itself and
adding the class ‘awesome’.

I find this to be pretty amazing. The code you write is basically the
same but the underlying way the framework goes about implementing the
behaviour is so very different. [jQuery](http://jquery.com/) is all
about augmenting the elements and adding the behaviour you when you make
the method calls. [Prototype](http://www.prototypejs.org/) on the other
hand has extended the JavaScript language and objects as soon as you
load it into the page. Two very different approaches to solving the same
problem.

This has just been a little peak into the different approaches you can
take to solving problems with JavaScript. I highly recommend trying out
a different framework than you normally use and seeing how they do
things, it will open your eyes to solutions you might never have thought
of before.
