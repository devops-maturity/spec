---
draft: false
aliases: ["/en/"]
layout: single
---

# DevOps Maturity Specification 1.0.0-next

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

| **Category**       |  **Code**| **Criteria**                                               |**Req.**|
|--------------------|----------|------------------------------------------------------------|--------|
| Basics             | D101     | [Branch Builds](#d101-branch-builds)                       | 🟢    |
|                    | D102     | [Pull Request Builds](#d102-pull-request-builds)           | 🟢    |
|                    | D103     | [Clean Build Environments](#d103-clean-build-environments) | 🟡    |
| Quality            | D201     | [Unit Testing](#d201-unit-testing)                         | 🟢    |
|                    | D202     | [Functional Testing](#d202-functional-testing)             | 🟢    |
|                    | D203     | [Performance Testing](#d203-performance-testing)           | 🟡    |
|                    | D204     | [Code Coverage](#d204-code-coverage)                       | 🟡    |
|                    | D205     | [Accessibility Testing](#d205-accessibility-testing)       | 🟡    |
| Security           | D301     | [Security Scanning](#d301-security-scanning)               | 🟢    |
|                    | D302     | [License Scanning](#d302-license-scanning)                 | 🟡    |
| Supply Chain Security| D401   | [Documented Build Process](#d401-documented-build-process) | 🟢    |
|                    | D402     | [CI/CD as Code](#d402-ci-cd-as-code)                       | 🟢    |
|                    | D403     | [Artifact Signing](#d403-artifact-signing)                 | 🟡    |
|                    | D404     | [Dependency Pinning](#d404-dependency-pinning)             | 🟡    |
| Analysis           | D501     | [Static Code Analysis](#d501-static-code-analysis)         | 🟡    |
|                    | D502     | [Dynamic Code Analysis](#d502-dynamic-code-analysis)       | 🟡    |
|                    | D503     | [Code Linting](#d503-code-linting)                         | 🟡    |
| Reporting          | D601     | [Notifications & Alerts](#d601-notifications--alerts)      | 🟢    |
|                    | D602     | [Attached Reports](#d602-attached-reports)                 | 🟢    |

- 🟢 MUST have (weight 1)
- 🟡 NICE have (weight 0.5)

## Badge Levels

Your score will generate one of the following badges:

| Level   | Score Range | Badge |
|---------|-------------| ------|
| WIP     | 0%          | ![WIP](https://img.shields.io/badge/DevOps%20Maturity-WIP-red.svg)   |
| PASSING | 1–49%       | ![PASSING](https://img.shields.io/badge/DevOps%20Maturity-PASSING-green.svg) |
| BRONZE  | 50–69%      | ![BRONZE](https://img.shields.io/badge/DevOps%20Maturity-BRONZE-yellow.svg) |
| SILVER  | 70–89%      | ![SILVER](https://img.shields.io/badge/DevOps%20Maturity-SILVER-silver.svg) |
| GOLD    | 90–100%     | ![GOLD](https://img.shields.io/badge/DevOps%20Maturity-GOLD-gold.svg) |

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

#### D101 Branch Builds

Supports builds from any specific branch, not just the `main` branch.

#### D102 Pull Request Builds

Supports building pull requests (PRs), not limited to direct pushes to branches.

#### D103 Clean Build Environments

Supports building in clean environments, such as containers or virtual machines (VMs).

#### D201 Unit Testing

Supports unit testing, including unit or component-level tests.

#### D202 Functional Testing

Supports functional testing, such as integration or end-to-end (E2E) tests.

#### D203 Performance Testing

Supports performance testing, including load, stress, or throughput testing.

#### D204 Code Coverage

Supports measuring code coverage, including line, branch, or function coverage.

#### D205 Accessibility Testing

Supports accessibility testing for standards compliance, such as WCAG.

#### D301 Security Scanning

Supports security scanning, including SAST (Static Application Security Testing) and DAST (Dynamic Application Security Testing).

#### D302 License Scanning

Supports license scanning using tools like SPDX, FOSSology, or license-checkers.

#### D401 Documented Build Process

Provides a documented build process, including build steps, manifests, or reproducibility details.

#### D402 CI/CD as Code

Supports CI/CD workflows defined as code, such as pipeline-as-code or infrastructure-as-code.

#### D403 Artifact Signing

Supports artifact signing (e.g., with PGP or GPG) to ensure authenticity and integrity.

#### D404 Dependency Pinning

Supports dependency pinning or version locking to ensure reproducible builds.

#### D501 Static Code Analysis

Supports static code analysis tools such as SonarQube, Polaris, or similar.

#### D502 Dynamic Code Analysis

Supports dynamic analysis, including runtime behavior analysis or fuzz testing.

#### D503 Code Linting

Supports code linting using tools like ESLint, Prettier, or pre-commit hooks.

#### D601 Notifications & Alerts

Supports notification systems such as email or Slack alerts.

#### D602 Attached Reports

Supports attaching detailed reports to builds, such as test results or coverage metrics.

---

## FAQ

### What tools can be used to caculate your score?

You can used [devops-maturity](https://github.com/devops-maturity/devops-maturity) which support web UI and CLI to calculate your score automatically.

### What is the difference between OpenSSF Best Practices and DevOps Maturity?

[OpenSSF Best Practices](https://www.bestpractices.dev/) targets open source projects across the entire software development lifecycle, while DevOps Maturity focuses specifically on DevOps practices applicable to both open source and internal enterprise projects. DevOps Maturity provides both a web UI and a CLI for automatic maturity scoring. In contrast, OpenSSF Best Practices only offers a web-based SaaS and does not support internal deployment.
