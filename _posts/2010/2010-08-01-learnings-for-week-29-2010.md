---
layout: post
title: "Learnings for Week 29 2010"
tags: [programming, learnings, javascript, rails, virtualbox, css, oracle]
author_name: John Duff
author_uri: http://twitter.com/johnduff
---

This past week I had learnings all over the place; javascript, rails,
oracle, css and probably more that I’ve already forgotten.

* Interesting post by Remy Sharp on "Throttling Javascript Function Calls":http://remysharp.com/2010/07/21/throttling-function-calls/ {% highlight javascript %}
function throttle(fn, delay) {
  var timer = null;
  return function () {
    var context = this, args = arguments;
    clearTimeout(timer);
    timer = setTimeout(function () {
      fn.apply(context, args);
    }, delay);
  };
}
{% endhighlight %}
Usage: {% highlight javascript %}
$('input.username').keypress(throttle(function (event) {
  // do the Ajax request
}, 250));
{% endhighlight %}
This will require there to be 250ms between a keypress before it will
execute the given function. Useful for things like Autocomplete where
you don’t want an AJAX request to fire until the person stops typing.

-   To access the Host machine from a VirtualBox Windows VM
    ‘\\\\vboxsvr\\share’ . You can also turn on Windows filesharing and
    access the VM from the Host.

<!-- -->

-   When Rails (as of 2.3.5) runs the ‘environment’ Rake task it sets
    the global variable $rails\_rake\_task = true. Since most tasks
    depend on the environment you can use this to do slightly different
    behavior if your code is running within a Rake task.

<!-- -->

-   Oracle DB [treats blank strings in VARCHAR/VARCHAR2 columns as
    NULL](http://stackoverflow.com/questions/203493/why-does-oracle-9i-treat-an-empty-string-as-null)

* IE has a property 'hasLayout' that determines "how to draw and bound elements":http://www.satzansatz.de/cssd/onhavinglayout.html. Some elements "have layout by default":http://www.satzansatz.de/cssd/onhavinglayout.html#wherefrom and others do not. Sometimes when an element does not have layout you can see odd behavior, like lists being numbered incorrectly or margins collapsing. To fix this you can "add certain css properties":http://www.satzansatz.de/cssd/onhavinglayout.html#prop to elements so that they will gain layout. {% highlight css %}
.element {
  height:1%;
}
{% endhighlight %}
Height is a property that will have an element gain layout but sometimes
you might still want the element to auto expand. Setting the height to
1% will give the element layout as well as allowing it to expand with
its content. This is known as the Holly Hack. \*\*Note: hasLayout may
not be an issue anymore as of IE8.
