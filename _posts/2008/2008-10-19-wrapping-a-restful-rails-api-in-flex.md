---
layout: post
title: Wrapping a RESTful Rails API in FLEX
tags: [programming]
author_name: John
author_uri: http://twitter.com/johnduff
---

<p>

A little while back I was talking about getting started with
<a href="/2008/10/01/rails-and-air/">writing an Air app in flex that
talks to a Rails backend</a> and some of the troubles I was having. 
I've been working on and off trying to fine tune what I started out with
and turn it into a set of base classes for wrapping a restful api (based
on the rails conventions).  I've finally got something, it's not ideal
and it's really not how I would have liked he design to turn out, but
it's better than anything I've come up with along the way.

</p>
<p>

I'll start out with how I would have like this little framework to have
turned out.  What I was really looking for was a couple of base classes
that defined the basic REST actions as well as some unifying way to
dispatch and listen for events on the api.

</p>
<p>

The second problem, 'event management' I guess, wasn't too hard to
solve, I created a Singleton (sort of, AS3 doesn't really let you do
this, but you can kind of fake it) that extended from EventDispatcher
and then added and made dispatch calls on the instance.  My class making
the REST calls now needed to know about this 'Controller' class to be
able to do the event dispatching, it also made sense to define the
endpoint url here.

</p>
<p>

Now, the main problem I was trying to solve, having a base class to
define the REST calls, kept giving me trouble.  At first defining
instance methods for create, destroy, etc made sense but then as I
started using the class having create as an instance method really
didn't make sense; create is building the object instance and should be
a static class method.  This is where my trouble started, since create
(and get) actions should be static, if I wanted to define the logic in
the base class then my subclass would still need to provide a wrapping
method, or I'd be calling something like
Base.create("object\_type&quot;) everywhere, which didn't really seem
right to me.  This lead me down a long road of messing this reflection
classes, and introspection methods (which are awful in AS3 in my
opinion) causing a lot of ugly code and me to become frustrated with my
solution.

</p>
<p>

After messing about like this for three separate coding sessions I had
enough and decided to get back to what it needs to do; blew away the
base classes and brought everything into the main class (for now this
was the Session) and structured things the way I wanted it to look for a
client of the api.  Once I got things working again it was again obvious
that some things could be abstracted away, but I still have the problem
that some api calls should be static and some not; which would pull me
into the same mess as before with a base class.

</p>
<p>

So, Instead of doing that I created an object that wrapped up all the
rest services into a single package then I created a static instance
variable of this 'ResourceHandler' inside my Session class and delegated
the work to it.  Now, this isn't as easy as extending from a class and
overriding a couple of methods, but it does hide away all the
HTTPService definitions, adding and removing event listeners, and other
redundancies from the classes.

</p>
<p>

I still think there should be a cleaner way to do some of this in AS3,
maybe I just don't know the language well enough though.  Part way
through I did find another framework that was trying to implement
<a href="http://code.google.com/p/as3-active-resource/">ActiveResource
in AS3</a>, but the project doesn't look very active anymore.  I'll post
a little walkthrough of how the classes work in a bit, it's still not
complete yet but if you want to take a look at the code in the meantime
leave a comment.

</p>
