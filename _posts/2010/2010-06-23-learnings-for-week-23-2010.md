---
layout: post
title: "Learnings for Week 23 2010"
tags: [programming, learnings, ruby, git, html5, jquery]
author_name: John Duff
author_uri: http://twitter.com/johnduff
---

-   Recently needed to ignore some files that were already being tracked
    by git. [This
    Link](http://pivotallabs.com/users/rolson/blog/articles/1278-ignoring-tracked-files-in-git)
    helped me out.
    -   git update-index —assume-unchanged config/database.yml
-   HTML5 ‘type=search’ renders a nice search box and degrades to a
    simple input in older browsers.
-   HTML5 ‘placeholder=text’ renders placeholder text into an input that
    goes away when you click into it.
-   case; when ‘one’, ‘two’; to match ‘one’ or ‘two’ in a Ruby case
    statement.
-   Rails hide\_action :action\_name in a controller will prevent the
    action from being routed to.
-   jQuery “input” event gets fired when typing, pasting, cutting etc.
    from an input field.
-   jQuery live != livequery plugin. Main difference is live can only
    bind an event handler to the matching elements, livequery can run a
    function every time another element matches.
-   <http://www.quickdiff.com> super easy online tool to diff text.
