## Resor

{% assign grouped_pages = site.pages | group_by:"trip_name" %}
{% for group in grouped_pages %}
{% unless group.name == "" %}

### {{ group.name }}

{% capture places %}{% for post in group.items %}{% if post.lat %}{% unless forloop.first %}|{% endunless %}{{ post.title }},{{ post.lat }},{{ post.lng }}{% endif %}{% endfor %}{% endcapture %}
{% capture links %}{% for post in group.items %}{% if post.lat %}{{ post.url }},{% endif %}{% endfor %}{% endcapture %}
{% if places %}{% include map.html places=places links=links id=group.name %}{% endif %}

{% endunless %}
{% endfor %}

### ToDo
- [ ] Förstasida
- [x] Karta över varje resa
