---
layout: post
title: "Making the Switch to VIM"
tags: [programming, ide, setup, config, vim]
author_name: John Duff
author_uri: http://twitter.com/johnduff
---

Well, after a couple years of using Textmate (and liking it for the most
part) I’ve decided to change editors and have happily been using VIM for
the last couple weeks. Why VIM? Nothing in particular stands out really.
One of my co-workers is a big fan of it, I have to use it once and
awhile when on the servers and emacs seemed to be a big pain in the ass
:).

Here’s a few of the plugins I’ve installed that helped make me feel more
at home in VIM:

[NERDTree](http://www.vim.org/scripts/script.php?script_id=1658)  
This plugin gives you a project tree that you can use to navigate your
project tree. I also mapped the \` key to toggle the tree making it
super easy to open and close.

[fuzzy finder](http://www.vim.org/scripts/script.php?script_id=1984) and
[fuzzy finder textmate](http://github.com/jamis/fuzzyfinder_textmate)  
These two plugins give the same functionality as cmd-t in Textmate,
letting you quickly open files in the project. I mapped this to ,+t and
,+r to refresh the list.

[rails vim](http://www.vim.org/scripts/script.php?script_id=1567)  
This gives a while pile of shortcuts and helpers for working with rails.

[snipMate](http://www.vim.org/scripts/script.php?script_id=2540)  
Just like it sounds, this plugin gives you snippets much like Textmate
has. Put that together with [the
snippets](http://github.com/scrooloose/snipmate-snippets) from
scrooloose (Martin Grenfell) and we have access to lots of cool
shortcuts.

These are the main plugins I added. I also included a shortcut to use
ACK for search and a number of other little scripts and shortcuts to
make myself more productive. I’ve got the whole set of [config
files](http://github.com/jduff/vimfiles) up on github so you can use it,
fork it, change it all you want.
