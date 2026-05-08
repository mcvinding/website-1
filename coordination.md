---
layout: page
title: "Coordination"
subtitle: "The team leading EEG101"
description: "Meet the EEG101 coordination team — Action Chair, Vice Chair, and coordinators leading the network."
permalink: /coordination/
---

EEG101 was officially launched in November 2025. The coordination team oversees scientific direction, grant administration, science communication, and network governance.

{% assign coordination = site.data.people | sort: "order" %}

<div class="people-grid">
{% for person in coordination %}
{% include person-card.html person=person %}
{% endfor %}
</div>

---

## Governance structure

EEG101 operates through a **Management Committee (MC)** comprising representatives from each COST Full Member country participating in the Action. The MC sets strategic direction, approves grant awards, and oversees Working Group activities.

**Core coordination roles:**

| Role | Responsibility |
|------|---------------|
| **Action Chair** | Overall scientific leadership and external representation |
| **Vice Chair** | Supports the Chair; co-leads governance and Code of Conduct |
| **Science Communication Coordinator** | Podcast, social media, and public engagement |
| **Grant Awarding Coordinator** | STSMs, VMGs, and Conference Grant administration |
| **Grant Holder Scientific Representative** | Liaison with host institution and financial administration |

## Working Group leadership

Each Working Group is led by a WG Leader and supported by Co-leaders, with a minimum of two Young Researcher & Innovator champions. See the [Working Groups page](/working-groups/) for full details.

## Contact the coordination team

For general enquiries: [{{ site.data.site.email }}](mailto:{{ site.data.site.email }})

For grant enquiries, contact the Grant Awarding Coordinator via the [Grants page](/grants/).

For Code of Conduct matters, contact the Action Chair or Vice Chair directly.
