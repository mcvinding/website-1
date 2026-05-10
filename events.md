---
layout: page
title: "Events"
subtitle: "EEG101 meetings and conferences"
description: "Upcoming and past events from the EEG101 COST Action — working group meetings, distributed conferences, and community events."
permalink: /events/
---

{::nomarkdown}
{% assign now_epoch = "now" | date: "%s" | plus: 0 %}
{% assign thirty_days_ago_epoch = now_epoch | minus: 2592000 %}

{% assign upcoming_events = "" | split: "" %}
{% assign recent_events = "" | split: "" %}
{% assign past_events = "" | split: "" %}

{% for event in site.data.events %}
  {% assign event_epoch = event.start_date | date: "%s" | plus: 0 %}
  {% if event_epoch >= now_epoch %}
    {% assign upcoming_events = upcoming_events | push: event %}
  {% elsif event_epoch >= thirty_days_ago_epoch %}
    {% assign recent_events = recent_events | push: event %}
  {% else %}
    {% assign past_events = past_events | push: event %}
  {% endif %}
{% endfor %}

{% assign upcoming_events = upcoming_events | sort: "start_date" %}
{% assign recent_events = recent_events | sort: "start_date" | reverse %}
{% assign past_events = past_events | sort: "start_date" | reverse %}

{% if upcoming_events.size > 0 %}
<h2>Upcoming events</h2>
<div class="row g-4">
{% for event in upcoming_events %}
<div class="col-12 col-md-6 col-lg-4">
{% include event-card.html event=event computed_status="upcoming" %}
</div>
{% endfor %}
</div>
<hr>
{% else %}
<p class="text-muted">No upcoming events are currently listed. Check back soon or <a href="https://e-services.cost.eu/" target="_blank" rel="noopener">join via e-COST ↗</a> to stay connected with the network.</p>
<hr>
{% endif %}

{% if recent_events.size > 0 %}
<h2>Recent announcements</h2>
<div class="row g-4">
{% for event in recent_events %}
<div class="col-12 col-md-6 col-lg-4">
{% include event-card.html event=event computed_status="recent" %}
</div>
{% endfor %}
</div>
<hr>
{% endif %}

{% if past_events.size > 0 %}
<h2>Past events</h2>
<div class="row g-4">
{% for event in past_events %}
<div class="col-12 col-md-6 col-lg-4">
{% include event-card.html event=event computed_status="past" %}
</div>
{% endfor %}
</div>
{% endif %}
{:/nomarkdown}

---

## EEG101 event formats

**Working Group meetings** are held regularly (online or hybrid) for each Working Group. All EEG101 members are welcome. Dates announced on [Discord]({{ site.data.site.discord_url }}).

**Distributed Conference** — EEG101 adopts and extends the CuttingGardens distributed conference model: simultaneous satellite events across Europe, connected through live streaming and shared programming.

**Management Committee meetings** — The MC meets annually to review progress, approve grants, and set strategic direction.
