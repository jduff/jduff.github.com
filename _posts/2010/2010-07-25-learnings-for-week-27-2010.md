---
layout: post
title: "Learnings for Week 27 2010"
tags: [programming, learnings, git, rails, facebook, voip]
author_name: John Duff
author_uri: http://twitter.com/johnduff
---

Late again, I know, but here’s my learnings from a couple weeks ago.

* If you need to use the Rails url helpers within a model or even script/console you just need these two lines: {% highlight ruby %}
include ActionController::UrlWriter
default_url_options[:host] = DEFAULT_HOST
{% endhighlight %}

* Alternatively within script/console you can use the "'app' or 'helper' variables to interact with the application":http://stackoverflow.com/questions/151030/how-do-i-call-controller-view-methods-from-the-console-in-rails {% highlight ruby %}
helper.number_to_currency('2342.33')
app.get '/'
{% endhighlight %}

-   If you want some piece of code to run after each request you can use
    a [‘config.to\_prepare’
    block](http://toolmantim.com/thoughts/environments_and_the_rails_initialisation_process).
    This might be useful if you have classes reloading in development
    and want to set settings after they have reloaded.

* Git can sometimes consider text files to be binary if they have Null characters at the end. You can still diff these files with this command: {% highlight bash %}
git diff -a
{% endhighlight %}

-   Super cool OS X soft phone
    [Telephone](http://www.pure-mac.com/downloads/telephonedl.html)

<!-- -->

-   Facebook applications must be created on a Personal Account, they
    can not be created with a Business Account.
