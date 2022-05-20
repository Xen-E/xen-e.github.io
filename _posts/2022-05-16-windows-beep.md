---
title: Windows Beep
tags:
- Beep
- Speakers
- Motherboard
- Windows
---

![Motherboard internal speakers]({{site.url}}/images/internal_speakers.jpg){:class="image_right"}
Computers back in the day used to be shipped with something called PC Internal Speakers which was mainly used by the BIOS and sometimes old software, today motherboards still have a port for them but you have to buy one now instead of getting it for free. i got mine from my old Pentium 4 PC when i was cleaning stuff i used it on my newer motherboard to see if still works and it did! but only when i turned on the PC not when i logged in to Windows. <!--more-->


The reason behind that is because Microsoft dropped the support for their "**beep**" driver which is located in "*C:\Windows\System32\drivers\beep.sys*". The affected systems are Windows XP 64-bit edition and Windows Vista. All Windows versions after that didn't support the classic "beep" sound in motherboards including Windows 7 which is i was using.

Here's how you fix it; Go to [this page](http://www.waldbauer.com/tmp/dl.php?download=beepx) and download the modified driver of "beep.sys" (They have a [64-bit version](http://www.waldbauer.com/tmp/dl.php?download=beepxp64) as well) then:

1. Un-zip the file
2. open **cmd** as admin and type:
```bash
sc config Beep start= demand
```
*notice the space before **demand***

4. Now right click on **beepxp.inf** and select **Install**. The driver will now be installed into the system. If there are no errors on installation, it will silently proceed.
5. Reboot/Restart your PC.

The new driver you just installed is called **BeepXP** and the old one is just **Beep**, so if you want to uninstall it just type in the **cmd**:
```bash
sc config BeepXP start= demand
sc config Beep start= auto
```
After restart you should have a full functioning internal speaker, I made a small single CPP file that can play a set of songs to test your speaker you can find it [here](https://github.com/Xen-E/windows-beep), just clone and build and start using it:
```bash
git clone https://github.com/Xen-E/windows-beep.git
cd windows-beep
build.bat
beep.exe test1
```

