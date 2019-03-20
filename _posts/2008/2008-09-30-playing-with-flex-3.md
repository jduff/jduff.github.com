---
layout: post
title: Playing with Flex 3
tags: [programming]
author_name: John
author_uri: http://twitter.com/johnduff
---

<p>

I've started playing around with Adobe Air and Flex 3 again, man is it
annoying sometimes.  I've been programming Ruby for awhile now and
really like it so maybe it's affecting how I look at other languages,
but I'm starting to notice how convoluted and confusing things seem to
be in other languages.  The thing that annoys me around every corner
with Flex (and ActionScript 3) is how heavily the rely on events.  I
understand the event pattern and how useful events can be, but most Flex
code I look at gets very confusing trying to follow all the events
jumping around.  Everything happens with events and listeners; click,
mouse move, service calls, image loaders, url loaders…

</p>
<p>

Why does everything need to happen based on events?  Why can't some
things, like service calls, block until they get a response instead of
fire and forget?  It would make a little more sense if flash was
multi-threaded but it isn't, so if something else starts happening and
holding the runtime up it doesn't matter if you're event gets fired. 
Maybe this is just me, but following from method call, to handler, to
another handler because the last one threw another event is really
annoying.

</p>
<p>

Well, now that I got that rant out of the way I'll start digging in and
trying to fit in with the Flex event based ways.

</p>
