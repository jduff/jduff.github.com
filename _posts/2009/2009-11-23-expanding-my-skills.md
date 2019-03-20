---
layout: post
title: "Expanding my Skills"
tags: [programming, random, skills, javascript]
author_name: John
author_uri: http://twitter.com/johnduff
---

In the last couple months I’ve been thinking a bit about expanding the
skills I have into some different areas. I’ve been working with Ruby on
Rails almost exclusively for over three years and have gotten to know
the ins and outs pretty well. I love Ruby and Rails, but I’m getting
that itch to play with something new. I’ve been playing around with
iPhone development a bit (though I’ve been slacking) and find that to be
really interesting, but I decided the other day to try something
different to fill this need (I will continue to play with iPhone stuff,
it’s just too cool to let go).

Javascript will be my next conquest. Writing Javascript with
[jQuery](http://jquery.com/) to be exact. I’ve had my love for
[jQuery](http://jquery.com/) reignited and it complements the other web
development skills I already have. I’d like to think I’m already pretty
good with [jQuery](http://jquery.com/), I’ve been using it for various
projects for awhile now, but my goal is to learn it in and out; all the
best practices and neat tricks as well as the limitations and how to
overcome them.

To do this I’m going to start out by trying my hand at writing a few
[jQuery plugins](http://docs.jquery.com/Plugins/Authoring) of my own and
try to integrate jQuery into any work I might be doing. To start out
I’ve been reading a few blogs and have come across a [really great
plugin
pattern](http://www.learningjquery.com/2007/10/a-plugin-development-pattern)
that I’m going to follow for most of my stuff.

### jQuery Plugin Pattern: Giving it jQuery

First thing we want to start with is giving our plugin access to jQuery.
This sounds like a no brainer but you have to be careful since the
jQuery helper method ($) can be redefined and therefore isn’t guaranteed
to exist. To overcome this the pattern below is usually used.

{% highlight javascript %}
(function($) {
  // plugin code here
})(jQuery);
{% endhighlight %}

This might look a little scary, but all we’re doing is defining a
function that takes a parameter. We’re then calling the function right
away passing in jQuery. Now we can use $ in our plugin without worry!

### Playing Nice: Returning jQuery

When using a jQuery plugin there are a couple of things that users come
to expect. The two main things is that the plugin should be able to work
on an array of objects and at the end it should return the jQuery object
to allow chain ability. Accomplishing this is very easy with the code
below.

{% highlight javascript %}
(function($) {
    // define the plugin
    $.fn.template = function(options) {
        // iterate through the matched elements
        // returning this at the end
        return this.each(function() {
          // plugin logic here
        });
    };
})(jQuery);
{% endhighlight %}

### Giving the User Control: Plugin Options and Defaults

The next thing we’re going to want to give our plugins is a way for the
user to pass in options to override the defaults. I also like the way
the [jQuery UI plugins](http://jqueryui.com/) give you public access to
the defaults so that you can set them once instead of every time the
plugin is called. [Learning
jQuery](http://www.learningjquery.com/2007/10/a-plugin-development-pattern)
has some code to do just that and looks something like what I have
below.

{% highlight javascript %}
(function($) {
  // define the plugin
  $.fn.template = function(options) {
    // extend the default options with those provided
    // extending an empty object prevents overriding of 
    // our defaults object
    var opts = $.extend({}, $.fn.template.defaults, options);
    
    // ...
  };
  
  // plugin defaults
  $.fn.template.defaults = {
    color: 'red'
  };
})(jQuery);
{% endhighlight %}

This code lets our plugin users do a couple interesting things. First
thing is they can pass options to plugin like below.

{% highlight javascript %}
  $('h1').template( { color: 'black' } )
{% endhighlight %}

What is more interesting is the fact that instead of having to pass the
same options in every time they could set the defaults at the start and
be done with it, only passing in options that differ from their own
defaults.

{% highlight javascript %}
  $.fn.template.defaults.color = 'black';
  $('h1').template(); // plugin default color is black
  
  $('h1').template( { color: 'orange' } ); // override the defaults
{% endhighlight %}

This gives the users a lot of flexibility and helps them to keep their
code nice and
[DRY](http://en.wikipedia.org/wiki/Don%27t_repeat_yourself).

### Giving the User Control: Exposing Public Functions

Sometimes it makes sense to expose plugin functions to the user so that
they can override the implementation with their own. This might not be
needed for all plugins, but I think it would be useful for most.

{% highlight javascript %}
  // ...
    return this.each(function() {
      // use the helper function
      var something = $.fn.template.helper();
      
      // plugin logic here
    });
  };
  
  // public helper function that can be overridden by the user
  $.fn.template.helper = function () {
    // do something that helps
  };
  // ...
{% endhighlight %}

This gives the user a lot of control over how the plugin behaves. Again,
it doesn’t make sense for all plugins but when sometimes it can be a
real life saver. All the user has to do to provide their own
implementation to the helper function is to redefine it like below.

{% highlight javascript %}
  $.fn.template.helper = function () {
    // do something different
  }
{% endhighlight %}

The big benefit to this that I see over having a callback is that you
could save the original function and use it in your implementation,
something like this.

{% highlight javascript %}
  var helper = $.fn.template.helper;
  $.fn.template.helper = function () {
    var results = helper();
    // do something different with the results
  }
{% endhighlight %}

This lets you build upon the original implementation if you want to,
meaning less repeated code.

### Wrapping Up

Well, that pretty much does it for how I want my jQuery plugins to be
structured. I’ve left out a bunch of stuff that beginners should
probably take a look at,
[these](http://www.learningjquery.com/2007/10/a-plugin-development-pattern)
[links](http://docs.jquery.com/Plugins/Authoring) should help if you’re
interested.

I’ve got the full template below and I’ve also put it up on
[Github](http://github.com/jduff/jquery-plugin-template) with a few more
comments, feel free to fork it and send me updates.

{% highlight javascript %}
(function($) {
  // define the plugin
  $.fn.template = function(options) {
    // extend the default options with those provided
    // extending an empty object prevents overriding 
    // of our defaults object
    var opts = $.extend({}, $.fn.template.defaults, options);
    
    // iterate through the matched elements
    // returning this at the end
    return this.each(function() {
      // use the helper function
      var something = $.fn.template.helper();
      
      // plugin logic here
    });
  };
  
  // public helper function that can be overridden by the user
  $.fn.template.helper = function () {
    // do something that helps
  };
  
  // plugin defaults
  $.fn.template.defaults = {
    color: 'red'
  };
})(jQuery);
{% endhighlight %}
