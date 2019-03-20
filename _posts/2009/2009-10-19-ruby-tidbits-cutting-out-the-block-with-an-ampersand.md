---
layout: post
title: "Ruby Tidbits: Cutting out the Block with an &proc"
tags: [ruby tidbits, ruby, programming]
author_name: John
author_uri: http://twitter.com/johnduff
---

I find one of the most useful ‘tricks’ in Ruby is to use the ‘&’
character to convert Ruby Proc objects into a block. What exactly does
this mean? Well, the best way to explain it is with a couple of
examples.

{% highlight ruby %}
words = %w(one two three)
words.collect!{|word| word.upcase }
puts words.inspect
=> ["ONE", "TWO", "THREE"]
{% endhighlight %}

This is a pretty simple block of code, all we’re doing is converting an
array of words to uppercase. Now say we’re good ruby programmers and
want to keep our code readable and concise, how does this stand up?
Well, it is a simple block so it is fairly readable, but how about we
take a look at the same piece of code using the ‘&’ method to convert a
proc into a block.

{% highlight ruby %}
words = %w(one two three)
words.collect!(&:upcase)
puts words.inspect
=> ["ONE", "TWO", "THREE"]
{% endhighlight %}

These two blocks do the exact same thing, but I find the second method
to dramatically improve the readability even in this simple example.

So, what’s really going on here? Well Ruby sees the ‘&’ so it wants to
convert the Proc to a block. Since we have a Symbol on the other side
Ruby type converts it to a proc by calling to\_proc on the Symbol which
returns a Proc that takes one argument and calls the method named by the
symbol on that object. The implementation of to\_proc on the Symbol
class might look something like this:

{% highlight ruby %}
def to_proc(arg)
  Proc.new {|arg| arg.send(self) }
end
{% endhighlight %}

The actual implementation is a little more complicated, allowing
multiple arguments etc, but you get the idea.

You can also use this method with a normal Proc object instead of just
with a Symbol, making something like this possible:

{% highlight ruby %}
numbers = [1,2,3,4]
proc = Proc.new {|num| num*num}
numbers.collect!(&proc)
puts numbers.inspect
=> [1, 4, 9, 16]
{% endhighlight %}

Pretty cool isn’t it? I’ve been using the Symbol technique for awhile
now to keep my code concise and readable, I never even thought about
using a Proc until doing a little bit of research for this article. If
you want to know more about all of this check out [Understanding Ruby
blocks, Procs and
methods](http://eli.thegreenplace.net/2006/04/18/understanding-ruby-blocks-procs-and-methods/)
by Eli Bendersky, I based some of my examples off of his article.
