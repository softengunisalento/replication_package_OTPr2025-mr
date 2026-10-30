# replication_package_OTPr2025-mr

This repository contains the data and the figures of the bibliometric analysis reported in the systematic literature review *One-Time Programs: Past, Present, and Future* by Simone Casciaro, Roberto Vergallo and Luca Mainetti.

The analysis covers the 52 primary studies of the review, published between 2008 and 2025.

## Contents

### Bibliographic data

| File | Content |
|---|---|
| `scopus3.csv` | Scopus export of the 52 primary studies (29 October 2026) with all field groups: citation information, bibliographical information, abstract and keywords, funding details and other information. Citation counts are those recorded in Scopus on that date. |

### VOSviewer files

| File | Content |
|---|---|
| `thesaurus_keywords.txt` | Thesaurus for the author keywords (82 rules). 36 rules merge synonyms and spelling variants into a single label; 46 rules remove generic terms (empty `replace by`). |
| `thesaurus_authors.txt` | Thesaurus for the authors. It merges two spellings of the same author name, which share the same Scopus author ID. |
| `*_map.txt`, `*_network.txt` | Map and network files saved by VOSviewer for the four analyses below. |

| Files | Type of analysis | Unit of analysis | Thesaurus | Minimum threshold | Items |
|---|---|---|---|---|---|
| `keyword_map.txt`, `keyword_network.txt` | Co-occurrence | Author keywords | `thesaurus_keywords.txt` | 1 occurrence | 15 keywords; the map shows the 14 connected ones |
| `country_map.txt`, `country_network.txt` | Co-authorship | Countries | – | 1 document | 20 countries |
| `authors_map.txt`, `authors_network.txt` | Co-authorship | Authors | `thesaurus_authors.txt` | 2 documents | 28 of 138 authors |
| `organization_map.txt`, `organization_network.txt` | Co-authorship | Organizations | – | 1 document | 118 organizations |

All analyses use full counting. A study is counted once for each of its authors, and once for each country and organization that appears in its author affiliations. The country counts therefore sum to 81 for the 52 studies.

**File format.**
- **Map files:** tab-separated, one row per item. Columns: `id`, `label`, the coordinates `x` and `y`, `cluster`, the weights (`Links`, `Total link strength`, `Documents` or `Occurrences`, `Citations`, ...) and the scores (`Avg. pub. year`, ...).
- **Network files:** tab-separated, without a header. Columns: the id of the first item, the id of the second item and the link strength.

### Figures

File names follow the LaTeX source of the paper, so they do not match the figure numbers.

| File | Figure in the paper | Content | Data |
|---|---|---|---|
| `Fig1.pdf` | Fig. 1 | PRISMA flow diagram of the search and selection process | Search results in Table 1 of the paper |
| `Fig3.pdf`, `Fig3.png` | Fig. 2 | Primary studies per year of publication | `Year` in `scopus3.csv` |
| `Fig4.pdf`, `Fig4.png` | Fig. 3 | Primary studies per country | `Documents` in `country_map.txt` |
| `Fig5.pdf`, `Fig5.png` | Fig. 4 | Citations per country | `Citations` in `country_map.txt` |
| `Fig6.pdf`, `Fig6.png` | Fig. 5 | Primary studies per author, for the 28 authors with at least two studies | `Documents` in `authors_map.txt` |
| `Fig7.pdf`, `Fig7.png` | Fig. 6 | Citations per author, for the same 28 authors | `Citations` in `authors_map.txt` |
| `Fig8.pdf` | Fig. 7 | Co-occurrence map of the author keywords (network visualization) | `keyword_map.txt`, `keyword_network.txt` |
| `Fig9.pdf` | Fig. 8 | Same map, colored by average publication year (overlay visualization) | `keyword_map.txt`, `keyword_network.txt` |
| `Fig2new.pdf` | Fig. 9 | Components used by the primary studies in each step of the construction of Goldwasser et al. (input, compiler and secure layers) | Data extraction of the review |

## How to reproduce the maps

1. In VOSviewer (version 1.6.21), choose *Create* → *Create a map based on bibliographic data* → *Read data from bibliographic database files*.
2. In the *Scopus* tab, select `scopus3.csv`.
3. Set the type of analysis, the unit of analysis, full counting, the thesaurus file and the threshold given in the table above.
4. VOSviewer asks whether to keep only the largest set of connected items. Answer *Yes* for the keyword map and *No* for the other analyses.

To view the saved maps without recomputing them, use *Open* in VOSviewer and select a map file together with its network file.