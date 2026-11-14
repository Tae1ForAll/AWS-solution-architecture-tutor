# Quiz History

## Summary

| Date | Topic | Score | Weak points |
|------|-------|-------|-------------|
| 2026-11-14 | 1.02 IAM fundamentals | 5/5 | None. No reasons given this time; reasoning shown earlier in the knowledge checks |
| 2026-11-14 | 1.01 Global infra & shared responsibility | 5/5 | None. Q1/Q5 were recognition (multiple choice), so recall still needs testing |

## Detailed Records

<!-- Newest first. Format:
### YYYY-MM-DD – Domain X.NN Topic
**Score:** n/m

**Q1.** (short scenario summary)
- My answer: B  | Correct: C  | ✅/❌
- Misunderstanding: ...
-->

### 2026-11-14 – Domain 1.02 IAM fundamentals
**Score:** 5/5

**Q1.** Root user best practices (choose TWO)
- My answer: A, C | Correct: A, C | ✅

**Q2.** 50 developers, same changing permissions, least overhead
- My answer: D | Correct: D | ✅

**Q3.** EC2 app reads one S3 bucket, most secure
- My answer: B | Correct: B | ✅

**Q4.** User in two groups: Allow ec2:* + Deny TerminateInstances
- My answer: C | Correct: C | ✅

**Q5.** Cross-account S3 read without assuming a role
- My answer: A | Correct: A | ✅

### 2026-11-14 – Domain 1.01 Global infrastructure & shared responsibility
**Score:** 5/5

**Q1.** Single EC2 + EBS in one AZ → survive AZ failure, least overhead
- My answer: B | Correct: B | ✅ (reason: EFS shares files across AZs)

**Q2.** EC2 customer responsibilities (choose TWO)
- My answer: A, C | Correct: A, C | ✅

**Q3.** EU data residency for S3 patient data
- My answer: A | Correct: A | ✅

**Q4.** PostgreSQL on EC2, cut patching overhead and OS-patch downtime
- My answer: C | Correct: C | ✅ (reason: Multi-AZ patches standby first, then fails over)

**Q5.** Move EBS volume from us-east-1a to us-east-1b
- My answer: D | Correct: D | ✅

