---
layout: post
title: "tmdb_party 0.9.0 Released"
tags: [ruby, gem, movies, tmdb_party]
author_name: John Duff
author_uri: http://twitter.com/johnduff
---

Over the weekend I spent a little bit of time cleaning up some of the
code and adding a few new features to my gem gem for talking to
[themoviedb.org](http://www.themoviedb.org/),
[tmdb\_party](https://github.com/jduff/tmdb_party). If you’ve never
heard of themoviedb.org you should really check it out. It’s a lot like
[IMDB](http://www.imdb.com/) but it is completely user generated and has
an [open api](http://api.themoviedb.org/2.1) that anyone can use.

So, what’s new in 0.9.0? Well, under the covers I did a
[bunch](https://github.com/jduff/tmdb_party/commit/92a4700e83ca34035ce03e65814103135e020f5a)
of
[house](https://github.com/jduff/tmdb_party/commit/bfb1778adae53ad21966bfa3a5cddc6e6f640d9a)
[cleaning](https://github.com/jduff/tmdb_party/commit/87e6d5ee58fe36255cb2f1ab7dc3fce06d97b5f6),
moved some files around and [removed some useless
extensions](https://github.com/jduff/tmdb_party/commit/f76cfaf3903341413524f5ea5353676ad8c53576)
to core classes that were used internally and just cluttering up your
classes. Nothing too special there, but should make the code a lot
easier to understand and maintain.

I also managed to implement two new features that I’m pretty happy
about. The first one is based on some work I noticed in forks by
[willchang](https://github.com/willchang) and
[razielgn](https://github.com/razielgn). They had both implemented the
[Movie.browse](http://api.themoviedb.org/2.1/methods/Movie.browse)
method from the api, but because of my recent changes I couldn’t pull
either of them very cleanly. Since it was a pretty straightforward
change I just added it myself, but kudos to those guys for making me
realize it was missing. Here’s a little example of what you can do with
this new method:

{% highlight ruby %}
tmdb = TMDBParty::Base.new('key')
tmdb.browse({:query=>'Transformers', :rating_min=>3, :min_votes=>3})
{% endhighlight %}

There’s a number of different options, all of which can be found in the
[api docs](http://api.themoviedb.org/2.1/methods/Movie.browse).

The other feature I added is something I find really cool. This comes
from talking to [John Tajima](http://twitter.com/#!/redronin) who told
me about this cool idea of being able to generate a unique hash from a
video file which you can use to identify the video. It turns out that
[themoviedb.org](http://www.themoviedb.org/) api already supports
searching based on the file hashes when using the
[Media.getInfo](http://api.themoviedb.org/2.1/methods/Media.getInfo)
method. So I went ahead and grabbed the [hashing
algorithm](http://trac.opensubtitles.org/projects/opensubtitles/wiki/HashSourceCodes),
made a few changes and [here we
are](https://github.com/jduff/tmdb_party/commit/e1a67bdbd1f003cbb590f6ca9bbfec639616566d).
Here’s how we use it:

{% highlight ruby %}
tmdb = TMDBParty::Base.new('key')
File.open('transformers.avi') do |file|
  info = tmdb.get_file_info(file)
end
{% endhighlight %}

This will generate the hash for the given file and use that in the query
to [Media.getInfo](http://api.themoviedb.org/2.1/methods/Media.getInfo)
returning all the information for whatever movie that might be. Now you
can easily figure out what all those randomly named files on your disk
really are.

The last thing I wanted to point out was some work that
[Mange](https://github.com/Mange) did awhile back adding support for
retrieving results in different languages, lots more tests, person
search and whole bunch more. Almost all of the methods take an optional
final parameter for the language you want your results in:

{% highlight ruby %}
tmdb = TMDBParty::Base.new('key')
tmdb.search('transformers', 'fr')
{% endhighlight %}

So that’s all there is for now, thanks again to everyone who has
contributed to this project with code, ideas, comments and everything
else. If you need help getting started check out the
[readme](https://github.com/jduff/tmdb_party) or give me a shout and
I’ll gladly help you out.
