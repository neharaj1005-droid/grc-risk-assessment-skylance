# Executive Summary: Information Security Risk Assessment

**Company:** Skylance (fictional, 50-person remote SaaS company) | **Prepared for:** CEO and leadership team | **Status:** Draft

## Bottom line

Skylance has **1 Critical**, **5 High** and 8 Medium risks to its customer data and service. Most fixes are configuration and process changes that can be done in **the next 90 days**. Completing the plan removes every Critical and High rating and cuts the average risk score by about **48%**.

## What we assessed

14 risks across the production app, customer database, cloud storage and backups, Google Workspace, code pipeline, staff and vendors. Each risk is scored 1-25 (likelihood x impact) before and after the planned fix.

| Rating | Today | After the plan |
|---|---|---|
| Critical | 1 | 0 |
| High | 5 | 0 |
| Medium | 8 | 12 |
| Low | 0 | 2 |
| Average score | 13.2 | 6.9 |

## The highest risks, in plain language

- **R08 (score 20):** Customer personal data in the main database is not encrypted and is open to too many people.
- **R01 (score 16):** Source code kept in cloud storage could be reached directly if the protective layers in front of it are set up wrongly.
- **R07 (score 16):** Attackers try passwords leaked from other companies on our login page, and reused passwords could let them in.
- **R11 (score 16):** Staff have no security training, and phishing emails are the most common way attackers get in.
- **R09 (score 15):** Backups sit next to the live system and have never been test-restored, so ransomware could take out both.
- **R10 (score 15):** Limited logging means a break-in could go unnoticed for weeks, which makes every other risk worse.

## Recommended plan

| When | Focus | Risks |
|---|---|---|
| Days 0-30 (P1) | Protect the customer database, lock down code storage, harden sign-in, train staff | R08, R01, R07, R11 |
| Days 31-60 (P2) | Logging and alerts, safe backups | R10, R09 |
| Days 61-90 (P3) | Patching, encryption in transit, vendors, incident plan, test data, DDoS protection | R04, R06, R12, R13, R14, R03 |
| Days 91-180 (P4) | Stronger sign-in and pipeline approvals | R02, R05 |

How each risk is handled: 13 reduced with new controls, and 1 shared with a vendor by contract (R12).

## What remains after the plan

No High risks remain, but **R01 still scores 12** (top of Medium) because the fixes make an attack less likely without shrinking the damage if one happens. Next steps are controls that limit damage, such as encryption and keeping passwords out of code.

## Decisions requested

- Approve the 90-day plan and the named risk owners.
- Confirm the risk appetite: Low risks accepted, High and Critical always treated.
- Agree to review the risk register every quarter.

*This is a fictional exercise built for portfolio purposes; all figures are illustrative.*
