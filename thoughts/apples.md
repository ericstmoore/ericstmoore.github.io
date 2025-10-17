---
layout: page
title: On Apples
subtitle: A Cultivar Criticism
category: thoughts
---

{% assign apples_by_date = site.data.apples | sort: "reviews" | reverse %}

{% for apple in apples_by_date %}
<strong>{{ apple.name }}:</strong><br>
{% if apple.rating -%}{{ apple.rating }}/10<br>{%- endif %}

{% assign sorted_reviews = apple.reviews | sort: "date" | reverse %}
{% for review in sorted_reviews %}
- {{ review.review }} ({{ review.date | date: "%Y.%m.%d" }})
{% endfor %}
{% endfor %}

<br>[See Rankings](/thoughts/apple_rankings.html)  

___

_Apples are evaluated only by their quality as a snack. Plain, uncooked, sometimes refrigerated. Unless otherwise noted, all specimens were purchased from grocery stores in Texas._

The birth of this page may be in response to judgement of my once-uneducated apple preferences. Never should the apple consumer consume apples blindly. Genuine apple criticism is the only true path to a riper age. 

&mdash; Eric Moore, 2025.10.04
