# Appendix D: Cost Estimation Worksheets by Migration Type

*Practical Worksheets and Methodologies for Accurate Migration Planning*

This appendix provides structured worksheets, calculators, and formulas to estimate AWS migration costs for each migration strategy. These templates are informed by AWS's own tools, prescriptive financial guidance, and best-practice review of real migration cost drivers.

***

## Overview of AWS Cost Estimation Tools

- **AWS Pricing Calculator**: AWS's primary tool for building detailed cost estimates across all major services, supporting bulk import via Excel for large-scale migrations and scenario analysis.
- **Migration Evaluator**: Complimentary to qualified customers, this tool inventories your environment and builds a data-driven cloud business case, including TCO and monthly/annual cost projections.
- **AWS Migration Hub**: Lets you track migration progress for free; pay only for migration tooling and provisioned AWS resources.[^7]
- **Manual Worksheets**: For custom needs or offline analysis, structured spreadsheet templates (see below) facilitate detailed estimation and aggregation.

***

## 1. Lift-and-Shift (Rehost) Cost Estimation Worksheet

| Cost Element | Input Example | Notes |
| :-- | :-- | :-- |
| EC2 Instances | \#, type, region | Use AWS Pricing Calculator for instance cost |
| EBS Volumes | \#, type, size | Account for provisioned IOPS or throughput |
| Data Transfer | Out to Internet/AWS Regions | Include peak vs. baseline estimates |
| Migration Tooling | AWS MGN (per server, per month) | Free for first 90 days, then paid per server |
| Support Plan | % of monthly AWS usage | Optional; for business/enterprise support |
| Parallel Run (Dual Ops) | \# months kept on-prem running | Overlap period, adds to overall cost |
| One-Time Migration Effort | Staff/Consultant hours | Labor costs, downtime mitigation |

**Example Calculation:**

- 20 m5.large EC2 instances, 2 TB EBS, AWS MGN for 2 months, standard data transfer.
- Use AWS Pricing Calculator's bulk import template for EC2/EBS.

***

## 2. Managed Service Migration (Replatform) Cost Estimation Worksheet

| Cost Element | Input Example | Notes |
| :-- | :-- | :-- |
| RDS/Aurora Instance | Engine, type, storage, features | Multi-AZ and backups increase cost |
| Elastic Beanstalk/ECS | \# environments and instance specs | Fargate/serverless pricing if used |
| Lambda Invocations | Requests, duration | Estimate baseline and peak usage |
| S3/EFS/FSx Storage | Volume, access frequency | Use proper storage class for optimal cost |
| Refactoring Effort | Staff hours, consulting | Professional services, code adaptation |
| Testing + Cutover | % of project time | Contingency buffer for validation |


***

## 3. SaaS/Repurchase Cost Worksheet

| Cost Element | Input Example | Notes |
| :-- | :-- | :-- |
| SaaS License Fees | Per user/month fees | Marketplace integration may affect billing |
| Data Migration/ETL | One-time cost (per GB or project) | Data extraction, validation effort |
| Support + Setup Fees | One-time or monthly | Implementation and training |
| Integration/Connectors | Middleware, APIs, lambda invocations | Ongoing or one-time, based on business flows |
| Legacy System Wind-down | \# months before full decommission | Maintaining old licenses, infra during overlap |


***

## 4. Refactor/Microservices Migration Worksheet

| Cost Element | Input Example | Notes |
| :-- | :-- | :-- |
| Lambda/API Gateway | Requests, execution duration, API calls | Per-GB-second, free tier available |
| EKS/ECS Fargate | vCPU, memory hours, clusters | Based on anticipated scaling and usage |
| DynamoDB/S3/Other Services | Capacity units or usage per month | Include backups and cross-region costs |
| Dev + Re-architecture | Team hours, consulting | More engineering cost for full refactor |
| Testing, CI/CD | Tool subscriptions, staff time | Integration into new pipeline |
| Ongoing Optimization | Rightsizing, monitoring tool costs | Cost saves with autoscaling, spot usage |


***

## 5. Hybrid/Retain Worksheet

| Cost Element | Input Example | Notes |
| :-- | :-- | :-- |
| VPN/Direct Connect/Storage Gateway | Monthly service cost, setup | Hybrid connectivity charges[^2] |
| Systems Manager/CloudWatch | Per server or metric monitored | Some features free, others metered |
| Ongoing On-Premises Ops | Maintain local infra, support, licenses | Account for both environments |


***

## Sample Generic Migration Cost Estimation Table

| Cost Area | Rehost | Replatform | Repurchase | Refactor | Retain | Retire |
| :-- | :-- | :-- | :-- | :-- | :-- | :-- |
| Compute (EC2, Lambda) | Moderate-High | Moderate | Usually N/A | Moderate-High | N/A (on-prem) | N/A |
| Storage (EBS, S3, DB) | Moderate | Moderate-Low | N/A | Low-High | N/A (on-prem) | N/A |
| Network/Data Transfer | Variable | Variable | Low | Moderate | N/A | N/A |
| License/SaaS Fees | No change | May drop | Increase | May drop | No change | Eliminated |
| Migration Tooling | Moderate | Low | Low | Moderate | None | None |
| Labor/Consulting | Low-Moderate | Moderate | Setup only | High | None | Low |
| Dual-Run (Overlap) | Yes | Maybe | Maybe | Often | No | No |


***

## Tips and Resources

- **Bulk import via AWS Pricing Calculator Excel Template**: For large migrations, download/import your server and storage inventory directly for automated calculations—Excel templates available.
- **Migration Evaluator**: Request AWS's free business case analysis to receive a customized TCO workbook.
- **Consult AWS Documentation**: For up-to-date price points and scenario walkthroughs, reference the AWS Pricing Calculator user guide and example estimates.
- **Service-Specific Price Pages**: Always verify with published AWS service pricing as underlying costs or tiers may change (e.g., EC2, RDS, Lambda, S3).

***

These worksheets and templates form a starting point. For major efforts, combine with AWS's automated tools and periodically update your assumptions as real cloud usage patterns emerge. For downloadable templates and up-to-date calculators, visit the AWS Pricing Calculator page or request the Migration Evaluator service for personalized guidance.




