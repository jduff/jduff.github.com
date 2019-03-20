---
layout: post
title: "Learnings for Week 34 2010"
tags: [programming, learnings, osx, adhearsion, ruby, glassfish, jruby, curl]
author_name: John Duff
author_uri: http://twitter.com/johnduff
---

-   In the latest version of X11 (on Snow Leopard at least) there is an
    option in the preferences to allow clicks to go through windows.
    This makes applications like Gimp actually usable in OS X since you
    don’t have to click twice anymore (once to activate the window and
    another time to click the actual tool or menu you wanted)

<!-- -->

-   The Asterisk background command can take multiple files to play,
    each joined by ‘&’

<!-- -->

-   Adhearsions get\_digits, :play\[“file1”, “file2”…\] plays the files
    in order and is interruptible by pressing a key, much like the
    Asterisk background command.

<!-- -->

-   If naming a class/module/file with the same name as something in the
    Ruby Standard Library they should be scoped by a unique name to
    prevent clashes.

* Rails adds 'collection_ids' method to models that have a belongs_to association. This gets you all the ids of the associated objects in an array. ex:{% highlight ruby %}
Organization.user_ids
{% endhighlight %}

 * If you're having trouble with the Glassfish Admin not loading it could be it's trying to check for updates over the network. We found some good instructions on <a href='http://http://techmythoughts.blogspot.com/2010/08/glassfish-v3-admin-console-taking-too.html'>how to disable this</a> by editing the glassfish domain.xml and removing some jars. Note that in our setup the xml file was at {% highlight bash %}%GLASSFISH_HOME/glassfish/domains/domain1/config/domain.xml{% endhighlight %}

# Update the {% highlight bash %}%GLASSFISH_HOME/glassfish/domains/domain1/domain.xml{% endhighlight %}{% highlight xml %}
{% endhighlight %}
<java-config>  
<jvm-options>-Dcom.sun.enterprise.tools.admingui.NO\_NETWORK=true</jvm-options>  
</java-config>

1.  Remove update tool jar (Backup and remove this JAR)  
    !include tomd-include-3.txt
2.  Delete this dir:  
    !include tomd-include-4.txt

* To follow redirects with curl add the -L option{% highlight bash %}
curl -L http://example.com
{% endhighlight %}

-   We watch a new <a href='http://vimeo.com/14435288'>webcast on
    JRuby</a> that highlights a few interesting features, most notable
    being that the next version of JRuby and warbler will allow you to
    build a executable jar file with a embedded web server. This is also
    interesting because you can have it only package class files so you
    don’t need to distribute your source with the application.

<!-- -->

-   Also from the JRuby webcast some interesting tools:

1.  <a href='https://visualvm.dev.java.net/'>VisualVM</a> for profiling
    your java or jruby applications.
2.  <a href='http://cupi2.uniandes.edu.co/web/javadoc/j2se/1.5.0/docs/tooldocs/share/jps.html'>jps</a>
    to show java process status.
3.  <a href='http://cupi2.uniandes.edu.co/site/images/recursos/javadoc/j2se/1.5.0/docs/tooldocs/share/jstack.html'>jstack</a>
    to print the stack of a running java process.
