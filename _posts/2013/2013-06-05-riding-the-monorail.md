---
layout: post
title: "Riding the Monorail"
tags: [ruby, rails, monorail]
author_name: John Duff
author_uri: http://twitter.com/johnduff
---

![Monorail](/images/posts/2013-06-05/monorail.jpg "Monorail")

A few months ago I had the amazing opportunity to speak at
[BigRubyConf](http://www.bigrubyconf.com). This is a new ruby conference
all about people doing big things with ruby and it was amazing. It was
great to get together and talk to people who are dealing with the same
or similar problems that we do at [Shopify](http://www.shopify.com) with
running large Rails applications.

One interesting thing I started to notice when talking to all these
developers with applications at a similar scale to
[Shopify](http://www.shopify.com) (code and/or traffic wise) is they
often referred to it as their ‘monorail’. This came up again a couple of
times when I was at [RailsConf](http://www.railsconf.com) as well. This
was a new thing to me and as I talked to more people the meaning of this
term became clearer and clearer.

When people used the term ‘monorail’ they were referring to their
single, core rails application. This is usually the application that the
company started with. This is also the application that they are often
chipping away at to turn into services. This is all well and good, the
interesting part to me was that almost everyone who referred to their
‘monorail’ did so in a negative way. This was the application that was
really hard to deal with, or that they were breaking apart into services
or the code was really complicated and scary.

So, back up a bit, I said we have a similar sized application at
[Shopify](http://www.shopify.com) but we don’t refer to it as our
‘monorail’. We have a few services around it, supplementary apps etc,
but still we don’t call the largest of them a ‘monorail’. What do we
call it? It is ‘Shopify Core’. Another interesting point is we don’t
refer to ‘Shopify Core’ in a negative way, I am extremely proud of this
application and the code that it holds. I tell all developers, even non
developers, that this holds the answers to all the questions you may
have about [Shopify](http://www.shopify.com) or how to do just about
anything in Ruby or Rails. “Chances are the problem you are trying to
solve has been solved in Shopify Core”. Since
[Shopify](http://www.shopify.com) has been in development for almost a
decade, started even before version 1.0 of Rails, then it is likely the
git history holds the solution to most Ruby / Rails problems in ANY
version of Rails. I find this incredible.

I guess the big question to ask is why do we look at Shopify Core so
differently? I would imagine the applications have a similar amount of
code and complexity, what makes us different? I think a big part of this
is the fact that [Shopify](http://www.shopify.com) has been built and is
still being driven by a team that holds a lot of value in writing
quality code. We even recently started a rotating team of developers
where when you are on that team your mandate is to reduce technical debt
and improve the quality of the code base. This is time when we don’t
work on features and make the code base better. Awesome.

Now, we’re not all magical developers that write perfect code. Far from
it. I think the difference is that we are able to and encouraged to go
back and improve things. I’ve heard Tobi talk often enough about how
while he was learning to program his mentor would often rip apart his
code and ask him to throw it away and write it again. This leads you to
not being tied to the code you write; it’s just a tool to get a task
done. This is a concept that Tobi and the rest of the team tries to
ingrain in developers. Once you get this it is much easier to throw away
a piece of code and rewrite it. It also helps that the core development
team that wrote most of the code that [Shopify](http://www.shopify.com)
launched with is still at the company.

Do I have a good answer for why we look at Shopify Core differently? Not
really. I have no concrete reason for why look at our core code base so
differently than other companies. It might have to do with the focus on
quality, or maybe not being tied to the code you write. It might be the
type of people we hire, or the culture of the company itself, I really
don’t know. To be honest it doesn’t matter to me that much; I’m happy
that I work on a code base that I can be proud of and that I enjoy
working with everyday, that’s all that really matter to me.
