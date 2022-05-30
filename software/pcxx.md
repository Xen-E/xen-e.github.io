---
layout: default
title: Playlist Converter++
description: Read, Manage, Fix, Convert & Create Professional Playlists with this powerful app.
tags:
- PCxx
- PC++
- PlaylistConverter++
- Download
- Install
---

# Playlist Converter++
### _Read, Manage, Convert & Create Playlists_

![ScreenShot](https://raw.github.com/xen-e/pcxx/main/screenshots/PCxx_1.0.png)

PC++ is a powerful playlist manager, You can use it to create or convert media playlists.
It can read the following playlist types:
- M3U/M3U8 (Mp3 URL)
- PLS (SHOUTcast)
- XML Shareable Playlist Format (XSPF)
- JSON Shareable Playlist Format (JSPF)
- foobar2000 Playlists (FPL)
- Microsoft Windows Media Player (WPL)
- Advanced Stream Redirector (ASX)
- Media Player Classic (MPCPL)
- AIMP Playlists (AIMPPL)
- Old Winamp playlists (B4S)
- Basic Text Files (TXT)

It can also create as many types and even more! 

## Features

- Cross-platform, You can run it on *nix systems, windows etc...
- i686 (32bit) support (Windows)
- Extremely fast and low on resources
- Highly customizable
- Unicode support
- ID3 Fixer, You can use it to fix and replenish playlists
- Can fix paths
- Drag & Drop support (Files and Directories)
- Detailed Logs
- Pretty modern interface available in two modes: Dark/Light
- much more!

## Downloads

[Windows 64bit](https://github.com/Xen-E/pcxx/releases/download/1.1/PCxx-1.1-x86_64-setup.exe){:class="downloadBtn"}
[Windows 32bit](https://github.com/Xen-E/pcxx/releases/download/1.1/PCxx-1.1-i686-setup.exe){:class="downloadBtn"}
[Linux (64bit)](https://github.com/Xen-E/pcxx/releases/download/1.1/PCxx_Linux_v1.1.zip){:class="downloadBtn"}

Don't forget to check out [Releases Page](https://github.com/Xen-E/pcxx/releases).

## User Installation

For Windows just download and double click the installer and then follow the instructions, For Linux in general download the compressed file, extract it then find a file called "Run Me" and double click it OR right click and hit "Run" thats's it! You don't need to make it executable just run it. Please notice that this binary was built using Ubuntu 20.04.2.0 LTS (Focal Fossa) which is based on Debian. So if you face any problems try to build the project yourself (Check below).


## Dev Installation

PC++ built using the [Qt](https://www.qt.io) framework (**5.15.2**), that means you need to have a Qt toolchain installed in your system... Make sure to have the **Qt Designer** as well so you can open the project file.

Also make sure you have [TagLib](https://taglib.org) library in your system, If you use Linux (Debian/Ubuntu...etc) open the terminal and type:
```console
sudo apt install libtag1-dev
```
Arch based:
```console
sudo pacman -S taglib
```

In Windows you gonna need to download the source files and build it yourself, Nothing special just cmake stuff... Example:
```console
mkdir build && cd build
cmake -DCMAKE_BUILD_TYPE=Release -DBUILD_SHARED_LIBS=OFF ..
make -j4
```
> Notice that `-DBUILD_SHARED_LIBS=OFF` will produce a **static** version which is important.

After that modify the Qt Project file (**PCxx_QT.pro**) and change the old library path to the new one.

## License
Playlist Converter++ is Licensed under the GNU Lesser General Public License version 3 (LGPLv3).
Please read the COPYING.LESSER file for more info. OR visit the [Free Software Foundation](https://www.gnu.org/licenses/lgpl-3.0.en.html) website.

