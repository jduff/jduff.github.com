---
layout: post
title: "Learnings for Week 33 2010"
tags: [programming, learnings, mail, git]
author_name: John Duff
author_uri: http://twitter.com/johnduff
---

* If you want to test that that an exception is raised and then test the message that is easily accomplished with assert_raise:{% highlight ruby %}
exception = assert_raise ArgumentError do
  #something
end
assert_match /something/, exception.message
{% endhighlight %}

* If you're working on an older Rails project (pre Rails 2.1)  you will be missing config.gem for Gem dependency management. If you have multiple versions of gems on the machine you can still load a specific version by using rubygems:{% highlight ruby %}
require 'rubygems'
gem 'RedCloth', '~>3.0'
{% endhighlight %}

-   Rails doesn’t check authenticity tokens on GET requests and doesn’t
    ever check them in the functional tests. More info on Rails
    authenticity token
    <a href="http://stackoverflow.com/questions/941594/understand-rails-authenticity-token">here</a>.
