---
layout: post
title: EC2 Makes Getting a Startup Going Suck Less
tags: [web, tech]
author_name: John
author_uri: http://twitter.com/johnduff
---

<p>

Obviously getting your startup going doesn't suck (well, hopefully not
all the time), but it is a shit load of work.  You need a kick ass idea,
people to build it, a way to distribute, somehow get people to pay for
what you're doing and countless other tasks.  This is a lot to deal
with, and since you're a startup it's probably you or a small team doing
all the work.  Well, if you happen to be building a web based product
<a href="http://aws.amazon.com/ec2/">Amazons EC2</a> platform is
defiantly something to check out.

</p>
<p>

EC2 is Amazons 'Elastic
<a href="http://en.wikipedia.org/wiki/Cloud_computing">Cloud
Computing</a>' platform and it lets you take advantage of Amazons huge
server and computing infrastructure to run your own server instances. 
There are countless advantages to running your application in the cloud
like this, the big ones in my opinion are cost savings as you
<a href="http://aws.amazon.com/ec2/#pricing">pay for what you use</a>,
flexibility in expanding your server farm and the reliability of a
distributed and proven network.

</p>
<p>

This is really cool.  If you think back to a couple of years ago how you
would setup your own infrastructure you'd need to go out and buy some
expensive servers and load balances, get it all setup somewhere  and
then hope the traffic doesn't blow up the machines before you can get
get more in to handle the load.  Now with EC2 you don't need to worry
about the hardware and over purchasing to handle the load or running out
and buying a new machine when one gets fried.

</p>
<p>

Things with EC2 aren't quite perfect yet, but they're not far off and a
lot of the pain points are going to be addressed in the near future
(2009) Amazon says.  From the
<a href="http://aws.typepad.com/aws/2008/10/big-day-for-ec2.html">Amazon
Web Services blog</a>, here's a couple of the things to look forward to:

</p>
<div style="margin-left: 40px;">

<em><strong>Management Console</strong> - The management console will
simplify the process of configuring and operating your applications in
the AWS cloud. You'll be able to get a global picture of your cloud
computing environment using a point-and-click web
interface.<br /><strong>Load Balancing</strong> - The load balancing
service will allow you to balance incoming requests and traffic across
multiple EC2 instances.<br /><strong>Automatic Scaling</strong> - The
auto-scaling service will allow you to grow and shrink your usage of EC2
capacity on demand based on application requirements.<br /><strong>Cloud
Monitoring</strong> - The cloud monitoring service will provide real
time, multi-dimensional monitoring of host resources across any number
of EC2 instances, with the ability to aggregate operational metrics
across instances, Availability Zones, and time slots.<br /></em>

</div>
<p>

<br />Awesomesauce.  Those are the exact things that have been creating
extra work when using their current offering, Amazon is spot on with the
features that their users are really looking for.

</p>
<p>

I really like what Amazon is doing in this space, but if you don't or if
it doesn't do what you need it to there are alternatives. 
<a href="http://code.google.com/appengine/">Google App Engine (GAE)</a>
is one such alternative that looks pretty neat.  It's neat because it's
built by google, on top of their infrastructure and allows easy
integration with existing google services (docs, accounts, etc).  In
it's current state it's nothing compared to EC2. 

</p>
<p>

The biggest difference is that with GAE you're tied to using python for
your application development and you can't really customize the platform
at all.  With EC2 you start with a basic linux (and now windows) that
you can then customize with whatever you want.  But if you don't want to
do all that work, and you're a python kind of person, GAE might be
perfect for you.  I, on the other hand, prefer the flexibility you get
with EC2 and can't wait to see where they go from here.

</p>
<p>

Go out,
<a href="http://docs.amazonwebservices.com/AmazonEC2/gsg/2006-06-26/">get
started</a>.

</p>
