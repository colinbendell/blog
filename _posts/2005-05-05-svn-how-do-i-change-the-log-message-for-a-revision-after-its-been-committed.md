---
layout: post
status: publish
published: true
title: 'SVN: How do I change the log message for a revision after it&#8217;s been
  committed?'
author: /colin
wordpress_url: http://www.bendell.ca/tech/?p=9
date: '2005-05-05 17:19:00 -0400'
categories:
- tech
tags: []
comments: []

---
From the [SVN FAQ](http://subversion.tigris.org/faq.html):
>Log messages are kept in the repository as properties attached to each revision.  By default, the log message property (`svn:log`) cannot be edited once it is committed.  That is because changes to [revision properties](http://svnbook.red-bean.com/svnbook/ch05.html#svn-ch-5-sect-1.2) (of which `svn:log` is one) cause the property's previous value to be permanently discarded, and Subversion tries to prevent you from doing this accidentally.  However, there are a couple of ways to get Subversion to change a revision property.
>
<br/>
>The first way is for the repository administrator to enable revision property modifications.  This is done by creating a hook called "pre-revprop-change" (see [this section](http://svnbook.red-bean.com/svnbook/ch05s02.html#svn-ch-5-sect-2.1) in the Subversion book for more details about how to do this). The "pre-revprop-change" hook has access to the old log message before it is changed, so it can preserve it in some way (for example, by sending an email). Once revision property modifications are enabled, you can change a revision's log message by passing the --revprop switch to `svn propedit` or `svn propset`, like either one of these:
>
>```bash
$ svn propedit -r N --revprop svn:log URL
$ svn propset -r N --revprop svn:log "new log message" URL
```

>where N is the revision number whose log message you wish to change, and URL is the location of the repository.  If you run this command from within a working copy, you can leave off the URL.
