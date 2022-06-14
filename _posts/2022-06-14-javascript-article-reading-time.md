---
title: Easily add "Reading Time" to your website or blog
description: How to use a simple code of javascript to calculate reading time of an article.
category: Dev
tags:
- Javascript
- Web
- Static
---

Have you ever stumbled upon a website or a blog with a "**T** read" feature? Usually under or next to the article title; I use this little trick myself so you probably noticed it already, Well this cool trick it can help your viewers decide if they want to read the current article right now or maybe save it for later, Instead of scrolling all the way to find out.<!--more-->

You may think implementing this feature in your website can be hard or you have to be more than a code monkey. But actually it's very easy and we can do it with some small Javascript code plus some HTML/CSS styling! This method will work with all websites, Dynamic or static. It doesn't matter because Javascript work out of the box unlike *PHP*, *Python*...etc.

Here's how:
1. First we make sure the article content is in a identified element so we can get the data
2. We extract the content and then split it into words using special characters (spaces)
3. Divide the words total by the average adult WPM (Words per Minute)
4. Show the result in a element

So let us begin. First of all make sure your article is inside of a identified element. Something like this:

```html
<div id="articleContent">CONTENT</div>
```
Now we're going to add our Javascript function, you can put it inside the `<head>` element but i don't recommend doing this because it will get loaded every time your website is used which is a waste of resources; just use the `<script>` tag and put it inside your post or article template or the file is used to display the article:

```javascript
function calcArticle() {
	//Getting the article inner text (content)
	const text  = document.getElementById("articleContent").innerText;

	//Average adult words per minute
	const wpm   = 238;

	//Splitting the article content into words using the space special char
	const words = text.trim().split(/\s+/).length;

	//Calculate reading time by dividing words by words per minute
	const time  = Math.ceil(words / wpm);

	//Display result into a element of our choice (readingTime)
	document.getElementById("readingTime").innerHTML = "~<strong>" + time + "</strong> " + "Minute(s) read. " + "<strong>" + words + "</strong> Words in this article.";
}
```

Now make sure you have the "**readingTime**" element ready, You can use a `span` or `div` it doesn't matter just make sure you identify it. Example:

```html
<span id="readingTime"></span>
```
Also use the `noscript` tag to handle errors when Javascript is disabled by user. Add this under or above "**readingTime**" element:
```html
<noscript style="color:orange;">Javascript is disabled. Can't calculate article reading time.</noscript>
```
Finally we're going to call the function after the content is loaded which's below the "**articleContent**" element:

```html
<script>calcArticle();</script>
```

That's it! We finished, give it a test and see how it looks. Now remember you can style it through CSS just like everything else:

```css
span#readingTime {
	font-size: 12px;
	font-style: italic;
	color: gray;
}
```

Also you may wonder how i knew that the average adult words per minute is **238**? Well...I did some quick googling and read many studies until i found [this paper](https://www.sciencedirect.com/science/article/abs/pii/S0749596X19300786#:~:text=Abstract,and%20260%20wpm%20for%20fiction.); It had a lot of citation and it was peer-reviewed.

> Based on the analysis of 190 studies (18,573 participants), we estimate that the average silent reading rate for adults in English is 238 words per minute (wpm) for non-fiction and 260 wpm for fiction.