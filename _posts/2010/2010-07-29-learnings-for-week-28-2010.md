---
layout: post
title: "Learnings for Week 28 2010"
tags: [programming, learnings, rails, sqlserver, gem, email]
author_name: John Duff
author_uri: http://twitter.com/johnduff
---

-   To get ActionMailer to work with GMail I needed to add the
    :enable\_starttls\_auto: true option [to the mailer
    configuration](http://www.justinball.com/2009/06/25/sending-email-with-ruby-on-rails-2-3-2-and-gmail/)

<!-- -->

-   You can [add global gem options to
    \~/.gemrc](http://stackoverflow.com/questions/1381725/how-to-make-no-ri-no-rdoc-default-for-gem-install),
    which is just a yml file
    -   ex. gem: —no-ri —no-rdoc

<!-- -->

-   SQLServer compatibility mode doesn’t make the server behave exactly
    what is specified, rather, it pulls in any functionality that may
    have been deprecated in the later releases (I think)

<!-- -->

-   [SendGrid](http://sendgrid.com/), [Google
    Apps](https://www.google.com/a/),
    [AuthSMTP](http://www.authsmtp.com/) are paid services that can be
    used for sending email so you don’t need to do it through your own
    server (or if you’re on EC2 and can’t reliably send mail from your
    server)
