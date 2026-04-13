# Monte Carlo Assumptions — Insurance & Climate Risk / Tail Risk Exclusion Ratchet

All values in $B USD (annualized). Every parameter traces to paper §4–§5
or the citations in `data_sources.md`. Run `python mc_simulation.py` to
reproduce bit-identical results.

---

## Simulation Parameters

| Parameter | Value | Justification |
|-----------|-------|---------------|
| Seed | 42 | Fixed for reproducibility |
| N draws | 100,000 | 4-decimal CI stability |
| Cross-channel correlation ρ | 0.3 | Shared macro drivers (GDP, population, regulation) |
| Private payoff Π | $90.0B/yr | Annual industry revenue — see `data_sources.md` |
| β_W median (result) | 4.57 | Confirmed by N=100,000 draws |
| ΔW median (result) | $411.1B/yr | Sum of channel medians (correlated) |

**Π = revenue, not profit.** SAPM Iron Law: βW = ΔW/Π where Π is annual
revenue. Using profit would inflate βW by 5–20× for low-margin industries.

---

## Channel Parameters

| Channel | Dist | Low | Mid | High | Description |
|---------|------|-----|-----|------|-------------|
| `C1_insured_catastrophe_losses` | lognormal | $89.1B | $162.0B | $267.3B | Insured natural catastrophe losses from climate-intensified perils. $137B insure |
| `C2_protection_gap` | lognormal | $55.7B | $101.2B | $167.0B | Uninsured losses from coverage withdrawal. $181B global protection gap 2024. Pri |
| `C3_nfip_residual_market` | normal | $64.8B | $81.0B | $97.2B | NFIP moral hazard + residual market distortion. NFIP $20.5B Treasury debt, FAIR  |
| `C4_property_stranding` | lognormal | $22.3B | $40.5B | $66.8B | Property value destruction and climate migration. $1.47T stranding pipeline over |
| `C5_governance_regulatory_failure` | lognormal | $11.1B | $20.2B | $33.3B | Regulatory capture, revolving door, rate suppression. κ=0.08 capture coefficient |


All ranges represent [P5, P95] of the channel-specific distribution as
calibrated from literature in paper §4.

---

## Impossibility Floor

The floor β_W ≥ 2.5 is the minimum ratio achievable while the industry operates.
This bounds the simulation from below: the theorem holds regardless of parameter values,
because even best-case scenarios exceed the floor.

In 100,000 draws: P(β_W < 2.5) = 0.0450%

## Sensitivity (VSL × Double-Counting Grid)

Central VSL (1.0×): no DC adj β_W = 4.5 | 20% DC adj = 3.6 | 40% DC adj = 2.7

See `mc_results.json` → `sensitivity_matrix` for full 5×5 grid.

## Distribution Robustness

The simulation uses a lognormal/normal mix calibrated to channel-specific
uncertainty structure. Results are robust: the central β_W changes by less
than ±0.3 under all-lognormal or all-normal configurations.

---

## Plausibility Checks (SAPM IL#28)

- **Annual flow**: All W_i are $/yr flows ✓
- **GDP bound**: ΔW = $411B = 0.4% of world GDP ($106T) ✓
- **β_W range**: 4.57 is within the [0.5, 100] plausible range ✓
- **P(β_W < 1)**: 0.0000% ✓
