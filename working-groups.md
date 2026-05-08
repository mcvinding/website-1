---
layout: page
title: "Working Groups"
subtitle: "Three focused groups driving EEG101's scientific programme"
description: "EEG101 operates through three Working Groups addressing reporting standards, data curation, and a community framework for open EEG science."
permalink: /working-groups/
---

EEG101's scientific programme is organised into three Working Groups, each addressing a distinct challenge in the field. The Working Groups are coordinated by the Management Committee and supported by education, dissemination, and community activities.

---

{% assign wgs = site.data.working_groups.working_groups %}

{% for wg in wgs %}
<section class="wg-section" id="{{ wg.id }}">
<div class="wg-section__header">
  <span class="wg-section__number">WG{{ wg.number }}</span>
  <div class="wg-section__icon" aria-hidden="true">{{ wg.icon }}</div>
  <h2 class="wg-section__title">{{ wg.title }}</h2>
  <p class="wg-section__tagline">{{ wg.tagline }}</p>
</div>

**Aim:** {{ wg.aim }}

<div class="row g-4 mt-2 mb-4">
<div class="col-12 col-md-4">

**Activities**
{% for activity in wg.activities %}
- {{ activity }}
{% endfor %}

</div>
<div class="col-12 col-md-4">

**Expected outputs**
{% for output in wg.outputs %}
- {{ output }}
{% endfor %}

</div>
<div class="col-12 col-md-4">

**MOU objectives**
{% for obj in wg.mou_objectives %}
- {{ obj }}
{% endfor %}

</div>
</div>

**Leadership:**
{% assign all_people = site.data.people %}
{% for leader_id in wg.leaders %}
{% assign leader = all_people | where: "id", leader_id | first %}
{% if leader %}*{{ leader.name }}* (WG Leader){% endif %}
{% endfor %}
{% for coleader_id in wg.co_leaders %}
{% assign coleader = all_people | where: "id", coleader_id | first %}
{% if coleader %} · *{{ coleader.name }}* (Co-leader){% endif %}
{% endfor %}

</section>
<hr class="section-divider">
{% endfor %}

## Activities and community programmes

In addition to the three Working Groups, EEG101 delivers a range of community activities coordinated by the Management Committee.

{% assign activities = site.data.working_groups.activities %}
<div class="row g-4 mt-2">
{% for activity in activities %}
<div class="col-12 col-sm-6 col-lg-4">
<div class="activity-card">
  <div class="activity-card__icon" aria-hidden="true">{{ activity.icon }}</div>
  <h3 class="activity-card__title">{{ activity.title }}</h3>
  <p class="activity-card__tagline">{{ activity.tagline }}</p>
  <p class="activity-card__desc">{{ activity.description }}</p>
</div>
</div>
{% endfor %}
</div>

---

## How to get involved

All EEG101 members are welcome to participate in Working Group activities. Join the [EEG101 Discord]({{ site.data.site.discord_url }}) and find the channel for your Working Group of interest, or [contact the coordination team](/contact/).

Working Group meetings are announced on [Discord](/join/) and the [Events page](/events/).
