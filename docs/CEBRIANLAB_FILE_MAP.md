# CebrianLab File Map

## 1. Project Tree

```text
.
├── .editorconfig
├── .github/
├── .gitignore
├── .hugo_build.lock
├── assets/
│   ├── media/
│   │   ├── Smart_grids.jpg
│   │   ├── coders.jpg
│   │   ├── contact.jpg
│   │   ├── icon.png
│   │   └── welcome.jpg
│   └── scss/
│       └── template.scss
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
│   │   ├── admin/
│   │   ├── AlunoGrad/
│   │   ├── Rennard/
│   │   └── 吳恩達/
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
│   ├── CEBRIANLAB_FILE_MAP.md
│   └── CEBRIANLAB_SITE_CONTEXT.md
├── images/
│   ├── screenshot.png
│   └── tn.png
├── layouts/
│   └── shortcodes/
│       ├── publications_list.html
│       ├── selected_publications.html
│       ├── team_members.html
│       └── team_summary.html
├── Metadata/
│   ├── lastupdate.json
│   ├── members.json
│   ├── projects.json
│   └── publications.json
├── static/
│   └── uploads/
├── go.mod
├── go.sum
├── LICENSE.md
├── netlify.toml
├── preview.png
├── README.md
└── theme.toml
```

## 2. Key Files

| file | controls |
|---|---|
| `content/_index.md` | Home page. HugoBlox `type: landing` page with hero and several markdown sections. |
| `config/_default/menus.yaml` | Main navigation menu. |
| `config/_default/hugo.yaml` | Core Hugo settings, site title, `baseURL`, taxonomies, outputs. |
| `config/_default/module.yaml` | HugoBlox module imports. |
| `config/_default/params.yaml` | Theme appearance, header/footer, SEO, search, maps, publication style. |
| `assets/scss/template.scss` | Custom CebrianLab visual styling. |
| `content/research/index.md` | Current Research landing page placeholder. |
| `content/team/index.md` | Current Team landing page using HugoBlox people block. |
| `content/publications/index.md` | Current Publications landing page using HugoBlox collection block. |
| `content/news/index.md` | Aggregated News & Events page. |
| `content/join/index.md` | Join Us placeholder page. |
| `content/contact/index.md` | Contact landing page with HugoBlox contact block. |
| `content/projects/_index.md` | Projects section index. |
| `content/projects/*/index.md` | Individual project pages. |
| `content/publication/_index.md` | HugoBlox publication section index. |
| `content/publication/*/index.md` | Individual HugoBlox publication entries. |
| `content/post/_index.md` | Blog/news post section index. |
| `content/event/_index.md` | Event section index. |
| `content/authors/*/_index.md` | HugoBlox author profiles used by people/publication features. |
| `layouts/shortcodes/team_members.html` | Data-driven team shortcode using `site.Data.members`. |
| `layouts/shortcodes/team_summary.html` | Team summary shortcode. |
| `layouts/shortcodes/publications_list.html` | Data-driven publications shortcode using `site.Data.publications`. |
| `layouts/shortcodes/selected_publications.html` | Selected publications shortcode. |
| `data/members.json` | Hugo-accessible member data. |
| `data/publications.json` | Hugo-accessible publication data. |
| `Metadata/projects.json` | Project and research focus data, not currently Hugo-accessible through `site.Data`. |
| `Metadata/members.json` | Duplicate/archive copy of member data. |
| `Metadata/publications.json` | Duplicate/archive copy of publication data. |
| `Metadata/lastupdate.json` | Empty update metadata file. |
| `netlify.toml` | Netlify build/deploy settings. |
| `go.mod` | Hugo module dependency declaration. |

## 3. What Each Area Does

### Configuration

`config/_default/` is the main control center for Hugo and HugoBlox:

- `hugo.yaml`: site identity, URLs, taxonomies, outputs, build behavior.
- `module.yaml`: module/theme imports.
- `menus.yaml`: navigation.
- `params.yaml`: visual theme, navbar, footer, SEO, search, maps, citations.
- `languages.yaml`: language metadata.

### Content

`content/` contains pages and sections:

- `content/_index.md`: Home.
- `content/research/`: Research.
- `content/team/`: preferred CebrianLab Team page.
- `content/people/`: alternate/starter people page.
- `content/publications/`: preferred CebrianLab Publications page.
- `content/publication/`: HugoBlox publication content type.
- `content/projects/`: internal project section.
- `content/news/`: aggregate news/events landing page.
- `content/post/`: news/blog posts.
- `content/event/`: event entries.
- `content/join/`: Join Us.
- `content/contact/`: Contact.
- `content/authors/`: profile pages.

### Data

`data/` is directly available to Hugo templates through `site.Data`.

- `data/members.json` -> `site.Data.members`
- `data/publications.json` -> `site.Data.publications`

`Metadata/` is not automatically used by Hugo as `site.Data`. It currently acts as a source/archive folder.

- `Metadata/projects.json` should probably be copied to `data/projects.json` in a later phase.
- Do not delete `Metadata/`.

### Layouts

`layouts/shortcodes/` contains custom reusable renderers:

- `team_members.html`: can render member cards from `data/members.json`.
- `publications_list.html`: can render publication listings from `data/publications.json`.
- `selected_publications.html`: can render selected publication snippets.
- `team_summary.html`: can render team counts/summary.

These shortcodes are useful for the next phases but are not yet wired into all target pages.

### Assets

`assets/media/` contains images processed by Hugo Pipes/HugoBlox.

`assets/scss/template.scss` contains custom styles for current CebrianLab visual components.

`static/uploads/` is available for static files copied directly to the published site.

## 4. Files Not To Touch Yet

Avoid changing these in R1 unless there is a specific build blocker:

- `content/_index.md`: Home is already complex; redesign belongs to R2.
- `assets/scss/template.scss`: visual polish belongs to later phases unless R1 creates a small compatibility issue.
- `data/members.json`: do not edit people data yet.
- `data/publications.json`: do not edit publication data yet.
- `Metadata/*.json`: preserve as source/archive.
- `content/authors/*`: do not clean author profiles until Team source-of-truth is decided.
- `content/publication/*`: do not delete sample publications yet.
- `content/post/*`: do not delete sample posts yet.
- `content/event/*`: do not delete sample events yet.
- `go.mod` / `go.sum`: do not change module versions in R1.
- `theme.toml`: theme metadata only.
- `README.md`: not necessary for R1.

## 5. Files Safe To Modify In The Next Phase

Recommended R1 edit scope:

- `config/_default/menus.yaml`
  - Set the desired compact main menu.
  - Remove `Projects` from main navigation.
  - Add `Impact`.

- `content/impact/index.md`
  - Create a minimal HugoBlox landing page placeholder.
  - Do not invent specific impact claims.

- Optional documentation update:
  - `docs/CEBRIANLAB_SITE_CONTEXT.md`
  - `docs/CEBRIANLAB_FILE_MAP.md`

Possible but defer unless needed:

- `content/projects/_index.md`
  - Can remain as internal section.
- `content/news/index.md`
  - Can remain as canonical News & Events route.

## 6. Files To Pass To ChatGPT For External Help

For architecture/navigation help:

- `docs/CEBRIANLAB_SITE_CONTEXT.md`
- `docs/CEBRIANLAB_FILE_MAP.md`
- `config/_default/menus.yaml`
- `config/_default/hugo.yaml`
- `config/_default/module.yaml`
- `config/_default/params.yaml`
- `theme.toml`
- `go.mod`

For Home redesign:

- `content/_index.md`
- `assets/scss/template.scss`
- `assets/media/` file list
- `data/members.json`
- `data/publications.json`
- `Metadata/projects.json`

For Team page:

- `content/team/index.md`
- `layouts/shortcodes/team_members.html`
- `layouts/shortcodes/team_summary.html`
- `data/members.json`
- relevant `content/authors/*/_index.md` files if HugoBlox author profiles remain in use.

For Publications page:

- `content/publications/index.md`
- `layouts/shortcodes/publications_list.html`
- `layouts/shortcodes/selected_publications.html`
- `data/publications.json`
- `content/publication/_index.md`
- sample `content/publication/*/index.md`

For Research/Impact/Projects:

- `content/research/index.md`
- `content/projects/_index.md`
- `content/projects/*/index.md`
- `Metadata/projects.json`
- future `content/impact/index.md`

For build/deployment:

- `netlify.toml`
- `go.mod`
- `go.sum`
- `config/_default/module.yaml`
- `config/_default/hugo.yaml`
- exact output of `hugo --printPathWarnings` or `hugo server`

## 7. DataHealth Architecture Notes

DataHealth Lab reference repository uses a similar HugoBlox stack but has a broader architecture:

- `content/about/`
- `content/people/`
- `content/research/`
- `content/publication/`
- `content/publication_all/`
- `content/impact/`
- `content/join/`
- `content/event/`
- `content/outreach/`
- `content/post/`
- `content/contact/`
- custom layouts under:
  - `layouts/partials/`
  - `layouts/publication_all/`
  - `layouts/section/`

Recommended CebrianLab adaptation:

- Keep the architecture compact.
- Use `/team/` instead of `/people/`.
- Use one `/publications/` page instead of separate featured/all publication routes.
- Add `/impact/`.
- Keep `/news/` as the menu route for News & Events.
- Leave Outreach/Resources for a future phase.

## 8. Current Validation Notes

Command tested:

```powershell
hugo --printPathWarnings
```

Current result:

```text
Error: failed to load modules: failed to download modules: binary with name "go" not found in PATH
```

JSON validation:

- `data/members.json`: valid.
- `data/publications.json`: valid.
- `Metadata/lastupdate.json`: no parse error reported, but file is empty.
- `Metadata/members.json`: valid.
- `Metadata/projects.json`: valid.
- `Metadata/publications.json`: valid.

Next validation after environment fix:

```powershell
hugo --printPathWarnings
hugo server
```
