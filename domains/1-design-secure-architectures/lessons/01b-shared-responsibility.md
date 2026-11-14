# 1.01 Part B – AWS Shared Responsibility Model

**Date:** 2026-11-14
**Guide reference:** Task 1.1 "AWS shared responsibility model".

## Summary
- **AWS = security OF the cloud**: hardware, hypervisor, networking, facilities, disposal of physical media.
- **Customer = security IN the cloud**: what this includes depends on the service type.
- The more managed the service, the more work moves to AWS. Data, IAM and encryption choices **always** stay with the customer.

| Service type | Example | Customer still manages |
|---|---|---|
| IaaS | EC2 | Guest OS patching, apps, security groups, IAM, data, encryption |
| Managed | RDS | DB users/permissions, security groups, encryption choice, backups, maintenance window |
| Serverless/abstracted | S3, DynamoDB, Lambda | Data, IAM & resource policies, encryption choice, code |

**Control types (AWS docs):** inherited (physical/environmental), shared (patching, configuration, training: each side does its own layer), customer-specific (e.g. zoning data inside security environments).

## Key exam points
- Patching: EC2 → customer. RDS / Lambda / S3 / DynamoDB → AWS patches the OS and platform.
- Security groups, NACLs, IAM, bucket policies → always configured by the customer.
- "Reduce operational/patching overhead" → pick the more managed service.
- A feature being available (e.g. encryption) ≠ it being enabled. Enabling it is the customer's job.

## Knowledge check result (EC2 MySQL → RDS)
- Correct: patching moves to AWS, and access control stays with the customer.
- Refine: be precise. AWS takes over **OS and DB engine** patching, but the customer still picks the maintenance window. Access control on RDS has three layers: IAM (who can manage the instance), security groups (network access) and database users/grants inside MySQL.
- Warm-up on EBS AZ scope: not answered.

## Follow-up: RDS maintenance window (2026-11-14)
- A weekly UTC range (min 30 min) when AWS applies OS and engine maintenance. AWS assigns a default if you don't set one. Changes can be "Apply immediately" or wait for the next window.
- Multi-AZ + **OS patch**: standby patched first → failover → old primary patched. Downtime ≈ one failover.
- Multi-AZ + **engine version upgrade**: primary and standby upgraded **at the same time** → real downtime.
- Don't confuse with **SSM Maintenance Windows**, which schedule *your own* tasks (e.g. EC2 patching).
- Check result: user explained the rolling OS patch correctly but didn't state that the engine upgrade causes more downtime.
