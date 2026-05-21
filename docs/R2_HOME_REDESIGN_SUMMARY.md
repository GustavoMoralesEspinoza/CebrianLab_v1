# R2 Home Redesign Summary

## 1. Files Modified

- `content/_index.md`
- `assets/scss/template.scss`

## 2. Files Created

- `docs/R2_HOME_REDESIGN_SUMMARY.md`

## 3. Final Home Sections

The Home page now uses the requested 11-section structure:

1. Hero principal
2. Expertise and Research Activities
3. Short institutional statement
4. Principal Investigator
5. Team preview
6. Research Highlights
7. Selected Publications
8. Impact preview
9. News & Events preview
10. Join CebrianLab
11. Contact / Footer link area

The page remains a HugoBlox landing page:

```yaml
type: landing
```

## 4. Images Used From `data/visual_assets.json`

The Home uses image paths already mapped in `data/visual_assets.json`. The paths were used without a leading slash for GitHub Pages compatibility.

Hero:

- `images/hero/hero-smart-distribution-grid.png`
- `images/webp/hero-smart-distribution-grid.webp`

Focus icons:

- `images/focus-icons/power-distribution-systems.png`
- `images/focus-icons/distribution-network-planning.png`
- `images/focus-icons/hosting-capacity-der.png`
- `images/focus-icons/grid-flexibility-demand-response.png`
- `images/focus-icons/power-quality-reliability-vtcd.png`
- `images/focus-icons/financial-losses-sensitive-customers.png`
- `images/focus-icons/resilience-self-healing-extreme-events.png`
- `images/focus-icons/optimization-ai-evolutionary.png`
- `images/focus-icons/smart-grids-iot-opendss-python.png`

Research Highlights:

- `images/projects/hosting-capacity-der-integration.png`
- `images/projects/distribution-expansion-planning.png`
- `images/projects/power-quality-vtcd-financial-losses.png`
- `images/projects/reliability-self-healing-restoration.png`

Team preview:

- `images/team/juan-carlos-cebrian-amasifen.png`
- `images/team/gustavo-lino-morales-espinoza.jpg`
- `images/team/rennard-de-oliveira-brito.jpg`

## 5. Data-Driven Sections

Selected Publications uses the existing shortcode:

```go-html-template
{{< selected_publications >}}
```

That shortcode reads from:

```text
data/publications.json
```

The Home also uses real values previously inspected from:

- `data/members.json`
- `Metadata/projects.json`
- `data/visual_assets.json`

Because HugoBlox front matter markdown blocks do not directly evaluate arbitrary `site.Data` expressions, most Home content is currently static HTML/Markdown assembled from real data. R3/R4 can convert these sections into custom shortcodes or partials.

## 6. Temporarily Static Sections

The following sections are static for now, but based on real local data or intentionally editable placeholders:

- Hero content
- Expertise and Research Activities cards
- Principal Investigator card
- Team preview and category counts
- Research Highlights cards
- Impact preview cards
- News & Events preview placeholders
- Join CebrianLab
- Get in touch

News & Events uses clearly editable placeholders because current `content/post/` and `content/event/` include demo/starter content.

## 7. Shortcodes Used

Used:

- `layouts/shortcodes/selected_publications.html`

Available but not needed directly in the Home after using relative static paths:

- `layouts/shortcodes/relurl.html`

## 8. CSS Changes

Updated `assets/scss/template.scss` with responsive styling for:

- `.cebrian-home-hero`
- `.cebrian-home-hero-content`
- `.cebrian-home-hero-media`
- `.cebrian-focus-card`
- `.cebrian-research-card-body`
- `.cebrian-team-preview`
- `.cebrian-team-card`
- `.cebrian-impact-preview`
- `.cebrian-impact-grid`
- `.cebrian-join-panel`
- `.cebrian-contact-strip`

The existing R1.5 classes continue to be used:

- `.cebrian-project-cover`
- `.cebrian-research-card`
- `.cebrian-research-card-image`
- `.cebrian-focus-icon`
- `.cebrian-team-avatar`
- `.cebrian-team-card`
- `.cebrian-bg-section`

## 9. Real Data Used

Principal Investigator data was taken from `data/members.json` and existing author profile content:

- Name: Juan Carlos Cebrian
- Role: Professor / Principal Investigator
- Position and affiliation
- Short bio
- Research interests
- Google Scholar, ORCID, ResearchGate, email

Team preview uses members from `data/members.json` with available portraits:

- Juan Carlos Cebrian
- Gustavo Lino Morales Espinoza
- Rennard de Oliveira Brito

Research Highlights are based on records in `Metadata/projects.json`:

- Hosting Capacity Assessment and DER Integration
- Distribution Expansion Planning for Modern and Sensitive Loads
- Power Quality, VTCD Impact Factor and Financial Losses
- Network Reliability, Automated Switching and Self-Healing Restoration

Publications are rendered from `data/publications.json`.

## 10. Placeholders Remaining

News & Events remains intentionally placeholder-based until demo content is reviewed or real news/events are added.

The Home still uses static excerpts for projects and team preview. Recommended later conversion:

- R3: project cards from `data/projects.json`
- R4: team preview from `data/members.json`
- R7: verified news/events collection

## 11. Validation

Command attempted first:

```powershell
hugo --printPathWarnings
```

Result:

- Failed because the default `hugo` command still points to non-Extended Hugo `v0.149.0`.
- Error source: Hugo image/SCSS processing requires Hugo Extended.

Successful build command:

```powershell
& "$env:LOCALAPPDATA\Microsoft\WinGet\Packages\Hugo.Hugo.Extended_Microsoft.Winget.Source_8wekyb3d8bbwe\hugo.exe" --printPathWarnings
```

Successful route checks through `hugo server`:

- `/`
- `/research/`
- `/team/`
- `/publications/`
- `/impact/`
- `/news/`
- `/join/`
- `/contact/`

Successful image checks:

- `/images/hero/hero-smart-distribution-grid.png`
- `/images/focus-icons/power-distribution-systems.png`
- `/images/projects/hosting-capacity-der-integration.png`

Menu check:

- `Impact` appears.
- `Projects` is not in the main menu.

## 12. Warnings

Hugo Extended build warnings:

- `languages.en.languageCode` deprecated in Hugo v0.158.0.
- HugoBlox/internal usage of `.Site.LanguageCode`, `.Site.Data`, and `.Site.AllPages` is deprecated in current Hugo.
- `blox-seo` sitemap render hook warning.
- Duplicate target paths remain for `author/gustavo-lino-morales-espinoza`.

The duplicate author warning appears related to remaining demo/author content and should be addressed in a later author/content cleanup phase, not as part of R2.

## 13. Recommendations For R3 Research

R3 should:

- Copy or adapt `Metadata/projects.json` into `data/projects.json`.
- Add image keys or map project IDs to `data/visual_assets.json.projects`.
- Replace static Research Highlights on the Home with a shortcode or partial.
- Build `/research/` around research focus icons and project cards.
- Use relative URLs or `relURL` for all images and links to stay compatible with GitHub Pages subpaths.
