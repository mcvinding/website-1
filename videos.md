---
layout: page
title: "Videos"
subtitle: "Talks, tutorials, and podcast episodes from EEG101"
description: "Watch EEG101 videos — podcast episodes, conference talks, tutorials, and working group content on YouTube."
permalink: /videos/
---

All EEG101 video content is published on the [EEG101 YouTube channel]({{ site.data.site.youtube_url }}){: target="_blank" rel="noopener"}. Subscribe to stay up to date.

<div class="text-center mb-5">
  <a href="{{ site.data.site.youtube_url }}" class="btn btn-primary" target="_blank" rel="noopener">
    Subscribe on YouTube ↗
  </a>
</div>

---

{% assign podcasts = site.data.videos | where: "category", "podcast" %}
{% assign talks = site.data.videos | where: "category", "talk" %}
{% assign tutorials = site.data.videos | where: "category", "tutorial" %}
{% assign all_videos = site.data.videos | sort: "date" | reverse %}

{% if podcasts.size > 0 %}
## Podcast episodes

<div class="row g-4 mb-5">
{% for video in podcasts %}
<div class="col-12 col-sm-6 col-lg-4">
{% include video-card.html video=video %}
</div>
{% endfor %}
</div>
{% endif %}

{% if talks.size > 0 %}
## Talks & presentations

<div class="row g-4 mb-5">
{% for video in talks %}
<div class="col-12 col-sm-6 col-lg-4">
{% include video-card.html video=video %}
</div>
{% endfor %}
</div>
{% endif %}

{% if tutorials.size > 0 %}
## Tutorials & training

<div class="row g-4 mb-5">
{% for video in tutorials %}
<div class="col-12 col-sm-6 col-lg-4">
{% include video-card.html video=video %}
</div>
{% endfor %}
</div>
{% endif %}

## All videos

<div class="row g-4">
{% for video in all_videos %}
<div class="col-12 col-sm-6 col-lg-4">
{% include video-card.html video=video %}
</div>
{% endfor %}
</div>

---

*To add a video, edit [`_data/videos.yml`](https://github.com/eeg101-costaction/website/blob/main/_data/videos.yml) — copy the YouTube video ID from the URL (the part after `?v=`) and add a new entry. See the README for step-by-step instructions.*
