# R5 Publications Implementation Summary

## 1. Files Modified

- `content/publications/index.md`
- `layouts/shortcodes/publications_list.html`
- `layouts/shortcodes/selected_publications.html`
- `assets/scss/template.scss`

No changes were made to `data/publications.json`.

## 2. Files Created

- `docs/R5_PUBLICATIONS_IMPLEMENTATION_SUMMARY.md`

## 3. Main Data Source

The public `/publications/` page now uses:

- `data/publications.json`

`Metadata/publications.json` remains untouched as a secondary/source copy.

## 4. Detected `data/publications.json` Structure

Detected fields:

- `authors`
- `doi`
- `doi_verified`
- `duplicate_title_group`
- `id`
- `keywords`
- `last_checked`
- `related_members`
- `source`
- `title`
- `type`
- `url`
- `venue`
- `volume_issue_pages`
- `year`

No `featured`, `selected`, or `highlight` fields were detected.

Detected optional resource fields:

- `url`: present in some records.
- no `pdf`, `pdf_url`, `code`, `code_url`, `poster`, `poster_url`, `presentation`, or `presentation_url` fields were detected.

## 5. Publications Processed

Total publications: 39.

Counts:

- With DOI: 35
- Without DOI: 4
- With venue: 36
- With keywords: 36
- With related members: 36
- With `doi_verified`: 36
- With source: 36
- With URL: 19

## 6. Grouping Used

The full list is sorted by year descending and grouped by year.

Detected years:

- 2026: 5
- 2025: 14
- 2024: 12
- 2023: 5
- 2022: 2
- 2020: 1

Within each year, publications are sorted by title.

## 7. Publication Types Detected

- `journal-article`: 16
- `conference-paper`: 20
- `preprint`: 2
- `book-chapter`: 1

Types are rendered as visible badges.

## 8. DOI Handling

DOI links are generated only when `doi` exists.

- If `doi` starts with `http`, it is used directly.
- Otherwise, it is converted to `https://doi.org/[doi]`.
- If `url` is the same as the DOI URL, the duplicate URL button is skipped.

## 9. Keywords Handling

`keywords` are rendered as compact tags.

The full publication list shows up to 8 keywords per record.

## 10. Related Members Handling

`related_members` are displayed when present.

The shortcode attempts to resolve member IDs against `data/members.json`:

- if a matching member exists, it displays `display_name` or `name`;
- if no match is found, it falls back to the raw value.

No member JSON data was modified.

## 11. `content/publications/index.md`

The page remains a HugoBlox `type: landing` page.

The old HugoBlox `collection` block was removed, so the page no longer uses demo entries from `content/publication/` as its main source.

Current structure:

1. Intro text.
2. `Selected / Recent Publications` using `{{< selected_publications >}}`.
3. `All Publications` using `{{< publications_list >}}`.
4. CTA linking to Join, Contact, and Research using `relurl`.

## 12. `publications_list.html`

The shortcode now:

- reads `site.Data.publications`,
- sorts by year descending,
- groups by year,
- renders academic publication cards,
- displays title, authors, year, type, venue, volume/pages, related members, keywords, source, and links when present,
- normalizes DOI links,
- supports optional PDF, URL, code, poster, and presentation fields if they are added later,
- does not show `last_checked`.

## 13. `selected_publications.html`

The shortcode now:

- reads `site.Data.publications`,
- prioritizes `featured`, then `selected`, then `highlight` if any of those fields exist,
- falls back to the most recent publications when no highlight field exists,
- renders up to 4 compact cards,
- shows title, authors, year, type, venue, and DOI link if present.

Home still uses this shortcode and was validated after the change.

## 14. Home Impact

`content/_index.md` was not modified.

Because Home already uses `{{< selected_publications >}}`, the rendered Home Selected Publications section now uses the refactored card markup. It was checked for successful rendering and no raw shortcode text.

## 15. `content/publication/` State

`content/publication/` still exists and was not modified or deleted.

Detected entries:

- `conference-paper`
- `journal-article`
- `preprint`

These appear to be HugoBlox publication/demo-style entries and are no longer the primary source for `/publications/`.

## 16. CSS Changes

Added/refined publication-specific classes in `assets/scss/template.scss`:

- `.cebrian-publications-page`
- `.cebrian-publications-section`
- `.cebrian-publication-year`
- `.cebrian-publication-card`
- `.cebrian-publication-title`
- `.cebrian-publication-meta`
- `.cebrian-publication-authors`
- `.cebrian-publication-venue`
- `.cebrian-publication-links`
- `.cebrian-publication-tags`
- `.cebrian-publication-badge`
- `.cebrian-publications-cta`
- `.cebrian-selected-publications`

The styles use the existing CebrianLab visual language and remain responsive.

## 17. Hugo Validation

JSON validation:

- `data/publications.json` parses successfully.

Default Hugo:

```powershell
hugo --printPathWarnings
```

Result: fails because the default Hugo binary is not Extended.

Hugo Extended:

```powershell
& "$env:LOCALAPPDATA\Microsoft\WinGet\Packages\Hugo.Hugo.Extended_Microsoft.Winget.Source_8wekyb3d8bbwe\hugo.exe" --printPathWarnings
```

Result: build succeeded.

Route checks returned `200`:

- `/`
- `/research/`
- `/team/`
- `/publications/`
- `/impact/`
- `/news/`
- `/join/`
- `/contact/`

Rendered `/publications/` checks:

- `Selected / Recent Publications` appears.
- `All Publications` appears.
- year sections such as 2026 and 2025 appear.
- DOI links render as `https://doi.org/...`.
- type badges render.
- keywords render as tags.
- related members render with display names where resolvable.
- no raw shortcode text appears.
- `Current Publication Entries` no longer appears.
- demo `publication/conference-paper` links do not appear as the main publications source.

## 18. Warnings Or Errors

Remaining Hugo Extended warnings:

- `languages.en.languageCode` is deprecated.
- HugoBlox uses deprecated `.Site.LanguageCode`, `.Site.Data`, and `.Site.AllPages`.
- `blox-seo` sitemap render hook warning.
- duplicate target paths for `author/gustavo-lino-morales-espinoza`.

These warnings predate R5 or are related to theme/content cleanup outside the Publications migration.

## 19. Recommendations For R6 Impact

R6 should build `/impact/` using `data/projects.json`, `data/publications.json`, and `data/visual_assets.json`.

Recommended approach:

- keep claims conservative and data-backed,
- connect impact cards to projects and selected publications,
- avoid inventing metrics,
- use visual assets already mapped in `data/visual_assets.json`,
- keep `/projects/` as an internal supporting section.
