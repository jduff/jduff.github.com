---
layout: post
title: "Learnings for Week 36 2010"
tags: [programming, learnings, terminal, photos, irb, ruby, rails]
author_name: John Duff
author_uri: http://twitter.com/johnduff
---

-   Google provides some modern
    <a href='http://code.google.com/webfonts'>webfonts</a> that anyone
    can use through their
    <a href='http://code.google.com/apis/webfonts/docs/getting_started.html'>font
    api</a>.

<!-- -->

-   SQL Authentication can be turned on for SQL Server through the
    Management Console under the Server Properties. More details can be
    found
    <a href='http://kbase.gfi.com/showarticle.asp?id=KBID002804'>here</a>.

* Using the "Facebooker2":http://github.com/mmangino/facebooker2 gem you must call 'fetch' on the Facebook user to get their user details.{% highlight ruby %}
current_facebook_user.fetch
{% endhighlight %}

* Posting to a users feed is really easy with "Facebooker2":http://github.com/mmangino/facebooker2{% highlight ruby %}
current_facebook_user.feed_create(Mogli::Post.new(:message=>message))
{% endhighlight %}

-   You can prevent Parallels from automatically switching to Coherence
    mode by changing the Startup View in Startup and Shutdown options
    for the VM. More details
    <a href='http://download.parallels.com/desktop/v5/docs/en/Parallels_Desktop_Users_Guide/26728.htm'>here</a>.

<!-- -->

-   Came across an article with
    <a href='http://www.queness.com/post/402/15-css-tips-and-tricks'>15
    CSS Tips and Tricks</a> that a had a few interesting points (IE6 PNG
    with filters) that I hadn’t known about.

<!-- -->

-   Rails 3 respond\_with calls as\_json on objects when returning a
    json response instead of to\_json

* Rails 3 respond_with returns " " on successful update or delete calls. jQuery has trouble parsing this as json so always fails. On the jQuery side this can be fixed by adding this line (I came up with this based some of the suggestions in <a href='http://www.kreusch.com.br/2010/03/30/rails-3-responders-jquery-1-4-and-empty-json-results'>this article</a>:{% highlight javascript %}
jQuery.ajaxSetup({ dataFilter: function(data, type){ 
  return (!data || jQuery.trim(data)=="") ? "{}" : data; 
} });
{% endhighlight %}
