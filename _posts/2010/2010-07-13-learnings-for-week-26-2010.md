---
layout: post
title: "Learnings for Week 26 2010"
tags: [programming, learnings, git, vmware, vim, engineyard, ec2]
author_name: John Duff
author_uri: http://twitter.com/johnduff
---

-   Git interactive rebase can reorder commits (just reorder them in the
    file)
-   “No such device eth0” after cloning VMWare Image
    -   run ‘sudo mv /etc/udev/rules.d/70-persistent-net.rules
        /etc/udev/rules.d/70-persistent-net.rules.old’ and then restart
        the machine to fix the problem. Found
        [here](http://muffinresearch.co.uk/archives/2008/07/13/vmware-siocsifaddr-no-such-device-eth0-after-cloning/).
-   [Any word completion with
    vim](http://vim.wikia.com/wiki/Any_word_completion)
    -   type some characters then ctrl-N or ctrl-P (next or previous
        match)
-   [EngineYard App Cloud](http://www.engineyard.com/products/appcloud)
    makes a lot of mundane server admin tasks very simple and still
    allowing complete customization with chef scripts or with root
    access on the server.
-   Many EC2 IPs are on Spam blacklists. Use a thirdparty such as gmail
    to do the emailing for you.
