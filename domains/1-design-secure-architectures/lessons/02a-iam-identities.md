# 1.02 Part A – IAM Identities (root, users, groups, roles, MFA, least privilege)

**Date:** 2026-11-14
**Guide reference:** Task 1.1 skills: "best practices to IAM users and root users (MFA)", "authorization model with IAM users, groups, roles, and policies"; knowledge: "principle of least privilege".
**Part B (policies & evaluation logic):** see 02b-iam-policies.md.

## Summary
- IAM is **global** and free. It handles authentication (who) and authorization (what).
- **Root user**: email + password, full unrestricted access. Use it only for root-only tasks (account settings, closing the account, Support plan, S3 MFA Delete). Turn on MFA, create no access keys, don't use it day to day.
- **IAM user**: long-term credentials (console password, access keys). Starts with no permissions. AWS now prefers federation (Identity Center) for people and roles for workloads.
- **IAM group**: a set of users that share attached policies. Users can be in several groups. **No nesting.** A group is not a principal.
- **IAM role**: no long-term credentials. Trusted entities assume it and get **temporary STS credentials**. Has a **trust policy** (who can assume it) and a **permissions policy** (what it can do). Used by EC2 (instance profile), Lambda (execution role), cross-account access and federated users.
- **Least privilege**: start with the minimum and add permissions as needed.

## Key exam points
- App on EC2 / Lambda / ECS needs AWS access → **role**. Never put access keys in code, env vars or AMIs.
- Same permissions for many users → **groups**.
- Secure root → MFA + no access keys + not for daily use.
- Choose the narrowest permissions. `"*"` / admin options are usually distractors.

## Knowledge check result (Lambda → DynamoDB with IAM user keys in env var)
- Correct: use an IAM role, because credentials expire automatically and there are no long-lived keys to leak.
- Refine: the role is the Lambda **execution role**. Lambda fetches and rotates its credentials automatically, and the role should be scoped to that one table and only the write actions it needs (least privilege).
