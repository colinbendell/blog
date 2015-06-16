---
layout: post
status: publish
published: true
title: SVN + UTF16 + SQL Management Studio = No SVN Merge
author: /colin
wordpress_url: http://www.bendell.ca/tech/?p=23
date: '2006-02-18 07:13:00 -0500'
categories:
- tech
tags: []
comments: []

---
##The problem:
By default SQL Management studio saves all files as "Unicode" which is Microsoft speak for UTF-16. This causes problems with SVN when you want to leverage merges and diffs. SVN treats UTF-16 as a binary file and therefore can't do textual diffs leaving no way for you to deal with conflicts other than to revert and manually integrate your changes from another saved copy.

##The Solution:
Open a sql file in the Management Studio and then select "Save As" from the File menu. Then select the drop down beside the "Save" button and select Save with encoding. From the encoding drop down select Western Europe which is Microsoft speak for Latin1 (ISO8859-1) or select UTF-8. Once you have saved one file, all new files will be saved with this encoding. Old files will need to be converted using another editor such as Notepad2.

You might need to svn remove and then svn add the file in order to change the associated mime type. This will need to be tested though.
