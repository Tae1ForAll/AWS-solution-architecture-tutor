# 1.03 Part B – Roles vs Resource-Based Policies, Service Roles & PassRole

**Date:** 2026-11-16
**Guide reference:** Task 1.1 skills: "cross-account access", "appropriate use of resource policies for AWS services".

## Summary
- **Assume a role:** the caller becomes the role and **gives up its own permissions** for the session. Works for any service.
- **Resource-based policy:** the caller **stays itself and keeps its own permissions**. Only for services that support resource policies (S3, SQS, SNS, KMS, Lambda, Secrets Manager, ECR and others).
- Cross-account access through a resource policy still needs an **allow on both sides**: the resource policy in B and the caller's identity policy in A.
- **Service role:** a role an AWS service assumes (trust principal such as `lambda.amazonaws.com`). You control its permissions.
- **Service-linked role:** created and defined by the service. You can't edit its permissions.
- **Instance profile:** a container for one role on EC2. Credentials come from IMDS and rotate automatically. Prefer IMDSv2. You can swap the role without restarting the instance.
- **`iam:PassRole`:** needed to give a role to a service (EC2, Lambda, CodeBuild and so on). Prevents **privilege escalation**. Scope it to specific role ARNs, optionally with `iam:PassedToService`.

## Key exam points
- Access keys on EC2 or in code → wrong. Use a role / instance profile.
- Caller must keep its own access while using another account's resource → resource-based policy.
- Service without resource policies (EC2, RDS API) → cross-account role.
- "Not authorized to perform iam:PassRole" → grant PassRole on that specific role, not `iam:*`.
- SCPs never grant permissions.

## Knowledge check result
- Q1 correct: bucket policy on B's bucket, because assuming a role gives up access to A's bucket. Raised a fair point that a role could also work (it would need a bucket policy on A's bucket trusting B's role). Concluded correctly that this is more complex.
- Q2 correct permission (`iam:PassRole`). Described the risk loosely; the term to use is **privilege escalation**. Also, the real fix is a least-privilege CodeBuild service role.
