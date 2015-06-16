---
layout: post
status: publish
published: true
title: 'MSBuild: A disappointment'
author: /colin
wordpress_url: http://www.bendell.ca/tech/?p=24
date: '2006-02-19 18:40:00 -0500'
categories:
- tech
tags: []
comments: []
---
The number one thing going for NAnt was that it learned from Java Ant but was not bound to the ideology and religious conviction of the Java Ant developers. The Java Ant architects assumed that you would only use Ant for compiling/building your product. They failed to realise and/or ignored the possibility that Ant could be used for much more than just building, include things like deployment and automation. Unfortunately, because of the conviction of several of the key architects, Java Ant still does not have an "if" task. (Oh sure you could mangle the "condition" task and leverage the "depends" attributes to do what you need, but the resulting code is very ugly and un-maintainable!).

NAnt was, therefore, in a position to grow from the stable library code of the Jakarta project and address the needs of the userbase. When NAnt entered the scene they had a lot of extra features that are lacking from Ant such as an If task and a much more extensible expression language.

Microsoft had a prime opportunity to learn from Ant and NAnt and deliver a rock solid, highly useable, strongly typed, xml scripting language backed by a legion of developers. Instead, Microsoft decided to ignore the experience of the community and re-invent the wheel. MSBuild assumes that it would be used to build your solution(s) - nothing more. Heaven forbid if you should want to deploy or automate with a 'build' script. Not to mention the severe lack of pre-bundled tasks and flexibility that any developer would need for standard build scenarios. I find it appalling that a non-Microsoft group would have to contribute an 'add' task. This should have been baked into their expression language.

I have been attempting to write a collection of useful MSBuild tasks for my current project. Unfortunately at every corner I turned I realised that there was more library code and supporting tasks that I would also have to create - functionality that should have been present at ship time. For example, MSBuild has no support for an expression language, Build containers, or enum properties.

Therefore, I have concluded that developing MSBuild tasks is a waste of our development time and resources. Although I believe that MSBuild may be here to stay, it has a lot of maturing to do before it can replace what NAnt already has out of the box. If I can develop a NAnt task in 1/5th the time of a MSBuild task then I am obligated to use the more effective and cost efficient tool.

Please Microsoft, do your homework before you release another developer tool that directly competes with a well embraced community tool.
