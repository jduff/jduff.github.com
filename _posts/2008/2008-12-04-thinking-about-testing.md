---
layout: post
title: Thinking about Testing
tags: [programming]
author_name: John
author_uri: http://twitter.com/johnduff
---

<p>

I've always been a big fan of including tests for any of the code I
write.  It was beaten into us in university, made sense when using
<a href="http://www.junit.org/">JUnit</a> and made easy in ruby with
<a href="http://www.ruby-doc.org/stdlib/libdoc/test/unit/rdoc/classes/Test/Unit.html">Test::Unit</a>. 
Sometimes I still get annoyed when writing tests though.  I've been
thinking about testing a little more than usual the last couple of
weeks, mostly about what bothers me when writings tests.  I hate writing
brittle tests.  I do my best to avoid this, but sometimes in a large
project when you're trying to test everything it becomes difficult.  The
other thing I really hate is trying to test everything.  I know, I know,
<a href="http://en.wikipedia.org/wiki/Code_coverage">code coverage</a>
is a good thing, but what good does 100% code coverage do your customers
or users?  Does it make the app suck less?  Well, I suppose it could,
but isn't it possible that 95% or even 80% coverage would be just as
good (for the users), depending on what was tested?  I'd say it's very
possible.

</p>
<p>

To get around my first annoyance, the brittle tests, I've started
creating the objects that I need in the test itself instead of using
fixtures (this is <a href="http://rubyonrails.com/">rails</a>).  This
lets me build up the objects for my test without worrying that adding
another fixture will break existing tests.  This works alright for unit
tests and smaller scenarios, but creates a bunch of duplicate code when
a number of tests use objects that are setup in a similar manner
(refactoring the setup into methods helps with this, but the tests get
confusing as you need to jump around methods).

</p>
<p>

Next problem, I want to write tests for things that need to be tested,
not some far off situation that I think could happen.  In Jamis Bucks
talk at RubyConf,
<a href="http://rubyconf2008.confreaks.com/recovering-from-enterprise.html">Recovering
from Enterprise</a>, he said that you should "<em>code just in time, not
just in case…there's no excuse to sit and play what if games</em>".  I
feel exactly the same way.  Now, I've been thinking over this for a
couple days, doing some reading and whatnot and have decided (hope!)
that RSpec will be my savior.  From the
<a href="http://rspec.info/">rspec.info</a> site, "<em>Rspec is a
Behavior Driven Development
(<a href="http://en.wikipedia.org/wiki/Behavior_driven_development">BDD</a>)
framework for Ruby</em>".  The way it works is you write
'specifications' (specs) that define how the system should behave.  By
writing he specs first and then writing the implementation methods
afterward you are building, and testing, the system as it should behave;
you're not testing arbitrary situations that probably wont occur. 
Writing tests first and implementation code afterwords also has a neat
catch phrase, Test Driven Development
(<a href="http://en.wikipedia.org/wiki/Test-driven_development">TDD</a>). 
RSpec allows you to nest scenarios as well which helps me with the first
problem I was having as I could build up the context of the test suite
as I went, reusing the earlier setup if I wanted.

</p>
<p>

So far I've done a lot of reading and have written a few specs, but
really haven't scratched the surface of what RSpec has to offer.  I'm
not sure if this will solve all my testing woes, but it's defiantly
making me think and test a bit differently, which I like.

</p>
