# R4 Team Implementation Summary

## 1. Files Modified

- `data/members.json`
- `content/team/index.md`
- `layouts/shortcodes/team_members.html`
- `layouts/shortcodes/team_summary.html`
- `assets/scss/template.scss`

## 2. Files Created

- `docs/R4_TEAM_IMPLEMENTATION_SUMMARY.md`

## 3. Changes In `data/members.json`

Only image fields were corrected.

- `david-koller-filiu`: removed the incorrect `image`, `image_alt`, and `image_status` fields that pointed to Jairo's portrait.
- `jairo-giacomini-jr`: changed `image` to `images/team/jairo-giacomini-jr.jpg` and `image_alt` to `Portrait of Jairo Giacomini Jr`.
- `gabriela-batista-silva`: added `image: images/team/gabriela-batista-silva.jpg`, `image_alt: Portrait of Gabriela Batista Silva`, and `image_status: candidate_needs_approval`.

No academic data, roles, emails, links, or biographies were changed.

## 4. Image Correction Confirmation

Verified before assignment:

- `static/images/team/jairo-giacomini-jr.jpg` exists.
- `static/images/team/gabriela-batista-silva.jpg` exists.

Final behavior:

- David Koller Filiu has no image and renders with initials fallback.
- Jairo Giacomini Jr uses his own portrait.
- Gabriela Batista Silva uses her local portrait.

## 5. Team Data Source

The public `/team/` page now uses `data/members.json` through `site.Data.members`.

`content/authors/` is no longer used as the primary Team directory source.

## 6. `content/team/index.md`

The old HugoBlox `people` block was removed.

The page remains a HugoBlox `type: landing` page with one markdown block containing:

- a short academic intro,
- `{{< team_members >}}`,
- a Join/Contact CTA using `relurl` for GitHub Pages-compatible links.

## 7. `team_members.html`

The shortcode was refactored to:

- read `site.Data.members`,
- include records where `active != false`,
- render Principal Investigator / Faculty separately,
- group the rest by category,
- skip empty categories,
- sort by `display_name`,
- use `relURL` for images,
- render initials when no reliable portrait exists,
- show only non-empty fields,
- show links only when present,
- avoid exposing `image_status` and `last_checked`.

Supported links:

- email
- Google Scholar
- ORCID
- ResearchGate
- Lattes
- institutional profile
- personal website
- Escavador
- FAPESP

## 8. `team_summary.html`

The summary shortcode now:

- reads `site.Data.members`,
- filters active members,
- counts real categories only,
- skips zero-count categories,
- includes a button to `/team/` using `relURL`.

It is ready for Home or future preview sections, but Home was not modified in R4.

## 9. Member Grouping

Visible grouping is based on `category`:

- `professor` -> Principal Investigator / Faculty
- `researcher` -> Researchers
- `postdoc` -> Postdoctoral Researchers
- `phd_student` -> PhD Students
- `msc_student` -> MSc Students
- `msc_researcher` -> MSc Researchers
- `undergraduate_student` -> Undergraduate Students
- `external_collaborator` -> External Collaborators
- `collaborator` -> Collaborators
- `alumni` -> Alumni

Only categories with members are rendered.

## 10. Principal Investigator Handling

Members with `category: professor` are shown in a highlighted Principal Investigator / Faculty section using `.cebrian-pi-profile`.

Current rendered PI:

- Juan Carlos Cebrian

## 11. Images And Fallbacks

Images are rendered with:

```go-html-template
{{ $photo | relURL }}
```

Members without an image render an initials fallback. David Koller Filiu currently renders as `DK`.

## 12. Candidate Images

Candidate images remain documented through `image_status: candidate_needs_approval` in `data/members.json`, but this status is not displayed publicly.

Candidate portraits:

- Juan Carlos Cebrian
- Carlos A. Carneiro
- Jairo Giacomini Jr
- Gabriela Batista Silva

## 13. Members Without Reliable Image

- David Koller Filiu

He now uses the initials fallback.

## 14. Home Team Preview

Home was not modified in R4.

Reason: the R2 Home preview is visually stable, and replacing it should be done with screenshot review in a later small pass.

## 15. CSS Changes

Added Team-specific styles in `assets/scss/template.scss`:

- `.cebrian-team-page`
- `.cebrian-team-section`
- `.cebrian-team-grid`
- `.cebrian-pi-profile`
- `.cebrian-team-card`
- `.cebrian-team-avatar`
- `.cebrian-avatar-fallback`
- `.cebrian-member-links`
- `.cebrian-member-tags`
- `.cebrian-team-cta`
- `.cebrian-team-summary`

The new Team card styles are scoped to `.cebrian-team-page` where needed so the existing Home Team preview is not intentionally redesigned.

## 16. `content/authors/` State

No `content/authors/` files were modified.

Known state remains:

- Some folders are draft/template profiles.
- Several draft profiles still contain Gustavo template content.
- `content/authors/` should remain for compatibility for now, but it is not the Team source of truth.

## 17. Duplicate Target Path Warning

The warning remains:

```text
Duplicate target paths: \author\gustavo-lino-morales-espinoza\index.html (2), \author\gustavo-lino-morales-espinoza\index.xml (2)
```

It was not changed in R4 because resolving it requires editing draft author profiles, and that cleanup is better handled as a separate content/authors phase.

## 18. Hugo Validation

Default Hugo command:

```powershell
hugo --printPathWarnings
```

Result: fails because the default `hugo` is not Extended and cannot run required image processing.

Hugo Extended command:

```powershell
& "$env:LOCALAPPDATA\Microsoft\WinGet\Packages\Hugo.Hugo.Extended_Microsoft.Winget.Source_8wekyb3d8bbwe\hugo.exe" --printPathWarnings
```

Result: build succeeded.

Server route checks returned `200`:

- `/`
- `/research/`
- `/projects/`
- `/team/`
- `/publications/`
- `/impact/`
- `/news/`
- `/join/`
- `/contact/`

Rendered `/team/` checks:

- Principal Investigator / Faculty appears.
- PhD Students, MSc Students, MSc Researchers, and External Collaborators appear.
- `Current Profiles` no longer appears.
- no raw `team_members` shortcode text appears.
- David Koller Filiu appears with initials fallback.
- Jairo image path appears as `/images/team/jairo-giacomini-jr.jpg`.
- Gabriela image path appears as `/images/team/gabriela-batista-silva.jpg`.
- empty links are not rendered.

## 19. Warnings Or Errors

Remaining Hugo Extended warnings:

- `languages.en.languageCode` is deprecated.
- HugoBlox uses deprecated `.Site.LanguageCode`, `.Site.Data`, and `.Site.AllPages`.
- `blox-seo` sitemap render hook warning.
- duplicate target paths for Gustavo author profile.

These warnings predate R4 or relate to theme/content cleanup outside the Team migration.

## 20. Recommendations For R5 Publications

R5 should migrate `/publications/` to `data/publications.json` with a data-driven shortcode, similar to R4:

- keep `content/publication/` for compatibility,
- avoid relying on demo publication entries,
- group publications by year and/or type,
- render DOI links only when present,
- keep route and links GitHub Pages-compatible with `relURL`.
