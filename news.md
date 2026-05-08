---
layout: page
title: "News"
subtitle: "Updates from the EEG101 network"
description: "Latest news and announcements from EEG101 COST Action CA24148."
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

*To add a news item, edit [`_data/news.yml`](https://github.com/eeg101-costaction/website/blob/main/_data/news.yml) — see the [README](https://github.com/eeg101-costaction/website#adding-a-news-item) for instructions.*
