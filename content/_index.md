---
draft: false
aliases: ["/en/"]
layout: single
---

# DevOps Maturity Specification 1.0.0

## Summary

DevOps Maturity Specification provides guidelines for DevOps best practices, aiming to enhance collaboration, automation, and efficiency across software development and operations.

## Key Points

- **Purpose**: Help organizations and teams assess DevOps practices, align on best practices, and drive continuous improvement.
- **Scope**: Covers key DevOps domains including build, testing, security, supply chain, analysis, and reporting.
- **Maturity Levels**: Tracks progress with clear visual badges (See [Badge Levels](#badge-levels)) to provide an easy and intuitive overview.
- **Scoring**: Criteria are weighted as MUST (🟢) or NICE (🟡) enabling clear and actionable evaluation.
- **Tooling**: Works with [devops-maturity](https://github.com/devops-maturity/devops-maturity) to automate scoring via Web UI or CLI.

---

## Specification

| **Category**       |**Code**| **Criteria**                     | **Req.**|
|--------------------|--------|----------------------------------|---------|
| Basics             | D101   | Branch Builds[^1]                | 🟢     |
|                    | D102   | Pull Request Builds[^2]          | 🟢     |
|                    | D103   | Clean Build Environments[^3]     | 🟡     |
| Quality            | D201   | Unit Testing[^4]                 | 🟢     |
|                    | D202   | Functional Testing[^5]           | 🟢     |
|                    | D203   | Performance Testing[^6]          | 🟡     |
|                    | D204   | Code Coverage[^7]                | 🟡     |
|                    | D205   | Accessibility Testing[^8]        | 🟡     |
| Security           | D301   | Security Scanning[^9]            | 🟢     |
|                    | D302   | License Scanning[^10]            | 🟡     |
| Supply Chain Security| D401 | Documented Build Process[^11]    | 🟢     |
|                    | D402   | CI/CD as Code[^12]               | 🟢     |
|                    | D403   | Artifact Signing[^13]            | 🟡     |
|                    | D404   | Dependency Pinning[^14]          | 🟡     |
| Analysis           | D501   | Static Code Analysis[^15]        | 🟡     |
|                    | D502   | Dynamic Code Analysis[^16]       | 🟡     |
|                    | D504   | Code Linting[^17]                | 🟡     |
| Reporting          | D601   | Notifications & Alerts[^18]      | 🟢     |
|                    | D602   | Attached Reports[^19]            | 🟢     |

- 🟢 MUST have (weight 1)
- 🟡 NICE have (weight 0.5)

### Maturity Code Map

|**Code**|**Description**|
|--------|---------------|
| D1xx   | Basics        |
| D2xx   | Quality       |
| D3xx   | Security      |
| D4xx   | Supply Chain Security|
| D5xx   | Analysis      |
| D6xx   | Reporting     |

- All criteria codes are prefixed by domain letter (e.g., `D` for DevOps)
- Code format: `DXYZ`
  - `D` = Domain (DevOps)
  - `X` = Category (e.g., 1: Basics, 2: Quality)
  - `YZ` = Criteria number


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

[OpenSSF Best Practices](https://www.bestpractices.dev/) targets open source projects across the entire software development lifecycle, while DevOps Maturity focuses specifically on DevOps practices applicable to both open source and internal enterprise projects. DevOps Maturity provides both a web UI and a CLI for automatic maturity scoring. In contrast, OpenSSF Best Practices only offers a web-based SaaS and does not support internal deployment.

[^1]: Supports builds from any specific branch, not just the `main` branch.
[^2]: Supports building pull requests (PRs), not limited to direct pushes to branches.
[^3]: Supports building in clean environments, such as containers or virtual machines (VMs).
[^4]: Supports unit testing, including unit or component-level tests.
[^5]: Supports functional testing, such as integration or end-to-end (E2E) tests.
[^6]: Supports performance testing, including load, stress, or throughput testing.
[^7]: Supports measuring code coverage, including line, branch, or function coverage.
[^8]: Supports accessibility testing for standards compliance, such as WCAG.
[^9]: Supports security scanning, including SAST (Static Application Security Testing) and DAST (Dynamic Application Security Testing).
[^10]: Supports license scanning using tools like SPDX, FOSSology, or license-checkers.
[^11]: Provides a documented build process, including build steps, manifests, or reproducibility details.
[^12]: Supports CI/CD workflows defined as code, such as pipeline-as-code or infrastructure-as-code.
[^13]: Supports artifact signing (e.g., with PGP or GPG) to ensure authenticity and integrity.
[^14]: Supports dependency pinning or version locking to ensure reproducible builds.
[^15]: Supports static code analysis tools such as SonarQube, Polaris, or similar.
[^16]: Supports dynamic analysis, including runtime behavior analysis or fuzz testing.
[^17]: Supports code linting using tools like ESLint, Prettier, or pre-commit hooks.
[^18]: Supports notification systems such as email or Slack alerts.
[^19]: Supports attaching detailed reports to builds, such as test results or coverage metrics.
