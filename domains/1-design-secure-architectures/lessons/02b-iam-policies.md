# 1.02 Part B – IAM Policies & Evaluation Logic

**Date:** 2026-11-14
**Guide reference:** Task 1.1 skills: "authorization model … policies", "appropriate use of resource policies for AWS services".

## Summary
- A policy is a JSON document. Statement elements: `Effect`, `Action`, `Resource`, optional `Condition`, and `Principal` (resource-based policies only).
- **Identity-based** (AWS managed / customer managed / inline): attached to a user, group or role.
- **Resource-based**: attached to the resource and includes a `Principal`. Examples: S3 bucket policy, KMS key policy, SQS/SNS/Lambda policies, a role's trust policy.
- **Permissions boundaries and SCPs** set the maximum permissions. They never grant anything.

## Evaluation logic (single account)
1. Implicit deny by default.
2. Explicit Deny anywhere → DENY (overrides everything).
3. SCP / boundary doesn't allow the action → DENY.
4. An Allow in an identity-based or resource-based policy → ALLOW.
5. Otherwise → DENY (implicit).

**Cross-account:** needs an Allow in the caller's identity policy **and** in the resource policy, or the caller assumes a role in the target account.

## Key exam points
- Explicit deny wins. With no allow anywhere, the implicit deny applies.
- Enforce HTTPS on S3: bucket policy with Deny + `aws:SecureTransport = false`.
- Condition keys: `aws:MultiFactorAuthPresent`, `aws:SourceIp`, `aws:RequestedRegion`, `aws:SecureTransport`.
- Least privilege: customer-managed policies with specific actions and ARNs. Access Analyzer can generate policies from CloudTrail activity.
- "Use an SCP to grant access" is a distractor.

## Knowledge check result
- Q1 correct: read allowed by the identity policy; delete blocked by the explicit Deny.
- Q2 correct conclusion (no read). Refine: the rule is **implicit (default) deny**. There is no Allow in *any* policy, identity or resource. In the same account, an Allow in either one would have been enough.
