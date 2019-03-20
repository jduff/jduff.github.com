---
layout: post
title: "Kernel Panic, TimeMachine to the Rescue!"
tags: [programming, learnings, mail, git]
author_name: John Duff
author_uri: http://twitter.com/johnduff
---

A couple weeks ago I sat down at my computer after dinner to do a little
bit of work and was greeted with a very, very sluggish machine. This
isn’t normal with my Macbook so I tried shutting down a few applications
and pull up Activity Monitor to see what was chewing up the cycles. This
seemed to be too much for the machine and it completely locked up, what
next? Well, the only thing I could do, hold down the power button until
it shut off and try turning it back on ([did you try turning it off and
on
again?](http://en.wikiquote.org/wiki/The_IT_Crowd#Yesterday.27s_Jam_.5B1.1.5D)).

At this point I wasn’t too worried, and sat waiting for OS X to load.
Waiting. And Waiting. And Waiting. It just sat there spinning away. This
is quite the dilemma. I hopped onto my iPhone and Goggled to see if
there was a way to start up to a command prompt. I found [this
link](http://support.apple.com/kb/ts1417) which had a bunch of
information, including holding command-s to boot to single user mode.

Off and On again, this time booting to single user mode and the command
prompt. The same link mentioned running ‘/sbin/fsck’ (file system check)
to fix any problems with the file system. I ran it. A billion errors,
half a billion couldn’t be fixed. Great… Well, it says you may need to
run it multiple times to fix everything, so I run it again. And again.
And again. Shit.

Maybe I should try reseting the PRAM like [this link
says](http://support.apple.com/kb/ht1379). Off and On again. Kernel
Panic. Off and On. Kernel Panic. Shit. (Kernel Panic is the OS X
equivalent to a Windows Blue Screen. They are rare so it is likely you
have never seen one, but you can check it out
[here](http://support.apple.com/kb/HT1392?viewlocale=en_US))

Well, now I’m screwed. At least I have Apple Care, into the Mac shop it
goes.

“Did you try turning it Off and On again?”, she asks.  
“Yep. I tried running the file system check, I tried reseting the PRAM
and I turned it Off and On a dozen times,” I told her.  
“Well, I’ll just try reseting the PRAM,” she said. “Oh, ya, Kernel
Panic. That’s not good. We’ll take a look and let you know what we can
do.”

Later that day, the Mac Store calls. “You need a new hard drive, we’ll
be sending your old one to Apple and probably get a new one in 3-5
business days.”  
“You don’t have them in stock?” I asked.  
“No, we don’t stock the brand Apple uses and to keep it covered by the
warranty we have to use one of theirs,” the girl from The Mac Store
says.

Four days later and I’m bringing my Macbook home with it’s fresh new
hard drive. I pop in my Snow Leopard disk and watch some TV while OS X
reinstalls. Once it finishes I’m asked if I want to import user settings
or restore from a Time Machine backup. Hell Yes, I’ll restore from the
Time Machine backups I started doing ONE WEEK EARLIER! A couple hours
later and I could barely remember that my hard drive had failed and I
had a new one in my machine. All my Applications were restored. All my
settings. Heck, even my desktop wallpaper came back.

The only thing that I had to reinstall was parallels, and that’s because
I ignored the folder where the Windows VM was saved (it seems like it
wouldn’t have worked from a restore anyways). The moral of the story is
spend $60 on a 500 gig hard drive and USE Time Machine. I’ve ignored a
number of places on my machine to keep the backup a little smaller and
taking less time, you can do the same (with my setup it is PROVEN that
you can still restore and get everything back):

{% highlight bash %}
~/.Trash
/.Trashes
/Library/Audio
~/Library/Caches
/Library/Caches
~/Downloads
~/Movies
~/Documents/Parallels
~/Music/iTunes/iTunes Music/Podcasts
{% endhighlight %}

Currently I have 20 days of backups and 300 gigs remaining on the drive.
Do it.

I have to note that my little dialog with the girl at the Mac shop was a
little contrived. They were actually really helpful and did a great job
bringing my Macbook (and me) back to life.
