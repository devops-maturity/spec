---
draft: false
aliases: ["/en/"]
layout: single
---

# DevOps Maturity Specification

## Summary

### What is the DevOps Maturity Specification?

The DevOps Maturity Specification is a set of guidelines and criteria designed to help organizations assess and improve their DevOps practices. It provides a structured approach to evaluate key areas such as Basics, Quality, Security, Supply Chain Security, Analysis, and Reporting. The specification is intended to align with best practices and provide a framework for continuous improvement within the DevOps community.

### Key Points

- **Purpose**: Help organizations and teams assess DevOps practices, align on best practices, and drive continuous improvement.
- **Scope**: Covers key DevOps domains including build, testing, security, supply chain, analysis, and reporting.
- **Maturity Levels**: Tracks progress with clear visual badges (See [Badge Levels](#badge-levels)) to provide an easy and intuitive overview.
- **Scoring**: Criteria are weighted as MUST (🟢) or NICE (🟡) enabling clear and actionable evaluation.
- **Tooling**: Works with [devops-maturity](https://github.com/devops-maturity/devops-maturity) to automate scoring via Web UI or CLI.

---

## Specification

| **Category**       | **Code**[^1]| **Criteria**[^2]            |**Req.**[^3]|
|--------------------|----------|--------------------------------|--------|
| Basics             | D101     | Branch Builds                  | 🟢    |
|                    | D102     | Pull Request Builds            | 🟢    |
|                    | D103     | Clean Build Environments       | 🟡    |
| Quality            | D201     | Unit Testing                   | 🟢    |
|                    | D202     | Functional Testing             | 🟢    |
|                    | D203     | Performance Testing            | 🟡    |
|                    | D204     | Code Coverage                  | 🟡    |
|                    | D205     | Accessibility Testing          | 🟡    |
| Security           | D301     | Vulnerability Scanning         | 🟢    |
|                    | D302     | License Scanning               | 🟡    |
| Supply Chain Security| D401   | Documented Build Process       | 🟢    |
|                    | D402     | CI/CD as Code                  | 🟢    |
|                    | D403     | Artifact Signing               | 🟡    |
|                    | D404     | Dependency Pinning             | 🟡    |
|                    | D405     | SBOM Generation                | 🟡    |
| Analysis           | D501     | Static Code Analysis           | 🟡    |
|                    | D502     | Dynamic Code Analysis          | 🟡    |
|                    | D503     | Code Linting                   | 🟡    |
| Reporting          | D601     | Notifications & Alerts         | 🟢    |
|                    | D602     | Attached Reports               | 🟡    |
|                    | D603     | Compliance Mapping & Auditability | 🟡    |

[^1]: A criteria ID code is a unique identifier assigned to specific criteria. For more details, see the [Code Map](#code-map).
[^2]: Detailed information on each criteria can be found in the [Criteria Details](#criteria-details) section.
[^3]: Required Levels: 🟢 Must-Have (Weight: 1), 🟡 Nice-to-Have (Weight: 0.5).

_Proposed a new criteria?_ Please [open an issue](https://github.com/devops-maturity/spec/issues).

## Badge Levels

Your score will generate one of the following badges:

| Level   | Score Range | Badge |
|---------|-------------| ------|
| WIP     | 0 - 29      | ![WIP](https://img.shields.io/badge/DevOps%20Maturity-WIP-blue.svg)   |
| PASSING | 30 - 49     | ![PASSING](https://img.shields.io/badge/DevOps%20Maturity-PASSING-green.svg) |
| BRONZE  | 50 - 69     | ![BRONZE](https://img.shields.io/badge/DevOps%20Maturity-BRONZE-yellow.svg) |
| SILVER  | 70 - 89     | ![SILVER](https://img.shields.io/badge/DevOps%20Maturity-SILVER-silver.svg) |
| GOLD    | 90 - 100    | ![GOLD](https://img.shields.io/badge/DevOps%20Maturity-GOLD-gold.svg) |

## Criteria Reference

### Code Map

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

## Criteria Details

{{< details title="Click to expand criteria details" >}} 

| **Code** | **Criteria**           | **Description**                            |
| ------ | ------------------------ | ------------------------------------------ |
| D101   | Branch Builds            | Enables builds to be triggered from any Git branch, not limited to the main or default branch. |
| D102   | Pull Request Builds      | Supports automatic builds for pull requests (PRs), allowing validation before merging into target branches. |
| D103   | Clean Build Environments | Ensures builds run in isolated, reproducible environments (e.g., containers or virtual machines) to avoid contamination from previous runs. |
| D201   | Unit Testing             | Supports execution of unit or component-level tests to validate individual functions or modules in isolation. |
| D202   | Functional Testing       | Enables running functional, integration, or end-to-end (E2E) tests to validate system behavior and interactions. |
| D203   | Performance Testing      | Supports performance-related testing, such as load, stress, and scalability tests, to evaluate system responsiveness and stability under pressure. |
| D204   | Code Coverage            | Enables measurement of test coverage, including metrics like line, branch, and function coverage, to assess test effectiveness. |
| D205   | Accessibility Testing    | Supports testing for compliance with accessibility standards (e.g., WCAG) to ensure usability for people with disabilities.|
| D301   | Vulnerability Scanning    | Scanning source code, containers, or infrastructure for known security vulnerabilities using tools like Snyk, Trivy, or SonarQube security rules. |
| D302   | License Scanning         | Checking open-source dependencies for license compliance and legal risks to avoid unapproved or incompatible usage. |
| D401   | Documented Build Process | CI/CD build steps are version-controlled and documented.|
| D402   | CI/CD as Code            | Pipelines and infrastructure are defined as code (IaC, PaC).  |
| D403   | Artifact Signing         | Build artifacts are cryptographically signed. |
| D404   | Dependency Pinning       | All dependencies are pinned to exact versions. |
| D405   | SBOM Generation          | Automatically generate and manage Software Bill of Materials (SBOMs) using SPDX or CycloneDX. |
| D501   | Static Code Analysis     | Analyzing code without executing it to detect bugs, code smells, or potential security issues. |
| D502   | Dynamic Code Analysis    | Analyzing running applications to detect runtime vulnerabilities, memory leaks, or behavioral issues. |
| D503   | Code Linting             | Checking code for style, formatting, and consistency rules. |
| D601   | Notifications & Alerts   | Notify stakeholders on key CI/CD events. |
| D602   | Attached Reports         | CI/CD runs produce and attach structured test and analysis reports.|
| D603   | Compliance Mapping & Auditability | Map controls to standards (e.g., SLSA, NIST, ISO 20243) and provide audit-ready reports. |

{{< /details >}}

---

## FAQ

### What is the difference between OpenSSF Best Practices and DevOps Maturity?

[OpenSSF Best Practices](https://www.bestpractices.dev/) targets open source projects across the entire software development lifecycle, while DevOps Maturity focuses specifically on DevOps practices applicable to both open source and internal enterprise projects. DevOps Maturity provides both a web UI and a CLI for automatic maturity scoring. In contrast, OpenSSF Best Practices only offers a web-based SaaS and does not support internal deployment.

### What is the difference between DevOps Maturity Model and DevOps Maturity Specification?

The DevOps Maturity Model is a conceptual framework that outlines the stages of DevOps adoption and maturity, while the DevOps Maturity Specification provides a detailed, actionable set of criteria and guidelines for assessing and improving DevOps practices.

### How can I contribute to the DevOps Maturity Specification?

You can contribute by proposing new criteria, features, or reporting bugs. Please [open an issue](https://github.com/devops-maturity/spec/issues) or [create a pull request](https://github.com/devops-maturity/spec/pulls) on GitHub. We welcome contributions from the community!

### How can I use the DevOps Maturity Specification in my organization?

You can integrate the DevOps Maturity Specification into your organization's DevOps practices by:
- Using the criteria to assess your current DevOps maturity level.
- Implementing the recommended criteria to improve your DevOps processes.
- Utilizing tools like [devops-maturity](https://github.com/devops-maturity/devops-maturity) to calculate maturity scores and generate badges automatically.
