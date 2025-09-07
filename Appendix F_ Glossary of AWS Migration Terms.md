<img src="https://r2cdn.perplexity.ai/pplx-full-logo-primary-dark%402x.png" style="height:64px;margin-right:32px"/>

# Appendix F: Glossary of AWS Migration Terms

*Comprehensive Reference Guide for AWS Migration Terminology*

This glossary provides clear definitions of key terms, acronyms, and concepts used throughout AWS cloud migrations. Definitions are based on AWS official documentation, industry best practices, and practical usage in enterprise migrations.

***

## Numbers

### 7 Rs

Seven common migration strategies for moving applications to the cloud, as defined by AWS:[^1][^3][^5]

- **Retire** - Decommission applications no longer needed
- **Retain** - Keep applications in source environment
- **Rehost** - Lift-and-shift to cloud without changes
- **Relocate** - Hypervisor-level lift-and-shift (e.g., VMware to VMware Cloud on AWS)
- **Replatform** - Lift-and-reshape with cloud optimizations
- **Repurchase** - Replace with SaaS solutions
- **Refactor** - Re-architect for cloud-native capabilities

***

## A

### Application Discovery Service (ADS)

AWS service that helps discover on-premises servers and their dependencies to plan migrations. Provides automated discovery through agents or agentless methods.

### Application Load Balancer (ALB)

Layer 7 load balancer that distributes incoming application traffic across multiple targets (EC2 instances, containers, IP addresses) in multiple Availability Zones.

### Application Migration Service (AWS MGN)

AWS service that automates lift-and-shift migrations by replicating source servers to AWS and enabling cutover with minimal downtime. Previously known as CloudEndure Migration.

### Assessment

The first phase of AWS migration methodology focused on evaluating current state, building business case, and planning migration approach.[^3]

### Auto Scaling

AWS capability that automatically adjusts the number of EC2 instances in response to changing demand patterns to maintain performance and optimize costs.

### Availability Zone (AZ)

Isolated data center locations within an AWS Region, designed to provide fault isolation and high availability for applications.

***

## B

### Business Case

Financial and strategic justification for cloud migration, typically including total cost of ownership (TCO) analysis, ROI projections, and business benefits quantification.

### Backup Window

Scheduled time period during which automated backups are performed, typically during low-activity hours to minimize performance impact.

***

## C

### Cloud Adoption Framework (CAF)

AWS methodology that provides guidance across six perspectives (Business, People, Governance, Platform, Security, Operations) to accelerate cloud adoption.

### CloudFormation

AWS infrastructure-as-code service that allows provisioning and managing AWS resources using templates written in JSON or YAML.

### CloudTrail

AWS service that records API calls and provides audit trails for compliance, security analysis, and operational troubleshooting.

### CloudWatch

AWS monitoring and observability service that collects metrics, logs, and events from AWS resources and applications.

### Cold Data

Infrequently accessed data that can be stored on lower-performance, lower-cost storage tiers such as Amazon S3 Glacier.

### Cutover

The process of switching from source systems to migrated systems in AWS, marking the completion of the migration for specific applications.

***

## D

### Database Migration Service (DMS)

AWS service that migrates databases to AWS with minimal downtime, supporting both homogeneous and heterogeneous migrations.[^2][^10]

### Data Transfer Service

Various AWS services for moving large amounts of data, including AWS DataSync, AWS Snowball family, and AWS Direct Connect.

### Direct Connect

Dedicated network connection between on-premises and AWS that provides consistent bandwidth and lower latency than internet connections.

### Discovery

Process of inventorying existing IT assets, understanding dependencies, and gathering information needed for migration planning.

***

## E

### Elastic Block Store (EBS)

High-performance block storage service for EC2 instances, providing persistent storage that persists independently of instance lifecycle.

### Elastic Compute Cloud (EC2)

AWS compute service that provides resizable virtual servers (instances) in the cloud with various instance types optimized for different use cases.

### Elastic File System (EFS)

Fully managed NFS file system that can be mounted on multiple EC2 instances simultaneously, providing shared storage.

### Elastic Load Balancer (ELB)

AWS service that automatically distributes incoming traffic across multiple targets to ensure high availability and fault tolerance.

***

## F

### Fargate

Serverless compute engine for containers that removes the need to provision and manage servers, allowing focus on application design.

### FSx

Fully managed file systems optimized for specific workloads, including FSx for Windows File Server, FSx for Lustre, and FSx for NetApp ONTAP.

***

## G

### GuardDuty

AWS threat detection service that uses machine learning to identify malicious activity and unauthorized behavior in AWS accounts.

***

## H

### Heterogeneous Database Migration

Migrating between different database engines (e.g., Oracle to PostgreSQL), typically requiring schema conversion.[^1]

### High Availability (HA)

System design that ensures continuous operation with minimal downtime through redundancy and failover mechanisms.[^1]

### Homogeneous Database Migration

Migrating between the same database engines (e.g., MySQL to MySQL), typically simpler than heterogeneous migrations.[^1]

### Hot Data

Frequently accessed data requiring high-performance storage tiers for fast query responses.[^1]

### Hybrid Cloud

Computing environment that combines on-premises infrastructure with cloud services, often used during migration transitions.

### Hypercare Period

Intensive monitoring and support period immediately following migration cutover, typically lasting 1-4 days.[^1]

***

## I

### Identity and Access Management (IAM)

AWS service for managing users, groups, roles, and permissions to control access to AWS resources securely.

### Infrastructure as Code (IaC)

Practice of managing and provisioning infrastructure through machine-readable configuration files rather than manual processes.

### Instance

Virtual server in Amazon EC2, available in various types optimized for different use cases (compute, memory, storage, networking).

***

## K

### Key Management Service (KMS)

AWS service for creating and managing encryption keys used to encrypt data across AWS services and applications.

***

## L

### Lambda

AWS serverless compute service that runs code in response to events without managing servers, paying only for compute time consumed.

### Landing Zone

Well-architected, multi-account AWS environment that serves as a foundation for deploying workloads and applications securely.

### Lift and Shift

See Rehost - migrating applications to cloud without significant changes to take advantage of cloud infrastructure.

***

## M

### Migration Acceleration Program (MAP)

AWS program providing consulting support, training, and services to help organizations migrate to cloud with proven methodologies.[^3][^1]

### Migration Factory

Cross-functional teams that streamline migration through automated, agile approaches, typically handling 20-50% of applications with repeated patterns.[^1]

### Migration Hub

AWS service providing a single location to track migration tasks across multiple AWS tools and partner solutions.[^4][^1]

### Migration Pattern

Repeatable migration task detailing strategy, destination, and tools/services used for specific types of applications.[^1]

### Migration Portfolio Assessment (MPA)

Online tool providing detailed portfolio assessment including server right-sizing, pricing, TCO analysis, and wave planning.[^1]

### Migration Readiness Assessment (MRA)

Process of evaluating organization's cloud readiness using AWS CAF, identifying strengths/weaknesses and building action plans.[^1]

### Migration Strategy

Approach used to migrate workloads to AWS Cloud, typically one of the 7 Rs migration strategies.[^1]

### Migration Wave

Grouping of applications migrated together based on dependencies, complexity, risk, and resource availability.

### Mobilize

Second phase of AWS migration methodology focused on building foundation, capabilities, and operating model for migration.[^3]

### Modernize

Process of updating applications to take advantage of cloud-native capabilities, often part of the migration and modernize phase.

***

## N

### Network Load Balancer (NLB)

Layer 4 load balancer that distributes traffic based on network protocols, providing ultra-high performance and static IP addresses.

***

## O

### Offline Migration

Migration method requiring source workload downtime during the process, typically used for non-critical applications.[^1]

### Online Migration

Migration method allowing source workload to remain operational during migration, minimizing or eliminating downtime.[^1]

### Operational Readiness Review (ORR)

Checklist and best practices to evaluate, prevent, or reduce scope of incidents and failures in migrated environments.[^1]

***

## P

### Pilot Migration

Small-scale migration of selected applications to validate processes, tools, and approaches before full-scale migration.

***

## R

### RDS (Relational Database Service)

AWS managed database service supporting multiple database engines (MySQL, PostgreSQL, Oracle, SQL Server, MariaDB).

### Refactor/Re-architect

Migration strategy involving significant code and architecture changes to take full advantage of cloud-native features.[^5][^3][^1]

### Region

Geographic area containing multiple isolated Availability Zones, allowing deployment of applications across multiple data centers.

### Rehost (Lift and Shift)

Migration strategy moving applications to cloud without changes, typically the fastest migration approach.[^5][^3][^1]

### Relocate (Hypervisor-level Lift and Shift)

Migration strategy for moving infrastructure without purchasing new hardware or rewriting applications, such as VMware to VMware Cloud on AWS.[^5][^3][^1]

### Replatform (Lift, Tinker, and Shift)

Migration strategy involving application migration with some cloud optimization without changing core architecture.[^3][^5][^1]

### Repurchase (Drop and Shop)

Migration strategy replacing applications with SaaS alternatives or different product versions.[^5][^3][^1]

### Reserved Instances (RI)

Purchasing model providing significant discounts compared to On-Demand pricing in exchange for capacity reservations.

### Retain (Revisit)

Migration strategy keeping applications in source environment, typically for applications requiring major refactoring or having no business justification for migration.[^3][^5][^1]

### Retire

Migration strategy involving decommissioning applications no longer needed, providing immediate cost savings.[^5][^3][^1]

### Right-sizing

Process of optimizing cloud resources (compute, storage, network) to match actual workload requirements and minimize costs.

### Route 53

AWS DNS web service providing domain registration, DNS routing, and health checking for applications.

***

## S

### S3 (Simple Storage Service)

AWS object storage service offering scalability, data availability, security, and performance for various use cases.

### Schema Conversion Tool (SCT)

AWS tool that converts database schemas between different database engines for heterogeneous migrations.

### Security Hub

AWS service providing centralized security findings aggregation and compliance status across AWS accounts and services.

### Serverless

Computing model where cloud provider manages server provisioning and scaling, allowing developers to focus on application logic.

### Shared Responsibility Model

AWS security model defining which security responsibilities belong to AWS (security "of" the cloud) versus customers (security "in" the cloud).

### SnowBall

AWS physical data transfer device for moving large amounts of data to AWS when network transfer is impractical.

### Spot Instances

EC2 pricing model offering unused capacity at discounts up to 90% compared to On-Demand prices, suitable for flexible workloads.

***

## T

### Total Cost of Ownership (TCO)

Comprehensive cost calculation including direct costs, operational costs, and hidden costs over the lifecycle of IT systems.

### Transit Gateway

AWS networking service connecting VPCs and on-premises networks through a central hub, simplifying network architecture.

***

## V

### VPC (Virtual Private Cloud)

Logically isolated section of AWS cloud where resources are launched in a virtual network with full control over networking environment.

### VPN (Virtual Private Network)

Secure connection between on-premises networks and AWS VPCs, providing encrypted data transmission over internet.

***

## W

### Wave Planning

Process of organizing applications into migration groups (waves) based on dependencies, complexity, business priorities, and resource availability.

### Well-Architected Framework

AWS best practices framework across six pillars: Operational Excellence, Security, Reliability, Performance Efficiency, Cost Optimization, and Sustainability.

### Workload

Collection of resources and code that delivers business value, such as customer-facing applications or backend processes.

***

This glossary serves as a comprehensive reference for AWS migration terminology. For the most current AWS terminology and definitions, always refer to the official AWS Glossary and service-specific documentation.[^8][^2][^4][^1]

**Key Resources for Updated Terminology:**

- [AWS Prescriptive Guidance Glossary](https://docs.aws.amazon.com/prescriptive-guidance/latest/migration-retiring-applications/apg-gloss.html)[^1]
- [AWS General Glossary](https://docs.aws.amazon.com/glossary/latest/reference/glos-chap.html)[^4]
- [AWS Migration Lens Definitions](https://docs.aws.amazon.com/wellarchitected/latest/migration-lens/definitions.html)[^3]
<span style="display:none">[^6][^7][^9]</span>

<div style="text-align: center">⁂</div>

[^1]: https://docs.aws.amazon.com/prescriptive-guidance/latest/migration-retiring-applications/apg-gloss.html

[^2]: https://docs.aws.amazon.com/dms/latest/userguide/glossary.html

[^3]: https://docs.aws.amazon.com/wellarchitected/latest/migration-lens/definitions.html

[^4]: https://docs.aws.amazon.com/glossary/latest/reference/glos-chap.html

[^5]: https://www.objectstyle.com/blog/a-cloud-migration-glossary-50-essential-terms

[^6]: https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/dotnet-migrating-applications-glossary.html

[^7]: https://graduate.northeastern.edu/knowledge-hub/aws-terminology/

[^8]: https://docs.aws.amazon.com/wellarchitected/latest/migration-lens/glossary.html

[^9]: https://www.clouddefense.ai/glossary/aws

[^10]: https://docs.aws.amazon.com/dms/latest/userguide/CHAP_Introduction.html

