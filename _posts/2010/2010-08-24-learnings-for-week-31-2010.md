---
layout: post
title: "Learnings for Week 31 2010"
tags: [programming, learnings, jquery, homebrew, json, wireit, carrierwave]
author_name: John Duff
author_uri: http://twitter.com/johnduff
---

Here’s my learnings from a couple weeks ago.

-   [jQAPI](http://www.jqapi.com/) - alternate location for JQuery
    documentation. Also provides offline versions you can download as
    [HMTL](http://www.jqapi.com/jqapi-latest.zip) or an [Adobe Air
    application](http://github.com/downloads/erikzaadi/jqapi/jQAPI-1.4.2.air?v=11072010).

<!-- -->

-   [Homebrew](http://mxcl.github.com/homebrew/) is a package manager
    for OS X. Packages are defined by formulas that are simple Ruby
    scripts which is stored in Git underneath.

<!-- -->

-   Older browsers [do not have a native JSON
    parser](http://stackoverflow.com/questions/1364842/json-is-not-defined-chrome)
    but this can be patched with <a href="http://www.JSON.org/js.html">
    a little bit of javascript from json.org</a>. We ran into this when
    working with
    <a href="http://javascript.neyric.com/wireit/">WireIt</a> which does
    include the <a href="http://developer.yahoo.com/yui/json/">Yahoo
    JSON parser</a>, but doesn’t actually use it everywhere. Adding in
    the version from json.org works as a stopgap before digging through
    all of WireIt.

* Ran into an issue calling to_json on a an object that has a carrierwave attachment and have <a href="http://github.com/jnicklas/carrierwave/issues/closed#issue/41">commented on an issue for it</a>. I am running Rails3 RC2 and using FileSystem storage. To get around this I'm simply excluding the file attachment from the to_json:{% highlight ruby %}
recipe.to_json(:except=>:photo)
{% endhighlight %}
