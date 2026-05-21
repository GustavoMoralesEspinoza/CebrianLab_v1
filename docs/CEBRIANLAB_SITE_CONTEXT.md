# CebrianLab Website Context

## 1. Repository Overview

This repository is a Hugo academic research group website for CebrianLab. It is based on the Hugo Research Group / Wowchemy starter and uses HugoBlox modules. The site already contains an early CebrianLab adaptation with a landing-style Home, academic content sections, sample posts/events/publications, custom shortcodes, custom SCSS, and laboratory metadata in JSON files.

The desired target is a compact research group site inspired by the DataHealth Lab architecture, without copying DataHealth content.

## 2. Detected Hugo Theme / Framework

Detected framework:

- Hugo static site generator.
- HugoBlox / Wowchemy page builder.
- Hugo Research Group starter theme.
- Bootstrap-based HugoBlox module stack.

Evidence:

- `theme.toml` names the theme as `Research Group`.
- `go.mod` declares `module github.com/wowchemy/starter-hugo-research-group`.
- `config/_default/module.yaml` imports:
  - `github.com/HugoBlox/hugo-blox-builder/modules/blox-plugin-decap-cms`
  - `github.com/HugoBlox/hugo-blox-builder/modules/blox-plugin-netlify`
  - `github.com/HugoBlox/hugo-blox-builder/modules/blox-bootstrap/v5`
- `content/_index.md` and several section pages use HugoBlox landing-page `sections`.

## 3. Folder Structure

Important current structure:

```text
.
├── .github/
├── assets/
│   ├── media/
│   └── scss/
├── config/
│   └── _default/
│       ├── hugo.yaml
│       ├── languages.yaml
│       ├── menus.yaml
│       ├── module.yaml
│       └── params.yaml
├── content/
│   ├── _index.md
│   ├── admin/
│   ├── authors/
│   ├── contact/
│   ├── event/
│   ├── join/
│   ├── news/
│   ├── people/
│   ├── post/
│   ├── projects/
│   ├── publication/
│   ├── publications/
│   ├── research/
│   ├── team/
│   └── tour/
├── data/
│   ├── members.json
│   └── publications.json
├── docs/
├── images/
├── layouts/
│   └── shortcodes/
├── Metadata/
│   ├── lastupdate.json
│   ├── members.json
│   ├── projects.json
│   └── publications.json
├── static/
│   └── uploads/
├── go.mod
├── netlify.toml
├── README.md
└── theme.toml
```

## 4. Key Configuration Files

| file | purpose | notes |
|---|---|---|
| `config/_default/hugo.yaml` | Main Hugo site config | Sets title, `baseURL`, language, taxonomies, outputs, imaging, permalinks. Current `baseURL` is `https://example.com/`. |
| `config/_default/module.yaml` | Hugo module imports | Loads HugoBlox/Wowchemy modules. Requires Go available in `PATH` for module resolution. |
| `config/_default/menus.yaml` | Main navigation | Current menu includes Home, Research, Projects, Team, Publications, News & Events, Join Us, Contact. |
| `config/_default/params.yaml` | Theme appearance and features | Controls theme, navbar, footer, SEO, analytics, search, maps, citation style. |
| `config/_default/languages.yaml` | Language metadata | Defines site language settings. |
| `go.mod` / `go.sum` | Hugo module dependency lock | Declares Wowchemy starter and HugoBlox dependencies. |
| `netlify.toml` | Netlify build config | Uses Hugo `0.135.0`, build command `hugo --gc --minify -b $URL`. |
| `theme.toml` | Theme metadata | Identifies the Hugo Research Group template. |
| `assets/scss/template.scss` | Custom styling | Contains CebrianLab-specific card grids, hero, PI card, publication styles, responsive rules. |

## 5. Current Content Structure

Current major pages and sections:

| route | file/folder | current status |
|---|---|---|
| `/` | `content/_index.md` | Active landing page with CebrianLab Home sections. |
| `/research/` | `content/research/index.md` | Placeholder research page. |
| `/team/` | `content/team/index.md` | Landing page using HugoBlox `people` block from `content/authors/`; mentions future JSON integration. |
| `/people/` | `content/people/index.md` | Additional people page, likely starter/template or alternate team page. |
| `/publications/` | `content/publications/index.md` | Landing page using HugoBlox collection from `content/publication/`; mentions future JSON integration. |
| `/publication/` | `content/publication/_index.md` plus children | HugoBlox publication section with sample/example publication entries. |
| `/projects/` | `content/projects/_index.md` plus children | Project section with CebrianLab-style project placeholder pages. |
| `/news/` | `content/news/index.md` | Landing page combining posts and events. |
| `/post/` | `content/post/_index.md` plus children | Blog/news post section with sample posts. |
| `/event/` | `content/event/_index.md` plus child | Event section with sample event. |
| `/join/` | `content/join/index.md` | Placeholder Join Us page. |
| `/contact/` | `content/contact/index.md` | HugoBlox contact block with USP/location/contact details. |
| `/tour/` | `content/tour/index.md` | Starter/template tour page. |
| `/admin/` | `content/admin/index.md` | Admin/CMS-related page. |
| `/author/.../` | `content/authors/*/_index.md` | Author profiles used by HugoBlox people/publication features. |

Some existing content appears to be demo/starter material and should be reviewed before public launch, especially sample authors, sample posts, sample events, and sample publications.

## 6. Current Home Structure

The Home page is built in `content/_index.md`.

Technical structure:

- Front matter format: YAML.
- `type: landing`.
- Uses HugoBlox `sections`.
- Uses a mix of HugoBlox blocks:
  - `hero`
  - `markdown`
- Contains substantial inline HTML for CebrianLab cards, buttons, PI card, project cards, selected publications, news cards, partners, join section.
- Uses image `assets/media/Smart_grids.jpg`.
- Styling depends heavily on custom classes in `assets/scss/template.scss`.

Current Home sections:

1. Hero.
2. Expertise and Research Activities.
3. Institutional research statement.
4. Principal Investigator.
5. Our Team preview.
6. Featured Projects.
7. Selected Publications.
8. Where to meet us.
9. Collaborations & Partners.
10. Join CebrianLab.

Recommendation: keep this file stable for now. In later phases, gradually replace hard-coded Home content with data-driven summaries from `data/members.json`, `data/publications.json`, and a copied/adapted `data/projects.json`.

## 7. Menu Configuration

The main menu is configured in:

```text
config/_default/menus.yaml
```

Current menu:

- Home -> `/`
- Research -> `research/`
- Projects -> `projects/`
- Team -> `team/`
- Publications -> `publications/`
- News & Events -> `news/`
- Join Us -> `join/`
- Contact -> `contact/`

Desired future menu:

- Home
- Research
- Team
- Publications
- Impact
- News & Events
- Join Us
- Contact

Recommendation: remove `Projects` from the main menu in R1 or move it under Research/Impact conceptually, but keep the `content/projects/` section available internally if useful.

## 8. Styling and Assets

Styling:

- Main custom stylesheet: `assets/scss/template.scss`.
- It defines CebrianLab-specific classes such as:
  - `.cebrian-hero-tagline`
  - `.cebrian-actions`
  - `.cebrian-card-grid`
  - `.cebrian-card`
  - `.cebrian-pi-card`
  - `.cebrian-stat-grid`
  - `.cebrian-publication-list`
  - `.cebrian-partner-grid`

Appearance config:

- `config/_default/params.yaml`
- Current day theme: `minimal`.
- Font: `native`.
- Navbar enabled, right-aligned, logo/search/day-night enabled.

Images and media:

- `assets/media/Smart_grids.jpg`: currently used by Home hero.
- `assets/media/welcome.jpg`: possible general/Home image.
- `assets/media/coders.jpg`: possible computational tools/team/research visual.
- `assets/media/contact.jpg`: used by Contact page.
- `assets/media/icon.png`: site icon/logo asset.
- `content/authors/admin/avatar.png`: Professor/PI avatar currently used by Home.
- Other author avatars exist under `content/authors/`.
- `images/screenshot.png`, `images/tn.png`, `preview.png`: theme/demo preview assets.

## 9. Data Files

### `data/members.json`

Location:

```text
data/members.json
```

Status:

- Valid JSON.
- Contains 7 member records.
- Duplicated in `Metadata/members.json`.

General structure:

- Top-level JSON array.
- Main fields include:
  - `id`
  - `name`
  - `display_name`
  - `name_variants`
  - `role`
  - `category`
  - `position`
  - `affiliation`
  - `school`
  - `department`
  - `country`
  - `city`
  - `email`
  - profile links such as `google_scholar`, `orcid`, `researchgate`, `github`, `linkedin`
  - `research_areas`
  - `short_bio`
  - `long_bio`
  - `education`
  - `skills`
  - `featured`
  - `active`
  - `last_checked`

Recommended use:

- Source of truth for the future Team page.
- Also useful for Home team preview and PI block.
- Existing shortcode `layouts/shortcodes/team_members.html` already reads `site.Data.members`, but `content/team/index.md` is not currently using that shortcode.

### `data/publications.json`

Location:

```text
data/publications.json
```

Status:

- Valid JSON.
- Contains 39 publication records.
- Duplicated in `Metadata/publications.json`.

General structure:

- Top-level JSON array.
- Main fields include:
  - `id`
  - `title`
  - `year`
  - `type`
  - `venue`
  - `doi`
  - `authors`
  - `related_members`
  - `keywords`
  - `source`
  - `doi_verified`
  - `last_checked`

Recommended use:

- Source of truth for the future `/publications/` page.
- Useful for Home selected publications.
- Existing shortcode `layouts/shortcodes/publications_list.html` reads `site.Data.publications`, but `content/publications/index.md` is not currently using that shortcode.

### `Metadata/projects.json`

Location:

```text
Metadata/projects.json
```

Status:

- Valid JSON.
- Contains 14 `research_focus` entries and 8 `projects`.
- There is no `data/projects.json` yet, so Hugo templates cannot access this through `site.Data.projects` unless it is copied or moved into `data/`.

General structure:

- Top-level object with:
  - `research_focus`: array of research focus strings.
  - `projects`: array of project objects.

Project fields include:

- `id`
- `name`
- `slug`
- `status`
- `development_stage`
- `main_researchers`
- `supervision`
- `collaborators`
- `research_topics`
- `description`
- `publication_ids`
- `publication_note`

Recommended use:

- Copy to `data/projects.json` in a later phase, keeping `Metadata/projects.json` untouched as a source/archive.
- Use for Research, Impact, Projects, and Home research highlights.

### `Metadata/lastupdate.json`

Location:

```text
Metadata/lastupdate.json
```

Status:

- File is empty but PowerShell `ConvertFrom-Json` did not throw an error on the empty content.
- It is not currently mirrored into `data/`.

Recommended use:

- Decide later whether this should become `data/lastupdate.json`.
- If used by Hugo templates, make it explicit valid JSON such as `{}` or a small object with update timestamps.

## 10. DataHealth Lab Reference Mapping

DataHealth Lab was cloned temporarily outside this repository only for architectural comparison. Its structure uses a similar HugoBlox base with more custom sections, including `about`, `people`, `research`, `publication`, `publication_all`, `impact`, `join`, `event`, `outreach`, `post`, and `contact`.

| DataHealth section | CebrianLab equivalent | Recommended action |
|---|---|---|
| `about` | Home / Identity | Do not create a large separate About page now. Keep identity in Home and distribute details into Research, Impact, Join Us. |
| `people` | Team | Prefer `/team/` as the public route. Use `data/members.json`; optionally redirect or retire `/people/` later. |
| `research` | Research | Build `/research/` as the main research areas and projects overview, using `projects.json.research_focus` and selected projects. |
| `publication` | Publications | Keep only one public CebrianLab `/publications/` page for now. Avoid separate featured/all publication sections. |
| `publication_all` | Publications | Use the idea of a full publication listing, but implement compactly in `/publications/` using `data/publications.json`. |
| `impact` | Impact | Add `/impact/` for applied outcomes, tools, datasets, partnerships, media, and project outputs. |
| `event` | News & Events | Can feed `/news/` or future `/events/`; keep menu label as News & Events. |
| `post` | News & Events | Use posts for news updates and project/lab announcements. |
| `join` | Join Us | Keep `/join/`; expand with student/collaborator pathways. |
| `contact` | Contact | Keep `/contact/`; audit encoding/contact details. |
| `outreach` | Future Resources / Outreach | Leave for a future phase. Do not include in main navigation now. |
| `project-impact` | Impact / Projects | Useful architectural idea for impact/project cards, but do not copy content. |
| `project-media` | Impact / News | Potential future pattern for media mentions. |

## 11. Proposed Final Navigation

Recommended final main navigation:

1. Home
2. Research
3. Team
4. Publications
5. Impact
6. News & Events
7. Join Us
8. Contact

Recommended route mapping:

- Home: `/`
- Research: `/research/`
- Team: `/team/`
- Publications: `/publications/`
- Impact: `/impact/`
- News & Events: `/news/`
- Join Us: `/join/`
- Contact: `/contact/`

Optional internal route:

- Projects: `/projects/`, not necessarily in the main menu.

## 12. Proposed Page Responsibilities

### Home

Fast, attractive overview of the laboratory:

- Hero.
- Expertise and Research Activities.
- Short institutional statement.
- Principal Investigator.
- Team preview.
- Featured projects or research highlights.
- Selected publications.
- Impact preview.
- News & Events preview.
- Join Us.
- Contact/footer.

### Research

Primary explanation of scientific areas:

- Research focus grid from `projects.json.research_focus`.
- Narrative about power distribution systems, smart grids, DERs, PV, BESS, EVs, power quality, reliability, resilience, optimization, AI, OpenDSS, and Python.
- Project highlights from `projects.json.projects`.
- Optional link to internal `/projects/`.

### Team

People directory:

- Principal Investigator.
- Researchers.
- PhD students.
- MSc students.
- Undergraduate students.
- Collaborators.
- Alumni.
- Data source should be `data/members.json`.

### Publications

Single consolidated publication section:

- Featured/recent publications.
- Full publication list grouped by year or type.
- DOI links.
- Keyword tags.
- Data source should be `data/publications.json`.
- Keep HugoBlox `content/publication/` entries only if needed for compatibility or individual pages.

### Impact

Applied and societal/technical impact:

- Research outputs.
- Tools and computational workflows.
- Grid planning/operation impacts.
- Partnerships.
- Selected project outcomes.
- Could draw from `projects.json` and future curated impact entries.

### News & Events

Combined updates:

- Lab news from `content/post/`.
- Events from `content/event/`.
- Conferences, seminars, workshops, publications, milestones.

### Join Us

Recruitment and collaboration:

- Undergraduate opportunities.
- MSc/PhD opportunities.
- Postdoctoral opportunities.
- External collaborators.
- Skills expected: power systems, OpenDSS, Python, optimization, data analysis.
- Clear contact/application instructions.

### Contact

Contact and location:

- Lab location.
- Emails.
- Map/contact block if working.
- Institutional links.
- Review encoding and coordinate formatting before launch.

## 13. Recommended Implementation Phases

R0. Audit and bridge file

- Create `docs/CEBRIANLAB_SITE_CONTEXT.md`.
- Create `docs/CEBRIANLAB_FILE_MAP.md`.
- Validate build status.
- Do not make large site changes.

R1. Base structure and navigation

- Update `config/_default/menus.yaml` to desired compact navigation.
- Add `content/impact/index.md`.
- Decide whether `/news/` is the canonical News & Events route.
- Keep `/projects/` internal and remove it from main navigation.
- Decide how to handle `/people/`, `/tour/`, and demo sections.

R2. Home redesign

- Keep the existing Home concept but clean hard-coded content.
- Align Home with the desired 11-part structure.
- Prepare Home to use data-driven summaries.

R3. Research page using `projects.json` / `research_focus`

- Copy/adapt `Metadata/projects.json` to `data/projects.json`.
- Build Research around focus areas and project highlights.

R4. Team using `members.json`

- Switch `/team/` from HugoBlox author profiles to `data/members.json`, or intentionally maintain both with a clear source-of-truth decision.
- Reuse or refine `layouts/shortcodes/team_members.html`.

R5. Publications using `publications.json`

- Switch `/publications/` to `data/publications.json`.
- Reuse or refine `layouts/shortcodes/publications_list.html`.

R6. Impact using `projects.json` and selected outputs

- Build `/impact/`.
- Connect selected impact cards to project metadata and curated outputs.

R7. News & Events

- Clean sample posts/events.
- Decide whether events remain under `/event/` while `/news/` aggregates them.

R8. Join Us and Contact

- Replace placeholders.
- Review contact data, email domains, map coordinates, encoding, and institutional links.

R9. Visual polish, responsive, SEO and deployment

- Review colors, spacing, typography, mobile layout, accessibility, metadata, baseURL, Netlify/GitHub Pages deployment.

## 14. Technical Risks

- Hugo module compilation currently requires Go in `PATH`; local build fails before content rendering.
- HugoBlox/Wowchemy APIs may differ by module version; custom sections should stay compatible with the installed module version.
- Some routes are duplicated or semantically overlapping: `/team/` and `/people/`, `/publications/` and `/publication/`, `/news/`, `/post/`, and `/event/`.
- `Metadata/` and `data/` contain duplicated JSON files; future updates can diverge unless a single source of truth is chosen.
- `Metadata/projects.json` is not accessible as `site.Data.projects` until it is placed under `data/`.
- Several starter/demo files remain and may appear publicly if not removed or hidden.
- Some text displays mojibake/encoding artifacts in terminal output, especially Portuguese names and symbols.
- Contact coordinates appear with encoded dash characters; map rendering may fail until fixed.
- Home has hard-coded data that can drift from JSON data.
- `baseURL` is still `https://example.com/`.
- GitHub Pages or Netlify deployment may require environment-specific Hugo/Go settings.

## Current Build Status

Build command tested:

```powershell
hugo --printPathWarnings
```

Result:

```text
Error: failed to load modules: failed to download modules: binary with name "go" not found in PATH
```

Interpretation:

- The site did not compile in the current local environment because Hugo cannot resolve Hugo modules without the Go binary available in `PATH`.
- This is an environment/dependency issue, not yet proven to be a content/layout issue.
- JSON files in `data/` and `Metadata/` were checked with PowerShell `ConvertFrom-Json`; no JSON parse errors were reported.

Recommended immediate fix before deeper implementation:

- Install Go or add Go to `PATH`.
- Re-run `hugo --printPathWarnings`.
- Then run `hugo server` for browser validation.

## 15. Recommended Next Prompt for Codex

Use this for R1:

```text
Actúa como desarrollador experto en Hugo/HugoBlox para CebrianLab. Ya existe docs/CEBRIANLAB_SITE_CONTEXT.md y docs/CEBRIANLAB_FILE_MAP.md. Implementa solo la fase R1: estructura base y navegación.

Objetivos:
- Actualiza config/_default/menus.yaml al menú principal: Home, Research, Team, Publications, Impact, News & Events, Join Us, Contact.
- Crea content/impact/index.md como página landing mínima, sin contenido inventado.
- Mantén content/projects/ como sección interna, pero quítala del menú principal.
- No borres archivos demo todavía; documenta cuáles quedan pendientes.
- No rediseñes el Home todavía.
- No modifiques JSON de datos salvo que sea necesario.
- Ejecuta validación Hugo al final y reporta errores/warnings.
```
