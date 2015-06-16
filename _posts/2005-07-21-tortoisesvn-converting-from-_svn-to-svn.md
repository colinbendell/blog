---
layout: post
status: publish
published: true
title: 'TortoiseSVN: converting from _svn to .svn'
author: /colin
wordpress_url: http://www.bendell.ca/tech/?p=13
date: '2005-07-21 18:18:00 -0400'
categories:
- tech
tags: []
comments:
- id: 4
  author: Thomas Broyer
  author_email: t.broyer@ltgt.net
  author_url: ''
  date: '2008-09-01 17:05:47 -0400'
  date_gmt: '2008-09-02 00:05:47 -0400'
  content: 'More than 3 years later but thanks a lot! (I''ve had to rename a few ones
    by hand though: "filename too long" or something like that &acirc;&euro;&ldquo;was
    "Nom de ficher ou extension trop long" in French&acirc;&euro;&ldquo;)'
- id: 5
  author: Ramesh
  author_email: ramezkumar@gmail.com
  author_url: ''
  date: '2010-09-24 00:15:36 -0400'
  date_gmt: '2010-09-24 07:15:36 -0400'
  content: The script is for linux . But im using in Windows . what is the procedure to convert the "_svn" to ".svn"  ??  .
  
---

After you have migrated all your VS 2003 solutions [away from web applications](http://develpickle.blogspot.com/2005/07/aspnet-applications-without-web.html), you will be able to use the standard svn tools.  Unfortunately, once you install the standard TortoiseSVN, your old projects will be unusable until they are re-checked out.

Don't worry!  There is a better way.

Below are two scripts that allow you to quickly and easily convert from a project using _svn (hacked TortoiseSVN) to .svn (standard TortoiseSVN).

```
@rem dotNetSVN.cmd 
@echo off

rem convert .svn folders to _svn

setlocal
for /f "delims=" %%a in ('dir /AH /b /s .svn*') do attrib -h "%%a"
for /f "delims=" %%a in ('dir /AD /b /s .svn*') do move "%%a" "%%a\..\_svn"
for /f "delims=" %%a in ('dir /AD /b /s _svn*') do attrib +h "%%a"
endlocal
```

```
@rem normalSVN.cmd 
@echo off

rem convert _svn folders to .svn

setlocal
for /f "delims=" %%a in ('dir /AH /b /s _svn*') do attrib -h "%%a"
for /f "delims=" %%a in ('dir /AD /b /s _svn*') do move "%%a" "%%a\..\.svn"
for /f "delims=" %%a in ('dir /AD /b /s .svn*') do attrib +h "%%a"
endlocal
```
