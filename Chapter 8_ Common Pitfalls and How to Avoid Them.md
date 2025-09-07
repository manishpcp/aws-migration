# Chapter 8: Common Pitfalls and How to Avoid Them

*Lessons Learned from the Field*

After thirty large-scale migrations, I noticed that almost every failure story had already been written—by someone else, at another company, sometimes years earlier. The most expensive migration mistakes are almost always avoidable.

Experienced teams know that recognizing and pre-empting common pitfalls is “cheap insurance” for migration success. This chapter compiles the patterns, failure points, and recovery techniques I’ve seen most often—plus the battle-hardened solutions that separate “cloud survivors” from “cloud scalers.”

***

## Strategy-Specific Challenges: The 12 Most Common Migration Pitfalls (and Solutions)

| **Pitfall** | **Description** | **Solution** |
| :-- | :-- | :-- |
| **1. Incomplete Discovery** | Hidden servers/dependencies cause failures during cutover. | Automated discovery with AWS ADS; dependency mapping; peer review. |
| **2. Underestimating Data Transfer** | Long transfer windows, failing to account for data size or change rate. | Use AWS DataSync, S3 Transfer Acceleration, plan for delta sync. |
| **3. Over-Reliance on Rehost** | Lift-and-shift chosen for all, leading to cloud inefficiency and higher cost. | Portfolio analysis; apply the right “R” to each workload. |
| **4. Ignoring Refactor Complexity** | Scope creep and failing to estimate rearchitecture effort. | Use pilots, stage delivery, strict backlog management. |
| **5. Configuration Drift** | Manual changes after migration break repeatability and IaC hygiene. | Guardrails, automated drift detection with AWS Config, IaC only. |
| **6. Security Gaps During Transition** | Old security practices don’t map to cloud, leaving exposures. | Re-baseline security controls with AWS Security Hub, IAM reviews. |
| **7. Compliance Blind Spots** | Regulatory controls missed (e.g., data residency, audit logs). | Automate compliance checks; enable AWS Config, CloudTrail, GuardDuty |
| **8. Missed Inter-App Dependencies** | Apps migrated out of order, breaking integrations. | Dependency mapping via ADS, Application Portfolio Management. |
| **9. Lack of Performance Baseline** | No before/after measurements, leading to user dissatisfaction. | Run pre/post-migration load tests; CloudWatch dashboards. |
| **10. Resource Shortfalls** | Teams spread too thin; skills/availability underestimated. | Realistic wave planning; train backups; use partners as force-multiplier. |
| **11. Inadequate Runbooks \& Testing** | Cutover steps improvised or untested. | Drill migrations; “game days”; runbook sign-off. |
| **12. Weak Post-Migration Monitoring** | Issues go undetected after go-live. | Automated CloudWatch/GuardDuty alerting and dashboarding. |


***

### Refactor Complexity Management for Large Migrations

**Why it hurts:** Refactor projects dominate migration cost overruns due to “unknown unknowns” in architecture and delivery velocity.

**Successful patterns:**

- **Pilot \& Stage:** Always start with a POC, then 1–2 core domains, before scaling to the whole app.
- **Monorepo or Modularization:** Use monorepos for small teams, strict modular architectures for larger teams to minimize integration hell and code bloat.
- **Incremental delivery:** Integrate early and often—NEVER “big bang” a refactor; automate deployments from day one.
- **Automated Testing:** Invest in contract tests, end-to-end tests, and continuous delivery; tie go/no-go to test passing, not personal “readiness.”
- **Technical Debt Tracking:** Use runbooks and backlog for tech debt, with real burn-down on the migration board.

***

### Resource Planning and Capacity Management

**Frequent issues:**

- **Overoptimistic wave planning:** Underestimating how long dependencies and issues will block progress.
- **Skill/bandwidth mismatch:** Cloud migration teams need 20–30% more capacity than estimated, especially early.

**How to avoid:**

- **Realistic team models:** For every 10 apps, at least 1 migration lead, 1–2 cloud engineers, 1–2 testers, 50% of original devs for QA/support, 1 PM; double for regulated industries.
- **Backfill critical roles:** Use partners or contractors to support BAU while the best internal staff focus on migration.
- **Wave calibration:** Run a “calibration wave” and adjust based on actual throughput and blockers, not plan.
- **Track burn rate by sprint:** Weekly or biweekly reviews to ensure velocity.

***

### Security and Compliance Considerations Across Different Rs

**Rehost/Replatform:**

- **IAM misconfiguration** is common: Over-permissive roles (“*”) left behind from testing; fix with fine-grained IAM policies and periodic reviews.
- **Legacy network patterns:** On-premises flat networks rerouted to security group sprawl; start with zero-trust, least-privilege security.
- **Encryption:** Ensure EBS, S3, RDS default to encryption; automate enforcement using AWS Config rules.
- **Data residency**: For regulated data, validate region and backup locations, automate evidence with tagging and logging.

**Repurchase/Refactor:**

- **Vendor lock-in:** SaaS providers may not match internal compliance/audit needs; conduct vendor due diligence with checklists, automate with 3rd-party audit APIs where possible.
- **Shared responsibility:** Cloud-native, serverless workloads shift security to application logic; build linting, static analysis, and dependency checks into CI/CD.
- **Logging gaps:** Managed services sometimes lack the granularity of on-prem logs; validate SLAs and auditability up front.

**Retain/Relocate:**

- **“Out of sight, out of mind”:** Non-migrated apps tend to fall behind on patching and compliance; implement review board to regularly assess and document status.
- **Hybrid boundaries:** Ensure cross-site VPN/cloud connectivity is encrypted, monitored, and governed for privileged access.

***

## Success Factors: Safeguards that Drive Migration Success

### Building Migration Expertise through Practical Training

- **Practice, not theory:** Workshops, “game days,” and cutover drills outperform classroom training.
- **Hands-on labs:** Simulate migration tasks, failures, and reversions; cross-train between ops, dev, and security.
- **Certification:** Track team certifications (AWS Solutions Architect, DevOps Engineer) but supplement with real-world exercises.


### Establishing Clear Governance and Accountability

- **Single-throat-to-choke:** Every migration wave must have a clear owner—avoid “committee paralysis.”
- **Decision-rights RACI:** Explicitly map accountability for each Rs decision, tools, configurations, and runbooks.
- **Change control:** No migrations allowed without approved runbooks and rollback plans.
- **Cross-functional review:** Include business, IT, security, and compliance in major cutover decisions.


### Continuous Improvement and Runbook Refinement

- **Living runbooks:** After-action reviews after every migration; update runbooks for every gap, work-around, or unexpected event.
- **Feedback loops:** Post-migration retrospectives with all stakeholders—not just the technical team.
- **Automation first:** Incorporate what’s learned into scripts, IaC, and automated pipelines. The pace of migration accelerates as manual steps disappear.


### Measuring and Reporting on Migration Success

- **Baseline and compare:** Always set operational, cost, and business performance baselines before migration; compare post-migration with objective dashboards.
- **KPI-driven:** Track time-to-migrate, outage/downtime, defect rates, cost savings, and stakeholder satisfaction.
- **Executive dashboards:** Use AWS Migration Hub, CloudWatch, and BI tools to keep leadership informed.
- **Celebrate wins, analyze failures:** Share successes widely for buy-in, but deconstruct failures for learning (not blame).

***

## Anti-Patterns: What *Not* to Do

- **“Big Bang” Everything:** Highest risk, most recoveries. Always break work into waves.
- **Manual Everything:** Increases errors and slows improvement. Automate as you go.
- **Ignoring the Business:** If all your metrics are technical, business value will be invisible.
- **No Rollback Plan:** The \#1 cause of deep pain. Always have a technical and communication rollback plan.
- **“Checklists Are Enough”:** If your runbook isn’t practiced, it will fail under stress.

***

## Hands-On Exercise

### For Beginners

**Objective:** Run a mock migration “game day” for a simple web application.

- Simulate migration waves, dependency mapping, and a sudden rollback (e.g., DB error).
- Document revised runbook steps after the exercise.


### For Professionals

**Scenario:** Lead a cross-team migration wave including refactor, replatform, and retire.

- Practice failover and rollback for at least one high-risk application.
- Deliver a scorecard tracking completion, defects, downtime, and business impact.
- Run a post-mortem and update runbooks and dashboards accordingly.

***

Successful migrations are built on lessons learned from past failures—yours and others'. If you treat problems as “rare,” you’ll always be surprised. If you institutionalize solutions, you’ll make migration routine. **The best migration teams are not those who make the fewest mistakes—but those who fix them the fastest.**

