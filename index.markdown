---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: default
---

{% for post in site.posts %}
<article>
	<h2><a href="{{post.url}}" title="{{post.title}}">{{post.title}}</a></h2>
	<time datetime="{{post.date | date: "%B %d. %Y"}}">{{post.date | date: "%B %d. %Y"}}</time>
	{% if post.excerpt %}
    	{{post.excerpt}}
	{% else %}
		{{post.content}}
	{% endif %}
</article>
<hr>
{% endfor %}