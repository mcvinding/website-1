---
layout: page
title: "Partners"
subtitle: "Initiatives and tools that EEG101 works with and supports"
description: "EEG101 partner organisations and initiatives — EEGManyLabs, CuttingEEG, INDOS, Global Brain Consortium, Global Brain Health Institute, FieldTrip, ARTEM-IS, African Brain Data Network."
permalink: /partners/
---

EEG101 works alongside a growing network of partner organisations and initiatives that share our commitment to open, rigorous, and globally inclusive EEG science.

---

{% assign initiatives = site.data.partners | where: "type", "initiative" %}
{% assign tools = site.data.partners | where: "type", "tool" %}

{% if initiatives.size > 0 %}
## Partner initiatives

<div class="row g-4">
{% for partner in initiatives %}
<div class="col-12 col-sm-6 col-lg-4">
<div class="partner-card">
<div class="partner-card__logo-wrap">
{% if partner.logo and partner.logo != "" %}
<img src="{{ partner.logo | relative_url }}" alt="{{ partner.name }} logo" class="partner-card__logo" loading="lazy">
{% else %}
<div class="partner-card__logo-placeholder">{{ partner.name | slice: 0, 2 | upcase }}</div>
{% endif %}
</div>
<div class="partner-card__body">
<h3 class="partner-card__name">{{ partner.name }}</h3>
<p class="partner-card__desc">{{ partner.description }}</p>
{% if partner.url and partner.url != "" %}
<a href="{{ partner.url }}" class="btn btn-outline-primary btn-sm" target="_blank" rel="noopener">Visit website ↗</a>
{% endif %}
</div>
</div>
</div>
{% endfor %}
</div>
{% endif %}

---

{% if tools.size > 0 %}
## Partner tools & platforms

<div class="row g-4">
{% for partner in tools %}
<div class="col-12 col-sm-6 col-lg-4">
<div class="partner-card">
<div class="partner-card__logo-wrap">
{% if partner.logo and partner.logo != "" %}
<img src="{{ partner.logo | relative_url }}" alt="{{ partner.name }} logo" class="partner-card__logo" loading="lazy">
{% else %}
<div class="partner-card__logo-placeholder">{{ partner.name | slice: 0, 2 | upcase }}</div>
{% endif %}
</div>
<div class="partner-card__body">
<h3 class="partner-card__name">{{ partner.name }}</h3>
<p class="partner-card__desc">{{ partner.description }}</p>
{% if partner.url and partner.url != "" %}
<a href="{{ partner.url }}" class="btn btn-outline-primary btn-sm" target="_blank" rel="noopener">Visit website ↗</a>
{% endif %}
</div>
</div>
</div>
{% endfor %}
</div>
{% endif %}

---

Interested in partnering with EEG101? Contact us at [{{ site.data.site.email }}](mailto:{{ site.data.site.email }}).
