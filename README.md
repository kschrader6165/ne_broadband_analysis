# Nebraska Broadband Gap Analysis

Analyzed FCC broadband availability data for Nebraska to find which providers and technologies serve the state, how many locations meet the FCC's 100/20 Mbps benchmark, where the gaps are, and where CenturyLink (Lumen) copper is the only wired option.

**Data:** FCC Broadband Data Collection, Nebraska fixed broadband availability, as of December 31, 2025. Copper, Cable, Fiber, and Licensed Fixed Wireless. Census Bureau 2020 county reference file for county names.
**Tools:** Python, pandas, SQLite, Jupyter
**Rows analyzed:** 3,458,420 provider offerings across 781,151 locations

## Key Findings

- 94.8% of locations have at least one 100/20 Mbps option, and 80.4% have fiber available
- The statewide number hides big gaps: in Hitchcock County only 28.4% of locations are served at 100/20
- CenturyLink copper reaches 244,688 locations, but only 11,943 (about 5%) have no fiber or cable alternative
- The largest copper-only clusters are in Douglas and Sarpy counties (metro Omaha), not just rural areas

## Data Quality

About 8.6% of rows reported 0/0 Mbps, mostly T-Mobile, CenturyLink, and AT&T. The smallest nonzero speed in the data is 10 Mbps and every zero row also had 0 upload, which suggests offerings below about 10/1 Mbps are recorded as zero. I kept these as underserved service for coverage questions and excluded them from speed averages. 94% of locations with a zero offering also had a 100+ Mbps option; only 7,752 had nothing better.

## Limitations

- Shows advertised availability, not what people actually subscribe to or the speeds they get
- Satellite (e.g. Starlink) excluded, so locations with only satellite service aren't counted
- Fixed wireless coverage depends on signal, so "served" on paper may overstate real service

## Files

- `analysis.ipynb`: data loading, cleaning, and SQL queries