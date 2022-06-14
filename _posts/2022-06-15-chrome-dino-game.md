---
title: How to Enable/Disable Google's "Dino" game in Chrome
description: The T-Rex video game that you accidentally discovered. 
category: How-To
tags:
- Google
- Chrome
- Games
- EasterEgg
---

Have you ever had internet issues while using Google Chrome and stumbled upon a small pixelated [T-Rex](https://en.wikipedia.org/wiki/Tyrannosaurus)? Did you wonder why there's an extinct animal in your web browser during connection problems? Well...That's actually a video game! and it is very addictive one!<!--more-->

You don't need to cut off your internet connection to play it, just head over to the error page here: `chrome://network-error/-106` or its own official URL which's here: `chrome://dino`

![Dino Game Disabled]({{site.url}}/images/chrome_no_internet.jpg){:class="image_center"}

If you ever get that error page again go ahead and press `Space` or `↑` on *Desktop*, Or by tapping the dinosaur on *Android* or *iOS* mobile devices; During the game, the Lonely T-Rex continuously moves from left to right across a black and white desert landscape, with the player attempting to avoid oncoming obstacles such as cactus plants or the extinct [Pteranodon](https://en.wikipedia.org/wiki/Pteranodon) by jumping or ducking.

Pressing `Space` or `↑`, Or tapping the dinosaur on mobile devices will cause the dinosaur to jump, while pressing the `↓` key will cause the dinosaur to duck. As the game progresses, the speed of play gradually increases until the player hits an obstacle, prompting an instant game over.

Once the player reaches around 700 points, the game switches from dark gray graphics on a white background to pale gray graphics on a black background, Representing a shift from day to night, with daytime sky graphics also becoming nighttime sky graphics. The color scheme then alternates as the game progresses. The game was designed to reach its maximum score after approximately 17 million years of playtime, in reference to how long the T-Rex existed before it went extinct during the [Cretaceous–Paleogene extinction event](https://en.wikipedia.org/wiki/Cretaceous%E2%80%93Paleogene_extinction_event).

If a network administrator (root) disables the Dino Game, An error message appears when attempting to play the game; which features an image of a meteor heading towards the Lonely T-Rex!

Here's how you disable the Dino game in Microsoft Windows:

1. Create a restore point just in case
2. Hold the `Win` key and then press `R`
3. Type **regedit** and hit the `Enter` key or just click "OK"
4. If a confirmation appears click on the "Yes" button
5. Navigate to **SOFTWARE** in **HKEY_LOCAL_MACHINE**
6. Then navigate to **Policies**
7. Right-click on **Policies** then select New > Key
8. Name it as **Google**
9. Right-click on **Google** then select New > Key
10. Name it as **Chrome**
11. Right-click on **Chrome** then select New > DWORD (32-bit) Value.
12. Name it as **AllowDinosaurEasterEgg**

By default the value of this key is **0** which means false or disabled. If you want to enable the Dino game in the future then just change the value to **1**.

In POSIX systems like Linux or Mac they don't have a Registry, instead they use pure files; Known as the [Unix Philosophy](https://en.wikipedia.org/wiki/Unix_philosophy).

Go to `/etc/opt/chrome` and try to find a directory called **policies**, if it doesn't exist then create one and then create another directory called **managed** inside of it. So the whole path is `/etc/opt/chrome/policies/managed`

Now create a JSON file and name it anything you want, example `DinoGame.json` and write the following code:

```json
{
	"AllowDinosaurEasterEgg": false
}
```
Save it and then restart Chrome if it is already running. Here's what is looks like when the game is disabled:

![Dino Game Disabled]({{site.url}}/images/chrome_dino_disabled.jpg){:class="image_center"}