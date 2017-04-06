---
id: 462
title: Reduce windows folder size on windows 7/8
date: 2017-04-03T00:19:05+00:00
author: Navy Su
layout: post
guid: http://navysu.x10host.com/?p=462
permalink: /2017/04/03/reduce-windows-folder-size-on-windows-78/
categories:
  - Windows
tags:
  - folder
  - large
  - reduce
  - size
  - windows
---
The following command will uninstall all previous versions of components without the scheduled task’s 30-day grace period:

<pre class="prettyprint">DISM.exe /online /Cleanup-Image /StartComponentCleanup</pre>

The following command will remove files needed for uninstallation of service packs. You won’t be able to uninstall any currently installed service packs after running this command:

<pre class="prettyprint">DISM.exe /online /Cleanup-Image /SPSuperseded</pre>

The following command will remove all old versions of every component. You won’t be able to uninstall any currently installed service packs or updates after this completes:

<pre class="prettyprint">DISM.exe /online /Cleanup-Image /StartComponentCleanup /ResetBase</pre>

Source:[ https://superuser.com/questions/669193/why-is-windows-folder-so-big-in-windows-8-1](https://superuser.com/questions/669193/why-is-windows-folder-so-big-in-windows-8-1)

<blockquote data-secret="SGsxa19CVd" class="wp-embedded-content">
  <p>
    <a href="https://www.howtogeek.com/174705/how-to-reduce-the-size-of-your-winsxs-folder-on-windows-7-or-8/">How to Reduce the Size of Your WinSXS Folder on Windows 7 or 8</a>
  </p>
</blockquote>