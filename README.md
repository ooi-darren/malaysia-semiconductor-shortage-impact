# Malaysia Semiconductor Shortage: Trade & Manufacturing Impact (2021–2023)

## The Question

How did the 2021–2023 global semiconductor shortage affect Malaysia's electrical & electronics (E&E) export performance, and what does the recovery pattern reveal about supply chain resilience for businesses operating here?

## Status

✅ **Analysis complete.** One notebook, testing the shortage's impact across two independent data sources — trade and manufacturing output — with the analysis window extended through mid-2026 to capture the full recovery arc.

## Key Findings

**Neither trade nor manufacturing data shows an isolable "shortage hits, then recovers" signature.** Both Section 7 (Machinery & Transport Equipment) trade values and Division 26 (Computer, Electronic & Optical Products) manufacturing output are continuously volatile across the entire 2021–2026 window — the dip observed in early 2023, initially suspected to be the shortage's mark, turns out to be indistinguishable from the sector's normal cyclical swings once compared against a longer baseline.

More notably, both series show substantial growth well beyond pre-shortage levels: Section 7 trade roughly doubled from 2021 to 2026, and Division 26 manufacturing output rose from a 2021 range of ~120–170 to consistently above 190 by 2025–2026. At this level of data granularity, there is no visible evidence of lasting damage from the 2021–2023 shortage — the sector not only recovered but grew substantially past its pre-shortage baseline. This is a stronger resilience finding than the original hypothesis (that manufacturing output would dip and recover before trade) set out to test — that hypothesis assumed an isolable disruption event, but the data shows continuous sector-wide volatility with no such event to isolate. *([Notebook 01](./notebooks/01-chip-shortage-trade-and-manufacturing-impact.ipynb))*

## Why This Project

A chip shortage is a textbook supply chain disruption story — but most public narratives about it stay qualitative ("factories struggled to get components"). This project tests that narrative against actual national trade and manufacturing data for Malaysia specifically, asking not just "did this happen" but "does it show up in the numbers, and if so, how."

## Data Sources

Both datasets are labeled **PUBLIC** (official government source). Full definitions and known limitations are documented in [`DATA_DICTIONARY.md`](./DATA_DICTIONARY.md).

| Dataset | Source | Classification | Frequency |
|---|---|---|---|
| Trade by SITC Section (1-digit) | DOSM (OpenDOSM) | PUBLIC | Monthly |
| Industrial Production Index by MSIC Division (2-digit) | DOSM (OpenDOSM) | PUBLIC | Monthly |

**A real limitation, stated plainly rather than buried:** Section 7 ("Machinery and Transport Equipment") is a broad trade category that bundles electronics with unrelated goods like vehicles and industrial machinery — it's a proxy for electronics trade, not an isolated figure. Division 26 ("Computer, Electronic and Optical Products") is a precise match for electronics manufacturing specifically, and carries more analytical confidence as a result. This asymmetry between the two datasets is discussed directly in the notebook's Confidence & Caveats section.

## Notebook

| # | Question | Data Rigor |
|---|---|---|
| [01 — Trade & Manufacturing Impact](./notebooks/01-chip-shortage-trade-and-manufacturing-impact.ipynb) | Did the 2021–2023 chip shortage leave a visible mark on Malaysia's E&E trade and manufacturing, and what does the recovery reveal about resilience? | PUBLIC |

## Methodology

Business problem → objectives → data acquisition → cleaning → analysis → visualization → insight → recommendation. The notebook opens with the question and the answer, then shows the reasoning between them — including the original hypothesis this analysis could not fully confirm.

## Repository Structure

```
data/
├── raw/          # Original files, unmodified, as downloaded from source
└── processed/    # Cleaned/compiled datasets ready for analysis
notebooks/        # Analysis notebooks
references/       # Source PDFs and supporting documents
DATA_DICTIONARY.md
```

## Author

Darren Ooi — [LinkedIn](https://www.linkedin.com/in/darrenooizhixian)