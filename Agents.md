# Agent reference — conanpodewitt.github.io

Personal website for **Conan (Po) Dewitt**. Static files on GitHub Pages, custom domain `conanpodewitt.com`.

**No build step, no npm, no JS runtime, no runtime network besides user-initiated clicks and the one YouTube iframe.** The page is a single HTML file plus vendored Bootswatch Sketchy CSS and self-hosted fonts. Do not add Google Fonts, CDNs, analytics, or extra auto-loaded embeds.

This is **not** a 3D / CRT / Three.js site. There is no `src/`, no ES modules, no `plain.html`, and no companion models. `pioneer.png` is in the repo but unused by the live page.

## Live site

| What | Value |
| --- | --- |
| Custom domain | https://conanpodewitt.com |
| Repo | https://github.com/conanpodewitt/conanpodewitt.github.io |
| CNAME | `conanpodewitt.com` |

Default remote branch is `main` (Pages). Work on `dev`. Preview with `python3 -m http.server 8000` from the repo root, or open `index.html` directly.

## Layout

```
index.html                      single-page CV (markup + page CSS)
CNAME                           conanpodewitt.com
LICENSE                         MIT
static/css/bootstrap.css        Bootswatch Sketchy 5.3.6 (MIT), fonts rewritten to local files
static/fonts/                   cabin-sketch.woff2, neucha-latin.woff2, neucha-cyrillic.woff2
static/files/conanpodewitt.pdf  resume download
static/images/                  favicon.ico, face.png (header), pioneer.png (unused)
docs/                           empty, unused
```

`static/vendor/` may exist locally as empty leftover directories from an abandoned CRT experiment. It is not part of the live site. Do not vendor Three.js or other libraries there.

## Page structure

Sticky cream header + centred column + cream footer.

- Column: `.site-inner` is `50vw` (max 980px, min 320px); `90vw` below 1000px.
- Header: name, subtitle `Software Engineer · Perth · Western Australia`, contact buttons (LinkedIn, GitHub, Email, Resume).
- Face photo (`static/images/face.png`) sits to the right on `md+`; CSS `spinY` 5s loop. Hidden on small screens. `onerror` hides a missing file.
- Sections, in order: **About** (`#about`), **Experience** (`#experience`), **Education** (`#education`), **Projects** (`#projects`).
- Footer: `© 2026 Conan (Po) Dewitt. All rights reserved.`

Theme overlay (in `index.html` `:root`), on top of Sketchy:

| Token | Value |
| --- | --- |
| `--cream-page` | `#FEFAE0` |
| `--cream-nav` / `--cream-footer` | `#FAEDCD` |
| `--text-color` | `#000000` |
| `--muted-color` | `#401F3E` |
| `--accent` | `#861657` |

Headings use Sketchy’s **Cabin Sketch**; body uses **Neucha**. Both are already self-hosted via `@font-face` in `bootstrap.css`.

## How to edit CV copy

**`index.html` is the source of truth for the public page.** There is no content module.

Use the existing item classes; do not invent a new section pattern:

| Class | Use |
| --- | --- |
| `.item-container` | One employer / degree / project block |
| `.item-name` | Org or project title |
| `.item-meta` | Org-level span, contract, location |
| `.item-description` | Prose |
| `.sub-item` | One role under an employer / one degree |
| `.sub-item-title` | Role or degree name |
| `.sub-item-meta` | Dates and duration |

Durations in the HTML are **hand-written** and go stale. Recalculate inclusive months if you change dates; do not invent new jobs, dates, or skills.

### Facts the HTML already has (do not regress)

- Rocket Software — Software Engineering Intern (NextGen), Feb 2026 – Present, Perth, on-site.
- Sir Charles Gairdner Hospital — Full-stack Developer, Apr 2024 – **Jan 2026** (ended). Work experience student Jan 2024 – Mar 2024.
- City of Bayswater — Shift Supervisor Apr 2024 – Dec 2024; Swim Instructor Sep 2020 – Apr 2024.
- UWA Master of Professional Engineering (Software Engineering), Jul 2023 – **Nov 2025** (finished). Bachelor of Science, Engineering Science, Feb 2020 – Jul 2023.
- Project: LLM-Driven Control for the Pioneer 3-AT Mobile Robot, Jul 2024 – May 2025.
- YouTube demo is an iframe: `https://www.youtube.com/embed/9ZTfI8QgTjU` inside `.video-embed`.
- ORCID: `https://orcid.org/0009-0003-2514-1643`.

### Resume PDF vs the page

`static/files/conanpodewitt.pdf` is a LinkedIn export and is **behind** the page:

- PDF summary still says the master’s is in progress. It is not. MPE ended Nov 2025.
- PDF still lists SCGH Full-stack Developer as Present and does not include Rocket Software.
- PDF includes a mobile number. **Phone number stays off the public page.**

Do not copy those PDF lines onto the site. If asked to refresh the PDF, update it to match `index.html` and keep the phone off the HTML.

## Conventions

- External links: `rel="noopener noreferrer"`. Current markup also uses `target="_blank"`; keep that consistent if you add links.
- User-initiated navigations only, except the existing YouTube embed in Projects.
- Resume download path: `static/files/conanpodewitt.pdf`.
- Contact email: `conanpodewitt@gmail.com`.
- Do not restyle Sketchy by editing the 12k-line `bootstrap.css` unless the task is specifically “update Bootswatch”. Page layout and cream palette live in the `<style>` block in `index.html`.

## Do not

- Introduce Vite/npm as a required deploy path unless Pages is switched to a GitHub Action and `node` is available.
- Load Bootstrap, fonts, or Three.js from a CDN.
- Add a CRT / WebGL / CSS3D desktop unless the user explicitly asks to rebuild that.
- Put a phone number on the public page.
- Treat `pioneer.png` as live content (it is unused).
- Invent jobs, dates, or skills.
- Mark the master’s as in progress.
