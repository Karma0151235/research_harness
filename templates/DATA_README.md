# Data provenance — <PROJECT>   (root AGENTS.md §3.10)

| File (data/raw/) | Source / publisher | URL or DOI | Access date | Licence / terms | Coverage (units × period) | Notes |
|---|---|---|---|---|---|---|

## Transformations
Every derived file, the script that produces it, and the order: `01_clean → 02_describe → 03_estimate → 04_robustness → 05_tables`.

## Known issues
Breaks in series, classification or base-year changes, revisions, missing units/years, suppressed cells.

## Reproduce
```
<environment setup command>
<single entry-point command, e.g. python run_all.py>
```
