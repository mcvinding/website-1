---
layout: page
title: "Resources"
subtitle: "Tools, templates, datasets, and community channels from EEG101"
description: "The EEG101 resource library — reporting templates, pre-registration tools, datasets, training materials, and community documents."
permalink: /resources/
---

A growing library of open resources developed by and for the EEG101 community. Resources are released as they become available throughout the Action.

---

## Resources

{% assign all_resources = site.data.resources %}

<div class="row g-4">
{% for resource in all_resources %}
<div class="col-12 col-sm-6 col-lg-4">
<div class="resource-card">
<span class="resource-card__icon" aria-hidden="true">{{ resource.icon }}</span>
<span class="resource-card__type">{{ resource.type | capitalize }}</span>
<h3 class="resource-card__title">{{ resource.title }}</h3>
<p class="resource-card__desc">{{ resource.description }}</p>
{% if resource.status %}<p class="resource-card__status">{{ resource.status }}</p>{% endif %}
<div class="resource-card__links">
{% if resource.url and resource.url != "" %}
<a href="{{ resource.url }}" class="btn btn-primary btn-sm" target="_blank" rel="noopener">Open ↗</a>
{% endif %}
{% if resource.file and resource.file != "" %}
<a href="{{ resource.file | relative_url }}" class="btn btn-outline-primary btn-sm" download>Download</a>
{% endif %}
</div>
</div>
</div>
{% endfor %}
</div>

---

## Videos

<div class="section-header d-flex justify-content-between align-items-center mb-4">
<p class="section-lead mb-0">Talks, tutorials, and podcast episodes from the EEG101 community.</p>
<a href="{{ site.data.site.youtube_url }}" class="btn btn-outline-primary btn-sm" target="_blank" rel="noopener">Subscribe on YouTube ↗</a>
</div>

<div class="row g-4">
{% for video in site.data.videos %}
<div class="col-12 col-md-4">
{% include video-card.html video=video %}
</div>
{% endfor %}
{% if site.data.videos.size == 0 %}
<div class="col-12">
<p class="text-muted">Video content coming soon. <a href="{{ site.data.site.youtube_url }}" target="_blank" rel="noopener">Subscribe on YouTube</a> to be notified.</p>
</div>
{% endif %}
</div>
