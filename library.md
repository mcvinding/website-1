---
layout: page
title: Library
permalink: /library/
---

<section class="section-library">
  <div class="container">
    <div class="row mb-4">
      <div class="col-lg-8">
        <p class="text-muted">Explore our collection of recordings from EEG101 workshops, symposia, and working group sessions. Filter by series or search by keyword to find specific topics.</p>
      </div>
    </div>

    <!-- Filter controls -->
    <div class="library-controls mb-4">
      <div class="row g-3">
        <div class="col-md-6">
          <input type="text" id="library-search" class="form-control library-search" placeholder="Search by title, speaker, or topic...">
        </div>
        <div class="col-md-6 d-flex align-items-center">
          <div class="library-filters d-flex flex-wrap gap-2" id="library-filters">
            <button class="filter-btn active" data-filter="all">All</button>
            <button class="filter-btn" data-filter="Mini-Symposium">Mini-Symposium</button>
            <button class="filter-btn" data-filter="Workshops">Workshops</button>
            <button class="filter-btn" data-filter="WG Sessions">WG Sessions</button>
          </div>
        </div>
      </div>
    </div>

    <p class="library-count mb-4" id="library-count">Showing {{ site.data.library | size }} videos</p>

    <!-- Video grid -->
    <div class="row row-cols-1 row-cols-md-2 row-cols-lg-3 g-4" id="library-grid">
      {% for video in site.data.library %}
      <div class="col video-card-wrapper" 
           data-series="{{ video.series }}" 
           data-title="{{ video.title | downcase }}" 
           data-tags="{{ video.tags | join: ' ' | downcase }}">
        <div class="library-video-card h-100">
          <a href="https://www.youtube.com/watch?v={{ video.id }}" 
             target="_blank" rel="noopener" 
             class="video-thumb-link">
            <div class="video-thumb">
              <img src="https://i.ytimg.com/vi/{{ video.id }}/mqdefault.jpg" 
                   alt="{{ video.title }}" 
                   loading="lazy"
                   class="img-fluid">
              <span class="video-duration">{{ video.duration }}</span>
              <div class="video-play-overlay">
                <svg viewBox="0 0 24 24" fill="currentColor" width="48" height="48"><path d="M8 5v14l11-7z"/></svg>
              </div>
            </div>
          </a>
          <div class="video-info p-3">
            <p class="video-series-label mb-1">{{ video.series }}</p>
            <h3 class="video-title h5 mb-2">
              <a href="https://www.youtube.com/watch?v={{ video.id }}" target="_blank" rel="noopener" class="text-decoration-none text-dark">{{ video.title }}</a>
            </h3>
            <div class="tag-list d-flex flex-wrap gap-1">
              {% for tag in video.tags %}
                <span class="library-tag">{{ tag }}</span>
              {% endfor %}
            </div>
          </div>
        </div>
      </div>
      {% endfor %}
    </div>

    <div class="library-empty text-center py-5" id="library-empty" style="display:none;">
      <p class="text-muted">No videos match your search criteria.</p>
    </div>

  </div>
</section>

<style>
/* Library Specific Styles */
.library-search {
  border-radius: 8px;
  padding: 0.6rem 1rem;
  border: 1px solid #dee2e6;
}
.library-search:focus {
  box-shadow: 0 0 0 0.25rem rgba(13, 110, 253, 0.1);
  border-color: #86b7fe;
}

.filter-btn {
  font-size: 0.85rem;
  font-weight: 500;
  padding: 0.4rem 1rem;
  border-radius: 50px;
  border: 1px solid #dee2e6;
  background: #fff;
  color: #6c757d;
  cursor: pointer;
  transition: all 0.2s;
}
.filter-btn:hover {
  border-color: #adb5bd;
  color: #495057;
}
.filter-btn.active {
  background: #1e2230;
  border-color: #1e2230;
  color: #fff;
}

.library-video-card {
  background: #fff;
  border-radius: 8px;
  overflow: hidden;
  border: 1px solid #e9ecef;
  transition: transform 0.2s, box-shadow 0.2s;
}
.library-video-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 10px 20px rgba(0,0,0,0.05);
}

.video-thumb {
  position: relative;
  aspect-ratio: 16/9;
  background: #f8f9fa;
  overflow: hidden;
}
.video-thumb img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: transform 0.3s;
}
.library-video-card:hover .video-thumb img {
  transform: scale(1.05);
}

.video-duration {
  position: absolute;
  bottom: 8px;
  right: 8px;
  background: rgba(0,0,0,0.8);
  color: #fff;
  font-size: 0.75rem;
  padding: 2px 6px;
  border-radius: 4px;
}

.video-play-overlay {
  position: absolute;
  inset: 0;
  display: flex;
  align-items: center;
  justify-content: center;
  background: rgba(0,0,0,0.2);
  color: #fff;
  opacity: 0;
  transition: opacity 0.2s;
}
.library-video-card:hover .video-play-overlay {
  opacity: 1;
}

.video-series-label {
  font-size: 0.7rem;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.05em;
  color: #c8a96e;
}

.video-title a:hover {
  color: #1e2230 !important;
  text-decoration: underline !important;
}

.library-tag {
  font-size: 0.7rem;
  padding: 2px 8px;
  background: #f1f3f5;
  color: #495057;
  border-radius: 4px;
}

.library-count {
  font-size: 0.9rem;
  color: #6c757d;
}
</style>

<script>
document.addEventListener('DOMContentLoaded', function() {
  const searchInput = document.getElementById('library-search');
  const filterBtns  = document.querySelectorAll('.filter-btn');
  const cards       = document.querySelectorAll('.video-card-wrapper');
  const countEl     = document.getElementById('library-count');
  const emptyEl     = document.getElementById('library-empty');

  let activeSeries = 'all';
  let searchTerm   = '';

  function update() {
    let visible = 0;
    cards.forEach(function(card) {
      const seriesMatch = activeSeries === 'all' || card.dataset.series === activeSeries;
      const searchMatch = searchTerm === '' || 
        card.dataset.title.includes(searchTerm) || 
        card.dataset.tags.includes(searchTerm);
      
      if (seriesMatch && searchMatch) {
        card.style.display = '';
        visible++;
      } else {
        card.style.display = 'none';
      }
    });
    countEl.textContent = 'Showing ' + visible + ' video' + (visible !== 1 ? 's' : '');
    emptyEl.style.display = visible === 0 ? '' : 'none';
  }

  filterBtns.forEach(function(btn) {
    btn.addEventListener('click', function() {
      filterBtns.forEach(function(b) { b.classList.remove('active'); });
      btn.classList.add('active');
      activeSeries = btn.dataset.filter;
      update();
    });
  });

  searchInput.addEventListener('input', function() {
    searchTerm = searchInput.value.toLowerCase().trim();
    update();
  });
});
</script>
