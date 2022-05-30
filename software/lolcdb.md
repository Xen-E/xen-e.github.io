---
layout: default
title: League of Legends Champion Database
description: LoLCDB is a very small app that can be used to get live champions data from Riot Games servers through HTTP.
tags:
- LoLCDB
- League
- Legends
- HTTP
- CMD
---

# League of Legends Champion Database

**LoLCDB** is a very small executable that can be used to get live champions data from Riot Games servers through HTTP using the legendary CURL.

You can customize how champion data is retrieved, like patch version or even language. Here's an example:

![LoLCDB on the good ol' cmd.exe](https://raw.github.com/xen-e/lolcdb/main/screenshots/windows_cmd.PNG?raw=true "LoLCDB on the good ol' cmd.exe") 

## Downloads

[Windows 64bit](https://github.com/Xen-E/lolcdb/releases/download/1.0/LoLCDB_1_0-x86_64-windows.zip){:class="downloadBtn"}
[Windows 32bit](https://github.com/Xen-E/lolcdb/releases/download/1.0/LoLCDB_1_0-i686-windows.zip){:class="downloadBtn"}
[Linux Binary (64bit)](https://github.com/Xen-E/lolcdb/releases/download/1.0/LoLCDB_1_0-x86_64-linux.tar.xz){:class="downloadBtn"}

Don't forget to check out [Releases Page](https://github.com/Xen-E/lolcdb/releases).

## User Installation

1. Un-zip/decompress the file you downloaded
2. Open the folder/directory
3. You're going to find the executable inside, DO NOT OPEN IT
4. Use terminal/command-line instead. By right clicking an empty space and select "**Open in Terminal**" or if you on Windows you can **Shift+Right Click** then select "**Open command window here**". You can also just open the terminal and then use the classic "**cd**" command followed by the folder path which will work on all systems.

*TIP: If you use Windows then you can copy and paste the executable to **C:\Windows** and then you can use it from anywhere! In Linux you can put the executable in the **Home** folder (**~/**).*

## Usage
[**Champion**] [**Patch**] [**Language**] **ANSI**

*OR* [**Champion**] [**Patch**]

*OR* [**Champion**] [**Language**]

*OR just* [**Champion**]

Use through a command-line. Call the executable name (lolcdb) followed by the champion name, example:
```bash
lolcdb karma
```
In POSIX systems you may need to start with **./**
```bash
./lolcdb karma
```
To minimize work time you can just copy the executable to **Windows** folder and then you can just press **Windows/SUPER Key + R** and type **cmd** and start using it, For Linux you can put it in Home folder and then **CTRL + ALT + T**.

That's it! You can pass more arguments to customize the request, like for example you can specify the patch version:
```bash
lolcdb karma 6.6.1
```
This will give you info on Karma from a patch that was released in 2016! Remember that you don't need to add the latest patch everytime because it will be added automatically.

If you'd like the data to be in a different language you can simply include the language code followed by underscore (**_**) then the country code, example:
```bash
lolcdb karma fr_FR
```
This will display data in french, For full supported codes use:
```bash
lolcdb codes
```
And for full available patch versions use:
```bash
lolcdb versions
```
And for help and more details use:
```bash
lolcdb help
```

## Dev Installation

This project uses two libraries, First one is [RapidJSON](https://github.com/Tencent/rapidjson). and is already included in include directory since it's a header-only library, The second one is the famous CURL which is already exists in all operation systems especially if you're on Linux, But make sure you have the development version as well (libcurl):

Debian based (Ubuntu, Mint, Pop!_ OS..etc)
```bash
sudo apt install libcurl4-openssl-dev
```
Arch based
```bash
sudo pacman -S libcurl-openssl-dev
```
Notice that this will install the openssl default version, there's other flavors. Check your package manager.

That's it! the rest of work is done by cmake, here's how:
```bash
mkdir build
cd build
cmake ..
make
```
If you're a Windows user i suggest you to setup a [MSYS2](https://www.msys2.org/) environment and get used to it, because Windows in general is not that great for software development, It also comes with a better terminal (command-line) Just make sure you have the GCC/libcurl installed and then use the cmake -G flag to generate the Makefiles:
```bash
mkdir build
cd build
cmake -G"MSYS Makefiles" ..
make
```
OR just download the [libcurl](https://curl.se/libcurl) library and use it. You can also download the source code and then build it with ./configure

## License
LoLCDB is Licensed under the GNU Lesser General Public License version 3 (LGPLv3).
Please read the COPYING.LESSER file for more info. OR visit the [Free Software Foundation](https://www.gnu.org/licenses/lgpl-3.0.en.html) website.