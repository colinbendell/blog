---
layout: post
status: publish
published: true
title: '&#34;Access is Denied&#34; in SVN: An unadvised work-around'
author: /colin
wordpress_url: http://www.bendell.ca/tech/?p=22
date: '2006-01-31 06:06:00 -0500'
categories:
- tech
tags: []
comments: []

---
##Problem:
SVN update or SVN checkout results in "access is denied" messages
##Solution:
*Temporarily* disable Norton Anti-Virus in the system tray. NAV is locking the .svn files and is slow at releasing the lock which causes SVN to abort because it can't access the file it just created.
