# Gap Analysis: Current State vs Target State

**Company:** Skylance (fictional). Data comes from `risk-register.csv`; the maturity scores below are estimates to review.

## How risks are prioritised

Risks are fixed in order of **score, highest first**. Ties are broken by impact, then by how easy the fix is. R08 is the only Critical risk (score 20) and goes first; Critical risks need action within 30 days and a report to the CEO.

| Priority | When | Rule |
|---|---|---|
| P1 | Days 0-30 | Score 16 or higher (Critical first) |
| P2 | Days 31-60 | Score 15 |
| P3 | Days 61-90 | Score 12 |
| P4 | Days 91-180 | Score 9 or lower |

Effort: S = under 1 week, M = 1-3 weeks. Any small-effort fix may be pulled forward as a quick win.

## Maturity by NIST CSF 2.0 category (estimates)

Scale: 0 none, 1 ad hoc, 2 partial, 3 defined and documented, 4 managed and measured.

| Category | Current | Target | Related risks |
|---|---|---|---|
| PR.AA Identity and access | 2 | 4 | R01, R02, R07, R08, R11 |
| PR.DS Data security | 2 | 4 | R06, R08, R09, R14 |
| PR.PS Platform security | 2 | 4 | R01, R04, R05, R14 |
| PR.IR Infrastructure resilience | 2 | 3 | R03, R06 |
| DE.CM Continuous monitoring | 1 | 3 | R10 |
| PR.AT Awareness and training | 1 | 3 | R11 |
| GV.SC Supply chain | 1 | 3 | R05, R12 |
| RS.MA Incident management | 1 | 3 | R13 |
| RC.RP Recovery | 2 | 3 | R09 |

## Remediation plan (in priority order)

| Priority | Risk | Score | Current state | Target state | Action | Effort | Owner | Residual score |
|---|---|---|---|---|---|---|---|---|
| P1 | R08 | 20 (Critical) | Broad database access and no encryption at rest | Database encrypted at rest; named-role access only, logged | Encryption at rest, least-privilege access, access logging | M | Head of Engineering | 8 (Medium) |
| P1 | R01 | 16 (High) | WAF/CDN poorly configured, so the bucket can be reached directly or is over-permissive | Bucket private; access only through least-privilege roles; changes guarded by the pipeline | Least-privilege IAM, TLS, firewall hardening, CI/CD guardrails | S | DevOps Lead | 12 (Medium) |
| P1 | R07 | 16 (High) | Password + OTP login only; no login rate limiting or breached-password checks | Passkeys/MFA, login rate limiting and breached-password checks in place | Passkeys/MFA, login rate limiting, breached-password checks | S | Head of IT | 8 (Medium) |
| P1 | R11 | 16 (High) | No security awareness training or phishing simulations | Training and quarterly simulations; passkeys for all staff | Onboarding training, quarterly phishing simulations, passkeys | S | People Ops Manager | 9 (Medium) |
| P2 | R09 | 15 (High) | Backups share an account with production; restores never tested | Immutable cross-account backups; quarterly restore tests | Separate-account immutable backups, quarterly restore tests | M | DevOps Lead | 6 (Medium) |
| P2 | R10 | 15 (High) | Limited central logging; no alerting or monitoring | Central logs; alerts to an on-call channel | Central logging, threat detection, alerts to an on-call channel | M | Head of Engineering | 6 (Medium) |
| P3 | R04 | 12 (Medium) | Unpatched vulnerabilities; no regular patch schedule | Monthly scans and patch deadlines met | Frequent patching and vulnerability scanning | M | Head of Engineering | 8 (Medium) |
| P3 | R06 | 12 (Medium) | TLS not enforced everywhere; weak TLS versions and no HSTS | TLS 1.2+ and HSTS enforced everywhere | Enforce TLS 1.2+, HSTS, certificate management | S | Head of Engineering | 8 (Medium) |
| P3 | R12 | 12 (Medium) | No vendor risk assessment or data processing agreements | Data processing agreements and vendor questionnaire; yearly review | Contracts and DPAs shifting liability; vendor questionnaire and annual review of key vendors | M | COO | 6 (Medium) |
| P3 | R13 | 12 (Medium) | No documented incident response plan or roles | Incident response policy adopted; yearly tabletop exercise | Incident response policy, defined roles, yearly tabletop exercise | S | CTO | 6 (Medium) |
| P3 | R14 | 12 (Medium) | Real production data is copied into QA/test with weaker controls | QA and test use synthetic or masked data only | CI/CD pipeline rebuild with RBAC enforced, WORM storage/sandboxing for QA/test, masked or synthetic data | M | Head of Engineering | 4 (Low) |
| P3 | R03 | 12 (Medium) | No rate limiting or DDoS protection in front of the app | Rate limiting and DDoS protection active and load-tested | Rate limiting plus a DDoS protection service/CDN | M | DevOps Lead | 6 (Medium) |
| P4 | R02 | 9 (Medium) | Login uses password + OTP only (no enforced MFA); malware can steal session cookies | MFA and passkeys enforced; short sessions; endpoint protection on all laptops | MFA and passkeys, endpoint protection, short session lifetimes | S | Head of IT | 6 (Medium) |
| P4 | R05 | 6 (Medium) | Broad deploy permissions and no mandatory review, so a compromised account or library can push code | Deploys need approval; dependencies scanned; yearly third-party audit | Mandatory approval step, automated scanners, third-party audits | S | DevOps Lead | 3 (Low) |

## Notes

- **Passkeys project:** R02, R07 and R11 share one control, so roll it out once for all three.
- **R10 (logging) speeds up the rest:** without it, attacks against the other risks would go unnoticed.
- **R08 is the only Critical risk (score 20).** It goes first and needs action within 30 days.
- **R01, R07 and R11 tie at 16** with the same impact (4), so all sit in P1: R01 is a quick configuration fix, and R07 and R11 share the passkeys project.
- **Impact after treatment:** R01 and R04 keep impact 4 because prevention lowers likelihood, not damage. Impact-reducing controls (encryption, keeping secrets out of code) are a next step.
