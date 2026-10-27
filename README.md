# AWS IAM Security Engineering Labs

### Hands-On AWS Identity & Access Management | Cloud Engineering | Cloud Security | DevSecOps

A practical collection of AWS Identity and Access Management (IAM) labs focused on designing, implementing, testing, troubleshooting, and securing AWS permissions and identities.

This repository documents hands-on experience with IAM users, groups, roles, policy evaluation, temporary credentials, least-privilege access, cross-account authentication, AWS Organizations, workload identities, auditing, and infrastructure as code.

The goal is to build the practical IAM skills required for Cloud Engineer, Cloud Security Engineer, DevOps Engineer, and Infrastructure Engineer roles.

---

## Objectives

- Understand AWS IAM from beginner to advanced levels.
- Write and troubleshoot JSON-based IAM policies.
- Implement secure identity and access management.
- Apply the principle of least privilege.
- Configure IAM roles for AWS workloads.
- Understand authentication and authorization.
- Implement secure cross-account access.
- Use temporary credentials through AWS STS.
- Apply IAM permission boundaries, conditions, and organizational guardrails.
- Secure CI/CD authentication using GitHub Actions OIDC.
- Audit IAM activities and investigate access issues.
- Automate IAM infrastructure using Terraform.
- Recognize and mitigate common IAM security misconfigurations.

---

## Technologies and Tools

| Technology | Purpose |
|---|---|
| AWS IAM | Identity and permission management |
| AWS CLI | Command-line AWS administration |
| AWS STS | Temporary security credentials |
| AWS EC2 | Instance roles and profiles |
| AWS Lambda | Serverless execution roles |
| Amazon S3 | Resource-based policies |
| AWS Organizations | Organizational security guardrails |
| IAM Identity Center | Centralized workforce access |
| AWS KMS | Encryption access control |
| IAM Access Analyzer | Permission and external access analysis |
| AWS CloudTrail | API activity auditing |
| Terraform | Infrastructure as Code |
| GitHub Actions | OIDC-based CI/CD authentication |
| Amazon ECS/EKS | Container workload IAM |

---

## Lab Roadmap

### Phase 1 — IAM Fundamentals

| Lab | Topic | Status |
|---|---|---|
| 01 | IAM Users, Groups, and Custom Policies | Planned |
| 02 | IAM Policy Evaluation and Explicit Deny | Planned |
| 03 | AWS CLI Profiles and STS | Planned |

### Phase 2 — IAM for Cloud Workloads

| Lab | Topic | Status |
|---|---|---|
| 04 | EC2 IAM Roles and Secure S3 Access | Planned |
| 05 | Lambda Execution Roles | Planned |
| 06 | S3 Bucket Policies and Resource-Based Access | Planned |
| 07 | IAM Conditions and MFA Restrictions | Planned |

### Phase 3 — Advanced Access Control

| Lab | Topic | Status |
|---|---|---|
| 08 | IAM Permissions Boundaries | Planned |
| 09 | Cross-Account IAM Role Assumption | Planned |
| 10 | Attribute-Based Access Control (ABAC) | Planned |
| 11 | AWS Organizations and SCP Guardrails | Planned |

### Phase 4 — Identity Security and Monitoring

| Lab | Topic | Status |
|---|---|---|
| 12 | GitHub Actions OIDC Federation | Planned |
| 13 | ECS and EKS Workload IAM | Planned |
| 14 | IAM Auditing, Access Analyzer, and CloudTrail | Planned |
| 15 | IAM Privilege Escalation Defense | Planned |

### Phase 5 — Production IAM Automation

| Lab | Topic | Status |
|---|---|---|
| 16 | Production IAM Architecture with Terraform | Planned |

---

## Lab Methodology

Each lab follows a consistent engineering workflow.

### 1. Understand the Problem

Identify the IAM requirement, its business purpose, and the associated security risks.

### 2. Design the Solution

Determine the required identities, roles, permissions, trust relationships, and AWS resources.

### 3. Implement the Configuration

Use the AWS Management Console, AWS CLI, IAM JSON policies, and Terraform where appropriate.

### 4. Verify Permissions

Test expected allowed and denied operations using suitable AWS CLI commands, policy simulation, or controlled API requests.

### 5. Troubleshoot

Reproduce IAM permission errors and investigate their causes.

Examples include:

- Missing IAM permissions
- Incorrect resource ARNs
- Invalid trust policies
- Explicit Deny restrictions
- Missing role-assumption permissions
- Resource-policy conflicts
- Expired STS credentials
- Incorrect AWS CLI profiles

### 6. Apply Security Remediation

Correct the configuration while maintaining least-privilege access.

### 7. Document the Results

Each completed lab includes:

- Lab objective
- Architecture or access-flow diagram
- AWS services used
- Prerequisites
- Implementation steps
- JSON, CLI, or Terraform configuration
- Verification commands
- Troubleshooting scenarios
- Root cause and remediation
- Screenshots or sanitized command output
- Security best practices
- Cleanup instructions
- Key lessons learned

---

## IAM Security Principles

### Principle of Least Privilege

Grant only the permissions necessary to perform a specific task.

### Default Deny

AWS permissions start from an implicit deny. Access requires an applicable Allow and must not be blocked by an applicable explicit Deny or other authorization limits.

### Temporary Credentials

Prefer IAM roles and AWS STS temporary credentials instead of long-lived access keys.

### Separation of Duties

Use different roles and permission sets for development, operations, security, and administration.

### Defense in Depth

Combine IAM policies with resource policies, organizational guardrails, monitoring, and encryption controls.

### Continuous Auditing

Review permissions, monitor sensitive IAM activity, and investigate unusual authorization patterns.

---

## Example IAM Policy

The following policy grants read access to objects in one S3 bucket.

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "AllowReadObjects",
      "Effect": "Allow",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::example-secure-bucket/*"
    }
  ]
}
```

This policy does not grant permission to upload, overwrite, or delete objects.

The effective access also depends on other applicable AWS authorization controls.

---

## Security Troubleshooting Examples

| Problem | Investigation Area |
|---|---|
| EC2 cannot access S3 | IAM role, instance profile, S3 permissions |
| Lambda receives AccessDenied | Execution role, resource ARN, applicable policies |
| STS AssumeRole fails | Trust policy, caller permissions, organizational restrictions |
| S3 access is denied | Identity policy, bucket policy, encryption requirements |
| Developer has excessive permissions | Policy scope, wildcards, least privilege |
| GitHub Actions cannot deploy | OIDC configuration, trust conditions, role permissions |
| EKS workload cannot access AWS | Pod Identity/IRSA, trust relationship, role permissions |
| Terraform receives AccessDenied | Active identity, IAM permissions, boundary or SCP |

---

## Security Considerations

All labs should be executed only in AWS accounts and environments where testing is authorized.

- Never commit AWS access keys, secret keys, or session tokens.
- Never publish sensitive account information or private infrastructure details.
- Use placeholder account IDs and resource names in documentation.
- Avoid broad administrator permissions unless explicitly necessary.
- Perform security experiments in isolated lab environments.
- Validate all policies before deploying them.
- Review IAM permissions regularly.
- Remove temporary resources after completing each lab.
- Monitor potential AWS charges, especially for EC2, networking, container, and logging resources.

---

## Expected Learning Outcomes

After completing the repository, the learner should be able to:

1. Design IAM access for cloud applications and infrastructure.
2. Create least-privilege IAM policies.
3. Configure trusted role-assumption workflows.
4. Troubleshoot common AWS authorization failures.
5. Implement temporary access for CI/CD and AWS workloads.
6. Apply resource-based access controls and organizational guardrails.
7. Audit IAM permissions and API activity.
8. Manage IAM resources using Terraform.
9. Identify and remediate common IAM security risks.
10. Explain IAM architecture and permission decisions in technical interviews.

---

## Official AWS Documentation

- [AWS IAM User Guide](https://docs.aws.amazon.com/IAM/latest/UserGuide/introduction.html)
- [IAM JSON Policy Reference](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies.html)
- [IAM Policy Evaluation Logic](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_evaluation-logic.html)
- [AWS STS Documentation](https://docs.aws.amazon.com/STS/latest/APIReference/welcome.html)
- [IAM Access Analyzer](https://docs.aws.amazon.com/IAM/latest/UserGuide/what-is-access-analyzer.html)
- [Terraform AWS Provider](https://registry.terraform.io/providers/hashicorp/aws/latest/docs)

---

## Repository Progress

**Completed Labs:** 0 / 16

This repository is being developed through hands-on AWS IAM security engineering practice. Each lab will be documented after its implementation and verification.

---

## Disclaimer

This repository is intended for educational and authorized security engineering practice. Example policies and configurations must be reviewed and adapted before use in production AWS environments.
