---
layout: page
title: "News & Events"
subtitle: "Stay updated with EEG101 activities"
description: "A combined feed of EEG101 announcements, grants, working group meetings, and community events."
permalink: /news/
---

{::nomarkdown}
{% assign now_epoch = "now" | date: "%s" | plus: 0 %}
{% assign thirty_days_ago_epoch = now_epoch | minus: 2592000 %}

<!-- Filter Bar -->
<div class="news-filter mb-4" id="unifiedFilter" role="group" aria-label="Filter news and events">
  <div class="d-flex flex-wrap gap-2">
    <button class="news-filter__btn active" data-filter-type="status" data-filter-val="upcoming-recent">Upcoming & Recent</button>
    <button class="news-filter__btn" data-filter-type="status" data-filter-val="all">All</button>
    <button class="news-filter__btn" data-filter-type="status" data-filter-val="upcoming">Upcoming</button>
    <button class="news-filter__btn" data-filter-type="status" data-filter-val="recent">Recent</button>
    <button class="news-filter__btn" data-filter-type="status" data-filter-val="past">Past</button>
  </div>
</div>

<div class="row g-4" id="unifiedGrid">
  <!-- Combine and Sort Logic -->
  {% assign combined_items = "" | split: "," %}
  
  {% for event in site.data.events %}
    {% assign combined_items = combined_items | push: event %}
  {% endfor %}
  
  {% for news in site.data.news %}
    {% assign combined_items = combined_items | push: news %}
  {% endfor %}
  
  <!-- Sort by date descending -->
  {% assign sorted_items = combined_items | sort: "start_date" | reverse %}
  <!-- Fallback for news items which use 'date' instead of 'start_date' -->
  {% assign sorted_items = combined_items | sort: "date" | reverse %}

  {% for item in sorted_items %}
    {% if item.start_date %}
      {% assign item_date = item.start_date %}
      {% assign is_event = true %}
    {% else %}
      {% assign item_date = item.date %}
      {% assign is_event = false %}
    {% endif %}

    {% assign item_epoch = item_date | date: "%s" | plus: 0 %}
    
    {% if item_epoch >= now_epoch %}
      {% assign status = "upcoming" %}
    {% elsif item_epoch >= thirty_days_ago_epoch %}
      {% assign status = "recent" %}
    {% else %}
      {% assign status = "past" %}
    {% endif %}

    <div class="col-12 col-md-6 col-lg-4 grid-item" data-status="{{ status }}">
      {% if is_event %}
        {% include event-card.html event=item computed_status=status %}
      {% else %}
        {% include news-card.html item=item %}
      {% endif %}
    </div>
  {% endfor %}
</div>

<div id="noItemsMessage" class="text-muted mt-4" style="display: none;">
  No items found in this category.
</div>

<script>
(function(){
  var btns = document.querySelectorAll('#unifiedFilter .news-filter__btn');
  var gridItems = document.querySelectorAll('#unifiedGrid .grid-item');
  var noItemsMsg = document.getElementById('noItemsMessage');

  function filterContent(filterVal) {
    var visibleCount = 0;
    gridItems.forEach(function(item) {
      var status = item.dataset.status;
      var isVisible = false;
      
      if (filterVal === 'all') {
        isVisible = true;
      } else if (filterVal === 'upcoming-recent') {
        isVisible = (status === 'upcoming' || status === 'recent');
      } else {
        isVisible = (status === filterVal);
      }
      
      item.style.display = isVisible ? '' : 'none';
      if (isVisible) visibleCount++;
    });
    
    noItemsMsg.style.display = (visibleCount === 0) ? '' : 'none';
  }

  btns.forEach(function(btn) {
    btn.addEventListener('click', function() {
      btns.forEach(function(b) { b.classList.remove('active'); });
      this.classList.add('active');
      filterContent(this.dataset.filterVal);
    });
  });

  // Initialize with default filter
  filterContent('upcoming-recent');
})();
</script>
{:/nomarkdown}
