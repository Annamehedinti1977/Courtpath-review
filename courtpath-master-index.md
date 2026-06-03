# CourtPath master index

## Purpose
This file is the master index for the CourtPath project. It is meant to become the starting point for organizing all product, business, design, and launch materials in one place.[cite:364][cite:367][cite:369] Repository and documentation best practices recommend a clear README or index file, a consistent directory structure, and a centralized source of truth so the project stays understandable as it grows.[cite:364][cite:367][cite:372]

## How to use this file
- Save this document in the main CourtPath project folder or repository root.[cite:364][cite:367]
- Keep it updated whenever a new major project file is created.[cite:372][cite:371]
- Use it as the table of contents for the entire project so product, business, and technical work stay aligned.[cite:369][cite:372]

## Recommended root folder structure
A clear directory structure improves reproducibility, collaboration, and long-term project maintenance.[cite:367][cite:365]

```text
CourtPath/
├── README.md
├── CHANGELOG.md
├── docs/
│   ├── business/
│   ├── product/
│   ├── technical/
│   ├── launch/
│   └── design/
├── app/
├── assets/
└── archive/
```

## File index

### Business documents
| File | Purpose | Suggested folder |
|---|---|---|
| `courtpath-founder-operator-package.md` | Combined founder/operator package connecting pitch, build, and launch strategy. | `docs/business/` |
| `courtpath-pitch-deck-draft.md` | Slide-by-slide investor pitch draft. | `docs/business/` |

### Product documents
| File | Purpose | Suggested folder |
|---|---|---|
| `courtpath-prd.md` | Product requirements document covering modules, user stories, and acceptance criteria. | `docs/product/` |
| `courtpath-developer-package.md` | Builder-facing package for implementation planning. | `docs/product/` |
| `courtpath-schema-api-spec.md` | Data model and API specification material. | `docs/technical/` |

### Launch and operations documents
| File | Purpose | Suggested folder |
|---|---|---|
| `courtpath-landing-page-copy.md` | Website and launch-page messaging draft. | `docs/launch/` |
| `courtpath-launch-checklist.md` | Launch execution and deployment checklist. | `docs/launch/` |
| `courtpath-package-note.md` | Short summary note describing the core package contents. | `docs/launch/` |

### Additional packet files
| File | Purpose | Suggested folder |
|---|---|---|
| `courtpath-founder-operator-packet.md` | Supporting founder packet material. | `docs/business/` |

## Recommended naming rules
Clear naming conventions and version tracking reduce confusion and make future collaboration easier.[cite:368][cite:374]

Use file names like:
- `courtpath-prd-v1.md`
- `courtpath-prd-v2.md`
- `courtpath-landing-page-copy-v1.md`
- `courtpath-pitch-deck-draft-v1.md`

If files become stable, the latest approved version can also live without a version number while older versions move to `archive/`.[cite:374][cite:368]

## Recommended version-control rules
Version-control best practices recommend a centralized system, clear naming, edit history, and regular backups.[cite:368][cite:371][cite:374]

Use this workflow:
1. Keep the live project in one main repository or cloud folder.[cite:368][cite:372]
2. Update this master index whenever a major file is added or replaced.[cite:372]
3. Add a changelog entry whenever a major product, business, or technical document changes.[cite:377][cite:371]
4. Archive older drafts instead of overwriting them blindly.[cite:374][cite:368]
5. Back up the whole project folder to cloud storage as well as local storage.[cite:371]

## Suggested changelog format
Changelog guidance recommends a consistent structure using categories such as Added, Changed, Fixed, and Removed, in reverse chronological order with dates and version numbers.[cite:377]

Example:

```text
## v0.3 — 2026-06-02
Added
- Initial CourtPath PRD
- Initial CourtPath pitch deck draft
- Landing page copy draft

Changed
- Expanded founder/operator package

Fixed
- Clarified folder organization
```

## Single source of truth rules
A single source of truth works best when one place is designated as the canonical project hub, roles are clear, and updates are made systematically instead of scattered across many duplicate files.[cite:369][cite:372][cite:375]

Recommended rules:
- Keep this index in the main repository root as the navigation file for the entire project.[cite:364][cite:372]
- Treat the newest approved PRD as the source for product scope.[cite:369]
- Treat the newest pitch deck draft as the source for investor messaging.[cite:369]
- Treat the newest landing page copy as the source for public launch messaging.[cite:369]
- Move retired files to `archive/` instead of deleting them immediately.[cite:374]

## Immediate next actions
- Download every CourtPath file already created and store them in one master CourtPath folder.[cite:367][cite:371]
- Create a GitHub repository or another central project repository with a README and clear folders.[cite:364][cite:367]
- Copy this file into the root folder as `README.md` or keep it beside `README.md` as `courtpath-master-index.md`.[cite:364]
- Start a `CHANGELOG.md` file and update it each time a major artifact changes.[cite:377]

## Current recommended status
CourtPath now has the beginnings of a real project documentation system: business narrative, product requirements, launch messaging, and implementation materials.[cite:364][cite:369] Organizing them now will make the next steps—prototype design, engineering, partnerships, and fundraising—much safer and easier to manage.[cite:367][cite:372]
