---
layout: post
title: "Learnings for Week 16 2010"
tags: [programming, learnings, rvm, ruby, jquery, css]
author_name: John Duff
author_uri: http://twitter.com/johnduff
---

Learnings for the past week. It was a busy one.

-   rvm uninstall leaves build files
    -   rvm remove gets rid of everything
-   Firefox on Ubuntu gets thin black borders around images that are
    resized in html/css
    -   Adding some transparency to the edges of the images fixes
-   rails i18n translation keys can’t have ‘.’ in them, even if escaped
-   -webkit-user-select/-moz-user-select:none; to disable selection on a
    webpage
-   Webkit doesn’t allow keyboard entry to 0 height inputs
-   Firefox and Webkit don’t allow keyboard entry to invisible inputs
    (display:none)
-   jQuery fadeOut doesn’t work on some (circle, line) svg elements in
    Webkit
-   jQuery.keypad on multiple inputs should check if the keyboard target
    is changing before updating the keypad (huge performance gains)
-   git cherry lists commits that don’t exist in another branch.
    Compares the changeset, not commit ids
-   gem install -f will install gem even if dependencies can’t be met
-   apt-get build-dep ruby1.8 will get you all the ruby build
    dependencies
-   git checkout -t -b BRANCH origin/BRANCH will checkout and track a
    remote branch
