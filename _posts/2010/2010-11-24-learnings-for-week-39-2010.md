---
layout: post
title: "Learnings for Week 39 2010"
tags: [programming, learnings, git, ssh, rails3, testing]
author_name: John Duff
author_uri: http://twitter.com/johnduff
---

* If you need to access Git on a remote machine and can't add an ssh key from that machine to the server adding a few options to the .ssh/config should do the trick:{% highlight bash %}
User jduff
Host git.server.com
{% endhighlight %}If you then ssh to the machine passing the -A option (to forward the agent) git should work perfectly.

-   In windows Run =\> \\\\tsclient (Terminal Server Client) will list
    network drives

<!-- -->

-   With Rails 3 unobtrusive Javascript (using
    <a href='http://github.com/rails/jquery-ujs'>jquery-ujs</a>) adding
    ‘data-remote=true’ and ‘action=URL’ attributes any input element can
    be made to do an ajax request without any extra work.

<!-- -->

-   <a href='http://github.com/tomas-stefano/infinity_test'>infinity\_test</a>
    is an alternative to
    <a href='http://ph7spot.com/musings/getting-started-with-autotest'>Autotest</a>
    that uses <a href='http://github.com/mynyml/watchr'>Watchr</a> and
    <a href='http://rvm.beginrescueend.com'>RVM</a> allowing you to
    easily run your tests against multiple rubies at once.
