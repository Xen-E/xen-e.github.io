---
layout: default
title: File URLs Doctor
description: Scan files and directories/folders for dead links.
tags:
- FUD
- File
- URL
- Doctor
- Links
- Dead
- 404
---

# File URLs Doctor

**FUD** is a very small executable that can be used to scan files/directories for dead links! It's cross-platform and highly customizable and can give you a lot of detailed information.

* IPv6 support
* Redirects following (28 Protocols!)
* Proxy with IPv6 support (http, https, socks4, socks4a, socks5, socks5h)
* Recursive scanning
* URL Duplication detection
* ANSI and Windows good ol' cmd.exe support

This small tool is very useful if you have a an old blog/website and you want to check all links in it if it still working or need to be updated. It can be used for other tasks as well.

## Downloads

[Windows 64bit](https://github.com/Xen-E/fud/releases/download/1.0/FUD_1_0-x86_64.zip){:class="downloadBtn"}
[Windows 32bit](https://github.com/Xen-E/fud/releases/download/1.0/FUD_1_0-i686.zip){:class="downloadBtn"}
[Linux Binary (64bit)](https://github.com/Xen-E/fud/releases/download/1.0/FUD_1_0-Linux-x86_64.tar.xz){:class="downloadBtn"}

Don't forget to check out [Releases Page](https://github.com/Xen-E/fud/releases).

## User Installation

1. Un-zip/decompress the file you downloaded
2. Open the folder/directory
3. You're going to find the executable inside, DO NOT OPEN IT
4. Use terminal/command-line instead. By right clicking an empty space and select "**Open in Terminal**" or if you on Windows you can **Shift+Right Click** then select "**Open command window here**". You can also just open the terminal and then use the classic "**cd**" command followed by the folder path which will work on all systems.

*TIP: If you use Windows then you can copy and paste the executable to **C:\Windows** and then you can use it from anywhere! In Linux you can put the executable in the **Home** folder (**~/**).*

## Usage

Call the executable name followed by files
```bash
./fud file1.html "file2.cpp" file3.js...etc
```
You can use directories/folders as well:
```bash
./fud dir1 "dir2" dir3...etc
```
The **--recursive** flag can be useful when you deal with directories, So instead of:
```bash
./fud dir1 dir1/dir2 dir1/dir2/dir3...etc
```
Use:
```bash
./fud dir1 --recursive
```
This will scan all the regular files in this directory recursively.

You can use **--help** for more info or continue reading...

* **--timeout=[NUMBER]**, Request timeout in seconds. default is 30sec.

* **--recursive**, Scans directories recursively. Takes no value and by default is disabled.

* **--ipv6=[TRUE,FALSE]**, Enables IPv6 support instead of IPv4, keep in mind that IPv6 is slower than IPv4, default is false.

* **--followredirects=[TRUE,FALSE]**, If set true then it will follow any HTTP redirect during request. default is true.
* **--maxredirects=[NUMBER]**, Requires previous flag. Maximum number of redirects to follow, using "-1" means for infinity. default is -1.

* **--redirectsprotocols=[protocols]**, Which protocols will be accepted during URL request redirect following process. If you desire to use other protocols you can use these: *all,http,https,ftp,ftps,file,gopher,imap,imaps,ldap,ldaps,pop3,pop3s,rtmp,rtmpe,rtmps, rtmpt,rtmpte,rtmpts,rtsp,scp,sftp,smb,smbs,smtp,smtps,telnet,tftp,dict*. Remember to separate them using comma(**,**) and without spaces. If no protocols specified then "**all**" option will be used by default which will activate the following protocols: HTTP, HTTPS, FTP, FTPS.

* **--ansi=[TRUE,FALSE]**, Enables ANSI escape sequences, Useful for modern terminals and POSIX systems. default is auto which means false in windows and true in other systems.

* **--verbose**, Enables verbose mode which will print more details, It's good for debugging. Takes no value and by default is disabled.

* **--duplicatecheck**, All URLs will be checked even the duplicates. Takes no value and by default is disabled.

* **--proxy=[SCHEME://PROXY:PORT]**, Uses proxy during requests; Numerical IPv6 proxies must be written within brackets **[]**, as for protocols you can use: *http, https, socks4, socks4a, socks5, socks5h*. if no scheme/protocol is specified then **http://** will be used, and if no port is specified then **1080** will be used.

## Dev Installation

Nothing special, just make sure you have **libcurl** installed in your OS/toolchain:

Debian based (Ubuntu, Mint, Pop!_ OS..etc)
```bash
sudo apt install libcurl4-openssl-dev
```
Arch based
```bash
sudo pacman -S libcurl-openssl-dev
```
*Notice that this will install the openssl default version, there's other flavors. Check your package manager.*

That's it! the rest of work is done by cmake, here's how:
```bash
mkdir build
cd build
cmake ..
make -j4
```
If you're a Windows user i suggest you to setup a [MSYS2](https://www.msys2.org/) environment and get used to it, because Windows in general is not that great for software development, It also comes with a better terminal (command-line) Just make sure you have the GCC/libcurl installed and then use the cmake -G flag to generate the Makefiles:
```bash
mkdir build
cd build
cmake -G"MSYS Makefiles" ..
make -j4
```
OR just download the [libcurl](https://curl.se/libcurl) library and use it. You can also download the source code and then build it with ./configure


## License
File URLs Doctor is Licensed under the GNU Lesser General Public License version 3 (LGPLv3).
Please read the COPYING.LESSER file for more info. OR visit the [Free Software Foundation](https://www.gnu.org/licenses/lgpl-3.0.en.html) website.
