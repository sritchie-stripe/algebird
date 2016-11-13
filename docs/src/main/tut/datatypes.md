---
layout: docs
title:  "Data Types"
section: "data"
position: 2
---

# Algebird's Data Types

Algebird is, first and foremost, a library of data structures for large-scale analytics. Here are the data structures currently implemented:

## Approximate Data Types

{% for x in site.pages %}
  {% if x.section == 'approx' %}
- [{{x.title}}]({{site.baseurl}}{{x.url}})
  {% endif %}
{% endfor %}

## Data Types

{% for x in site.pages %}
  {% if x.section == 'data' %}
- [{{x.title}}]({{site.baseurl}}{{x.url}})
  {% endif %}
{% endfor %}

## Combinators

{% for x in site.pages %}
  {% if x.section == 'combinator' %}
- [{{x.title}}]({{site.baseurl}}{{x.url}})
  {% endif %}
{% endfor %}

## Summers

{% for x in site.pages %}
  {% if x.section == 'summer' %}
- [{{x.title}}]({{site.baseurl}}{{x.url}})
  {% endif %}
{% endfor %}
