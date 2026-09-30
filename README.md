# SOC 2 Readiness Assessment Lab

A hands-on SOC 2 readiness assessment of **Monvive Cloud**, a
simulated SaaS booking platform for home repair services.

**Live risk register app:** https://soc2riskregister.netlify.app

## The Result

Monvive Cloud is **not yet ready** for a SOC 2 Type I audit.
The assessment tested 20 controls and identified 12 findings,
including 4 high-severity gaps in access management, policy
governance, and incident response. A 90-day remediation
roadmap is included.

**Top finding:** A sample access review found a former
employee with active system access 45 days after leaving.

## What's Inside

| Step | File | What it is |
|---|---|---|
| 1 | 01-system-description.md | System scope and boundaries |
| 2 | 02-risk-register/ | 15 risks scored by likelihood x impact |
| 3 | 03-control-matrix/ | 20 controls mapped to SOC 2 Common Criteria |
| 4 | 04-policies/ | Access Control, Incident Response, Vendor Management, and Acceptable Use policies |
| 5 | 05-evidence/ | Screenshots, sample access review, and evidence index |
| 6 | 06-gap-assessment.md | Final readiness report with findings and roadmap |

## Skills Demonstrated

- Scoping a system for a SOC 2 audit
- Risk assessment and risk scoring
- Control design and mapping to SOC 2 Trust Services Criteria
- Policy writing
- Evidence collection and access review testing
- Writing audit findings (condition, criteria, cause, effect, corrective action)
- Remediation planning
- Building a risk register web app (HTML, CSS, JavaScript, deployed on Netlify)

## Tools

GitHub, Netlify, GitHub rulesets, Dependabot, HTML/CSS/JavaScript

## Note

Monvive Cloud is a fictional company created for this lab.
Personal GitHub and Netlify accounts stand in for company
systems, and the access review uses sample data. This is a
readiness assessment, not an audit opinion.
