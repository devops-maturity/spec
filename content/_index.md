---
draft: false
aliases: ["/en/"]
layout: single
---

# DevOps Maturity Specification 1.0.0

## Summary

DevOps Maturity Specification is a set of guidelines for DevOps best practices, focusing on improving collaboration, automation, and efficiency in software development and operations.

---

## Specification

### DevOps Maturity Criteria

must have → 🟢
nice to have → 🟡

| **Category**        | **Criteria**                               | **Req.** | **Weight** |
|---------------------|--------------------------------------------|----------|------------|
| CI/CD Basic         | Build a specific branch                    | 🟢       | 1          |
|                     | Build upon pull request                    | 🟢       | 1          |
|                     | Build from clean environment               | 🟡       | 0.5        |
| Quality             | Automated Testing: Functional testing      | 🟢       | 1          |
|                     | Automated Testing: Performance testing     | 🟢       | 1          |
|                     | Code Coverage                              | 🟡       | 0.5        |
|                     | Accessibility Testing                      | 🟡       | 0.5        |
| Security            | Security scan                              | 🟢       | 1          |
|                     | License scan                               | 🟡       | 0.5        |
| Secure Supply Chain | Documented Build Chain                     | 🟢       | 1          |
|                     | CICD as coded                              | 🟢       | 1          |
|                     | Artifacts are signed                       | 🟡       | 0.5        |
|                     | Artifactory download for Package Managers  | 🟡       | 0.5        |
| Analysis            | Quality Gate                               | 🟡       | 0.5        |
|                     | Code Lint                                  | 🟡       | 0.5        |
|                     | Static code analysis                       | 🟡       | 0.5        |
|                     | Dynamic code analysis                      | 🟡       | 0.5        |
| Reporting           | Email/Slack reporting functionality        | 🟢       | 1          |


## Badge Levels

Your score will generate one of the following badges:

* WIP: 0%
* PASSING: 1–49%
* BRONZE: 50–69%
* SILVER: 70–89%
* GOLD: 90–100%

---

## FAQ

### What tools can be used to caculate your score?

You can used [devops-maturity](https://pypi.org/project/devops-maturity) CLI to caculate your score.

