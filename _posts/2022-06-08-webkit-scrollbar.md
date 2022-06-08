---
title: How to create beautiful Scrollbars using pure CSS
description: For your website or your electron app.
category: Dev
tags:
- CSS
- Web
---

Before anything; This tutorial is for browsers that uses the **Blink** engine, Like Chrome/Edge/Opera...etc. Firefox is excluded because it has it's own engine called "gecko" and there's a new one under development called "servo" written in their new programming language "Rust". Unfortunately none of these two engines support custom scrollbars (only color/width) and their performance is limited compared to Blink as well.<!--more-->

Blink is a fork of the WebCore component of **WebKit** which was originally a fork of the KHTML and KJS libraries from KDE. That's why when we write CSS for Chrome for example we use the keyword "webkit".

Anyway, let's get this tutorial started. First of all make sure you have your **style.css** file ready and linked then begin with this line:

```css
::-webkit-scrollbar { width: 13px; }
```

This will determinate the scrollbar width, change the pixel number if you want. Now let's color the scrollbar:

```css
::-webkit-scrollbar-track { background: #303030; }
::-webkit-scrollbar-thumb { background: #b5e853; }
```

This will color the track and the thumb (handle) of the scrollbar, Now let's give the thumb a hover effect:

```css
::-webkit-scrollbar-thumb:hover { background: #7fad28; }
```

Cool, You can now test it but our job is not done because there's no Buttons! Add them:

```css
::-webkit-scrollbar-button {
	background-size: 100%;
	background-color: #b5e853;
	height: 13px;
	width: 13px;
}
::-webkit-scrollbar-button:hover { background-color: #7fad28; }
```

Notice that we also added the hover effect by using the **:hover** selector. Now let's finish our buttons by adding icons to them:

```css
::-webkit-scrollbar-button:vertical:increment {
	background-image: url(../images/scroll_down.png);
}
::-webkit-scrollbar-button:vertical:decrement {
	background-image: url(../images/scroll_up.png);
}
::-webkit-scrollbar-button:horizontal:increment {
	background-image: url(../images/scroll_right.png);
}
::-webkit-scrollbar-button:horizontal:decrement {
	background-image: url(../images/scroll_left.png);
}
```

*You may wonder why there's 4 icons? because you forgot about the horizontal scrollbar :)*

Change **../images/ICON.png** to your desired path. And here's the icons:

1. [scroll_down.png](/assets/images/scroll_down.png)
2. [scroll_up.png](/assets/images/scroll_up.png)
3. [scroll_right.png](/assets/images/scroll_right.png)
4. [scroll_left.png](/assets/images/scroll_left.png)

Now head over to your web-page and test the scrollbar! 

Psst! Here's a little trick that you can use to get the buttons next to each other just like in Mac OS X or other fancy products:

```css
::-webkit-scrollbar-button:end { display: block; }
::-webkit-scrollbar-button:start { display: none; }
```

Here's the full code and also you can test the final result right here:

```css
/* Width */
::-webkit-scrollbar { width: 13px; }
/* Track */
::-webkit-scrollbar-track { background: #303030; }
/* Handle */
::-webkit-scrollbar-thumb { background: #b5e853; }
/* Handle on mouse hover */
::-webkit-scrollbar-thumb:hover { background: #7fad28; }

/* UP/DOWN Buttons */
::-webkit-scrollbar-button {
	background-size: 100%;
	background-color: #b5e853;
	height: 13px;
	width: 13px;
}
/* UP/DOWN Buttons on mouse hover */
::-webkit-scrollbar-button:hover { background-color: #7fad28; }

/* VERTICAL SCROLLBAR */
::-webkit-scrollbar-button:vertical:increment {
	background-image: url(../images/scroll_down.png);
}
::-webkit-scrollbar-button:vertical:decrement {
	background-image: url(../images/scroll_up.png);
}
/* HORIZONTAL SCROLLBAR */
::-webkit-scrollbar-button:horizontal:increment {
	background-image: url(../images/scroll_right.png);
}
::-webkit-scrollbar-button:horizontal:decrement {
	background-image: url(../images/scroll_left.png);
}

/* Moves Buttons next to each other <3 */
::-webkit-scrollbar-button:end { display: block; }
::-webkit-scrollbar-button:start { display: none; }
```