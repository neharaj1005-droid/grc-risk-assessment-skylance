# Incident Response Policy

**Company:** Skylance (fictional) | **Version:** 0.1 draft | **Owner:** CTO | **Review:** annually and after each major incident
**Supports:** R13 (no incident response plan), R10 (slow detection), R09 (backup recovery) | **ISO 27001:2022:** A.5.24, A.5.26, A.5.30 | **NIST CSF 2.0:** RS.MA, RC.RP

## 1. Purpose and scope
This policy defines how Skylance detects, responds to, and learns from security incidents affecting its systems, staff, or customer data. It applies to all employees and contractors.

## 2. Severity levels
| Level | Description | Initial response time |
|---|---|---|
| SEV1 | Confirmed customer data exposure, or a production outage caused by an attack | Immediately, 24/7 |
| SEV2 | Suspected compromise of an account, server, or pipeline | Within 1 hour |
| SEV3 | Contained event with no data impact (for example, a blocked phishing attempt) | Next business day |

## 3. Roles
| Role | Responsibility |
|---|---|
| Incident Commander (CTO or delegate) | Leads the response and makes containment decisions |
| Technical Lead | Investigates, contains, and recovers affected systems |
| Communications Lead (COO) | Handles customer, regulator, and staff messaging |
| Scribe | Keeps a timestamped log of every action taken |

## 4. Process
1. **Detect and report.** Anyone who notices a suspected incident reports it to the security channel or security@skylance.example. Central logging and alerting (see R10) is the main way incidents are caught early.
2. **Triage.** Assign a severity level and name an Incident Commander.
3. **Contain.** Isolate affected accounts, systems, or access keys to stop the incident from spreading.
4. **Eradicate and recover.** Remove the cause, restore from tested backups where needed (see R09), and verify the fix before resuming normal operations.
5. **Notify.** The Communications Lead assesses legal and contractual notification duties, and checks regulator and customer deadlines with legal counsel.
6. **Review.** Hold a blameless post-incident review within 5 working days. Record what happened, what worked, and what needs to change, and track the resulting actions to completion.

## 5. Preparedness
- Keep the contact list and runbooks current.
- Run a tabletop exercise at least once a year, walking through a realistic scenario (for example, a ransomware attack or a leaked credential).
- Test backup restores quarterly, so recovery is proven before it's needed (see R09).

## 6. Evidence handling
Preserve logs and snapshots of affected systems before making changes, wherever it's safe to do so. This protects Skylance's ability to investigate the incident properly and, if needed, to support a legal or insurance claim.

## 7. Communication during an incident
- Internal updates go to the security channel at a cadence set by the Incident Commander, at least once every few hours during a SEV1.
- External communication (to customers, regulators or the public) is reviewed by the Communications Lead and legal counsel before release.
- Nobody outside the response team speaks publicly about an active incident without the Communications Lead's approval.
