---
layout: post
status: publish
published: true
title: Google Images &#38; Picasa
author: /colin
wordpress_url: http://www.bendell.ca/tech/?p=8
date: '2005-05-03 14:54:00 -0400'
categories:
- tech
tags: []
comments: []

---
Google openly admits that it reads metadata information from image files to help contextualize the image for better searching.  However, it is not known what fields and what formats google actually supports.  The general feeling is that it supports many of the EXIF and IPTC headers.  Again, it is unclear which headers it uses and what kind of weighting it applies to these values.  One thing that we do know is that images manipulated with picassa and assigned a caption rank well in google images.

As it turns out, Picasa does not use either the Exif or IPTC formats for its keywords and caption fields. Picasa uses the Photoshop 3.0 8BIM annotations.  The first segment after the jpeg magic bytes is called the jfif header.  The header can contain many segments including exif and iptc data.  Photoshop, since version 3.0 also adds a segment (usually the first segment) to add extra annotations such as keywords and captions. 

Here are some good resources in understanding the jpeg headers can be found here:

* http://www.obrador.com/essentialjpeg/headerinfo.htm [dead]
* Some sample code for reading the Photoshop 8BIM header can be found at codeproject: [Extracting IPTC header information from JPEG images](http://www.codeproject.com/Articles/1208/Extracting-IPTC-header-information-from-JPEG-image) 
