# AWS Migration

A practical toolkit and reference for planning, executing, and automating migrations to AWS across common patterns: rehost (lift-and-shift), replatform, and selective modernization. It is designed to help bootstrap migration projects with reproducible scripts, recommended folder structure, and step-by-step runbooks.

## Table of Contents

- Overview
- Features
- Repository Structure
- Prerequisites
- Quick Start
- Usage
- Configuration
- Architecture
- Migration Runbooks
- Testing
- Troubleshooting
- Roadmap
- Contributing
- License
- Acknowledgments


## Overview

This repository provides scripts, templates, and guidance to accelerate workload migration into AWS, including examples for AWS Application Migration Service (MGN), Database Migration Service (DMS), and containerization paths. It also includes opinionated CSV-driven automation patterns for configuring EC2 launch templates during rehost migrations.

## Features

- Rehost automation scaffolding using AWS MGN with CSV import of launch settings and templates.
- Replatform examples and references for Elastic Beanstalk and DMS-based database moves.
- Modernization pointers to containerization on Amazon ECS as a post-migration step.
- Standardized README-driven documentation approach for easier adoption and contributions.


## Repository Structure

- /scripts: Helper scripts for discovery, CSV prep, and AWS service automation.
- /runbooks: Step-by-step guides for rehost, replatform, and modernization phases.
- /templates: Sample CSVs, parameter files, and policy templates.
- /docs: Additional notes, diagrams, and architectural guidance.
- /examples: Optional example workloads and environment stubs.

This structure is based on patterns seen in AWS migration workshops and sample repos for clarity and reuse.

## Prerequisites

- AWS account with appropriate permissions for MGN, DMS, EC2, IAM, and networking.
- AWS CLI v2 installed and configured with a default region and credentials.
- Python 3.9+ for CSV-driven automation scripts described in the MGN launch template workflow.
- Network access and security group allowances for replication and cutover activities.


## Quick Start

1) Clone the repository:
git clone https://github.com/manishpcp/aws-migration.git
cd aws-migration

2) Review templates/sample_template.csv to understand the flat-file format for configuring MGN launch settings and EC2 Launch Templates at scale.
3) Configure AWS CLI and environment variables for the target account and region:
aws configure
export AWS_REGION=us-east-1

4) Dry run a CSV validation helper script (if included in /scripts) to confirm format compliance before updates.

## Usage

- Rehost (Lift-and-Shift) with AWS MGN:
    - Prepare a flat CSV from discovery outputs (CMDB or assessment tools) using templates/sample_template.csv.
    - Run the import script to apply General Launch Settings and EC2 Launch Template parameters for each source machine.
    - Validate target configuration and proceed through test and cutover waves as per runbooks.
- Replatform:
    - Web/app tiers: use Elastic Beanstalk for quick environment provisioning and deployment.
    - Databases: use AWS DMS for homogeneous or heterogeneous migration to managed engines.
- Modernize:
    - Containerize suitable services and deploy to Amazon ECS as a phased modernization after landing in AWS.

These workflows align to assess, mobilize, migrate, and modernize phases commonly used in AWS migration programs.

## Configuration

- CSV format rules:
    - Use device index prefixes to map subnets and security groups to NICs, e.g.:
        - Subnet column: 0:subnet-xxxxxxxx,1:subnet-yyyyyyyy
        - Security Group column: 0:sg-xxxxxxxx,1:sg-yyyyyyy
    - Ensure all required columns match the script’s expected headers.
- Store environment-specific parameters (VPC IDs, subnets, SGs, KMS, roles) in a param file or CI/CD secrets vault per environment.


## Architecture

Typical migration reference architecture includes:

- Source environment discovery feeding a CSV inventory.
- AWS MGN for replication and launch configuration.
- Optional EventBridge/Lambda automation patterns and parameter management via SSM/Secrets, as seen in AWS integration examples.
- Post-migration replatform or modernization with Elastic Beanstalk, DMS, and ECS as needed.

Diagrams and detailed flows can be added under /docs as the repository evolves.

## Migration Runbooks

- Rehost Runbook: Assess inventory, prepare CSV, configure MGN replication, validate target templates, test, then cut over by wave.
- Replatform Runbook: Identify quick wins to managed services (Beanstalk, DMS), validate functional and performance baselines before cutover.
- Modernization Runbook: Containerize suitable components and shift to ECS while leveraging existing VPC, security, and observability baselines.

Runbooks mirror the approach from public AWS migration workshops and can be adapted to project-specific SLAs and controls.

## Testing

- Validate CSV formatting with a linter or pre-commit hook to catch schema drift.
- Use non-production waves for launch template verification before production cutovers.
- Incorporate unit tests for any Python utilities under /scripts with fixtures for sample CSVs.


## Troubleshooting

- Launch template mismatches: check device index mapping and ensure subnets/SGs exist in the target region/account.
- Permissions errors: verify IAM roles and least-privilege policies for MGN, EC2, DMS, and supporting services.
- API throttling: introduce backoff/retry in bulk import scripts and stagger large waves.


## Roadmap

- Add opinionated Terraform/CDK samples for landing zones and baseline networking.
- Include DMS task templates for common source/target pairs.
- Provide example modernization blueprints for ECS on Fargate.


## Contributing

Contributions are welcome. Please open issues for bugs or enhancements, and include clear descriptions and reproduction steps. For pull requests, follow conventional commits and include tests where applicable. See examples in AWS sample repos for phrasing and contribution language.

By submitting a pull request, confirm the right to use, modify, copy, and redistribute your contribution under the selected license.

## License

Choose an appropriate open-source license (e.g., MIT, Apache-2.0) and add a LICENSE file at the root. For guidance, see choosealicense.com and GitHub’s repository best practices.

## Acknowledgments

- Inspired by AWS Application Migration workshops and associated resources that demonstrate rehost, replatform, and modernization paths.
- CSV-driven MGN configuration patterns informed by AWS blog guidance for managing EC2 Launch Templates at scale.
- General README guidance adapted from community best practices.



