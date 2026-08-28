# Data Dictionary

This document defines every variable used in the Malaysia Semiconductor Shortage Impact analysis (2021–2023). Every dataset is classified as **PUBLIC** (published directly by an official source), **DERIVED** (calculated from public data), or **ESTIMATED** (third-party market research, not government-verified).

---

## trade_sitc_1d.csv

**Source:** Department of Statistics Malaysia (DOSM), OpenDOSM Data Catalogue
**URL:** open.dosm.gov.my/data-catalogue (Monthly Trade by SITC Section, 1 digit)
**Classification:** PUBLIC
**Frequency:** Monthly
**Coverage used:** Jan 2021 – Dec 2023
**Description:** Malaysia's monthly exports and imports broken down by SITC (Standard International Trade Classification) 1-digit section. Section 7 ("Machinery and Transport Equipment") is used as a proxy for electronics/E&E trade.

### Columns

| Column | Type | Description |
|---|---|---|
| `date` | date | First day of the reporting month |
| `section` | string | SITC 1-digit section code (0–9). Section `7` = Machinery and Transport Equipment |
| `exports` | float | Total exports for the section (RM) |
| `imports` | float | Total imports for the section (RM) |

### Known limitations
- **Section 7 is broader than electronics.** It bundles E&E together with other machinery and transport equipment (e.g. industrial machinery, vehicles). This is a proxy for electronics trade, not an isolated electronics-specific figure. A more granular SITC breakdown (2 or 3-digit) was not found as a clean download on OpenDOSM at time of writing.

## ipi.csv

**Source:** Department of Statistics Malaysia (DOSM), OpenDOSM Data Catalogue
**URL:** open.dosm.gov.my/data-catalogue (Industrial Production Index, headline)
**Classification:** PUBLIC
**Frequency:** Monthly
**Coverage used:** Jan 2021 – Jun 2026
**Description:** Malaysia's national headline Industrial Production Index, covering the whole economy (mining, manufacturing, electricity combined) — not broken down by sector. Used in notebook 02 as a baseline to test whether Division 26's volatility is sector-specific or reflects manufacturing-wide behavior.

### Columns

| Column | Type | Description |
|---|---|---|
| `series` | string | `abs` (absolute value), `growth_yoy`, or `growth_mom` — filter to `abs` before treating `index` as a raw number, same rule as `ipi_2d.csv` |
| `date` | date | First day of the reporting month |
| `index` | float | National production index value, not seasonally adjusted |
| `index_sa` | float | Same index, seasonally adjusted |

### Known limitations
- This is an economy-wide aggregate (mining + manufacturing + electricity), broader even than "all manufacturing" — a real difference from `ipi_2d.csv`'s Division 26, which isolates one specific manufacturing sub-sector. Any comparison between the two should account for this scope difference, not just treat them as directly equivalent baselines.

## ipi_2d.csv

**Source:** Department of Statistics Malaysia (DOSM), OpenDOSM Data Catalogue
**URL:** open.dosm.gov.my/data-catalogue (Industrial Production Index by 2-digit MSIC Division)
**Classification:** PUBLIC
**Frequency:** Monthly
**Coverage used:** Jan 2021 – Dec 2023
**Description:** Malaysia's Industrial Production Index broken down by 2-digit MSIC (Malaysia Standard Industrial Classification) division. Division 26 ("Manufacture of computer, electronic and optical products") isolates electronics manufacturing output specifically.

### Columns

| Column | Type | Description |
|---|---|---|
| `series` | string | `abs` (absolute value), `growth_yoy` (year-on-year % change), or `growth_mom` (month-on-month % change) — filter to `abs` before treating `index` as a raw number, same rule as `iowrt.csv` and `trade_headline.csv` in Project 001 |
| `date` | date | First day of the reporting month |
| `division` | string | 2-digit MSIC division code. Division `26` = Manufacture of computer, electronic and optical products |
| `index` | float | Production index value (base year varies; not seasonally adjusted) |

### Known limitations
- This dataset does not include a seasonally-adjusted column (`index_sa`), unlike `iowrt.csv` — only the raw `index`. Seasonal patterns in manufacturing output should be considered when interpreting month-to-month changes.
- Division 26 is a genuine, specific match to electronics manufacturing (unlike the trade data's Section 7 proxy) — this is the stronger of the two datasets for isolating the semiconductor story specifically.
## Context / Secondary Sources (Qualitative)

Notebook 01's "Why Is This Happening?" section adds secondary-sourced explanation (industry/institutional reporting) for why Malaysia's E&E sector didn't show an isolable shortage dip — not new PUBLIC data, so kept separate from the tables above.

- Lowy Institute, "Can Malaysia's semiconductor industry stream upwards?" https://www.lowyinstitute.org/the-interpreter/can-malaysia-s-semiconductor-industry-stream-upwards
- Bank Negara Malaysia, "Malaysia's Position in the Global E&E Value Chain" (Economic Monitor Review 2024, Box 1). https://www.bnm.gov.my/publications/emr2024/box1
