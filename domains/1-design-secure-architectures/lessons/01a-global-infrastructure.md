# 1.01 Part A – AWS Global Infrastructure

**Date:** 2026-11-12 (taught) · 2026-11-13 (knowledge check)
**Guide reference:** Task 1.1 "AWS global infrastructure (for example, Availability Zones, AWS Regions)"; also Tasks 2.2, 3.3, 4.2.
**Part B (shared responsibility model):** see 01b-shared-responsibility.md.

## Summary

- **Region**: a separate, isolated geographic area. Data stays in the Region you choose unless you replicate it.
- **Availability Zone (AZ)**: one or more separate data centres in a Region, with independent power, networking and connectivity, joined to the other AZs by low-latency links.
- **Edge location**: a site close to users for CloudFront, Route 53 and Global Accelerator. It speeds things up; it does not add resilience.
- **Other infrastructure types**: Local Zones (a Region extended into a city), Wavelength (inside 5G networks), Outposts (AWS racks on-premises).

## Service scope

| Scope | Examples |
|-------|----------|
| Global | IAM, Route 53, CloudFront |
| Regional | S3 bucket, DynamoDB, Lambda, VPC, EFS |
| Zonal | EC2 instance, **EBS volume**, subnet |

## Choosing a Region
1. Compliance / data residency
2. Latency to users
3. Service and feature availability
4. Price

## Key exam points
- High availability → **multi-AZ** (cheaper and the default answer). Region-level DR, global latency or regulatory reasons → **multi-Region**.
- An EBS volume is tied to **one AZ**. To move it, take a snapshot and create a new volume in the target AZ.
- A subnet sits in one AZ; a VPC spans all AZs in its Region.
- IAM is global; S3 bucket names are global, but every bucket lives in one Region.
- AZ names (`us-east-1a`) differ between accounts; AZ IDs (`use1-az1`) do not.
- Words like "data residency" or "sovereignty" point to the choice of Region.

## Typical multi-AZ web tier
ALB → Auto Scaling group with instances in subnets across ≥ 2 AZs → each instance has its **own** EBS volume.
Shared data goes in a Regional or Multi-AZ service (RDS Multi-AZ, EFS, S3), not in an EBS volume.

## Knowledge check result
- Correct: found the single point of failure, chose multi-AZ inside Australia, and explained why multi-Region is mainly for DR.
- Gap: thought one EBS volume could be placed "on multiple AZs", and left out the load balancer and Auto Scaling group.
