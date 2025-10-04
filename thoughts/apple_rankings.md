---
layout: page
title: Results
subtitle: Best Apples, Ranked Objectively
---

{% assign sorted_by_rating = site.data.apples | sort: "rating" | reverse %}

{% for apple in sorted_by_rating %}
<strong>{{ apple.name }}:</strong> {{ apple.rating }}/10<br>
{% endfor %}
