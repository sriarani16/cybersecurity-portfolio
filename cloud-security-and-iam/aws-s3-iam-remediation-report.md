# AWS Cloud Posture Audit & IAM Hardening Case Study

## Overview
Evaluated an AWS environment (`us-east-1`) using **Prowler** and **AWS CloudTrail** to identify misconfigurations across storage, networking, databases, compute, and identity controls, then remediated high-risk S3 exposure and identity weaknesses.

## Key Findings & Risk Themes
- **Storage Exposure & Governance:** Publicly accessible S3 bucket configuration (`1669381-sriarani`), missing account-level Block Public Access, cross-account policy exposure, and lack of access logging, MFA Delete, or transport security enforcement.
- **Identity & Access Control:** Root account lacking MFA and holding an active access key, alongside overly broad IAM access patterns.
- **Network, Compute & Database Hardening Gaps:** Unprotected public-facing/SSH exposure, missing firewall/subnet segmentation controls, IMDSv1 availability, and default encryption or missing backup/recovery protections on DynamoDB.

## Remediation Actions & Verification
1. **S3 Lockdown:** Enabled account/bucket Block Public Access, enforced bucket-owner object ownership (disabling ACLs), and replaced permissive bucket access with least-privilege controls.
2. **Least-Privilege IAM & Cross-Account Access:** Applied read-only IAM policies for individual users (`s3:ListBucket`, `s3:GetObject` on the target bucket/prefix) and configured a cross-account IAM role (`ReadOnlyS3AccessRole`) with `sts:AssumeRole` trust scoped to a trusted external AWS account.
3. **Root MFA & Audit Trail:** Enabled MFA on the root account and verified administrative and access events in CloudTrail alongside post-remediation Prowler checks and access denial testing on unauthorized actions.
