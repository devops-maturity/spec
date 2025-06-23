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

MUST have → 🟢 (weight 1)
NICE to have → 🟡 (weight 0.5)

| **Category**       |**Code**| **Criteria**                               | **Req.**|
|--------------------|--------|--------------------------------------------|---------|
| Basics             | D101   | Build a specific branch                    | 🟢     |
|                    | D102   | Build upon pull request                    | 🟢     |
|                    | D103   | Build from clean environment               | 🟡     |
| Quality            | D201   | Automated Testing: Functional testing      | 🟢     |
|                    | D202   | Automated Testing: Performance testing     | 🟡     |
|                    | D203   | Code Coverage                              | 🟡     |
|                    | D204   | Accessibility Testing                      | 🟡     |
| Security           | D301   | Security scan                              | 🟢     |
|                    | D302   | License scan                               | 🟡     |
| Secure Supply Chain| D401   | Documented Build Chain                     | 🟢     |
|                    | D402   | CI/CD as coded                             | 🟢     |
|                    | D403   | Artifacts are signed                       | 🟡     |
|                    | D404   | Artifactory download for Package Managers  | 🟡     |
| Analysis           | D501   | Static code analysis                       | 🟡     |
|                    | D502   | Dynamic code analysis                      | 🟡     |
|                    | D503   | Quality Gate                               | 🟡     |
|                    | D504   | Code Lint                                  | 🟡     |
| Reporting          | D601   | Email/Slack reporting functionality        | 🟢     |
|                    | D602   | Attached Reports                           | 🟢     |


### Code Groupings

|**Code**| **Description**|
|-------|---------------|
| D1xx   | Basics         |
| D2xx   | Quality        |
| D3xx   | Security      |
| D4xx   | Secure Supply Chain |
| D5xx   | Analysis       |
| D6xx   | Reporting      |


## Badge Levels

Your score will generate one of the following badges:

| Level   | Score Range | Badge |
|---------|-------------| ------|
| WIP     | 0%          | ![WIP](https://img.shields.io/badge/DevOps%20Maturity-WIP-red.svg)   |
| PASSING | 1–49%       | ![PASSING](https://img.shields.io/badge/DevOps%20Maturity-PASSING-green.svg) |
| BRONZE  | 50–69%      | ![BRONZE](https://img.shields.io/badge/DevOps%20Maturity-BRONZE-yellow.svg) |
| SILVER  | 70–89%      | ![SILVER](https://img.shields.io/badge/DevOps%20Maturity-SILVER-silver.svg) |
| GOLD    | 90–100%     | ![GOLD](https://img.shields.io/badge/DevOps%20Maturity-GOLD-gold.svg) |

---

## FAQ

### What tools can be used to caculate your score?

You can used [devops-maturity](https://github.com/devops-maturity/devops-maturity) which support web UI and CLI to calculate your score automatically.

### What is the difference between OpenSSF Best Practices and DevOps Maturity?

[OpenSSF Best Practices](https://www.bestpractices.dev/) targets open source projects, while DevOps Maturity applies to both open source and internal enterprise projects.

DevOps Maturity offers a web UI and CLI for automatically calculating your maturity score. OpenSSF Best Practices is web-based SaaS and may not support internal deployment.
