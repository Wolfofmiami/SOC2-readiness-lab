# SOC 2 Readiness Assessment: Monvive Cloud

| Prepared by | Jo (Assessor) |
|---|---|
| Date | 2026-09-30 |
| Framework | SOC 2, Security (Common Criteria) |
| Report type assessed | Type I readiness |

## 1. Executive Summary

Monvive Cloud is **not yet ready** for a SOC 2 Type I audit.

Of 20 controls tested, 3 are fully in place, 1 was fixed
during this assessment, 7 are partially in place, and 9
are not in place. The biggest problems are around
**access**: a former employee still has access 45 days
after leaving, no one reviews who has access, and
security policies have never been approved.

With focused effort, Monvive Cloud could be ready for a
Type I audit in about **90 days**.

## 2. Scope

- **In scope:** booking web app, customer database
  (Supabase), Google Workspace, GitHub, Netlify
- **Out of scope:** payment card data (handled fully
  by Stripe)
- **Criteria:** SOC 2 Security (CC1 through CC9)

See: 01-system-description.md

## 3. Approach

1. Documented the system and its boundaries
2. Identified and scored 15 risks (likelihood x impact)
3. Mapped 20 controls to risks and SOC 2 criteria
4. Drafted 4 core security policies
5. Collected evidence and ran a sample access review
6. Graded each control and wrote up gaps

## 4. Results at a Glance

| Status | Count | Controls |
|---|---|---|
| In place | 3 | C07, C16, C18 |
| Fixed during assessment | 1 | C19 |
| Partial | 7 | C01, C03, C05, C06, C08, C12, C14 |
| Not in place | 9 | C02, C04, C09, C10, C11, C13, C15, C17, C20 |

## 5. Findings Summary

| ID | Finding | Control | Criteria | Severity |
|---|---|---|---|---|
| F01 | Former employees keep access | C02 | CC6.2 | High |
| F02 | No access reviews; users over-privileged | C04, C05 | CC6.2, CC6.3 | High |
| F03 | Policies not approved or signed | C17 | CC2.2, CC5.3 | High |
| F04 | Incident response plan never tested | C11 | CC7.3, CC7.4 | High |
| F05 | MFA not verified on all systems | C01 | CC6.1 | Medium |
| F06 | Code review not possible with one developer | C08 | CC8.1 | Medium |
| F07 | No log monitoring | C10 | CC7.2 | Medium |
| F08 | No security awareness training | C09 | CC1.4, CC2.2 | Medium |
| F09 | Vendors never reviewed | C15 | CC9.2 | Medium |
| F10 | Backups never tested | C12 | CC7.5, CC9.1 | Medium |
| F11 | Field tech phones not managed | C13 | CC6.7 | Medium |
| F12 | No plan for vendor outages | C20 | CC9.1 | Low |

**Severity key**
- **High:** customer data at real risk and would likely
  fail an audit
- **Medium:** a real gap, but lower risk or partly covered
- **Low:** minor, fix when possible

## 6. Detailed Findings (High)

### F01: Former employees keep access
- **Condition:** A sample access review found a support
  rep who left in August 2026 still has an active Google
  Workspace account 45 days later. No offboarding
  records exist.
- **Criteria:** CC6.2 and the Access Control Policy
  require access to be removed within 24 hours.
- **Cause:** There is no offboarding checklist or
  owner for removing access.
- **Effect:** A former employee could view or take
  customer data (Risk R01, score 16).
- **Corrective action:** Remove the account today.
  Create an offboarding checklist owned by the Ops
  Manager, and track every departure.
- **Evidence:** C04_access-review-sample.md

### F02: No access reviews; users over-privileged
- **Condition:** No access reviews have ever been done.
  The sample review found 2 developers with admin
  access they don't need.
- **Criteria:** CC6.2 and CC6.3 require access to be
  approved, limited, and reviewed regularly.
- **Cause:** No review process or schedule exists.
- **Effect:** Extra access means one stolen login can
  do more damage (Risk R06).
- **Corrective action:** Downgrade the 2 accounts.
  Run and sign an access review every quarter.
- **Evidence:** C04_access-review-sample.md

### F03: Policies not approved or signed
- **Condition:** 4 security policies exist but all
  show "Approved by: Pending." No employee has
  signed them.
- **Criteria:** CC2.2 and CC5.3 require policies to be
  approved by leadership and communicated to staff.
- **Cause:** Policies were drafted but never formally
  rolled out.
- **Effect:** Employees can't follow rules they were
  never given, and an auditor would treat the policies
  as not in effect.
- **Corrective action:** CEO approves all 4 policies.
  Every employee signs the Acceptable Use Policy.
- **Evidence:** 04-policies folder

### F04: Incident response plan never tested
- **Condition:** An incident response policy was
  drafted, but it has never been approved or practiced.
- **Criteria:** CC7.3 and CC7.4 require the company to
  evaluate and respond to security incidents.
- **Cause:** Incident response has never been a
  priority at the company's size.
- **Effect:** A breach would be handled slowly and
  inconsistently (Risk R09).
- **Corrective action:** Approve the plan and run a
  tabletop exercise (a practice phishing scenario)
  with the CEO, CTO, and Ops Manager.

## 7. What's Working

- **Encryption (C07):** HTTPS is active. This is an
  inherited control provided by Netlify.
- **Risk management (C16):** A live risk register
  exists and is tracked in version control.
- **Hiring (C18):** Background checks are done on
  all new hires.
- **Vulnerability alerts (C19):** Dependabot was
  turned on during this assessment.
- **Change protection:** Branch rules now block
  deleting the main branch and rewriting history.

## 8. Notes on Medium Findings

- **F06 Code review:** With one developer, true peer
  review isn't possible. This is a segregation of
  duties problem. Until a second developer is hired,
  use a **compensating control**: the CTO reviews all
  changes after they go live, every week, and signs off.
- **F09 Vendors:** Monvive Cloud relies on Netlify for
  encryption but has never reviewed Netlify's security.
  Collect SOC 2 reports from Netlify, Supabase, Stripe,
  and Google.

## 9. Remediation Roadmap

**Days 1 to 30: Lock the doors**
- F01: Remove former employee access; create offboarding checklist
- F02: Fix over-privileged accounts; run first access review
- F03: Approve policies; collect employee signatures
- F05: Turn on MFA for Supabase and Google Workspace

**Days 31 to 60: Train and prepare**
- F04: Run the incident response tabletop exercise
- F08: Launch security awareness training
- F09: Collect vendor SOC 2 reports
- F10: Test a backup restore

**Days 61 to 90: Watch and protect**
- F07: Set up log monitoring and weekly reviews
- F11: Set up phone management with remote wipe
- F06: Start the weekly compensating code review
- F12: Write a vendor outage plan

**Day 90:** Re-test all controls, then schedule the
Type I audit.

## 10. Limitations

- Monvive Cloud is a fictional company built for this
  lab. Personal GitHub and Netlify accounts stand in
  for company systems.
- The access review used sample data.
- This is a readiness assessment, not an audit opinion.
  Only a licensed CPA firm can issue a SOC 2 report.
