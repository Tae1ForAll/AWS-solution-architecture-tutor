# Learning Progress

**Target certification:** AWS Certified Solutions Architect – Associate (SAA-C03) — exam guide v1.1 (Oct 29 2026), validated 2026-11-12
**Pass mark:** 720 / 1,000 (scaled)
**Started:** 2026-11-12
**Target exam date:** _not set_

## Status Legend

- `Not started` – not yet covered
- `In progress` – lesson started, not finished
- `Taught` – lesson completed, **not yet proven**
- `Understood` – supported by evidence (correct quiz answers / clear explanation in my own words)

## Domain Summary

| Domain | Sections | Taught | Understood |
|--------|----------|--------|------------|
| 1 – Secure (30%) | 10 | 3 | 3 |
| 2 – Resilient (26%) | 10 | 0 | 0 |
| 3 – High-Performing (24%) | 11 | 0 | 0 |
| 4 – Cost-Optimized (20%) | 9 | 0 | 0 |

Per-section status lives in each `domains/*/README.md`.

## Session Log

<!-- Newest first. Format:
### YYYY-MM-DD – Domain X.NN Topic
- Covered:
- Evidence of understanding:
- Next step:
-->

### 2026-11-16 – Quiz 1.03 Part B
- Score: 5/5, including the tricky two-sided cross-account question (Q2: C over B). No reasons given, but the Part B knowledge check showed correct reasoning on role vs resource policy. Part A quiz was also 5/5.
- Status: 1.03 → `Understood`. Recall still to be tested: External ID / confused deputy, privilege escalation (PassRole).
- Next step: 1.04 Multi-account security & federation.

### 2026-11-16 – Domain 1.03 Part B: Roles vs resource-based policies, service roles, PassRole
- Covered: role vs resource-based policy for cross-account access (permissions given up vs kept), service roles, service-linked roles, instance profiles and IMDSv2, iam:PassRole and privilege escalation.
- Evidence: Knowledge check Q1 correct with good reasoning, and noticed on their own that a role could also work if A's bucket trusts it. Q2 named iam:PassRole correctly but described the risk loosely (didn't say "privilege escalation").
- Status: 1.03 → `Taught` (Parts A + B). Part A quizzed 5/5; Part B not yet quizzed.
- Next step: quiz on 1.03 Part B (or all of 1.03), then 1.04 Multi-account security & federation.

### 2026-11-15 – Quiz 1.03 Part A
- Score: 5/5 (no reasons given). External ID weak topic answered correctly in Q1 → resolved (recognition only).
- Status: 1.03 stays `In progress`; Part A has quiz evidence, Part B not yet taught.
- Next step: 1.03 Part B: roles vs resource-based policies, service roles, iam:PassRole.

### 2026-11-15 – Domain 1.03 Part A: STS & assuming roles
- Covered: STS temporary credentials, AssumeRole flow (trust policy + caller's sts:AssumeRole permission), session duration and role chaining, STS API variants, cross-account role pattern, External ID / confused deputy, revoking sessions.
- Evidence: Knowledge check Q1 correct (role in member accounts trusting the Audit account). Q2 missed External ID / confused deputy. Also thought the owner generates credentials for the third party.
- Status: 1.03 `In progress` (Part B, roles vs resource-based policies and PassRole, not yet taught).
- Next step: quiz on Part A, or start Part B.

### 2026-11-14 – Quiz 1.02
- Score: 5/5, including explicit deny vs allow, cross-account two-sided allow, roles vs access keys, groups, root best practices. Supported by correct knowledge-check reasoning in Parts A and B.
- Status: 1.02 → `Understood`.
- Next step: 1.03 Roles, STS & cross-account access.

### 2026-11-14 – Domain 1.02 Part B: IAM policies & evaluation logic
- Covered: policy JSON elements, identity vs resource-based policies, boundaries/SCPs as limits, evaluation logic (explicit deny > allow > implicit deny), cross-account two-sided allow, conditions.
- Evidence: Knowledge check correct on both parts. Didn't name "implicit deny" as the rule in Q2.
- Status: 1.02 → `Taught` (Parts A + B). Not `Understood` until quizzed.
- Next step: quiz on 1.02.

### 2026-11-14 – Domain 1.02 Part A: IAM identities
- Covered: root user best practices, IAM users, groups (no nesting, not a principal), roles (trust + permissions policy, STS temporary credentials), MFA, least privilege.
- Evidence: Knowledge check correct (role instead of access keys; credentials expire automatically; no long-lived keys to leak). Didn't mention scoping to the single table.
- Status: 1.02 `In progress` (Part B, policies & evaluation logic, not yet taught).
- Next step: quiz on Part A, or start Part B.

### 2026-11-14 – Quiz 1.01
- Score: 5/5, with correct reasons on Q1 and Q4. Also explained the Multi-AZ rolling OS patch in their own words during the maintenance-window follow-up.
- Status: 1.01 → `Understood`. Both open weak topics resolved.
- Next step: 1.02 IAM fundamentals.

### 2026-11-14 – Domain 1.01 Part B: Shared responsibility model
- Covered: security OF vs IN the cloud, responsibilities by service type (EC2 / RDS / serverless), inherited / shared / customer-specific controls.
- Evidence: Knowledge check correct in broad terms (patching moves to AWS, access control stays with the customer). Could be more precise about OS + DB engine patching and the three access layers on RDS (IAM, security groups, DB users). Skipped the EBS warm-up.
- Status: 1.01 now `Taught` (Parts A + B). Not yet `Understood`: no quiz evidence.
- Next step: quiz on 1.01 (A + B), including the EBS/multi-AZ weak topics; then 1.02 IAM fundamentals.

### 2026-11-13 – Domain 1.01 Part A: Global infrastructure
- Covered: Regions, AZs, edge locations, Local Zones / Wavelength / Outposts, global vs regional vs zonal scope, choosing a Region.
- Evidence: Knowledge check partly correct. Found the SPOF, chose multi-AZ, and explained multi-AZ vs multi-Region well. Gaps: thought EBS could span AZs; left out ALB + ASG.
- Status: still `In progress` (Part B, shared responsibility, not taught yet).
- Next step: quiz on Part A, or start Part B.
