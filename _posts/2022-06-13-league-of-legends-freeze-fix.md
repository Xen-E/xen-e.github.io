---
title: League of Legends freeze at minute 7 fix
description: The game freezes at minute 7 or 8? Here's how to fix it.
category: How-To
tags:
- League
- Legends
- Games
- Fix
- Freeze
---

League of Legends is one of the best games of all time. This according to statistics and whether we like it or not, it's very addictive; So if you're a millennial or a zoomer you definitely have tried it before in your life and if you say otherwise i won't believe you :)<!--more-->

MOBA games in general relays mainly on three things: **Teamwork**, **High FPS** and **Low Ping**. You can live without the first one and maybe carry your trash team, but the last two are necessary for having a good quality gaming.

One of the most frustrating experience i had in this game (besides matchmaking) is the minute 7 or 8 freezing bug! Basically you open up the client and you login then queue up then go through champion select and then get into a game; everything works fine and smooth... BUT when minute 7 or 8 approach the game freezes and nothing you can do to bring it back, not even your friend **CTRL+ALT+DEL**! Also you can't kill it from the task manager by selecting "End Process".

This mysterious bug drove me crazy; and i almost quit the game because of it. I found 0 solutions/explanations online not even in Riot Games forums. Until months later some clues began to appear, here's some:

* The bug only happens to Intel processors.
* The bug only occur on Windows.
* This means that this bug has a connection with DirectX. The framework Riot Games used to create this game.
* The bug didn't occur in old patches. that means something changed by the software engineers created this bug.

## FIX
There's two ways to fix this annoying bug; The good ol' fashioned way or using the new option which was implemented recently by Riot Games in their client:

### Old ways:
1. Make sure everything related to LoL or Riot Games is closed.
2. Go to Riot Games installation folder (**C:\Riot Games**), then enter "**League of Legends**" directory then into "**Config**" directory; So the full path is: **C:\Riot Games\League of Legends\Config**.
3. Find a configuration file called "**game.cfg**".
4. Open it with your favorite text editor or just the classical Windows notepad.exe
5. Find a option called "**PreferDX9LegacyMode**" and change it's value from 0 to **1**. Example: **PreferDX9LegacyMode=1**
6. Save the config file that you just edited

### New Easy Method:
1. Open the LoL client and login to your account
2. Open the options menu from the top right corner (between **X** and **_**)
3. Select "**GAME**" from the left panel
4. In the first section "**GRAPHICS**" you're going to find a option called "**Prefer DX9 Legacy Mode**"; Check it and then click "**DONE**".

That's it! This should fix this damn annoying bug and also roll back the DirectX version to 9 which in my opinion is much better.