# M409 Final Project — Replication of Chiles (2017)

Replication of **Tables 6 and 9** from Chiles, *Shrouded Prices and Firm Reputation: Evidence from the U.S. Hotel Industry* — a triple-difference study of how online hotel ratings respond when resort fees are presented upfront vs. shrouded.

## Files

| File | What it is |
|---|---|
| `Chiles_Replication.ipynb` | Main deliverable. Pretty-printed Table 6 + Table 9 replications plus the four discussion-question answers. |
| `Hotel_Data.csv` | Review-level dataset (120,498 reviews × 199 cols, ~92 MB). |
| `Chiles_ShroudedPricesFirmReputation-1.pdf` | Source paper. |

## Headline replication results

**Table 6 — DinD treatment effect (`tripadv × resort fee`)**

| Model | Paper | Ours |
|---|---|---|
| (1) | −0.15\*\*\* | −0.15\*\*\* |
| (2) | −0.14\*\*\* | −0.14\*\*\* |
| (3) | −0.14\*\*\* | −0.14\*\*\* |
| (4) | −0.13\*\*\* | −0.14\*\*\* |
| (5) | −0.13\*\*\* | −0.15\*\*\* |

**Table 9 — treatment effect by hotel tier**

| Sub-sample | Paper | Ours |
|---|---|---|
| Low-tier (≤ 2★) | −0.34\*\*\* | −0.39\*\*\* |
| Mid-tier (2 < · < 3.5★) | −0.11\*\* | −0.14\*\*\* |
| High-tier (≥ 3.5★) | −0.08 | −0.08 |
| Mid/High × resort amenities provided | −0.06 | −0.05 |
| Mid/High × no resort amenities | −0.12\*\*\* | −0.16\*\*\* |

## Reproducing

```bash
pip install pandas numpy pyfixest jupyter
jupyter nbconvert --to notebook --execute --inplace Chiles_Replication.ipynb
```

Regressions use `pyfixest` for multi-way absorbed fixed effects with cluster-robust SEs on `master_id` (hotel).
