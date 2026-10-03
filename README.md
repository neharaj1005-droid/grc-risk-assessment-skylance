# GRC Project: Risk Assessment and Gap Analysis for Skylance

A hands-on Governance, Risk and Compliance (GRC) project. It follows a fictional company through a risk assessment, control mapping to **NIST CSF 2.0** and **ISO/IEC 27001:2022 Annex A**, a prioritised gap analysis and an executive summary.

> **Skylance is entirely fictional** and is not affiliated with any real organisation. All data and findings are invented for learning and portfolio purposes.

## Scenario
Skylance is a 50-person, fully remote B2B SaaS company. It runs on AWS, keeps source code in S3 buckets, moves code through prod, QA and test environments using CI/CD pipelines, and stores customer personal data. Staff sign in to Google Workspace with email, password and a one-time code (OTP), without enforced MFA. The company has no formal security programme.

## Repo contents
| File | What it is |
|---|---|
| `01-scope-and-assets/asset-inventory.csv` | 8 assets with owner, data classification and criticality |
| `02-risk-assessment/methodology.md` | Likelihood/impact scales, rating bands, risk appetite and treatment options |
| `02-risk-assessment/risk-register.csv` | 14 risks with threat, weakness, likelihood x impact score, treatment, owner and residual score |
| `02-risk-assessment/risk-heatmap.png` | Inherent vs residual risk, plotted on a 5x5 grid |
| `03-control-mapping/nist-csf-iso27001-mapping.csv` | Each risk mapped to NIST CSF 2.0 categories and ISO 27001:2022 controls |
| `04-gap-analysis/gap-analysis.md` | Current vs target state and a 180-day prioritised remediation plan |
| `05-policies/incident-response-policy.md` | Severity levels, roles and the response process |
| `06-executive-summary/exec-summary.md` | One-page summary for non-technical leadership |

Risk IDs (R01-R14) are used consistently across every file.

## Method
1. Identify assets and the threats and weaknesses that affect them.
2. Score each risk: **likelihood (1-5) x impact (1-5)**. Ratings: 1-5 Low, 6-12 Medium, 13-19 High, 20-25 Critical.
3. Choose a treatment: mitigate, transfer, avoid or accept.
4. Score the **residual** risk assuming the plan is carried out.
5. Map risks to controls, then prioritise fixes by score (highest first).

## Key findings
- **14 risks:** 1 Critical, 5 High and 8 Medium today. Highest scores: R08 (20), R01 (16), R07 (16).
- After the plan, no Critical or High risks remain (12 Medium, 2 Low) and the average score falls from **13.2 to 6.9** (about 48%).
- Treatments used: 13 mitigate, 1 transfer.
- **R08 (customer database breach) is the only Critical risk**, because that data is Skylance's most valuable asset and a breach would be severe.

## Lessons learned
- Most preventive controls lower **likelihood**, not **impact**. Impact only falls with controls that limit damage, such as encryption or separate backups.
- A risk should describe **one threat** and a **specific weakness** ("no rate limiting"), not a vague area ("bad code").
- A good plan mixes **preventive** controls (approval steps) and **detective** ones (scanning, logging).
- If the residual score equals the starting score, the plan is not doing anything and needs rethinking.

## Still to add
An access control policy and an acceptable use policy (the incident response policy is done).

## Next projects
Vendor risk assessment questionnaire, incident response tabletop exercise, ISO 27001 policy pack, SOC 2 or PCI-DSS readiness checklist.

## Limitations
Single assessor, qualitative scores and invented data. A real assessment would validate scores with asset owners and use incident and threat data.

## Author
Neha Raj
