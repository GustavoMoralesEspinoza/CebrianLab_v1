# R3 Research Page Summary

## 1. Files Modified

- `content/research/index.md`
- `content/projects/_index.md`
- `assets/scss/template.scss`

## 2. Files Created

- `data/projects.json`
- `layouts/shortcodes/research_focus_grid.html`
- `layouts/shortcodes/research_projects_grid.html`
- `layouts/shortcodes/featured_projects.html`
- `docs/R3_RESEARCH_PAGE_SUMMARY.md`

## 3. `data/projects.json`

Created `data/projects.json` from:

```text
Metadata/projects.json
```

`Metadata/projects.json` was not modified.

The generated `data/projects.json` preserves:

- `research_focus`
- `projects`
- project metadata such as `id`, `name`, `slug`, `status`, `development_stage`, `main_researchers`, `supervision`, `collaborators`, `research_topics`, `description`, `publication_ids`, and `publication_note`

Derived visual fields were added only to `data/projects.json`:

- `image_key`
- `image`
- `webp`
- `image_alt`

The file was saved as UTF-8 without BOM after Hugo rejected the first PowerShell-generated version with a BOM.

## 4. Project Image Mapping

Project images were mapped from `data/visual_assets.json.projects`.

| project id | visual asset key |
|---|---|
| `hosting-capacity-der-integration` | `hosting-capacity-der-integration` |
| `distribution-expansion-planning-sensitive-loads` | `distribution-expansion-planning` |
| `power-quality-financial-impact-vtcd` | `power-quality-vtcd-financial-losses` |
| `der-control-voltage-regulation-consensus` | `der-control-voltage-regulation` |
| `reliability-automated-switches-self-healing` | `reliability-self-healing-restoration` |
| `extreme-events-der-restoration` | `extreme-events-der-restoration` |
| `non-technical-losses-ai` | `non-technical-losses-ai` |
| `smart-grids-interoperability-iot` | `smart-grids-iot-interoperability` |

All 8 projects received image mappings.

## 5. Focus Icon Mapping

`layouts/shortcodes/research_focus_grid.html` maps `site.Data.projects.research_focus` entries to `data/visual_assets.json.focus_icons`.

Some icons are intentionally reused for related focus areas:

- DER and hosting capacity topics use `hosting-capacity-der`.
- Reliability, resilience, self-healing, extreme events, and switching topics use `resilience-self-healing-extreme-events`.
- OpenDSS, Python, smart grids, IoT, and interoperability topics use `smart-grids-iot-opendss-python`.
- Energy transition uses `power-distribution-systems`.

## 6. Shortcodes Created

### `research_focus_grid.html`

Purpose:

- Reads `site.Data.projects.research_focus`.
- Reads `site.Data.visual_assets.focus_icons`.
- Renders a responsive grid of focus-area cards.
- Uses `relURL` for images.
- Falls back to `power-distribution-systems` if no mapping is found.

### `research_projects_grid.html`

Purpose:

- Reads `site.Data.projects.projects`.
- Renders all project cards.
- Displays image, status, title, truncated description, first 4 research topics, and a link.
- Uses `relURL` for images and links.
- Does not fail if image or optional fields are missing.

### `featured_projects.html`

Purpose:

- Renders the same 4 featured projects used in the Home Research Highlights.
- Prepared for a future Home migration.

The R2 Home was not replaced with this shortcode during R3 to avoid introducing layout churn after the Home redesign was already validated. It can be migrated safely in a later cleanup once screenshots are reviewed.

## 7. Final `/research/` Structure

`content/research/index.md` is now a HugoBlox landing page with:

1. Header / intro.
2. Visual research introduction using `hero-flexible-grids`.
3. Research Focus Areas via `{{< research_focus_grid >}}`.
4. Research Projects via `{{< research_projects_grid >}}`.
5. Closing CTA linking to Join, Contact, Publications, and Impact.

## 8. `/projects/` Update

`content/projects/_index.md` was lightly updated as an internal project listing using:

```go-html-template
{{< research_projects_grid >}}
```

No individual project pages were deleted or migrated.

Potential future issue:

- Some individual `content/projects/*` pages may have slugs that do not match the 8 IDs in `data/projects.json`. That should be reviewed in a future project-pages cleanup.

## 9. Home Research Highlights

Home Research Highlights were not replaced in R3.

Reason:

- The R2 Home was already validated and visually stable.
- The new `featured_projects.html` shortcode is available and can replace the static Home section in a later pass after screenshot review.

## 10. CSS Changes

Added/expanded classes in `assets/scss/template.scss`:

- `.cebrian-status-badge`
- `.cebrian-research-hero`
- `.cebrian-research-hero-copy`
- `.cebrian-research-hero-image`
- `.cebrian-section-intro`
- `.cebrian-focus-grid`
- `.cebrian-project-tags`
- `.cebrian-research-cta`

Existing classes reused:

- `.cebrian-research-card`
- `.cebrian-research-card-image`
- `.cebrian-project-cover`
- `.cebrian-focus-icon`
- `.cebrian-card-grid`
- `.cebrian-card`
- `.cebrian-actions`

## 11. Validation

Command attempted first:

```powershell
hugo --printPathWarnings
```

Result:

- Failed because default `hugo` still points to non-Extended Hugo `v0.149.0`.
- The first run also revealed `data/projects.json` had a UTF-8 BOM; this was fixed by rewriting the file as UTF-8 without BOM.

Successful build command:

```powershell
& "$env:LOCALAPPDATA\Microsoft\WinGet\Packages\Hugo.Hugo.Extended_Microsoft.Winget.Source_8wekyb3d8bbwe\hugo.exe" --printPathWarnings
```

Successful route checks:

- `/research/`
- `/projects/`
- `/`
- `/team/`
- `/publications/`
- `/impact/`
- `/join/`
- `/contact/`

Successful image checks:

- `/images/hero/hero-flexible-grids.png`
- `/images/projects/reliability-self-healing-restoration.png`

Rendered `/research/` checks:

- Research Focus Areas present.
- Research Projects present.
- Hero image present.
- Project images present.
- No raw shortcode text remained in the rendered HTML.

## 12. Warnings

Hugo Extended build warnings remain:

- `languages.en.languageCode` deprecated in Hugo v0.158.0.
- HugoBlox/internal `.Site.LanguageCode`, `.Site.Data`, and `.Site.AllPages` deprecation warnings.
- `blox-seo` sitemap render hook warning.
- Duplicate target paths for `author/gustavo-lino-morales-espinoza`.

These warnings are not introduced by R3 and should be handled in later config/content cleanup.

## 13. Recommendations

R4 Team:

- Resolve author profile duplicates and mismatched placeholder profiles.
- Decide whether Team should render from `data/members.json` instead of HugoBlox author folders.
- Review candidate photos before official publication.

R6 Impact:

- Use `data/projects.json` and `data/visual_assets.json` to build impact cards.
- Connect project outputs, publications, and tools without inventing metrics.

Future Home cleanup:

- Replace static Home Research Highlights with `{{< featured_projects >}}` after a screenshot review.
