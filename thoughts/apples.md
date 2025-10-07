---
layout: page
title: On Apples
subtitle: A Cultivar Criticism
category: thoughts
---

{% assign sorted_apples = site.data.apples | sort: "date" | reverse %}

{% for apple in sorted_apples %}
<strong>{{ apple.name }}:</strong><br>
{% if apple.rating -%}{{ apple.rating }}/10<br>{%- endif %}

- {{ apple.review }} ({{ apple.date | date: "%Y.%m.%d" }})
{% endfor %}



<br>[See Rankings](/thoughts/apple_rankings.html)  

___

_Apples are evaluated only by their quality as a snack. Plain, uncooked, sometimes refrigerated. Unless otherwise noted, all specimens were purchased from grocery stores in Texas._

The birth of this page may be in response to judgement of my once-uneducated apple preferences. Never should the apple consumer consume apples blindly. Genuine apple criticism is the only true path to a riper age. 

&mdash; Eric Moore, 2025.10.04