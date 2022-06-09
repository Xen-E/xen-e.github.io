---
title: How to easily setup a Toolchain in Windows (Any Language)
description: For C/C++ or any other language of your choice.
category: Dev
tags:
- Toolchain
- Windows
- GCC
- Clang
- Compilers
- MSYS2
---

Microsoft Windows is one of the best operation systems out there when it comes to casual desktop use or gaming. Unfortunately the same cannot be said when it comes to software or web development, For many reasons; like for example the lack of the famous unix shell which was designed by the legendary [Ken Thompson](https://en.wikipedia.org/wiki/Ken_Thompson) himself back in the early 70's. Microsoft tried to implement it in Windows 10 through a setting called "Windows Subsystem for Linux" but it didn't took off because many people hated Windows 10 including myself and also didn't solve many other issues, It was much easier to use a 3rd party software or just dual-boot than developing apps on Windows under WSL.<!--more-->


As of now i use Ubuntu 20.04.4 LTS (Focal Fossa) as my main driver and planning to upgrade next LTS release which is going to be around late july/August. But i also use Windows 7 (Ultimate, Service Pack 1) and i do enjoy it despite Microsoft drop it back in 2020 (F*ck this year); And i don't think i'm going to upgrade any time soon!

I use Windows 7 for causal web browsing or gaming, but sometimes i use it to make software as well or test my source code if it works in Windows... Here's how i created a powerful toolchain that works with most programming languages:

## MSYS2
[Minimal System 2](https://www.msys2.org) is a software distribution and a development platform for Microsoft Windows, It's an alternative to Cygwin, WSL...etc; Based on my experience it is one of the best in town and also have the second best package manager (**pacman**).

## Installation
either head over to the [releases page](https://github.com/msys2/msys2-installer/releases) and pick your installer from there or you can download this [msys2-x86_64-20220603.exe](https://github.com/msys2/msys2-installer/releases/download/2022-06-03/msys2-x86_64-20220603.exe) version.


After downloading the executable; run it and follow the instruction, Remember you're going to need Windows 7 or newer, and only 64bit. Also it's highly recommended to install it in **C:/msys64**.

## Getting Things Done
After you made sure the MSYS2 is installed and ready you're going to end up with 3 types of terminals (command-line):

1. The 32bit version (**mingw32.exe**), Has a greyish color.
2. The 64bit version (**mingw64.exe**), Has a blue color.
3. The standard shell launcher (**msys2.exe**), Has a purple color.

The first two are used for toolchains, The 3rd is used when you need to control MSYS2, Like for example right now we need to update our packages because we just did a fresh install; Open the executable **msys2.exe** and type:

```bash
pacman -Syu
```
This will check for any updates available and will ask you if you want to proceed or not (y for YES, n for NO).

## Fun
Now that everything is installed and setup you can pick whatever package you want to install. Just use:

```bash
pacman -S [PACKAGE]
```

So if you're a C/C++ lover you can get your GCC toolchain by using:

```bash
pacman -S --needed base-devel mingw-w64-x86_64-toolchain
```

OR Clang:

```bash
pacman -S --needed base-devel mingw-w64-clang-x86_64-toolchain
```

Rust:
```bash
pacman -S mingw-w64-x86_64-rust
```

Python v3+ (latest):
```bash
pacman -S mingw-w64-x86_64-python
```

Python v2
```bash
pacman -S mingw-w64-x86_64-python2
```

CMake:
```bash
pacman -S mingw-w64-x86_64-cmake
```

Ninja:
```bash
pacman -S mingw-w64-x86_64-ninja
```


If you want a 32bit version of the package then simply replace **x86_64** with **i686**:
* mingw-w64-i686-toolchain
* mingw-w64-clang-i686-toolchain
* mingw-w64-i686-rust
* mingw-w64-i686-python
* mingw-w64-i686-python2
* mingw-w64-i686-cmake
* mingw-w64-i686-ninja
* ...etc

Remember to use the 64bit (**mingw64.exe**) shell for **x86_64** packages and the 32bit (**mingw32.exe**) for **i686** packages.

Many more programming/script languages and other packages are available [HERE](https://packages.msys2.org).

This toolchain is highly customizable and very easy to use, It makes developing software under Windows fun and no different from POSIX systems.
