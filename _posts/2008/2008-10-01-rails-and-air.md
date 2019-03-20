---
layout: post
title: Rails and Air
tags: [programming]
author_name: John
author_uri: http://twitter.com/johnduff
---

<p>

As I said last time I've started playing around with Adobe Air, what I'm
doing is a little Rails app with a Air desktop app written in Flex 3. 
For the Rails portion I'm going with the standard REST actions with
responses for html and xml.  The Air application then uses the REST api
to communicate with the back end.  Everything is pretty straight
forward, but getting flex to play nice was kind of frustrating.

</p>
<p>

The main problem was getting rails to accept the requests.  I started
out with something like this:

</p>

{% highlight as3 %}
  var service:HTTPService = new HTTPService();
  service.url = 'http://localhost:3000/sessions';
  service.addEventListener(ResultEvent.RESULT, complete);
  service.send({login:'user',password:'password'});
{% endhighlight %}

<p>

The first problem I ran into with this is that Rails was ignoring the
requests and kept giving me a ActionController::InvalidAuthenticityToken
error.  It took a little googling but I finally tracked it down to the
CRSF protection in Rails 2; basically all forms submitted required a
auth token to be sent with the data to validate  the form was generated
by the server it is being submitted to.  This is only required for HTML
forms being submitted, if the content-type is something else (like xml
for my api services) the Authenticity Token is not required.

</p>
<p>

Once I got that figured out the requests were making it a little bit
further but still getting hung up.  This time it was the xml parsing
saying I was trying to add a second root node to the xml.  This was
pretty obvious, I was passing login and password without being wrapped
in anything, a couple little changes and this is where I'm at:

</p>

{% highlight as3 %}
    var service:HTTPService = new HTTPService();
    service.method = 'POST';
    service.url = 'http://localhost:3000/sessions';
    service.contentType = HTTPService.CONTENT_TYPE_XML;
    service.addEventListener(ResultEvent.RESULT, complete);
    service.send({session:{login:'user',password:'password'}});
{% endhighlight %}

<p>

A little change on the server so it looks for the login and password
within the session object and off to the races.  Well, sort of.  You
might notice that I slipped in that service.method = "POST&quot;;
HTTPService supports POST, GET, PUT, DELETE etc for the method.  This
was great so I banged out another method for logging out, basically the
same as the previous one but with service.method = "DELETE&quot;.  This
lead to a couple hours of debugging, googling and cURLing to try and
figure out why logging out wasn't working.  Long story short, the only
type of requests HTTPService actually does is POST and GET, no matter
what you set the service method to.  So, reach back and pull out the
hacks to come up with this for the logout action url:

</p>

{% highlight as3 %}
    service.url = 'http://localhost:3000/sessions?_method=DELETE';
{% endhighlight %}

<p>

Now Rails can pick that out and knows that I'm trying to do a delete and
routes the request correctly.  Now that I'm rolling it's easy to keep
defining service objects and making calls to my Rails server but it's
becoming clear that a lot of this can be abstracted away.  In my next
post I'll talk about how I've started designing that abstraction and how
it's going.

</p>
