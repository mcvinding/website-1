---
layout: page
title: "Grants"
subtitle: "Funding opportunities for EEG101 network members"
description: "EEG101 COST Action grant schemes: Short-Term Scientific Missions, Virtual Mobility Grants, and Conference Grants. Deadlines and application guidance."
permalink: /grants/
---

EEG101 offers several COST grant schemes to support research collaboration, training, and dissemination. Grants are open to researchers affiliated with institutions in COST Full Member or Cooperating Member countries.

<div class="grants-status-banner">
  <strong>Round 1 deadline: 31 October 2026, 17:00 CET.</strong>
  Decisions will be communicated by 30 April 2026.
  Apply via <a href="{{ site.data.grants.schemes[0].application_url }}" target="_blank" rel="noopener">e-COST ↗</a>
</div>

---

## Grant schemes

{% for grant in site.data.grants.schemes %}
<section class="grant-detail" id="{{ grant.id }}">
<div class="grant-detail__header">
  <span class="grant-detail__icon" aria-hidden="true">{{ grant.icon }}</span>
  <div>
    <h2 class="grant-detail__title">{{ grant.title }}</h2>
    <span class="grant-detail__value">{{ grant.value }}</span>
    <span class="grant-status grant-status--{{ grant.status }}">
      {% if grant.status == "open" %}● Open now
      {% elsif grant.status == "upcoming" %}◌ Coming soon
      {% else %}✕ Closed{% endif %}
    </span>
  </div>
</div>

{{ grant.summary }}

<div class="row g-4 mt-1 mb-3">
<div class="col-12 col-md-6">

**Eligibility**
{{ grant.eligibility }}

**Duration:** {{ grant.duration }}

</div>
<div class="col-12 col-md-6">

**Who is this for?**
{% if grant.yri_track %}✓ Young Researchers & Innovators (YRIs) {% endif %}
{% if grant.itc_track %}✓ ITC-based researchers {% endif %}
{% if grant.industry_track %}✓ Industry-involved projects {% endif %}

{% if grant.deadline and grant.deadline != "" %}
**Deadline:** {{ grant.deadline }}
{% endif %}

{% if grant.notes and grant.notes != "" %}
**Notes:** {{ grant.notes }}
{% endif %}

</div>
</div>

<div class="grant-detail__actions">
{% if grant.status == "open" and grant.application_url != "" %}
<a href="{{ grant.application_url }}" class="btn btn-primary" target="_blank" rel="noopener">Apply on e-COST ↗</a>
{% endif %}
{% if grant.guidance_url and grant.guidance_url != "" %}
<a href="{{ grant.guidance_url }}" class="btn btn-outline-primary" target="_blank" rel="noopener">COST guidance ↗</a>
{% endif %}
{% if grant.contact and grant.contact != "" %}
<a href="mailto:{{ grant.contact }}" class="btn btn-outline-primary">Email grants team</a>
{% endif %}
</div>

</section>
<hr class="section-divider">
{% endfor %}

---

## How to apply

{% for step in site.data.grants.application_process %}

<div class="process-step">
  <div class="process-step__number">{{ step.step }}</div>
  <div class="process-step__content">
    <h3 class="process-step__title">{{ step.title }}</h3>
    <p class="process-step__desc">{{ step.description }}</p>
  </div>
</div>
{% endfor %}

---

## Frequently asked questions

**Who can apply for EEG101 grants?**
Applicants must be affiliated with an institution in a COST Full Member or Cooperating Member country. You do not need to be from the same country as your host institution. Membership of EEG101 is free — [join first](/join/).

**Do I need to be a current EEG101 member?**
Yes. Join the Action through e-COST before submitting a grant application.

**Can early career researchers apply?**
Absolutely — EEG101 prioritises Young Researchers & Innovators and ITC-based applicants for all grant schemes.

**Can I apply for a STSM with an industry partner?**
Yes. EEG101 has a dedicated industry engagement track. At least five funded projects will involve industry partners.

**Where can I find host institutions?**
Connect with the network on [Discord]({{ site.data.site.discord_url }}) to identify potential hosts, or contact the [coordination team](/contact/).

**What happens after my grant?**
A short scientific report is required within 30 days of completion. Payment is released upon approval of your report.

For further guidance, contact the Grant Awarding Coordinator via [{{ site.data.site.email }}](mailto:{{ site.data.site.email }}) or consult the [COST funding pages](https://www.cost.eu/funding/funding-opportunities/).
