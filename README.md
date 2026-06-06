# MSA 409 — Final Project

Replication of **Chiles (2018), "Shrouded Prices and Firm Reputation: Evidence from the U.S. Hotel Industry."**

## What's in here

```
project/
├── Chiles_Replication.ipynb         ← main deliverable (run this)
├── Chiles_ShroudedPricesFirmReputation-1.pdf   ← the paper
├── Hotel_Data.csv                   ← 120,498 hotel reviews (96MB)
└── Worker_Data.csv                  ← not used; data for the Chen & Sheldon paper (alternate project option)
AI_Transcript.docx                   ← Claude conversation transcript per assignment rules
```

## What the notebook produces

| Section | Output |
|---|---|
| §1 | Variable map (paper notation → CSV columns) |
| §2 | **Table 6** replication — 5 DiD specifications |
| §2a | **Separate-fee placebo** — the falsification check (paper §4.2) |
| §2b | **Figure 5 replication** — event-study showing parallel pre-trends |
| §2c | **Pooled triple-difference** — explicit DDD as the assignment asks |
| §3 | **Table 9** replication — heterogeneity by tier × price × amenities |
| §4.1 | Discussion: the three differences and what each controls |
| §4.2 | Discussion: should hotels shroud, and which have the biggest incentive |
| §4.3 | Discussion: should a platform allow shrouding |

## How to run

```bash
# Requires Python 3.10+ and pyfixest
pip install pandas numpy pyfixest matplotlib jupyter

# From the project/ directory:
jupyter nbconvert --to notebook --execute --inplace Chiles_Replication.ipynb
# or interactively:
jupyter lab Chiles_Replication.ipynb
```

End-to-end runtime is ~60 seconds on a 2024 MacBook. The notebook expects `Hotel_Data.csv` in the same directory.

## Replication quality

| Metric | Paper | This notebook |
|---|---|---|
| Table 6 Model (5) `ta × rfee` | −0.13*** | −0.13*** ✓ |
| Table 6 Model (5) N | 42,082 | 42,082 ✓ |
| Adopters / Droppers | 104 / 67 | 104 / 67 ✓ |
| Separate-fee placebo `ta × rfeesep` | insignificant | +0.025, p=0.34 ✓ |
| Separate-fee placebo hotel clusters | 237 | 237 ✓ |
| Event-study mean post-period coef | −0.10 to −0.15 | −0.14 ✓ |
| Table 9 Low-Tier treatment | −0.34*** | −0.33*** ✓ |
| Table 9 Mid/High × amenities (pre-treatment hotel count) | 48 | 48 ✓ (regression sample is 47 — one hotel drops for missing price; see notebook §3) |
| Pooled DDD `ta × fee × Inc` | n/a (not in paper) | −0.16*** |

See the in-notebook "Reproducibility notes" cell at the bottom for the small remaining gaps and what causes them.
