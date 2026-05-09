---
layout: page
title: "Coordination"
subtitle: "The team leading EEG101"
description: "Meet the EEG101 coordination team — Action Chair, Vice Chair, and coordinators leading the network."
permalink: /coordination/
---

EEG101 was officially launched in November 2025. The coordination team oversees scientific direction, grant administration, science communication, and network governance.

{::nomarkdown}
<div class="people-filter" id="peopleFilter" role="group" aria-label="Filter by group">
<button class="people-filter__btn active" data-filter="all">All</button><button class="people-filter__btn" data-filter="Leadership">Leadership</button><button class="people-filter__btn" data-filter="Core Group">Core Group</button><button class="people-filter__btn" data-filter="WG1">WG1</button><button class="people-filter__btn" data-filter="WG2">WG2</button><button class="people-filter__btn" data-filter="WG3">WG3</button>
</div>

<div class="people-grid" id="peopleGrid">
{% assign coordination = site.data.people | sort: "order" %}
{% for person in coordination %}
{% include person-card.html person=person %}
{% endfor %}
</div>
{:/nomarkdown}

<script>
(function(){var btns=document.querySelectorAll('#peopleFilter .people-filter__btn');btns.forEach(function(btn){btn.addEventListener('click',function(){btns.forEach(function(b){b.classList.remove('active');});this.classList.add('active');var f=this.dataset.filter;document.querySelectorAll('#peopleGrid .person-card').forEach(function(card){var tags=card.dataset.tags||'';card.style.display=(f==='all'||tags.split(',').indexOf(f)>-1)?'':'none';});});});})();
</script>

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

---

## Code of Conduct

EEG101 is committed to a respectful, inclusive, and scientifically rigorous community. Our full [Code of Conduct](/code-of-conduct/) applies to all EEG101 spaces — including mailing lists, in-person and online events, working group meetings, and collaborative projects.
