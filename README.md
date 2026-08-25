# Yuelong Zhang — Personal Academic Website

Personal research website for Yuelong Zhang, focused on bio-inspired robotics, compliant mechanisms, bipedal locomotion, and robot learning.

Target public URL: [https://zhangyuelong.github.io](https://zhangyuelong.github.io)

The site is intentionally implemented as a small Jekyll project for GitHub Pages. It uses Liquid, HTML, CSS, Markdown, and YAML; there is no JavaScript framework, CMS, or database.

## Navigation and public scope

| Navigation | Path | Behavior |
| --- | --- | --- |
| about | `/` | Home and About are the same page. |
| publications | `/publications/` | Publication data from `_data/publications.yml`. |
| projects | `/projects/` | Public entries from the Jekyll `projects` collection. |
| CV | `/files/CV.pdf` | Opens the stable PDF URL in a new tab. |

The first public version contains one formal project: **STERS**. BioArm is not currently public and has no page, card, or publication entry.

Email and LinkedIn are configured centrally in `_config.yml`. The email address is confirmed from the current CV. `linkedin_url` remains an explicit TODO until the correct profile URL is confirmed.

## STERS project page

`/projects/sters/` follows the research narrative below:

1. Overview
2. Energy Recirculation Across the Stance Phase
3. Dynamics and Stiffness Optimization
4. Contact-Aware Locomotion
5. Reinforcement Learning and Control
6. Experimental Model Validation
7. Real-World Locomotion
8. Disturbance Recovery
9. Walking Performance and Energy Efficiency
10. Project Overview Video
11. Publication / BibTeX

The source manuscript in `files/sters-paper.pdf` is retained but excluded from the built site because the current file is an under-review revision rather than a clean public manuscript. Add a `paper` field only after a public version is confirmed.

## Repository structure

```text
zhangyuelong.github.io/
├── .gitignore
├── _config.yml
├── Gemfile
├── README.md
├── index.html
├── _data/
│   ├── news.yml
│   └── publications.yml
├── _includes/
│   ├── footer.html
│   └── header.html
├── _layouts/
│   ├── default.html
│   └── project.html
├── _projects/
│   └── sters.md
├── assets/
│   ├── css/
│   │   └── style.css
│   ├── images/
│   │   ├── profile/
│   │   ├── projects/
│   │   │   └── sters/
│   │   └── source/              # Preserved original image assets
│   └── videos/
│       ├── source/              # Preserved HEVC source clips
│       └── sters/               # Browser-ready STERS videos
├── files/
│   ├── CV.pdf                    # Stable public CV path
│   ├── Zyl.pdf                   # Preserved source CV
│   └── sters-paper.pdf           # Preserved under-review manuscript
├── projects/
│   └── index.html
└── publications/
    └── index.html
```

`_config.yml` excludes source-only media and non-public PDFs from the generated `_site` directory.

## Local development on macOS

Prerequisites:

- Ruby
- Bundler
- Jekyll (installed through Bundler)

From the repository root:

```bash
bundle install
bundle exec jekyll serve
```

Open [http://localhost:4000](http://localhost:4000). The Gemfile uses Jekyll 4 for local development and only core Jekyll/Liquid features that remain compatible with GitHub Pages.

## Routine update workflow

1. Save the edited files.
2. Run `bundle exec jekyll serve`.
3. Check the changed pages at `localhost:4000`, including mobile widths when layout changes.
4. Run `git status` and review the diff.
5. Stage and commit the intended files.
6. Push to `main`.
7. Confirm the GitHub Pages deployment.

VS Code Source Control can be used for Stage, Commit, and Sync/Push.

## Add a project

Create `_projects/<slug>.md` and add web assets under:

```text
assets/images/projects/<slug>/
assets/videos/<slug>/
```

Use front matter matching the fields consumed by the current layouts:

```yaml
---
title: Project Name
subtitle: Formal project or paper subtitle
description: One or two concise sentences for listing cards.
short_label: Research area
thumbnail: /assets/images/projects/<slug>/cover.png
thumbnail_alt: Accessible description of the thumbnail
hero: /assets/images/projects/<slug>/cover.png
hero_alt: Accessible description of the project hero
order: 2
selected: false
published: true
paper: /files/public-paper.pdf   # Optional; use only for a public file
video: "#project-video"          # Optional project-page anchor or URL
tags:
  - Robotics
  - Mechanism Design
---
```

Projects with `published: true` automatically appear on `/projects/`. Projects also require `selected: true` to appear in Selected Research on the home page.

To publish BioArm later, add `_projects/bioarm.md` and the corresponding `assets/images/projects/bioarm/` and `assets/videos/bioarm/` directories. Do not add a placeholder before public content is ready.

## Add a publication

Add an item to `_data/publications.yml`. The listing currently uses these fields:

```yaml
- id: short-id
  status: Under review
  venue: Confirmed venue or status destination
  title: Formal paper title
  authors: Authors in confirmed order
  image: /assets/images/projects/example/cover.png
  image_alt: Accessible image description
  paper: /files/public-paper.pdf  # Optional
  project: /projects/example/
  tags:
    - Robotics
```

Do not add a year, DOI, venue, status, author order, or paper link until it is verified from a public manuscript or the current CV.

## Update news

`_data/news.yml` is currently an empty YAML list, so the home page hides the News section. Add confirmed items without editing `index.html`:

```yaml
- date: 2026-08-01
  text: Concise, factual update.
  url: https://example.com/optional-link
```

## Update the CV

Replace `files/CV.pdf` while keeping the filename unchanged. The stable public URL remains:

```text
https://zhangyuelong.github.io/files/CV.pdf
```

## Media conventions

Use lowercase English names with digits and hyphens:

- `sters-overview.png`
- `sters-real-walking-1.mp4`
- `public-paper.pdf`

Avoid spaces, Chinese filenames, special characters, and names such as `final-final-v2`.

- Use JPG for photographs and PNG for technical figures, diagrams, and plots.
- Use H.264 MP4 with `yuv420p` and fast-start metadata for browser video.
- Short silent demonstrations may use `muted autoplay loop playsinline`.
- Long videos must use controls and must not autoplay.
- Do not crop dense technical figures; link them to the original-resolution asset when close inspection is useful.
- Preserve original research media under a source directory when a browser-ready derivative is required.

Never commit passwords, tokens, private API keys, credentials, private addresses, unpublished data, or other sensitive research material.
