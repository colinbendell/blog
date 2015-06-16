---
layout: post
status: publish
published: true
title: Fiddler for HTTP Debugging
author: /colin
wordpress_url: http://www.bendell.ca/tech/?p=4
date: '2005-02-08 17:50:00 -0500'
categories:
- tech
tags: []
comments: []

---
One of the Program Mangagers of the IE team has written a very handy tool called [Fiddler](http://www.fiddlertool.com/fiddler/).  

One of the significant differences between Fiddler and [TracePlus WebDetective](http://www.sstinc.com/webpro.html) is that it does not require you to respawn your browser in order to investigate http traffic.  Once the tool is open all subsequent activity in IE will automatically be captured.  To trace the activity of other non-IE clients/browsers you will need to configure the proxy settings to `localhost:8888`.  

You can also attach scripts to be invoked during a request or response events.  More details about the event model can be found on this recent [MSDN article](http://msdn.microsoft.com/library/default.asp?url=/library/en-us/dnwebgen/html/IE_IntroFiddler.asp).

Oh yea, and the other cool thing about this tool - its written in c#!
