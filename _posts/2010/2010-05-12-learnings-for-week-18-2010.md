---
layout: post
title: "Learnings for Week 18 2010"
tags: [programming, learnings, ruby, vim, devise]
author_name: John Duff
author_uri: http://twitter.com/johnduff
---

Learnings for the past week.

-   more vim fun
    -   zf5j to fold the next 5 lines
    -   zo to open a fold
    -   zc to close a fold
    -   c in visual block to substitute
    -   ctrl+\_ to complete html tag (with closetag plugin)
    -   ctrl+w+\_ to maximize splits vertically
    -   ctrl+w+\| to maximize splits horizontally
    -   ctrl+w+= to equalize splits
-   after\_initialize in a ruby model if you want something to happen
    when both new or create are called
-   instance\_eval can be given a block. This is really powerful if you
    want to whip up a quick DSL to clean up some code (highly
    recommended).
-   Devise authentication plugin dropped support for MongoMapper until
    it conforms to ActiveModel (MongoMapper is in turn waiting until
    Rails 3 is final before making this change)
