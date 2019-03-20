---
layout: post
title: "mySQL, Rails and OS X Fun"
tags: [programming, mysql, ruby, rails, osx]
author_name: John
author_uri: http://twitter.com/johnduff
---

In the last little while I started working on a Rails project that had
been targeting an older version of mySQL. I ran into a few confusing
problems while getting started so I thought I’d bring together all the
various mySQL and Rails related info I came across to fix my problems
into one place.

### Problem: ActiveRecord failing with a default field value of blank

This is a problem that a few people have posted on
[ruby-forum](http://www.ruby-forum.com/topic/197243) without getting
much of a response, but what is there pointed me in the right direction.
The main problem is that older versions of mySQL (pre 5.0.45 I believe)
treat a NULL value inserted into a string column as a blank string.
Newer versions of mySQL fix this issue but this fix causes some
confusing behaviour.

What happens in the older version is maybe you forget to pass a value
for that NOT NULL string; mySQL happily treats that as a blank string
and gives you no errors. When you upgrade mySQL to a version that
‘fixes’ this you end up with all kinds of errors because the constraint
isn’t being met anymore.

#### Solution

Well, if you don’t actually need the constraint remove it, otherwise
explicitly send a value so the constraint is met. Update your tests and
validations so you’re passing and checking that the correct values are
being passed.

### Problem: Error: uninitialized constant MysqlCompat::MysqlRes

Another one that also shows up on a [ruby forum
post](http://www.ruby-forum.com/topic/192550). The root of this problem
is that on OS X the mysql gem has to be told where the installed mySQL
libraries are and which architecture your machine is.

#### Solution

I found the solution
[here](http://wonko.com/post/how-to-install-the-mysqlruby-gem-on-mac-os-x-leopard)
but had to modify the gem install slightly for my 64 bit machine.

{% highlight bash %}
  sudo env ARCHFLAGS="-arch x86_64" gem install mysql -- \
    --with-mysql-dir=/usr/local/mysql --with-mysql-lib=/usr/local/mysql/lib \
    --with-mysql-include=/usr/local/mysql/include
  
{% endhighlight %}

This might be slightly different depending on where mysql ended up on
your machine and your machines architecture.

### Problem: mySQL can’t install because a newer version exists

Or, removing mySQL for real. While dealing with my first problem I tried
installing and uninstalling different versions of mySQL along the way
the mySQL install got angry because some files weren’t removed and
wouldn’t install the version I wanted.

#### Solution

I managed to get mySQL off my machine by combining the approaches from a
[blog
post](http://akrabat.com/2008/09/11/uninstalling-mysql-on-mac-os-x-leopard/)
and an answer found on [Stack
Overflow](http://stackoverflow.com/questions/1436425/how-do-you-uninstall-mysql-from-mac-os-x/1447758#1447758).
Before doing this I did run the mySQL uninstaller, but it seems to leave
some goodies behind.

In the end it boiled down to running the following commands:

{% highlight bash %}
  sudo rm /usr/local/mysql
  sudo rm -rf /usr/local/mysql*
  sudo rm -rf /Library/StartupItems/MySQLCOM
  sudo rm -rf /Library/PreferencePanes/My*
  edit /etc/hostconfig and removed the line MYSQLCOM=-YES-
  rm -rf ~/Library/PreferencePanes/My*
  sudo rm -rf /Library/Receipts/mysql*
  sudo rm -rf /Library/Receipts/MySQL*
  sudo rm -rf /var/db/receipts/com.mysql.*
{% endhighlight %}

I know it’s a lot of mumbo jumbo, but mySQL seems to hook itself in all
over the place and this, in the end, did seem to get rid of everything.

### Conclusion

Well, that’s all I’ve got for mySQL right now. It was a pretty
frustrating trip, but in the end I managed to find a solution to all the
problems and now it’s all in one place for all of time.

As a side note I’m really starting to find [Stack
Overflow](http://stackoverflow.com) to be an incredibly useful resource.
Sometimes it might even save time trying a quick search there before
hitting up Google.
