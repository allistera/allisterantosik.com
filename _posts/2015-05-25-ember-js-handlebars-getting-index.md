---
layout:     post
title:      Ember.js Tip - Getting index in handbars loop
date:       2015-05-25
summary:    Quick tip on getting the current index when looping around an array in handlebars.js 
---

Just a quick tip for Ember.js handbars templates.

To return the current index we can use the <code>_view.contentIndex</code>
variable from within an each loop.

Quick Example:

{% hightlight javascript %}
{{#each result in calculation-results}}
  Index: {{_view.contentIndex}}
{{/each}}
{% endhightlight %}
