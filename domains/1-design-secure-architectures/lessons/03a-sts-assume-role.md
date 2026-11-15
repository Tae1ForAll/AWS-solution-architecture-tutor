# 1.03 Part A – AWS STS & Assuming Roles

**Date:** 2026-11-15
**Guide reference:** Task 1.1 skills: "AWS STS", "role switching", "cross-account access".

## Summary
- **STS** issues temporary credentials (access key ID + secret key + session token) that expire automatically.
- Assuming a role needs **two allows**: the role's **trust policy** (who may assume it) and the caller's **identity policy** allowing `sts:AssumeRole` on the role ARN (always required cross-account).
- Session duration: 1 hour by default. You can request 15 minutes up to the role's max session duration (configurable up to 12 hours). **Role chaining** caps a session at 1 hour.
- While using a role, the caller **gives up its original permissions**.
- APIs: `AssumeRole` (users/roles, cross-account), `AssumeRoleWithSAML` (SAML IdP), `AssumeRoleWithWebIdentity` (OIDC: Google, Cognito, EKS), `GetSessionToken` (IAM user + MFA).

## Cross-account pattern
- In account B: a role whose trust policy names account A (`arn:aws:iam::A:root`) or specific principals, plus a permissions policy.
- In account A: an identity policy allowing `sts:AssumeRole` on B's role ARN.
- Console "Switch Role" = AssumeRole.

## Third parties
- Role trusting the vendor's account + condition `sts:ExternalId`, which prevents the **confused deputy** problem.
- The third party calls AssumeRole itself. You never hand out keys or credentials.

## Key exam points
- Vendor or third-party access → role + External ID. Sharing access keys or creating IAM users is wrong.
- "Temporary", "short-lived", "avoid storing credentials" → STS / roles.
- To cut off sessions that are already active: "Revoke active sessions" on the role (adds a deny for tokens issued before that time).

## Knowledge check result
- Q1 correct: role in each member account with S3 read permissions, Audit account in the trust policy. (Not asked, but completes the picture: the Audit account also needs `sts:AssumeRole` allowed in its identity policies.)
- Q2 partly correct: scoped role + vendor in the trust policy + STS credentials. **Missed the External ID condition and the confused deputy problem**, which were the main point. Also, the firm calls AssumeRole itself; the account owner doesn't generate credentials for them.
