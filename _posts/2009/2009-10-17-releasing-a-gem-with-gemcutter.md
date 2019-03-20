---
layout: post
title: Releasing a Gem with Gemcutter
tags: [programming, ruby, gem, tmdb_party]
author_name: John
author_uri: http://twitter.com/johnduff
---

The other day [Jon Maddox](http://github.com/maddox) sent me a message
on Github to see if I was thinking of putting my gem
[tmdb\_party](http://github.com/jduff/tmdb_party) up on
[Gemcutter](http://gemcutter.org/), the new RubyGem host on the block.
At the time I hadn’t really thought much about doing this thought what
the heck? It didn’t seem like it was too difficult so I thought I’d put
it to the test around midnight on a Saturday night.

Well, I have got to say, this was probably the easiest thing I’ve ever
done. I was going into this thinking it wouldn’t be too difficult but I
was still impressed with how it went.

1.  The first step is to sign up for a Gemcutter account [right
    here](http://gemcutter.org/session/new) which takes about 10
    seconds.
2.  The next step is to update your Jeweler Rakefile to add the
    Gemcutter task. I’ve included a sample of what my Rakefile looks
    like below.  
    !include tomd-include-0.txt
3.  Now all you need to do is push your gem the new task and provide
    your Gemcutter credentials  
    !include tomd-include-1.txt

That’s it, now my tmdb\_party gem is [up on
Gemcutter](http://gemcutter.org/gems/tmdb_party). On a side note, if
you’re not using [Jeweler](http://github.com/technicalpickles/jeweler/)
to manage and release your gems you really should, it makes releasing a
gem incredibly simple.

Now go put your gems up on [Gemcutter](http://gemcutter.org/)!

<i>update:  
[Jon](http://github.com/maddox) just reminded me that if you don’t want
to add the Jeweler task it’s still just one simple command to release
your gem:

{% highlight bash %}
gem push pkg/tmdb_party_0.4.0.gem
{% endhighlight %}

Boom! Released! Thanks for the reminder Jon!</i>
