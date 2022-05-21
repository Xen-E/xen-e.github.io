---
title: How to make GCC/Clang produce a very small executable
description: Learn how to force the GCC and Clang compilers to produce a very small binary files using special flags.
tags:
- GCC
- Clang
- Compilers
- Flags
- Binary
- UPX
---

Sometimes size matters! especially if you're working with medium/big projects that will produce a gigantic executables. Well... Here's my secret sauce to make compilers generate very small files + another trick that you may not know about.

First of all let's make a small program to test our new compiling flags, you can make your own or just use this code i made for this experiment:<!--more-->

```cpp
/*
	This CPP file will print the classic fibonacci series after done checking for errors
	this was made for: https://xen-e.github.io/2022/05/21/gcc-clang-small-binary.html
	i needed a small program for an example.
	- Xen
*/

#include <iostream>
using namespace std;

int main()
{
	//Init vars
	int n, t1 = 0, t2 = 1, nextTerm = 0;

	cout << "Enter a positive number: "; cin >> n;

	//Checking everything is OK before we start
	if (!cin) {
		cerr << "Not a number.";
		return -1; //exit with error code
	}

	if (n < 0) {
		cerr << "Not a positive number.";
		return -1;
	}

	cout << endl << "Fibonacci Series: ";

	for (int i = 1; i <= n; i++) {
		//displays the first two terms which is always 0 and 1
		if (i == 1) { cout << t1 << ", "; continue; }
		if (i == 2) { cout << t2 << ", "; continue; }
		
		//Calculates and prints the sum of previous two numbers
		nextTerm = t1 + t2;
		t1 = t2;
		t2 = nextTerm;
		
		cout << nextTerm;

		//Use comma only when needed
		if (i < n) cout << ", "; else cout << endl;
	}

	return 0; //exit with success code
}
```

Compiling this using the **g++ version 10.2.0** with "**g++ fibonacci.cpp**" on **Windows 7 Ultimate Service Pack 1 64bit** produced a **128KB** binary file (131,743 bytes), this info was taken from Properties window.

Now let's compile again the source file using the same toolchain and OS but with these following flags instead and then see the difference:

```bash
g++ -Os -s -ffunction-sections -fdata-sections -Wl,--gc-sections -DNDEBUG fibonacci.cpp -o fibonacci
```

1. **-Os**, "O" is short for optimization/optimize and "s" is for size.
2. **-s**, removes a set of unnecessary info during linking time.
4. **-ffunction-sections**, **-fdata-sections**, **-Wl,--gc-sections**, these flags will remove all the unused sections, like functions and symbols...etc.
5. **-DNDEBUG**, this is a macro that disables debugging.

The binary file size now is **16KB**! (16,384 bytes) Which means the new executable is now **87%** smaller!

Now let's take it even further beyond and use the classic [UPX](https://upx.github.io) compressing tool:

```bash
upx fibonacci.exe
```

This is the output:
```bash

                       Ultimate Packer for eXecutables
                          Copyright (C) 1996 - 2020
UPX 3.96w       Markus Oberhumer, Laszlo Molnar & John Reiser   Jan 23rd 2020

        File size         Ratio      Format      Name
   --------------------   ------   -----------   -----------
     16384 ->      9216   56.25%    win64/pe     fibonacci.exe
```

The binary file now is **9KB** (9,216 bytes).

This tutorial also applies to the Clang compiler by LLVM because it can accept the GCC flags as well. All the tools i used here are cross-platform, so you're not forced to use Windows.