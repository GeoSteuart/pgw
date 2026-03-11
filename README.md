# GeoSteuart GitHub: Naming Convention Standard and README Templates
**Applies to:** pgw, gws, gwsmedia, PGWDocs  
**Adopted:** March 2026

---

## Part I: Naming Convention Standard

### Governing Principles

1. Filenames are the permanent citation anchor. Once a file is pushed to GitHub, its name should not change, because URLs derived from it may be embedded in footnotes, Zotero entries, or external references.
2. Filenames must be self-describing. A researcher looking at a directory listing should be able to identify the document without opening it.
3. Dates go in YYYY-MM-DD or YYYY format at the start of the filename, before the descriptive title, so that alphabetical sort equals chronological sort.
4. Source prefixes identify provenance at a glance.
5. No special characters except hyphens and underscores. No parentheses, ampersands, apostrophes, colons, slashes, pipes, or percent signs. GitHub renders these in URLs as encoded strings that break copy-paste citation.

---

### Standard Format

```
[DATE]_[SOURCE-PREFIX]_[DESCRIPTIVE-TITLE].[ext]
```

#### Date field
- Known date: `1997-03-05` (YYYY-MM-DD)
- Year only known: `1997_`
- Date range: `1996-01_1996-09_`
- Undated: `undated_`

#### Source prefix (use consistently)

| Prefix | Meaning |
|--------|---------|
| `CIA` | Central Intelligence Agency document |
| `DIA` | Defense Intelligence Agency |
| `DOD` | Department of Defense / OSD |
| `OSAGWI` | Office of the Special Assistant for Gulf War Illnesses |
| `CIA-OSAGWI` | Joint CIA/OSAGWI product |
| `UNSCOM` | UN Special Commission inspection report |
| `IIR` | Intelligence Information Report |
| `SENATE` | U.S. Senate report or testimony |
| `HOUSE` | U.S. House report or testimony |
| `PAC` | Presidential Advisory Committee on Gulf War Illnesses |
| `NYT` | New York Times |
| `WP` | Washington Post |
| `CNN` | CNN |
| `AP` | Associated Press |
| `REUTERS` | Reuters |
| `MISC-PRESS` | Newspaper/wire source not listed above |
| `JOUR` | Peer-reviewed journal article |
| `KB` | Knowledge base export (Google Drive markdown) |
| `BIB` | Bibliography file (RIS, CSV, MD) |
| `THESIS` | Thesis or dissertation document |
| `FIELD` | Field notes, unit logs, operational records |

#### Descriptive title
- Title case, words separated by hyphens
- Aim for 4–8 words that uniquely identify the document
- Do not repeat the source prefix in the title
- Abbreviations: `Khamisiyah` → `Kham`, `Gulf-War-Illness` → `GWI`, `Chemical-Weapons` → `CW`

#### Extension
- `.pdf` for all PDFs
- `.txt` for plain text transcripts
- `.ris` for RIS bibliography files
- `.csv` for spreadsheet/bibliography exports
- `.md` for markdown documents
- `.jpg`, `.gif`, `.png` for images

---

### Examples: Applying the Standard to Existing Files

| Current filename | Renamed under standard |
|-----------------|----------------------|
| `kham osagwi feb 21 97.pdf` | `1997-02-21_OSAGWI_Khamisiyah-Investigation-Report.pdf` |
| `IIR 6 021 0020 92_UNSCOM 20 (CW6) INSPECTION.pdf` | `1992_IIR_6-021-0020-92-UNSCOM-CW6-Inspection.pdf` |
| `TAB E - Methodology for Modeling a Possible Chemical Warfare Agent Release at Khamisiyah.pdf` | `1997_OSAGWI_TAB-E-Methodology-Modeling-CWA-Release-Kham.pdf` |
| `Peer Review Comments_ Methodology of Refined Modeling of the Khamisiyah Pit Demolition (March 2000).pdf` | `2000-03_DOD_Peer-Review-Comments-Pit-Demolition-Methodology.pdf` |
| `ussenate_reportofthesiuongulfwarillnesses_reportno105-39parti_1998.pdf` | `1998_SENATE_Report-105-39-Part-I-SIU-GWI.pdf` |
| `C.I.A. Data Suggests Wider Spread of Gulf War Nerve Gas.pdf` | `1997_NYT_CIA-Data-Wider-Spread-Nerve-Gas.pdf` |
| `CNN - Powell_ Didn't get CIA's chemical weapons warning - April 17, 1997.pdf` | `1997-04-17_CNN_Powell-Did-Not-Get-CIA-CW-Warning.pdf` |
| `Modeling_Critique_Khamisiyah.md.pdf` | `2025_KB_Modeling-Critique-Khamisiyah.pdf` |
| `Altered_immune_pathway_activity_under_ex.pdf` | `JOUR_Altered-Immune-Pathway-Activity-GWI.pdf` |

**Note on existing files:** Do not rename files already pushed to GitHub unless you are prepared to update all Zotero links and any embedded footnote URLs that reference those raw GitHub paths. For new uploads, apply the standard from the start.

---

### Repository-Specific Rules

**pgw (primary sources and KB exports)**
- KB exports: always use `KB` prefix, retain the Google Drive document title in the descriptive field
- Primary government documents: use agency prefix + document identifier where one exists (TAB letter, IIR number, report number)
- Double extension `.md.pdf` is legacy; new KB exports should be named `[DATE]_KB_[Title].pdf`

**gws (medical literature)**
- Journal articles: use `JOUR` prefix; include first author last name and year: `JOUR_Haley-1997_Three-Syndromes-GWI.pdf`
- Where author is unknown from filename alone, leave as `JOUR` prefix with descriptive title

**gwsmedia (media PDFs)**
- Source prefix is the outlet: `NYT`, `WP`, `CNN`, `AP`, `REUTERS`, `MISC-PRESS`
- Date at front: `1997-04-17_CNN_Powell-Did-Not-Get-CIA-CW-Warning.pdf`
- Images: `[DATE]_[DESCRIPTION].[ext]` — example: `1997-04-11_Newspaper-Graphic-Exposure-Map.gif`

**PGWDocs (text transcripts)**
- Mirror gwsmedia naming exactly, substituting `.txt` for `.pdf`
- Unique items (editorials not in gwsmedia): use `MISC-PRESS` prefix with date if known

---

## Part II: README Files

---

### README for pgw

```markdown
# pgw — Persian Gulf War: Khamisiyah Investigation
**Researcher:** Jeffrey Ford (GeoSteuart)  
**Repository URL:** https://github.com/GeoSteuart/pgw  
**Branch:** master

## Purpose
Primary source documents, knowledge base exports, and bibliography files supporting
the book *Fire in the Hole: The Khamisiyah Cover-Up and the Betrayal of America's
Gulf War Veterans* and associated academic work on the March 1991 Khamisiyah
ammunition depot demolitions.

## Repository Structure

```
pgw/
├── [root]              Primary source PDFs — government documents, intelligence
│                       reports, UNSCOM records, modeling assessments
├── bibliography/       Master bibliography files
│   ├── My_Library11_clean.ris              (379 entries, Zotero export)
│   ├── MASTER_BIB_DEDUPED_v3.csv          (621 unique entries, all sources)
│   ├── MASTER_BIB_DEDUPED_v3_DOIURL.csv  (same, with resolved DOI URLs)
│   └── MASTER_BIB_CHICAGO17_My_Library11.md  (Chicago 17 formatted, 379 entries)
└── pdfs/               35 Zotero-linked PDFs (flat, from My_Library11 export)
```

## Key Documents

| Document | Description |
|----------|-------------|
| `ussenate_reportofthesiuongulfwarillnesses_reportno105-39parti_1998.pdf` | U.S. Senate Report 105-39, Part I (1998) |
| `TAB E - Methodology for Modeling...Khamisiyah.pdf` | Official OSAGWI modeling methodology |
| `Peer Review Comments_...Pit Demolition (March 2000).pdf` | 2000 peer review of revised Pit modeling |
| `IIR 6 021 0020 92_UNSCOM 20 (CW6) INSPECTION.pdf` | UNSCOM CW6 inspection intelligence report |
| `kham osagwi feb 21 97.pdf` | OSAGWI Khamisiyah report, February 1997 |
| `full kham from dtic.pdf` | Full Khamisiyah assessment, DTIC |
| `DOD meeting on Khamisiyah demolitions 18 December 2018 (1).pdf` | 2018 DoD meeting transcript |

## KB Export Files (.md.pdf)
Files with double extension `.md.pdf` are PDF snapshots of Google Drive knowledge
base documents. The live editable versions reside in Google Drive. These snapshots
are point-in-time exports and may not reflect the most current version.

| File | Google Drive KB Document |
|------|--------------------------|
| `Bibliography_Master_Khamisiyah.md.pdf` | Bibliography KB |
| `Dugway_Testing_Khamisiyah.md.pdf` | Dugway testing analysis |
| `March4_Specific_Khamisiyah.md.pdf` | March 4 Bunker 73 analysis |
| `Modeling_Critique_Khamisiyah.md.pdf` | Modeling critique |
| `Weather_Institutional_Epi_Contradictions_Khamisiyah.md.pdf` | Weather/epidemiology contradictions |
| `chapter_bunker73_dugway_comprehensive.md.pdf` | Bunker 73 / Dugway chapter |
| `methodological_comparison_miranda_khamisiyah.md.pdf` | Miranda methodology comparison |

## Naming Convention
New files should follow the standard in `NAMING_CONVENTION.md` (see bibliography/).
Existing filenames are preserved to maintain stable URLs.

## Related Repositories
- **gws** — Gulf War Illness medical literature
- **gwsmedia** — Media coverage PDFs
- **PGWDocs** — Media coverage text transcripts
```

---

### README for gws

```markdown
# gws — Gulf War Illness: Medical and Scientific Literature
**Researcher:** Jeffrey Ford (GeoSteuart)  
**Repository URL:** https://github.com/GeoSteuart/gws  
**Branch:** main

## Purpose
Peer-reviewed journal articles on the pathophysiology, biomarkers, clinical presentation,
and treatment of Gulf War Illness (GWI). Supports chapters on biological mechanisms
and epidemiology in *Fire in the Hole*.

## Contents
14 PDF articles covering the following research areas:

- Mitochondrial dysfunction in GWI
- Acetylcholinesterase inhibitors and organophosphate neurotoxicity
- Immune pathway dysregulation
- Gut microbiome alterations in GWI veterans
- Exercise challenge studies and GWI subtypes
- Bioenergetic biomarkers
- Longitudinal symptom persistence studies
- LNFPIII immunomodulation treatment trials
- Prevalence and pattern studies (Kansas Veterans Study)
- Health care access in GWI veterans

## Naming Convention for New Additions
New journal articles should follow:
`JOUR_[FirstAuthorLastname]-[Year]_[Short-Descriptive-Title].pdf`

Example: `JOUR_Haley-1997_Three-Syndromes-in-GWI.pdf`

## Related Repositories
- **pgw** — Primary government and intelligence documents
- **gwsmedia** — Media coverage PDFs
- **PGWDocs** — Media coverage text transcripts
```

---

### README for gwsmedia

```markdown
# gwsmedia — Persian Gulf War: Media Coverage Archive
**Researcher:** Jeffrey Ford (GeoSteuart)  
**Repository URL:** https://github.com/GeoSteuart/gwsmedia  
**Branch:** main

## Purpose
PDF archive of newspaper and wire service articles covering the Khamisiyah
chemical weapons investigation, Gulf War Illness policy debates, and CIA/Pentagon
accountability controversies. Coverage concentrated in 1996–1998, the period of
peak public and congressional attention to the Khamisiyah affair.

## Coverage
Approximately 70 PDFs plus images. Major outlets represented:

- The New York Times
- The Washington Post
- CNN (web articles)
- Reuters
- Associated Press / Yahoo! News
- Boston Globe
- Hartford Courant
- Newsday

## Key Themes
- CIA foreknowledge of chemical weapons at Khamisiyah
- Pentagon record-keeping failures and missing unit logs
- Presidential Advisory Committee (PAC) findings and disputes
- Congressional oversight and testimony (Powell, Schwarzkopf, Cohen)
- Exposure notification delays and veteran claims

## Companion Repository
**PGWDocs** (https://github.com/GeoSteuart/PGWDocs) contains plain-text transcripts
of the same articles for full-text search. Filenames mirror this repository exactly,
with `.txt` substituted for `.pdf`.

## Images
| File | Description |
|------|-------------|
| `307 frago.JPG` | 307th Engineer Battalion fragmentary order |
| `970411-ta.gif` | April 11, 1997 — newspaper graphic |
| `IMG_0318.JPG` | [Verify content] |

## Naming Convention for New Additions
```
[YYYY-MM-DD]_[SOURCE-PREFIX]_[Descriptive-Title-in-Title-Case].pdf
```
Example: `1997-04-17_CNN_Powell-Did-Not-Get-CIA-CW-Warning.pdf`

Source prefixes: `NYT`, `WP`, `CNN`, `AP`, `REUTERS`, `MISC-PRESS`

## Related Repositories
- **pgw** — Primary government and intelligence documents
- **gws** — Gulf War Illness medical literature
- **PGWDocs** — Text transcripts of this archive
```

---

### README for PGWDocs

```markdown
# PGWDocs — Persian Gulf War: Media Text Transcripts
**Researcher:** Jeffrey Ford (GeoSteuart)  
**Repository URL:** https://github.com/GeoSteuart/PGWDocs  
**Branch:** main

## Purpose
Plain-text (.txt) transcripts of newspaper and wire service articles covering the
Khamisiyah investigation and Gulf War Illness policy controversies. Enables full-text
search, quotation extraction, and AI-assisted analysis without requiring PDF parsing.

## Relationship to gwsmedia
This repository mirrors **gwsmedia** (https://github.com/GeoSteuart/gwsmedia).
Each PDF in gwsmedia has a corresponding .txt file here with an identical filename
(extension changed from .pdf to .txt). Use gwsmedia for the original document scans;
use PGWDocs for text search and extraction.

## Items in PGWDocs Not Present in gwsmedia
The following files exist here but have no PDF counterpart in gwsmedia:

| File | Notes |
|------|-------|
| `_It's About Time_.txt` | Editorial — verify source and date |
| `_Nerve Gas Stonewall_.txt` | Editorial — verify source and date |
| `_Not in Good Faith_.txt` | Editorial — verify source and date |
| `newsday.com _ News.txt` | Newsday article — verify headline and date |
| `locations sitrep.pdf` | Unit locations situation report (PDF, not a transcript) |
| `media` | Verify — may be a folder or file |

These items should have metadata headers added (see below) and corresponding PDFs
uploaded to gwsmedia if originals are available.

## Recommended Text File Header Format
Each .txt file should begin with a metadata block:

```
SOURCE: [Outlet name]
DATE: [YYYY-MM-DD or approximate]
HEADLINE: [Full headline]
AUTHOR: [Byline if known]
URL: [Original URL if archived]
GITHUB-PDF: https://github.com/GeoSteuart/gwsmedia/blob/main/[encoded-filename].pdf
---
[Article text]
```

## Naming Convention for New Additions
Mirror gwsmedia naming exactly, substituting `.txt` for `.pdf`:
```
[YYYY-MM-DD]_[SOURCE-PREFIX]_[Descriptive-Title-in-Title-Case].txt
```

## Related Repositories
- **pgw** — Primary government and intelligence documents
- **gws** — Gulf War Illness medical literature
- **gwsmedia** — PDF originals of this text archive
```

---

## Part III: Deployment Instructions

To add READMEs to each repo, create a file named `README.md` in the root of each repository and push it. GitHub renders the root README.md automatically on the repo landing page.

```powershell
# For each repo, from inside the cloned directory:

# gwsmedia
cd "D:\AA Kham Master folder\gwsmedia"
# Copy README content → README.md
git add README.md
git commit -m "Add README with repository description and naming convention"
git push

# Repeat for gws, PGWDocs, pgw
```

To add the naming convention standard to pgw for permanent reference:

```powershell
cd "D:\AA Kham Master folder\pgw"
# Copy NAMING_CONVENTION.md → bibliography/NAMING_CONVENTION.md
git add bibliography/NAMING_CONVENTION.md
git commit -m "Add naming convention standard to bibliography folder"
git push
```
