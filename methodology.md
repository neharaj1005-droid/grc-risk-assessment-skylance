# Risk Assessment Methodology

**Company:** Skylance (fictional). **Approach:** qualitative, asset-based.

## Process
1. Identify assets (`asset-inventory.csv`).
2. For each asset, identify a threat (what could happen) and a vulnerability (the specific weakness that allows it).
3. Score **inherent** risk: Likelihood (1-5) x Impact (1-5).
4. Choose a treatment: Mitigate, Transfer, Avoid or Accept.
5. Score **residual** risk assuming the treatment is carried out.
6. Map each risk to controls (`nist-csf-iso27001-mapping.csv`) and prioritise fixes (`gap-analysis.md`).

`ORG` in the register means an organisation-wide process risk not tied to a single asset (for example, having no incident response plan).

## Likelihood scale
| Score | Label | Description |
|---|---|---|
| 1 | Rare | Less than once in 5 years |
| 2 | Unlikely | Once in 3-5 years |
| 3 | Possible | Once in 1-3 years |
| 4 | Likely | About once a year |
| 5 | Almost certain | Multiple times a year |

## Impact scale
| Score | Label | Description |
|---|---|---|
| 1 | Negligible | Under $1k; no customer impact |
| 2 | Minor | Under $10k; internal disruption under 4 hours |
| 3 | Moderate | Under $50k; limited customer impact, under 1 day |
| 4 | Major | Under $250k; limited customer data exposure, possible breach notification |
| 5 | Severe | Over $250k; large-scale customer data breach, loss of key customers or regulatory action |

## Rating bands
| Score | Rating | Required response |
|---|---|---|
| 1-5 | Low | Accept or monitor |
| 6-12 | Medium | Treatment plan within 90 days |
| 13-19 | High | Treatment plan within 60 days, owner assigned |
| 20-25 | Critical | Immediate action within 30 days, reported to the CEO |

## Risk appetite
Skylance accepts Low risks. Any Medium, High or Critical risk is treated. Risks affecting customer personal data are prioritised over internal-only risks at an equal score (see the R08 judgment call in `gap-analysis.md`).

## Treatment options
- **Mitigate:** reduce likelihood or impact with controls. Used for 13 of 14 risks.
- **Transfer:** shift part of the impact by contract, insurance or a third party. Used for 1 risk (R12, vendors).
- **Avoid:** stop the activity or remove the asset so the risk no longer applies.
- **Accept:** knowingly live with a risk, documented and approved. Used for risks too small to justify the cost of a control.

## A note on residual scoring
Most preventive controls (access restrictions, patching, approval steps) lower **likelihood**, not **impact** - they make an attack less likely to succeed, but the damage is the same if it does happen. Controls that genuinely lower **impact** change what is lost or how fast it can be recovered, for example encryption at rest, separate immutable backups, or removing real customer data from lower environments. A good residual score reflects this difference rather than lowering both numbers by habit.

## Review
The register is reviewed quarterly and after any major incident or infrastructure change.

## Limitations
Scores are estimates for a fictional company, made by a single assessor. In a real engagement, likelihood and impact would be validated with asset owners, incident history and threat intelligence, rather than judgment alone.
