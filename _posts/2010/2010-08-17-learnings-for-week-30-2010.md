---
layout: post
title: "Learnings for Week 30 2010"
tags: [programming, learnings, javascript, rails, css, paypal]
author_name: John Duff
author_uri: http://twitter.com/johnduff
---

Well, I’ve been slacking again, here’s the learnings from a couple weeks
ago.

* IE must "haveLayout for opacity":http://joseph.randomnetworks.com/archives/2006/08/16/css-opacity-in-internet-explorer-ie/ (alpha filter) to work. You can use the IE zoom rule to give an element layout if needed:{% highlight css %}
zoom: 1;
{% endhighlight %}

* To add custom Date/Time formats in Rails:{% highlight ruby %}
Time::DATE_FORMATS.merge!(:article => "%A, %B %d, %Y")
Date::DATE_FORMATS.merge!(:article => "%A, %B %d, %Y")
{% endhighlight %}
Don't forget to add your custom formats to Date as well, they use a different hash. This can then be used like so:{% highlight ruby %}
Date.today.to_s(:article)
{% endhighlight %}

* When using Paypal buttons you can change the Currency that is used by "adding a hidden field":https://www.paypal.com/us/cgi-bin/webscr?cmd=p/sell/mc/mc_wa-outside:{% highlight html %}
<input type="hidden" name="currency_code" value="CAD">
{% endhighlight %}

* The Rails Request object has a number of useful methods for "finding the url that was used for the request":http://programming-tut.blogspot.com/2010/06/ruby-on-rails-request-url.html:{% highlight ruby %}
request.host_with_port => example.com:3000
request.path           => /controller/action
request.url            => http://example.com:3000/controller/action
{% endhighlight %}
