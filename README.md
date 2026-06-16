# ABL Developer Blog

A Jekyll blog covering Agent Blueprint Language (ABL) on the Kore AI platform — hosted on GitHub Pages using the [Chirpy](https://github.com/cotes2046/jekyll-theme-chirpy) theme.

Live site: **https://dgwartney.github.io/kore-abl-blog**

---

## Prerequisites

- [Homebrew](https://brew.sh)
- Ruby 3.3 (installed via Homebrew — see setup below)

---

## First-Time Setup

```bash
# Install Ruby 3.3 if not already present
brew install ruby@3.3

# Add Ruby 3.3 to your PATH (add this line to ~/.zshrc for persistence)
export PATH="/opt/homebrew/opt/ruby@3.3/bin:$PATH"

# Clone and install dependencies
git clone https://github.com/dgwartney/kore-abl-blog.git
cd kore-abl-blog
bundle install
```

---

## Writing a Post

### 1. Create a draft

```bash
bin/new-post "Your Post Title"
```

This creates `_drafts/<slug>.md` with front matter pre-filled:

```yaml
---
title: "Your Post Title"
date: 2026-06-16 09:00:00 -0700
categories: [ABL]
tags: []
---
```

Edit the file, then fill in `categories` and `tags` before publishing.

### 2. Preview locally

```bash
bundle exec jekyll serve --drafts
```

Opens at `http://localhost:4000`. The `--drafts` flag includes unpublished posts. Omit it to preview the published-only view.

### 3. Publish

Rename the draft to `_posts/` with today's date prepended:

```bash
mv _drafts/your-post-title.md _posts/2026-06-16-your-post-title.md
```

The filename date controls the post's publication date and URL.

### 4. Deploy

```bash
git add _posts/2026-06-16-your-post-title.md
git commit -m "Post: Your Post Title"
git push
```

GitHub Actions picks up the push and deploys automatically. The live site updates in ~1 minute.

---

## Front Matter Reference

```yaml
---
title: "Post Title"                          # required
date: 2026-06-16 09:00:00 -0700             # required — controls sort order and URL
categories: [ABL, Tools]                     # 1–2 broad categories
tags: [agents, orchestration, multi-agent]   # 3–8 specific tags
image:
  path: /assets/img/posts/cover.png          # optional — cover image shown in post list
  alt: "Descriptive alt text"
---
```

**Category conventions:**

| Category | Use for |
|----------|---------|
| `ABL` | Language syntax, semantics, patterns |
| `Tools` | Tool and MCP server integration |
| `Orchestration` | Multi-agent design, supervisor patterns |
| `Memory` | State management, persistence |
| `Safety` | Guardrails, output validation |
| `Testing` | Debugging, evals, observability |
| `Announcements` | Meta posts about the blog itself |

---

## Directory Structure

```
kore-abl-blog/
├── _posts/           # Published posts — filename: YYYY-MM-DD-title.md
├── _drafts/          # Work-in-progress — no date prefix, never deployed
├── _tabs/            # Chirpy navigation pages (About, Archives, Categories, Tags)
├── assets/
│   └── img/
│       ├── avatars/  # Author avatar image
│       └── posts/    # Per-post cover images
├── bin/
│   └── new-post      # Script to scaffold a new draft
├── _config.yml       # Site configuration
├── Gemfile           # Ruby dependencies
└── .github/
    └── workflows/
        └── pages-deploy.yml  # GitHub Actions deploy workflow
```

---

## Configuration

Key settings in `_config.yml`:

| Key | Description |
|-----|-------------|
| `title` | Blog name shown in the header |
| `tagline` | Subtitle shown under the title |
| `url` / `baseurl` | Full URL of the live site |
| `theme_mode` | `light`, `dark`, or blank (follows OS preference) |
| `toc` | Show table of contents on posts (`true`/`false`) |
| `comments.active` | Enable comments — set to `giscus` or `disqus` when ready |
| `paginate` | Number of posts per page (default: 10) |

---

## GitHub Pages Setup

The blog deploys automatically via GitHub Actions on every push to `main`. To enable it on a new repository:

1. Push the repo to GitHub
2. Go to **Settings → Pages**
3. Set **Source** to **GitHub Actions**

The workflow file is at `.github/workflows/pages-deploy.yml`. It only rebuilds when relevant files change (`_posts/`, `_config.yml`, `assets/`, etc.).

---

## Local Build Commands

```bash
# Build only (no server)
bundle exec jekyll build

# Serve with live reload, including drafts
bundle exec jekyll serve --drafts --livereload

# Production build (no drafts, minified assets)
JEKYLL_ENV=production bundle exec jekyll build
```

---

## Related

- [ABL Developer Guide](https://github.com/dgwartney/kore-abl-developer-guide) — the companion reference PDF
- [Chirpy Theme Docs](https://chirpy.cotes.page) — full theme documentation
- [Jekyll Docs](https://jekyllrb.com/docs/) — Jekyll reference
