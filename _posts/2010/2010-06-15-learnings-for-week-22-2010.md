---
layout: post
title: "Learnings for Week 22 2010"
tags: [programming, learnings, ruby, grep, sqlserver, phocus, harmony, "holy grail", javascript, testing]
author_name: John Duff
author_uri: http://twitter.com/johnduff
---

-   grep -rl ‘structure\_dump’ . to recursivly search through a folder
    for the given string. mvim \`grep..\` to open them up.
-   alias ls=‘ls -GF’ so that ls is colored in all consoles.
-   [nvarchar in
    SQLServer](http://msdn.microsoft.com/en-us/library/ms186939.aspx)
    takes a limit from 0 to 4000 OR the keyword MAX. MAX != 4000, it is
    actually much larger.
-   When using Rails and the JDBC adapter queries SQLServer for nvarchar
    columns it gets the value back for limit, which when created with
    MAX is much larger than a limit you can use. This comes up when
    trying to create the database from schema.rb (testing).
-   [Phocus](http://github.com/mynyml/phocus) gem to temporarily focus
    some tests, ignoring all others, even across test classes.
-   [Harmony](http://github.com/mynyml/harmony) provides a simple DSL to
    execute javascript + DOM code within ruby.
-   [Holy Grail](http://github.com/mynyml/holygrail) execute
    browser-less, console-based, javascript + DOM code right from within
    your Rails test suite.
