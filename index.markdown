---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: default
---

{% for post in site.posts %}
<article>
	<h2><a href="{{post.url}}" title="{{post.title}}">{{post.title}}</a></h2>
	<time datetime="{{post.date | date: "%Y-%m-%d"}}">{{post.date | date_to_long_string}}</time>	
	{% if post.excerpt %}
    	{{post.excerpt}}
	{% else %}
		{{post.content}}
	{% endif %}
</article>
{% endfor %}