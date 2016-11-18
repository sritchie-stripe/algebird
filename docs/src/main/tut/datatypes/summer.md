---
layout: docs
title:  "Summers"
section: "data"
---

Talk about StatefulSummer

# StatefulSummer

/**
 * A Stateful summer is something that is potentially more efficient
 * (a buffer, a cache, etc...) that has the same result as a sum:
 * Law 1: Semigroup.sumOption(items) ==
 *   (Monoid.plus(items.map { stateful.put(_) }.filter { _.isDefined }, stateful.flush) &&
 *     stateful.isFlushed)
 * Law 2: isFlushed == flush.isEmpty
 */


# Summers

{% for x in site.pages %}
  {% if x.subsection == 'summer' %}
- [{{x.title}}]({{site.baseurl}}{{x.url}})
  {% endif %}
{% endfor %}
