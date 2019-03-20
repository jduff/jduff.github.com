---
layout: post
title: "Learnings for Week 21 2010"
tags: [programming, learnings, ruby, alias_method_chain, jquery, selectors]
author_name: John Duff
author_uri: http://twitter.com/johnduff
---

-   A couple of interesting resources for getting rid of
    alias\_method\_chain in your code
    [here](http://gist.github.com/413965) and
    [here](http://yehudakatz.com/2009/03/06/alias_method_chain-in-models/)
    -   The basic idea in both of these is to create a module that
        defines the method you want to chain and call super in your
        redefinition. When you include the module into your class the
        modules method is insterted right above the instance’s class in
        the inheritance tree.
-   jQuery [nextAll](http://api.jquery.com/nextAll/) and
    [prevAll](http://api.jquery.com/prevAll/) functions to get all
    following/previous siblings of each element in the set of matched
    elements
    -   [next](http://api.jquery.com/next/),
        [nextUntil](http://api.jquery.com/nextUntil/),
        [prev](http://api.jquery.com/prev/) and
        [prevUntil](http://api.jquery.com/prevUntil/) are in the same
        family
-   cmd-shift-t reopens last closed tab in the web browser (chrome,
    firefox, safari).
-   A selected like ‘input + label’ matches all the labels that are
    directly beside an input. There is no way, with the same markup, to
    target the inputs directly beside a label (‘input - label’ someday,
    maybe?)
