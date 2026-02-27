
---

## Approach

### Step 1 – Baseline Architecture Definition
Since no specific on-premises architecture was provided, a 
realistic two-tier baseline was defined: a single web server 
and a single database server, both running in one location 
with no redundancy, no backups, no encryption, open network 
access, and manual operations. This baseline is detailed in 
Task 1 of the report.

### Step 2 – WAF Assessment
Each of the five WAF pillars was applied to the baseline 
architecture to identify one strength and one weakness per 
pillar. A specific AWS service or feature was recommended 
to address each weakness. Findings are presented in a 
structured table followed by detailed reasoning for each 
pillar.

### Step 3 – CAF Readiness Assessment
Each of the six CAF perspectives was used to assess the 
organization's readiness for migration. Each perspective 
summary identifies the current state and the actions needed 
before or during migration. Summaries are approximately 
150–200 words each.

### Step 4 – Improved Architecture Design
A revised AWS architecture was designed to address all 
weaknesses identified in Tasks 1 and 2. The design was 
documented in writing and visualized as a diagram using 
Lucidchart. The architecture covers networking, compute, 
caching, database, security, monitoring, and deployment 
automation.

---

## Key AWS Services Used in the Revised Architecture

| Layer | AWS Service | Purpose |
|---|---|---|
| DNS | Amazon Route 53 | Domain resolution and health routing |
| CDN | Amazon CloudFront | Edge caching and static asset delivery |
| Storage | Amazon S3 | Static asset storage |
| Security | AWS WAF | Web traffic filtering |
| Load Balancing | Application Load Balancer | Traffic distribution and health checks |
| Compute | Amazon EC2 + Auto Scaling | Web tier with automatic scaling |
| Caching | Amazon ElastiCache (Redis) | Database read offloading |
| Database | Amazon RDS Multi-AZ | Managed database with automatic failover |
| Encryption | AWS KMS | Encryption key management |
| Secrets | AWS Secrets Manager | Secure credential storage and rotation |
| Monitoring | Amazon CloudWatch | Metrics, logs, and alarms |
| Audit | AWS CloudTrail | API activity logging |
| Threat Detection | Amazon GuardDuty | Continuous threat monitoring |
| Backup | AWS Backup | Automated backup policies |
| Deployment | AWS CodePipeline | CI/CD pipeline automation |
| Infrastructure | AWS CloudFormation | Infrastructure as code |
| Access | AWS Systems Manager | Shell access without open SSH ports |
| Cost | AWS Budgets + Cost Explorer | Spending visibility and alerts |

---

## WAF Pillars Summary

| Pillar | Primary Improvement | Key Service |
|---|---|---|
| Operational Excellence | CI/CD pipeline and infrastructure as code | CodePipeline, CloudFormation |
| Security | Private subnets, IAM roles, encryption, audit logging | IAM, KMS, CloudTrail, WAF |
| Reliability | Multi-AZ deployment and automated backups | RDS Multi-AZ, Auto Scaling, AWS Backup |
| Performance Efficiency | Caching layer and CDN for static assets | ElastiCache, CloudFront |
| Cost Optimization | Auto scaling and cost visibility tooling | Auto Scaling, AWS Budgets |

---

## CAF Perspectives Summary

| Perspective | Key Action |
|---|---|
| Business | Define a migration business case with measurable outcomes |
| People | Identify skill gaps and implement AWS training paths |
| Governance | Establish tagging standards, account structure, and budget controls |
| Platform | Externalize configuration, adopt managed services, define IaC |
| Security | Apply least-privilege IAM, enable encryption, activate GuardDuty |
| Operations | Configure monitoring baselines, write runbooks, define RTO and RPO |

---

## Architecture Diagram

The diagram covers the following layers flowing top to bottom:

1. User entry through Route 53 and CloudFront
2. AWS WAF filtering traffic before the load balancer
3. Application Load Balancer distributing traffic across two AZs
4. EC2 Auto Scaling Group in private subnets
5. ElastiCache Redis caching layer
6. RDS Multi-AZ database in isolated private subnets
7. Supporting operations and security services

---

## Frameworks Referenced

- [AWS Well-Architected Framework](https://aws.amazon.com/architecture/well-architected/)
- [AWS Cloud Adoption Framework](https://aws.amazon.com/cloud/cloud-adoption-framework/)
- [AWS Architecture Center](https://aws.amazon.com/architecture/)

---

## Submission

Submitted in partial fulfillment of the AmaliTech Cloud Engineering 
lab requirement:

**Lab Title:** Design and Evaluate an AWS Solution Using the 
Well-Architected and Cloud Adoption Frameworks



