# SAPM Monte Carlo — Insurance & Climate Risk / Tail Risk Exclusion Ratchet

**Public replication repository for quantitative results in:**

> Postnieks, E. (2026). *Insurance & Climate Risk (Tail Risk Exclusion Ratchet).* SAPM Working Paper. SSRN.

This repository provides everything needed to independently reproduce, audit,
and extend the Monte Carlo simulation underlying the paper's core results.
The paper is available on SSRN.

---

## Results (N = 100,000 draws, seed = 42)

| Statistic | Value |
|-----------|-------|
| **β_W median** | **4.57** |
| β_W mean | 4.67 |
| β_W std | 0.92 |
| **90% CI** | **[3.3, 6.3]** |
| 99% CI | [2.9, 7.3] |
| P(β_W < 1) | 0.0000% |
| **ΔW median** | **$411.1B/yr** |
| Π (revenue) | $90.0B/yr |

**β_W = 4.57** means the insurance & climate risk industry destroys **$4.57 in system
welfare for every $1.00 in revenue** — across 5 channels and 100,000 Monte Carlo draws.

**Classification**: Class 2 — Intractability

---

## What Is β_W?

```
β_W = ΔW / Π
```

- **ΔW** = total annualized welfare destruction ($B/yr) across all channels
- **Π** = annual industry **revenue** ($B/yr) — not profit

β_W > 1: industry destroys more welfare than it captures in revenue.
β_W > 3: Strong Intractability threshold — reform requires structural replacement.

---

## Quick Start

```bash
git clone https://github.com/epostnieks/sapm-mc-insurance-climate.git
cd sapm-mc-insurance-climate
pip install numpy scipy
python mc_simulation.py
```

Expected output: `β_W median : 4.57` and `ΔW median : $411.1B/yr`

---

## Welfare Channels

| Channel | Median ($B/yr) | 90% CI | Distribution |
|---------|---------------|--------|--------------|
| C1_insured_catastrophe_losses | $161.8B | [$98.0B, $266.1B] | Lognormal |
| C2_protection_gap | $101.1B | [$61.3B, $167.1B] | Lognormal |
| C3_nfip_residual_market | $81.0B | [$64.8B, $97.2B] | Normal |
| C4_property_stranding | $40.5B | [$24.6B, $66.9B] | Lognormal |
| C5_governance_regulatory_failure | $20.2B | [$12.2B, $33.3B] | Lognormal |
| **Total ΔW** | **$411.1B** | **[$300.6B, $570.1B]** | Correlated (ρ=0.3) |

---

## Impossibility Floor

The floor β_W ≥ 2.5 cannot be breached by any policy while the
industry continues to operate. In 100,000 draws, only **0.0450%**
fall below this floor — confirming the structural constraint.

## Repository Contents

| File | Description |
|------|-------------|
| `mc_simulation.py` | Self-contained simulation — no private pipeline imports |
| `mc_results.json` | Pre-run results (100K draws, seed=42) — matches paper |
| `mc_histogram.json` | Binned β_W distribution (80 bins) for companion chart |
| `assumptions.md` | Every parameter: value, derivation, source |
| `data_sources.md` | Full citation list for all empirical inputs |

---

## Replication Notes

Results are seeded and deterministic. Tested with:
```
numpy==1.26.4  scipy==1.12.0  Python 3.11.9
```

The `median` and `ci_90` (to 1 decimal) match exactly across compatible versions.

---

## License

CC BY 4.0. Cite as:

> Postnieks, E. (2026). *SAPM Monte Carlo — Insurance & Climate Risk (Tail Risk Exclusion Ratchet)*.
> GitHub: epostnieks/sapm-mc-insurance-climate.
> https://github.com/epostnieks/sapm-mc-insurance-climate
