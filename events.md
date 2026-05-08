---
layout: page
title: "Events"
subtitle: "EEG101 meetings, schools, and conferences"
description: "Upcoming and past events from the EEG101 COST Action — working group meetings, summer schools, and distributed conferences."
permalink: /events/
---

{% assign upcoming = site.data.events | where: "status", "upcoming" | sort: "start_date" %}
{% assign past = site.data.events | where: "status", "past" | sort: "start_date" | reverse %}

{% if upcoming.size > 0 %}
## Upcoming events

<div class="row g-4">
{% for event in upcoming %}
<div class="col-12 col-md-6 col-lg-4">
{% include event-card.html event=event %}
</div>
{% endfor %}
</div>
{% else %}
<p class="text-muted">No upcoming events are currently listed. Check back soon or join <a href="{{ site.data.site.discord_url }}" target="_blank" rel="noopener">Discord</a> for announcements.</p>
{% endif %}

---

{% if past.size > 0 %}
## Past events

<div class="row g-4">
{% for event in past %}
<div class="col-12 col-md-6 col-lg-4">
{% include event-card.html event=event %}
</div>
{% endfor %}
</div>
{% endif %}

---

## EEG101 event formats

**Working Group meetings** are held regularly (online or hybrid) for each Working Group. All EEG101 members are welcome. Dates announced on [Discord]({{ site.data.site.discord_url }}).

**EEG101 Summer Schools** provide immersive, hands-on training in state-of-the-art EEG methodologies. Three schools are planned from Year 2 (Months 18, 30, and 42). Priority places for Young Researchers & Innovators and ITC-based participants.

**Distributed Conference** — EEG101 adopts and extends the CuttingGardens distributed conference model: simultaneous satellite events across Europe, connected through live streaming and shared programming.

**Management Committee meetings** — The MC meets annually to review progress, approve grants, and set strategic direction.

---

*To add an event, edit [`_data/events.yml`](https://github.com/eeg101-costaction/website/blob/main/_data/events.yml) — see the README for instructions.*
