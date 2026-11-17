# 1.04 Part A – AWS Organizations, SCPs & Control Tower

**Date:** 2026-11-17
**Guide reference:** Task 1.1: "Organizations, SCPs, Control Tower", multi-account strategies.

## Summary
- **Organizations:** a management account plus member accounts, grouped in OUs (nestable, policies are inherited). Consolidated billing: combined volume tiers, and RI/Savings Plans discounts shared by default. SCPs need **all features** enabled.
- **SCP:** maximum permissions for IAM users and roles in member accounts. **Never grants.** Effective permissions = SCP ∩ IAM, minus explicit deny. `FullAWSAccess` is attached by default. An action must be allowed at every level from the root to the account.
  - Affects: all users and roles in member accounts, **including the member root user**.
  - Doesn't affect: the **management account**, **service-linked roles**, or external principals.
- **`aws:PrincipalOrgID`** in resource policies → allow the whole organisation without listing account IDs.
- **Control Tower:** automated landing zone (Organizations, Security OU with Log Archive and Audit accounts, IAM Identity Center, Account Factory). Controls: preventive (SCPs), detective (Config rules), proactive (CloudFormation hooks).
- RCPs (late 2024) exist; their SAA-C03 relevance is uncertain.

## Key exam points
- Restrict everyone, including admins and the root user, in member accounts → SCP.
- "Grant with an SCP" → always wrong.
- Multi-account with best practices and least effort → Control Tower.
- One bill / shared discounts → consolidated billing.
- SCP vs permissions boundary: account/OU-wide vs per user or role. Neither grants.

## Knowledge check result
- Q1 correct tool and placement (Deny SCP on the Production OU). Two refinements:
  - Deny only the *disabling* actions (for example `guardduty:DeleteDetector`), not the whole GuardDuty API.
  - The core reason is that **IAM policies can't restrict the root user, and account admins can edit their own IAM policies**. An SCP sits outside the account's control. ("Can't attach to an OU" is true but secondary.)
- Q2 missed the core point: **SCPs never grant permissions**. The suggested "Allow" SCP grants nothing and doesn't block disabling anything.
