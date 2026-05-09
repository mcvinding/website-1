---
layout: page
title: "News & Events"
subtitle: "Updates, announcements, and upcoming events from the EEG101 network"
description: "Latest news and events from EEG101 COST Action CA24148."
permalink: /news/
---

{% assign featured = site.data.news | where: "featured", true %}
{% assign all_news = site.data.news | sort: "date" | reverse %}

{% if featured.size > 0 %}
## Featured

<div class="row g-4 mb-5">
{% for item in featured %}
<div class="col-12 col-md-6">
{% include news-card.html item=item %}
</div>
{% endfor %}
</div>

---
{% endif %}

## All news

<div class="row g-4">
{% for item in all_news %}
<div class="col-12 col-sm-6 col-lg-4">
{% include news-card.html item=item %}
</div>
{% endfor %}
</div>

---

## Events

{% assign upcoming = site.data.events | where: "status", "upcoming" | sort: "start_date" %}
{% assign past_events = site.data.events | where: "status", "past" | sort: "start_date" | reverse %}

{% if upcoming.size > 0 %}
### Upcoming

<div class="row g-4">
{% for event in upcoming %}
<div class="col-12 col-md-6 col-lg-4">
{% include event-card.html event=event %}
</div>
{% endfor %}
</div>
{% endif %}

{% if past_events.size > 0 %}
### Past events

<div class="row g-4 mt-2">
{% for event in past_events %}
<div class="col-12 col-md-6 col-lg-4">
{% include event-card.html event=event %}
</div>
{% endfor %}
</div>
{% endif %}
