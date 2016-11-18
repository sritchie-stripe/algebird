---
layout: docs
title:  "Type Classes"
section: "typeclasses"
position: 1
---

# Type Classes

{% for x in site.pages %}
{% if x.section == 'typeclasses' %}
- [{{x.title}}]({{site.baseurl}}{{x.url}})
{% endif %}
{% endfor %}
