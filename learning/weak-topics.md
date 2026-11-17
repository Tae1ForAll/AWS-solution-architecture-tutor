# Weak Topics

Topics that need further review. Remove an entry (move to "Resolved")
only after a later quiz shows the misunderstanding is fixed.

## Open

| Topic | Domain | Misunderstanding | First seen | Last reviewed |
|-------|--------|------------------|------------|---------------|

## Resolved

| Topic | Resolved on | Evidence |
|-------|-------------|----------|
| SCPs never grant permissions | 2026-11-17 | 1.04A quiz Q1 + Q5-E correct; follow-up recall: "IAM policy must grant s3 also" (SCP only limits) |
| Why an SCP instead of IAM for org-wide guardrails | 2026-11-17 | 1.04A quiz Q2: chose SCP, reason "limit maximum permissions for root users also" (recall). Didn't mention that admins can't remove it |
| External ID / confused deputy for third-party role access | 2026-11-15 | 1.03A quiz Q1: chose role + External ID over role-without-ExternalID and hand-delivered STS creds (recognition; retest with recall later) |
| EBS is zonal / sharing data across AZs | 2026-11-14 | 1.01 quiz: Q5 correct (snapshot → new volume in target AZ); rejected the shared-EBS and Multi-AZ options in Q1 |
| Components of a multi-AZ web tier | 2026-11-14 | 1.01 quiz Q1: chose ALB + ASG across 2 AZs + EFS (recognition; retest with recall later) |
