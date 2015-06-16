---
layout: post
status: publish
published: true
title: ASP.NET Applications without Web Projects
author: /colin
wordpress_url: http://www.bendell.ca/tech/?p=12
date: '2005-07-19 17:54:00 -0400'
categories:
- tech
tags: []
comments: []

---
Fritz Onion tells you all you need to know to create a [ASP.NET Application without Web Projects](http://www.pluralsight.com/fritz/Samples/aspdotnet_without_web_projects.htm). He even talks about how to convert an existing web project to a c# library.  This will benefit us because:

1. Svn will work out of the box (no _svn hack required).  Any SVN tool will work
2. Project load time will be faster, especially if you are using Resharper
3. You can check-out the application to any directory and load the solution without IIS configuration<
4. You can recompile the solution without IIS configuration
5. You don't have to configure IIS to use the solution
6. You don't have to configure IIS to use the solution

Here is the article:

>##ASP.NET Applications without Web Projects
>
>*Reference prepared by [Fritz Onion](http://staff.develop.com/onion/)*
>
>The Web Project wizard in Visual Studio .NET is convenient for creating quick ASP.NET applications on your local machine, but in an effort to simplify your life, it also makes many decisions for you that are difficult to change if you need more flexibility. My biggest pet peeve with Web      Projects is that you cannot even open a .sln file if the virtual directory mapping in IIS is not set up correctly. I also dislike the way it places `.sln` and `.csproj` | `.vbproj` files in a separate location from the actual source      files (I understand that this is necessary to allow application creation directly on a server, but I never deploy that way).
>
>As a result, most of my web projects are created as standard class library projects. Unfortunately this means that you don't get the nice Web component wizards (like WebForms and UserControls). However, with a little tweaking, you can have it all.  I have prepared this document describing how to enable these wizards in class library projects (thanks to      Dan Sullivan for pointing out how to do this), as well as how to convert existing Web Projects to class library projects and still keep the nice integrated debugging.
>
>###To enable Web wizards in a class library project:
>In a directory called `C:\Program Files\Microsoft Visual Studio .NET 2003\VC#\CSharpProjectItems\LocalProjectItems` is a file callled `localprojectitems.vsdir`. Likewise in a directory `C:\Program Files\Microsoft Visual Studio .NET 2003\VC#\CSharpProjectItems\WebProjectItems` is a file called `webprojectitems.vsdir`. If open the second file with notepad you can figure out the lines to copy to the first file to be able to add the usual files you need to create an aspx page or web service to a class lib project.
>
>Once you have copied these thing open VS, open a class lib and go to add new item and you will see these additional file types available.
>
>###To set the output of a class library project to go to a /bin directory of your choosing:
>1. Right-click on the project and select properties
>2. Set Configuration to 'All Configurations' to affect both debug and release builds
>3. Under configuration properties/build set the OutputPath to the `/bin` directory
>
>###To convert an existing web project into a class library project:
>1. Open the .sln file in a text editor, and change the reference to the project  from an `http://...` reference to a simple reference to the .csproj (or .vbproj)  filename. For example:
>
>```
>change:
>Project("{FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}") = "WebApplication133", "http://localhost/WebApplication133/WebApplication133.csproj", "{39CB37A5-F735-4684-B5DA-DD355B683090}"
>
>to:
>Project("{FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}") = "WebApplication133", "WebApplication133.csproj", "{39CB37A5-F735-4684-B5DA-DD355B683090}"
>```
>
>2. If there is one, delete the .webinfo file
>3. Open the .csproj (or .vbproj) file and change the ProjectType attribute from  "Web" to "Local"
>
>###To set up a class library project to run a browser when you debug it:
>1. Right-click on the project in the solution explorer and select properties
>2. Under Configuration Properties/Debugging, change Debug Mode from 'Project' to  'URL'
>3. Hit Apply
>4. In the Start URL field, enter the complete url to the page you want to hit to debug, like: `http://localhost/testproj/webform1.aspx`
