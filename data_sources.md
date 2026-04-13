# Data Sources — Insurance & Climate Risk Monte Carlo Simulation

Channel parameters in `mc_simulation.py` trace to the sources listed here.
The paper (Insurance & Climate Risk: Tail Risk Exclusion Ratchet) is available on SSRN and contains the full
reference list and §4 calibration narrative.

---

## Channel Sources

### `C1_insured_catastrophe_losses`

Insured natural catastrophe losses from climate-intensified perils. $137B insured losses 2024 (Swiss Re sigma), $148B projected 2026. Subsidized premiums induce construction in high-risk zones. Sources: Swiss Re sigma, Munich Re NatCatSERVICE.

*Full citations: paper §4 (available SSRN).*

### `C2_protection_gap`

Uninsured losses from coverage withdrawal. $181B global protection gap 2024. Private insurers non-renew as actuarial losses accumulate; State Farm, Allstate exit CA. Sources: Swiss Re, Geneva Association, First Street Foundation.

*Full citations: paper §4 (available SSRN).*

### `C3_nfip_residual_market`

NFIP moral hazard + residual market distortion. NFIP $20.5B Treasury debt, FAIR Plan exposure $50B→$650B in 7yrs, FL Citizens 1.42M policies peak. Premiums set below actuarial cost for political palatability. Sources: FEMA, NAIC, CA FAIR Plan.

*Full citations: paper §4 (available SSRN).*

### `C4_property_stranding`

Property value destruction and climate migration. $1.47T stranding pipeline over 30yrs (First Street). 84% of US census tracts face downward property value pressure. Annualized ~$50B understates correlated correction tail risk. Sources: First Street Foundation, Zillow.

*Full citations: paper §4 (available SSRN).*

### `C5_governance_regulatory_failure`

Regulatory capture, revolving door, rate suppression. κ=0.08 capture coefficient. Insurance lobbying generates orders-of-magnitude-larger welfare costs. 12 LA insurers insolvent 2021-2023. Sources: NAIC, state insurance dept filings, OpenSecrets.

*Full citations: paper §4 (available SSRN).*

---

## Industry Revenue (Π)

The private payoff Π = $90.0B/yr is global annual industry revenue.
Source: paper §2 and §4. See paper §DA-1 (Decision Audit Field 7) for full
revenue source documentation.

---

## SAPM Framework

- Postnieks, E. (2026). *The Private Pareto Theorem*. SAPM Foundation Paper. SSRN.
- Postnieks, E. (2026). *Insurance & Climate Risk (Tail Risk Exclusion Ratchet)*. SAPM Working Paper. SSRN.

---

## Distribution Methodology

- Iman, R. L., & Conover, W. J. (1982). A distribution-free approach to
  inducing rank correlation among input variables. *Communications in
  Statistics — Simulation and Computation*, 11(3), 311–334.
- Cooke, R. M. (1991). *Experts in Uncertainty*. Oxford University Press.
