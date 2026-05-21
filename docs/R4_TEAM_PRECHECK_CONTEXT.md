# R4 Team Precheck Context

## 1. Current Project State

CebrianLab is a Hugo / HugoBlox / Wowchemy research-group site. R0, R1, R1.5, R2, and R3 are implemented.

- R0 created the main audit/context documentation.
- R1 aligned the main navigation to Home, Research, Team, Publications, Impact, News & Events, Join Us, and Contact. Projects remains available as an internal section.
- R1.5 copied visual assets into `static/images/`, created `data/visual_assets.json`, copied team photos into `static/images/team/`, added `relurl.html`, and marked multiple author folders as draft or empty `user_groups`.
- R2 redesigned Home as an 11-section landing page and uses `selected_publications`.
- R3 created `data/projects.json`, added research/project shortcodes, updated `/research/`, and kept `/projects/` internal.

Do not implement R4 yet. The current Team page still uses HugoBlox author profiles.

## 2. Relevant Files For R4

Read or inspect:

- `content/team/index.md`
- `content/people/index.md`
- `data/members.json`
- `Metadata/members.json`
- `content/authors/`
- `content/authors/photo_manifest.json`
- `layouts/shortcodes/team_members.html`
- `layouts/shortcodes/team_summary.html`
- `static/images/team/`
- `assets/scss/template.scss`
- `content/_index.md`

Likely R4 implementation files:

- `content/team/index.md`
- `layouts/shortcodes/team_members.html`
- `layouts/shortcodes/team_summary.html`
- `assets/scss/template.scss`
- optionally `content/_index.md` only if the Home Team preview is intentionally migrated in R4

## 3. Current Team Page

`content/team/index.md` is a HugoBlox landing page. It contains:

- A markdown intro section.
- A HugoBlox `people` block titled `Current Profiles`.
- `user_groups` from `content/authors/*/_index.md`.

It does not currently use `{{< team_members >}}` or `{{< team_summary >}}`. It still states that the page will be connected to `Metadata/members.json` in a future phase, but the better Hugo data source is now `data/members.json`.

Rendered `/team/` currently shows author-profile output, including duplicate appearances for Juan Cebrian and Gustavo because they belong to multiple HugoBlox `user_groups`.

## 4. Members Data Analysis

`data/members.json` is valid JSON and contains 7 records.

Counts:

- Total members: 7
- Active members: 7
- Featured members: 1
- Categories: `professor` 1, `phd_student` 3, `msc_student` 1, `msc_researcher` 1, `external_collaborator` 1
- Roles: Professor / Principal Investigator 1, PhD Researcher 3, MSc Student and Researcher 1, MSc Researcher 1, External Collaborator / PhD Researcher 1
- Members with `image`: 6
- Members without `image`: 1
- Members with `image_status`: 6
- Members with `image_status: candidate_needs_approval`: 4
- Members with email: 3
- Members with Google Scholar: 5
- Members with ORCID: 3
- Members with ResearchGate: 5
- Members with GitHub: 0
- Members with LinkedIn: 0
- Members with `short_bio`: 7
- Members with `research_areas`: 7

Fields observed:

`active`, `affiliation`, `category`, `city`, `country`, `department`, `display_name`, `education`, `email`, `escavador`, `fapesp_profile`, `featured`, `github`, `google_scholar`, `id`, `image`, `image_alt`, `image_status`, `institutional_profile`, `interests`, `lab_page`, `last_checked`, `lattes`, `linkedin`, `long_bio`, `name`, `name_variants`, `orcid`, `personal_website`, `position`, `professional_affiliation`, `professional_area`, `publications_status`, `research_areas`, `research_group`, `researchgate`, `role`, `school`, `secondary_affiliation`, `short_bio`, `skills`, `teaching`.

Important image-data issue:

- `david-koller-filiu` points to `images/team/jairo-giacomini-jr.jpg`.
- `jairo-giacomini-jr` points to `images/team/gabriela-batista-silva.jpg`.
- `gabriela-batista-silva` has no `image`, although `static/images/team/gabriela-batista-silva.jpg` exists.

## 5. Authors Folder Analysis

Author folders found:

- `admin`
- `AlunoGrad`
- `Base`
- `Carlos`
- `David_Koller`
- `David_Liu`
- `Gabriela`
- `Gustavo`
- `Jairo`
- `Jhon`
- `Marcos`
- `Rennard`
- `Yasmin`

All folders have `_index.md`.

Currently active author profiles, based on no `draft: true` and non-empty `user_groups`:

- `admin`: Juan Cebrian Amasifen, `Principal Investigators` and `Researchers`
- `Gustavo`: Gustavo Lino Morales Espinoza, `Researchers` and `PhD Students`
- `Rennard`: Rennard de Oliveira Brito, `Masters Students`

Draft and empty-group profiles:

- `AlunoGrad`
- `Base`
- `Carlos`
- `David_Koller`
- `David_Liu`
- `Gabriela`
- `Jairo`
- `Jhon`
- `Marcos`
- `Yasmin`

Profiles that look demo/template or mismatched:

- `Base`, `Carlos`, `David_Koller`, `David_Liu`, `Gabriela`, `Jairo`, `Jhon`, `Marcos`, and `Yasmin` have Gustavo template content.
- `AlunoGrad` has Juan Cebrian content under an undergraduate-style folder.

Photo notes:

- Real/plausible author photos: `admin/avatar.png`, `Gustavo/avatar.jpg`, `Rennard/avatar.jpg`, `Carlos/carlos-alberto-carneiro.jpg`, `Gabriela/gabriela-batista-silva.jpg`, `Jairo/jairo-giacomini-jr.jpg`.
- Generic placeholder photos: `Avatar.jpg`, `AvatarMuejr.jpg`, and folders using those files.

The duplicate target warning for `author/gustavo-lino-morales-espinoza` is likely caused by multiple author folders with `title: Gustavo Lino Morales Espinoza`, even when some are draft or have `user_groups: []`.

## 6. Team Images Analysis

Files in `static/images/team/`:

- `carlos-alberto-carneiro.jpg`
- `gabriela-batista-silva.jpg`
- `gustavo-lino-morales-espinoza.jpg`
- `jairo-giacomini-jr.jpg`
- `juan-carlos-cebrian-amasifen.png`
- `rennard-de-oliveira-brito.jpg`

All current non-empty `image` paths in `data/members.json` point to files that exist.

Members with apparently correct connected image:

- Juan Carlos Cebrian
- Gustavo Lino Morales Espinoza
- Carlos A. Carneiro
- Rennard de Oliveira Brito

Members with suspicious or missing image mapping:

- David Koller Filiu: points to Jairo image.
- Jairo Giacomini Jr: points to Gabriela image.
- Gabriela Batista Silva: no image field, despite a local image file existing.

Candidate images from R1.5 / manifest:

- Juan Carlos Cebrian
- Carlos Alberto Carneiro
- Jairo Giacomini Jr
- Gabriela Batista Silva

## 7. Existing Team Shortcodes

### `team_members.html`

Exists and reads `site.Data.members`.

Behavior:

- Filters active members with `where $members "active" "!=" false`.
- Groups by fixed `category` values.
- Renders Principal Investigator as a featured group.
- Sorts each group by `display_name`.
- Shows images using `.photo`, `.avatar`, then `.image`.
- Has initials fallback when no photo exists.
- Shows role, name, position, affiliation, short bio, first 5 research areas, and available links.

Issues before R4:

- Uses `src="{{ $photo }}"` directly instead of `relURL`, so relative deployment paths may break.
- Has an old hard-coded fallback for Juan to `/author/admin/avatar.png`.
- Does not explicitly flag candidate images.
- Mostly robust to missing optional fields, but image URL handling should be improved.

### `team_summary.html`

Exists and reads `site.Data.members`.

Behavior:

- Filters active members.
- Counts fixed categories and renders a `.cebrian-stat-grid`.
- Uses categories: professor, PhD, MSc, MSc researcher, undergraduate, collaborator, alumni.

Issues before R4:

- Uses `site.Data.members`, which works now but triggers Hugo deprecation warnings in current Hugo. This is also true of other existing shortcodes.
- It does not include `researcher` or `postdoc`, although `team_members.html` does.
- It is safe for missing categories because it only renders counts greater than zero.

## 8. Known Issues Before R4

- `/team/` still uses HugoBlox `people` and `content/authors/`, not `data/members.json`.
- Active author profiles duplicate people across user groups on the rendered Team page.
- Multiple draft/template author folders have the same title as Gustavo, likely causing the duplicate target path warning.
- Several author folders contain demo or copied template content.
- Several author folders use generic placeholder photos.
- Candidate team photos need approval before official publication.
- `data/members.json` image assignments for David, Jairo, and Gabriela are inconsistent.
- `data/members.json` and `content/authors/` are not aligned one-to-one.
- Team shortcodes exist but are not wired into `/team/`.
- `team_members.html` should use `relURL` for member images in R4.

## 9. Recommended R4 Strategy

- Use `data/members.json` as the primary Team source.
- Do not use `content/authors/` as the primary Team source.
- Replace the HugoBlox `people` block in `content/team/index.md` with the `team_members` shortcode.
- Use `team_summary` only if the current category counts are acceptable and CSS already supports it.
- Keep `content/authors/` for HugoBlox compatibility and publication author pages, but do not depend on it for the Team directory.
- Refactor `team_members.html` only as needed: `relURL` for images, no empty fields, initials fallback, robust grouping.
- Document candidate photos and avoid implying that candidate portraits are final.
- Before showing all portraits publicly, fix the David/Jairo/Gabriela image mapping or let those members fall back to initials.

## 10. Files Safe To Modify In R4

- `content/team/index.md`
- `layouts/shortcodes/team_members.html`
- `layouts/shortcodes/team_summary.html`
- `assets/scss/template.scss`
- `docs/R4_TEAM_IMPLEMENTATION_SUMMARY.md` or equivalent new documentation
- optionally `content/_index.md` if R4 explicitly includes Home Team preview migration

Only modify `data/members.json` in R4 if the prompt explicitly authorizes correcting the image mappings.

## 11. Files Not To Touch In R4

- Do not delete files or folders from `content/authors/`.
- Do not delete files from `static/images/team/`.
- Do not modify `Metadata/members.json` unless there is an explicit synchronization decision.
- Do not modify publications, projects, Research, Impact, News, Join, or Contact unless a build blocker is discovered.
- Do not make broad visual redesigns outside Team-related CSS.

## 12. Suggested Next Prompt

Implement R4 only: migrate `/team/` from the HugoBlox `people` block to a data-driven Team page using `data/members.json` and the existing Team shortcodes. Keep changes scoped to `content/team/index.md`, Team shortcodes, and necessary Team CSS. Do not delete author folders, do not invent missing data, use `relURL` for images, use initials fallbacks for missing or questionable portraits, and document remaining candidate-photo/image-mapping issues.
