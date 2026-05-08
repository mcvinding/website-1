---
layout: page
title: "Resources"
subtitle: "Tools, templates, datasets, and documents from EEG101"
description: "The EEG101 resource library — reporting templates, pre-registration tools, datasets, training materials, and community documents."
permalink: /resources/
---

A growing library of open resources developed by and for the EEG101 community. Resources are developed by Working Groups and released as they become available throughout the Action.

---

{% assign general = site.data.resources | where: "working_group", "" %}
{% assign wg1_resources = site.data.resources | where: "working_group", "wg1" %}
{% assign wg2_resources = site.data.resources | where: "working_group", "wg2" %}
{% assign wg3_resources = site.data.resources | where: "working_group", "wg3" %}

{% if general.size > 0 %}
## General resources

<div class="row g-4">
{% for resource in general %}
<div class="col-12 col-sm-6 col-lg-4">
<div class="resource-card">
  <div class="resource-card__icon" aria-hidden="true">{{ resource.icon }}</div>
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
{% endif %}

---

## WG1 — Reporting Standards

<p class="text-muted">Resources from Working Group 1: standardised reporting templates, pre-registration tools, and instructional materials.</p>

<div class="row g-4">
{% for resource in wg1_resources %}
<div class="col-12 col-sm-6 col-lg-4">
<div class="resource-card resource-card--wg1">
  <div class="resource-card__icon" aria-hidden="true">{{ resource.icon }}</div>
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
{% if wg1_resources.size == 0 %}
<div class="col-12"><p class="text-muted">WG1 resources in development — check back from Month 18.</p></div>
{% endif %}
</div>

---

## WG2 — Curation & Harmonisation

<p class="text-muted">Resources from Working Group 2: datasets, pipelines, harmonisation protocols, and the EEG data platform.</p>

<div class="row g-4">
{% for resource in wg2_resources %}
<div class="col-12 col-sm-6 col-lg-4">
<div class="resource-card resource-card--wg2">
  <div class="resource-card__icon" aria-hidden="true">{{ resource.icon }}</div>
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
{% if wg2_resources.size == 0 %}
<div class="col-12"><p class="text-muted">WG2 platform and resources in development — expected by Month 12.</p></div>
{% endif %}
</div>

---

## WG3 — EEG Community Framework

<p class="text-muted">Resources from Working Group 3: the EEG Manifesto, ethical guidelines, and community pledge platform.</p>

<div class="row g-4">
{% for resource in wg3_resources %}
<div class="col-12 col-sm-6 col-lg-4">
<div class="resource-card resource-card--wg3">
  <div class="resource-card__icon" aria-hidden="true">{{ resource.icon }}</div>
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
{% if wg3_resources.size == 0 %}
<div class="col-12"><p class="text-muted">WG3 resources in development — the EEG Manifesto is being developed through community consultation.</p></div>
{% endif %}
</div>

---

*To add a resource, edit [`_data/resources.yml`](https://github.com/eeg101-costaction/website/blob/main/_data/resources.yml). For large files, place them in `assets/docs/` and reference the path.*
