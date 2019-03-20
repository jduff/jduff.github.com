---
layout: post
title: "Learnings for Week 20 2010"
tags: [programming, learnings, ruby, rr, rails3, devise]
author_name: John Duff
author_uri: http://twitter.com/johnduff
---

-   If, for whatever reason, your Win XP install doesn’t show Remote
    Desktop in the start menu running ‘mstsc’ will start it up.
-   Until
    [recently](http://github.com/jnunemaker/httparty/commit/179ef878808686b7f286174404023b1e1616f5f9)
    you couldn’t access the raw response from HTTParty. This can be
    confusing but most of the data can be found using proxied methods on
    the HTTParty::Response (code, headers, body, message).
-   Two very cool gems for simplifying html forms in rails:
    [simple\_form](http://github.com/plataformatec/simple_form) and
    [formtastic](http://github.com/justinfrench/formtastic). I’m using
    simple\_form in a project right now and loving it.
-   [rr](http://github.com/btakita/rr) seems to have a problem with
    mocked class methods sticking around between test calls. [Issue
    opened](http://github.com/btakita/rr/issues#issue/35).
-   Rails 3 respond\_with helps clean up controllers by packaging up the
    standard respond\_to cases for html, json, xml etc into one method.
    It’s also very extendable ([responders
    gem](http://github.com/plataformatec/responders) has some nice
    ones).
-   Getting [devise](http://github.com/plataformatec/devise) to
    authenticate by email or login is less trickier than it seems. [Matt
    Tanase](http://www.howradical.com/getting-devise-to-accept-a-username-or-email)
    has a nice little post on how to do it. The key is remembering to
    change your initializer to have ‘config.authorization\_keys :login’
    in it.
