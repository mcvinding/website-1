# EEG101 Website

Source for [www.eeg101.eu](https://www.eeg101.eu) — the EEG101 COST Action website (CA24148).

Built with [Jekyll](https://jekyllrb.com) and deployed automatically to [GitHub Pages](https://pages.github.com) when changes are pushed to the `main` branch.

---

## How deployment works

Push any change to the `main` branch → GitHub Actions builds the site → live within ~2 minutes at [www.eeg101.eu](https://www.eeg101.eu).

You do **not** need to build the site locally to update content. Edit a YAML file, commit, push — done.

---

## Editing content — quick guide

Almost all content lives in `_data/` as YAML files.

### Edit homepage text

Open `_data/content.yml`. Change any text under `hero:`, `about:`, `objectives:`, etc. YAML uses `>` for multi-line text — keep indentation consistent.

### Add a news item

Open `_data/news.yml`. Copy the example at the bottom and fill in:

```yaml
- title: "Your headline here"
  date: 2026-06-15
  category: "Announcement"
  summary: >
    A 1-3 sentence summary shown on the card.
  image: "/assets/images/news/your-image.jpg"
  alt: "Descriptive alt text"
  featured: false
  external_url: ""
  internal_url: ""
  button_label: "Read more"
  tags:
    - announcement
```

Place the image in `assets/images/news/`. Recommended size: **800×450px (16:9)**, JPEG or WebP.

### Add a person

Open `_data/people.yml`. Copy an existing entry. Place the photo in `assets/images/people/` — recommended size: **400×400px square**, JPEG or WebP.

### Add an event

Open `_data/events.yml`. Copy the example at the bottom. Set `status:` to `upcoming`, `ongoing`, or `past`.

### Add a YouTube video

Find the video ID from the YouTube URL (the part after `?v=`), then add to `_data/videos.yml`:

```yaml
- id: unique-id
  title: "Video title"
  youtube_id: "abc123XYZ"
  date: 2026-06-01
  speaker: "Speaker Name"
  summary: >
    A short description.
  category: "podcast"
  thumbnail: ""
```

### Update grants / calls

Open `_data/grants.yml`. Change `status:` (`open` / `closed` / `upcoming`), update `deadline:`, and update `application_url:` when a new round opens.

### Update navigation

Open `_data/navigation.yml`. Add, remove, or reorder items under `main:` for the header, or `footer:` for footer links.

---

## Where to place files

| Type | Folder | Recommended size |
|------|--------|-----------------|
| News images | `assets/images/news/` | 800×450px, JPEG/WebP, <200KB |
| Event images | `assets/images/events/` | 800×450px, JPEG/WebP, <200KB |
| People photos | `assets/images/people/` | 400×400px square, <100KB |
| Partner logos | `assets/images/partners/` | 200×80px, transparent PNG |
| Logo files | `assets/images/logo/` | Keep existing names |
| Hero video | `assets/video/hero.mp4` | H.264 MP4, 1920×1080, loopable |
| Hero fallback | `assets/images/hero-fallback.jpg` | 1920×1080px, <500KB |
| PDFs / docs | `assets/docs/` | Any name |

---

## Previewing locally

```bash
bundle install          # First time only
bundle exec jekyll serve
# Open http://localhost:4000
```

---

## Common YAML mistakes

- **Indentation** — Use spaces, not tabs. 2 spaces per level.
- **Colons in text** — Wrap in quotes: `title: "EEG101: A Network"`
- **Multi-line text** — Use `>` then indent the text block.
- **Dates** — Always `YYYY-MM-DD`: `date: 2026-06-15`
- **Empty fields** — Use `""` rather than deleting the field.

If the site fails to build, check the GitHub Actions log — it shows the exact error line.

---

## Site structure

```
_config.yml          # Jekyll configuration
_data/               # All editable content (YAML)
  site.yml           # Site-wide settings
  navigation.yml     # Header and footer navigation
  content.yml        # Homepage text blocks
  people.yml         # Team profiles
  working_groups.yml # Working group descriptions
  grants.yml         # Grant schemes
  news.yml           # News items
  events.yml         # Events
  videos.yml         # YouTube video entries
  resources.yml      # Resource library
  partners.yml       # Partners
_includes/           # Reusable HTML components
_layouts/            # Page templates
assets/css/style.css # All visual styling
assets/images/       # Images by type
assets/video/        # Hero video
*.md                 # Page content files
```

---

## Licence

Content: [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/). Code: MIT.
