---
title: Create a pretty website scroll indicator
description: Learn how to create a website scrolling progress indicator 
category: Dev
tags:
- Web
- CSS
- Javascript
---

Most modern websites have a gauge or a [progress bar](https://en.wikipedia.org/wiki/Progress_bar) at the top of their page indicating something. It could be used to show loading time like for example in Youtube/Github... OR it can be used to show current scrolling position and how much left, Which can be very useful to your visitors. This can be seen and tested right here in this site because i use it myself. You can say that this new idea is now part of the **Web3** culture and it's not going away any time soon; so you most adapt.<!--more-->

Here's how you can implement an easy customizable progress bar for your website or blog; First of all we need to add our HTML code inside the `body` element (tag), make sure to put it right below it (first in order):
```html
<div class="PBContainer">
    <div class="PB" id="PB"></div>
</div>
```
Now let's style it little bit, Remember that you can modify this codes to your needs and you don't have to mimic everything:
```css
.PBContainer {
	position: fixed; /* Making sure it scrolls with content */
	z-index: 9999; /* This will put the PB on top of all elements and give it priority */
	width: 100%;
	height: 8px;
	background: rgb(107, 107, 107);
}
.PB {
	width: 0%;
	height: 8px;
	border-radius: 0 5px 5px 0; /* Remove it if you hate curvy borders */
	background: #b5e853;
}
```
That's it! Now you have a progress bar on the top of your webpage ready to be used; Now let's use it for indicating the window scrolling progress!

Add this Javascript code to your header inside a `<script>` element or create a new JS file with this code then link it using `<script src="myscript.js"></script>`:
```javascript
window.onscroll = function() {

    //Getting current scrolling position
    var winScroll = document.body.scrollTop || document.documentElement.scrollTop;

    //Getting the total height of current webpage
    var height    = document.documentElement.scrollHeight - document.documentElement.clientHeight;

    //Percentage formula: (value/total value)×100%
    var scrolled  = (winScroll / height) * 100;

    //Changing CSS property "width" by percentage using "%" instead of "px" or "cm"...
    document.getElementById("PB").style.width = scrolled + "%";
};
```
As you can see we're using the `onscroll` event of current window to trigger action, This function will be called every time the user scrolls, It doesn't matter if he/she uses Mouse-Wheel or Mouse buttons/Keyboard...etc; As long the window scrolls this will be called immediately and the progress bar gets updated.