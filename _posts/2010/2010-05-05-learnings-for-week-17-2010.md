---
layout: post
title: "Learnings for Week 17 2010"
tags: [programming, learnings, ruby, vim, autotest, assert]
author_name: John Duff
author_uri: http://twitter.com/johnduff
---

Learnings for the past week.

-   vim (I made the switch this week!)
    -   ctrl+v to enter visual mode (useful for block comments)
    -   :sp to split a window
    -   :vsp for vertical split
    -   :A for alternate file (rails plugin)
    -   snipmate for awesome snippets
        ([plugin](http://www.vim.org/scripts/script.php?script_id=2540),
        [snippets](http://github.com/scrooloose/snipmate-snippets))
    -   \* searches for current word
    -   :%s/search/replace/modifiers
        -   if you leave search blank it uses your previous search
        -   g modifier for global search, c to confirm each replacement
            (very useful!)
-   autotest doesn’t run in ruby 1.9.1
    -   It fails for me saying “set a breakpoint in malloc\_error\_break
        to debug” and that’s about all
-   ruby -e “code to run”
-   assert\_select(‘input’, 0) doesn’t work, need to use (assert\_select
    ‘input’, :count=\>0)
    -   This is confusing since assert\_select(‘input’, 5) works just
        fine

That’s it for this week. If I find some time I’ll post my vim config and
talk about that a bit and maybe discuss what I did about autotest not
working.
