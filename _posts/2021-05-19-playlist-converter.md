---
title: Playlist Converter++
tags:
- PCxx
- PC++
- PlaylistConverter++
---

This project started as a small script i made for myself to fix and convert my music playlists (Yes i still use local music players), Then i turn it into a small GUI tool that uses the [wxWidgets](https://www.wxwidgets.org) library...I worked on it over the time until it became a large project, But unfortunately i had to dump wxWidgets for [Qt](https://www.qt.io) due to building problems on GNU/Linux because i wanted it to be cross platform, Everything worked well on Windows though. It was static linking issues and a lot of CMake headaches.<!--more-->

The good thing about Qt framework it has it's own building system (`qmake`) and it's very simple and highly effective and it works on all platforms even solaris with just few lines of code. Not only that but i also found out later that Qt is feature rich and has a lot of platform independent libraries and tools that speed up the developing process and even making it fun; Designer, JSON, XML classes...etc. wxWidgets have these classes too but they're very basic i also didn't know that earlier (*sigh*) i thought it's just a GUI library, and because of that i used [RapidXML](http://rapidxml.sourceforge.net) and some [popular JSON library](https://github.com/nlohmann/json) which also i had to drop them later and rewrite the code.

Here's what the first ever version of PC++ looked like (wxWidgets, Windows 7):
![First version of Playlist Converter++]({{site.url}}/_images/screenshots/pcxx_old_wxwidgets_simple.png)

And here's the second attempt also using wxWidgets library:
![Second version of Playlist Converter++]({{site.url}}/_images/screenshots/pcxx_old_wxwidgets_complex.png)

These two executables are fully functional and work fine with Windows, But a lot of work needs to be done to get them to run on Linux/Darwin...etc.

I worked with many programming languages before. especially scripting languages, But my C/C++ knowledge is not that great i just got started, So this was like a practice for me and i learned a LOT from it.
