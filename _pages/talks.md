---
title: "Talks"
layout: gridlay
sitemap: false
permalink: /talks/
---

### Talks

{% if site.data.talks.conference_talks %}
## Conference presentations
<div class="rowl1" style="padding-top: 10px;">

{% for talk in site.data.talks.conference_talks %}
{{ forloop.index }}. <strong>{{ talk.title }}</strong> <br/> <i>{{ talk.authors }}</i>, {{ talk.conf }} ({{ talk.year }}).
{% endfor %}
</div>
{% endif %}

{% if site.data.talks.invited_talks %}
## Talks and webinars
<div class="rowl1" style="padding-top: 10px;">

{% for talk in site.data.talks.invited_talks %}
{{ forloop.index }}. {% if talk.link %}<a href="{{ talk.link }}" target="_blank">{% endif %}<strong>{{ talk.title }}</strong>{% if talk.link %}</a>{% endif %} ({{ talk.year }}){% if talk.subtitle %}<br>{{ talk.subtitle }}{% endif %}.
{% endfor %}
</div>
{% endif %}