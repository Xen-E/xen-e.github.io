---
title: Add pagination to your Github page or Jekyll website
description: Learn how to easily implement pagination to jekyll, the static site generator.
category: How-To
tags:
- Pagination
- Jekyll
- Plugin
---

My modified github pages theme didn't have pagination implemented already despite jekyll have a built-in plugin for it called **jekyll-paginate**, so i spent a lot of time trying to understand how it works until i got it done, here's how in short and a simplified manner.

If you're on github pages you don't need to install anything because it's already installed by default and cannot be removed, otherwise install the plugin i just mentioned in your jekyll system by using:<!--more-->

```bash
gem install jekyll-paginate
```

...After making sure the plugin is installed now open your config file "**_config.yml**" and add these two lines:

```bash
paginate: 5
paginate_path: "/page:num/"
```

Obviously the number "5" is how many posts you want to display per page, while the other is used for URL. "**:num**" is the number of page, you can change the word "**page**" with something else but it's recommended to leave like that.

Now in the same folder/directory find file called "**index.md**" or "**index.markdown**" and change the extension to HTML (**index.html**), if it's already an HTML file then leave like that and open the file.

You're going to find a loop that display posts using the "site.posts", change **site** to **paginator**. the code should be something like this:

{% raw %}
```html
<!-- Notice the "paginator.posts", it's important -->
{% for post in paginator.posts %}
<article>
	<h2><a href="{{post.url}}" title="{{post.title}}">{{post.title}}</a></h2>
	<time datetime='{{post.date | date: "%B %d. %Y"}}'>{{post.date | date: "%B %d. %Y"}}</time>
	{{post.content}}
</article>
{% endfor %}
```
{% endraw %}

Remember to keep your own original HTML code you don't have to to use this code, just change the loop originator.

Now head over to "**_layouts**" folder and find a file called **default.html** and open it. Pick a place where you want to show the pagination and add the following code:

{% raw %}
```html
<!-- Checks if current page is front page -->
{% if page.url == "/" or page.url contains "/page" %}
	<!-- Pagination div -->
	<div class="pagination">
		<!-- Previous span -->
		<span id="previous">{% if paginator.previous_page %}<a href="{{ paginator.previous_page_path }}">Previous</a>{% else %}<span>Previous</span>{% endif %}</span>
		<!-- Page Numbers span -->
		<span id="page_number"> | Page: {{ paginator.page }} of {{ paginator.total_pages }} | </span>
		<!-- Next span -->
		<span id="next">{% if paginator.next_page %}<a href="{{ paginator.next_page_path }}">Next</a>{% else %}<span>Next</span>{% endif %}</span>
	</div>
{% endif %}
```
{% endraw %}

The first conditional statement will make sure to show pagination only when user is on the front page and not in a post or other pages. Notice the **contains "/page"**, if you changed the **paginate_path** option in config file to other words then make sure to add them in this code as well. Example. if you used this option:

```bash
paginate_path: "/blog/pages:num/"
```

Then the first conditional statement should be:

{% raw %}
```html
{% if page.url == "/" or page.url contains "/blog/pages" %}
```
{% endraw %}

That's it! The only thing now left is the styling (CSS) which is fun! Here's a little example i made:

```css
/*
* This file is part of the jekyll pagination tutorial i made.
* For full article visit:
* https://xen-e.github.io/2022/05/22/jekyll-pagination.html
* - Xen
*/
.pagination {
	margin: auto;
	width: 60%;
	border: 2px solid rgb(175, 89, 175);
	border-radius: 7px;
	padding: 10px;
	text-align: center;
	font-size: 16px;
	background-color: rgb(241, 223, 241);
	color: rgb(162, 126, 185);
	cursor: default;
}
.pagination #previous a {
	cursor: pointer;
	text-decoration: none;
	font-weight: bold;
	color: hotpink;
}
.pagination #previous a:hover { color: rgb(243, 172, 208); }

.pagination #next a {
	cursor: pointer;
	text-decoration: none;
	font-weight: bold;
	color: hotpink;
}
.pagination #next a:hover { color: rgb(243, 172, 208); }

.pagination #page_number {
	font-size: 14px;
	padding: 0 10px;
}
```