---
layout: page
title: "Events"
subtitle: "EEG101 meetings and conferences"
description: "Upcoming and past events from the EEG101 COST Action — working group meetings, distributed conferences, and community events."
permalink: /events/
---

{::nomarkdown}
{% assign now_epoch = "now" | date: "%s" | plus: 0 %}
{% assign thirty_days_ago_epoch = now_epoch | minus: 2592000 %}

<div class="news-filter mb-4" id="eventFilter" role="group" aria-label="Filter events by status">
<button class="news-filter__btn active" data-filter="upcoming-recent">Upcoming & Recent</button>
<button class="news-filter__btn" data-filter="upcoming">Upcoming</button>
<button class="news-filter__btn" data-filter="recent">Recent</button>
<button class="news-filter__btn" data-filter="past">Past</button>
</div>

<div class="row g-4" id="eventGrid">
{% for event in site.data.events %}
  {% assign event_epoch = event.start_date | date: "%s" | plus: 0 %}
  {% if event_epoch >= now_epoch %}
    {% assign status = "upcoming" %}
  {% elsif event_epoch >= thirty_days_ago_epoch %}
    {% assign status = "recent" %}
  {% else %}
    {% assign status = "past" %}
  {% endif %}
  
  <div class="col-12 col-md-6 col-lg-4" data-status="{{ status }}">
    {% include event-card.html event=event computed_status=status %}
  </div>
{% endfor %}
</div>

<div id="noEventsMessage" class="text-muted mt-4" style="display: none;">
  No events found in this category. Check back soon or <a href="https://e-services.cost.eu/" target="_blank" rel="noopener">join via e-COST ↗</a> to stay connected with the network.
</div>

<script>
(function(){
  var btns = document.querySelectorAll('#eventFilter .news-filter__btn');
  var gridItems = document.querySelectorAll('#eventGrid [data-status]');
  var noEventsMsg = document.getElementById('noEventsMessage');

  function filterEvents(filter) {
    var visibleCount = 0;
    gridItems.forEach(function(item) {
      var status = item.dataset.status;
      var isVisible = false;
      
      if (filter === 'upcoming-recent') {
        isVisible = (status === 'upcoming' || status === 'recent');
      } else {
        isVisible = (status === filter);
      }
      
      item.style.display = isVisible ? '' : 'none';
      if (isVisible) visibleCount++;
    });
    
    noEventsMsg.style.display = (visibleCount === 0) ? '' : 'none';
  }

  btns.forEach(function(btn) {
    btn.addEventListener('click', function() {
      btns.forEach(function(b) { b.classList.remove('active'); });
      this.classList.add('active');
      filterEvents(this.dataset.filter);
    });
  });

  // Initialize with default filter
  filterEvents('upcoming-recent');
})();
</script>
{:/nomarkdown}

---

## EEG101 event formats

**Working Group meetings** are held regularly (online or hybrid) for each Working Group. All EEG101 members are welcome. Dates announced on [Discord]({{ site.data.site.discord_url }}).

**Distributed Conference** — EEG101 adopts and extends the CuttingGardens distributed conference model: simultaneous satellite events across Europe, connected through live streaming and shared programming.

**Management Committee meetings** — The MC meets annually to review progress, approve grants, and set strategic direction.
