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

{::nomarkdown}
<div class="news-filter" id="newsFilter" role="group" aria-label="Filter news by category">
<button class="news-filter__btn active" data-filter="all">All</button><button class="news-filter__btn" data-filter="Announcement">Announcements</button><button class="news-filter__btn" data-filter="Grants">Grants</button><button class="news-filter__btn" data-filter="Events">Events</button>
</div>
{:/nomarkdown}

<div class="row g-4" id="newsGrid">
{% for item in all_news %}
<div class="col-12 col-sm-6 col-lg-4" data-category="{{ item.category }}">
{% include news-card.html item=item %}
</div>
{% endfor %}
</div>

<script>
(function(){var btns=document.querySelectorAll('.news-filter__btn');btns.forEach(function(btn){btn.addEventListener('click',function(){btns.forEach(function(b){b.classList.remove('active');});this.classList.add('active');var f=this.dataset.filter;document.querySelectorAll('#newsGrid [data-category]').forEach(function(c){c.style.display=(f==='all'||c.dataset.category===f)?'':'none';});});});})();
</script>

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
