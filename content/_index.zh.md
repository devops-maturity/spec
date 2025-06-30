---
draft: false
aliases: ["/zh/"]
layout: single
---

# DevOps 成熟度规范 

## 概述

DevOps 成熟度规范为 DevOps 最佳实践提供指导，旨在提升软件开发与运维过程中的协作、自动化和效率。

## 关键要点

- **目标**：帮助组织和团队评估 DevOps 实践，对齐最佳实践，并推动持续改进。
- **范围**：涵盖 DevOps 的关键领域，包括构建、测试、安全、供应链、分析和报告。
- **成熟度等级**：通过清晰的可视化徽章（见[徽章等级](#徽章等级)）跟踪进展，提供直观易懂的概览。
- **评分方式**：评估项分为必选（🟢）和可选（🟡），实现清晰且可操作的评估。
- **工具支持**：可结合 [devops-maturity](https://github.com/devops-maturity/devops-maturity) 工具，通过 Web UI 或 CLI 自动化评分。

---

## 规范

### DevOps 成熟度评估标准

| **类别**  | **代码**[^1] | **评估项**[^2]               | **要求**[^3] |
|-----------|----------|---------------------------------|----------|
| 基础      | D101     | [分支构建](#d101-分支构建)        | 🟢       |
|           | D102     | [PR 构建](#d102-pr-构建)         | 🟢       |
|           | D103     | [干净环境构建](#d103-干净环境构建) | 🟡       |
| 质量      | D201     | [单元测试](#d201-单元测试)        | 🟢       |
|           | D202     | [功能测试](#d202-功能测试)       | 🟢       |
|           | D203     | [性能测试](#d203-性能测试)       | 🟡       |
|           | D204     | [代码覆盖率](#d204-代码覆盖率)    | 🟡       |
|           | D205     | [可访问性测试](#d205-可访问性测试) | 🟡       |
| 安全      | D301     | [安全扫描](#d301-安全扫描)        | 🟢       |
|           | D302     | [许可证扫描](#d302-许可证扫描)    | 🟡       |
| 供应链安全 | D401     | [构建过程文档化](#d401-构建过程文档化) | 🟢       |
|           | D402     | [CI/CD 代码化](#d402-ci-cd-代码化) | 🟢       |
|           | D403     | [制品签名](#d403-制品签名)        | 🟡       |
|           | D404     | [依赖锁定](#d404-依赖锁定)        | 🟡       |
| 分析      | D501     | [静态代码分析](#d501-静态代码分析) | 🟡       |
|           | D502     | [动态代码分析](#d502-动态代码分析) | 🟡       |
|           | D503     | [代码风格检查](#d503-代码风格检查) | 🟡       |
| 报告      | D601     | [通知与告警](#d601-通知与告警)     | 🟢       |
|           | D602     | [附加报告](#d602-附加报告)        | 🟢       |

[^1]: 评估项 ID 代码是分配给特定评估项的唯一标识符。更多详情见[代码说明](#评估项代码说明)。
[^2]: 每个评估项的详细信息可在[评估项详情](#评估项详情)部分找到。
[^3]: 要求等级：🟢 必选（权重：1），🟡 可选（权重：0.5）。

_提出新的评估项？_ 请[提交 issue](https://github.com/devops-maturity/spec/issues)。

## 徽章等级

你的得分将获得以下徽章之一：

| 等级    | 分数范围   | 徽章 |
|---------|-----------|------|
| WIP     | 0 - 29        | ![WIP](https://img.shields.io/badge/DevOps%20Maturity-WIP-red.svg)   |
| PASSING | 30 - 49   | ![PASSING](https://img.shields.io/badge/DevOps%20Maturity-PASSING-green.svg) |
| BRONZE  | 50 - 69    | ![BRONZE](https://img.shields.io/badge/DevOps%20Maturity-BRONZE-yellow.svg) |
| SILVER  | 70 - 89    | ![SILVER](https://img.shields.io/badge/DevOps%20Maturity-SILVER-silver.svg) |
| GOLD    | 90 - 100   | ![GOLD](https://img.shields.io/badge/DevOps%20Maturity-GOLD-gold.svg) |

## 评估项代码说明

|**代码**|**说明**|
|--------|--------|
| D1xx   | 基础   |
| D2xx   | 质量   |
| D3xx   | 安全   |
| D4xx   | 供应链安全 |
| D5xx   | 分析   |
| D6xx   | 报告   |

- 所有评估项代码以领域字母为前缀（如 `D` 代表 DevOps）
- 代码格式：`DXYZ`
  - `D` = 领域（DevOps）
  - `X` = 类别（如 1: 基础, 2: 质量）
  - `YZ` = 评估项编号

## 评估项详情

{{< details title="点击展开评估项详情" >}} 

| **ID**   | **评估项**         | **说明**                      |
|----------|--------------------|-----------------------------|
| D101     | 分支构建           | 支持从任意指定分支进行构建，而不仅限于 `main` 分支。|
| D102     | PR 构建            | 支持对 Pull Request（PR）进行构建，不仅限于直接推送到分支。|
| D103     | 干净环境构建       | 支持在干净环境（如容器或虚拟机）中进行构建。|
| D201     | 单元测试           | 支持单元测试，包括单元或组件级测试。       |
| D202     | 功能测试           | 支持功能测试，如集成测试或端到端（E2E）测试。|
| D203     | 性能测试           | 支持性能测试，包括负载、压力或吞吐量测试。  |
| D204     | 代码覆盖率         | 支持代码覆盖率测量，包括行、分支或函数覆盖率。|
| D205     | 可访问性测试       | 支持可访问性测试，符合如 WCAG 等标准。       |
| D301     | 安全扫描           | 支持安全扫描，包括 SAST 和 DAST。           |
| D302     | 许可证扫描         | 支持许可证扫描，如 SPDX、FOSSology 或 license-checkers 等工具。|
| D401     | 构建过程文档化     | 提供构建过程文档，包括构建步骤、清单或可复现性说明。|
| D402     | CI/CD 代码化       | 支持以代码形式定义 CI/CD 工作流，如流水线即代码或基础设施即代码。|
| D403     | 制品签名           | 支持制品签名（如 PGP 或 GPG），确保真实性和完整性。|
| D404     | 依赖锁定           | 支持依赖锁定或版本固定，确保可复现构建。          |
| D501     | 静态代码分析       | 支持静态代码分析工具，如 SonarQube、Polaris 等。 |
| D502     | 动态代码分析       | 支持动态分析，包括运行时行为分析或模糊测试。      |
| D503     | 代码风格检查       | 支持代码风格检查，如 ESLint、Prettier 或 pre-commit 钩子。|
| D601     | 通知与告警         | 支持通知系统，如邮件或 Slack 告警。             |
| D602     | 附加报告           | 支持将详细报告附加到构建，如测试结果或覆盖率指标。|

{{< /details >}}

---

## 常见问题解答

### 如何自动计算成熟度得分？

你可以使用 [devops-maturity](https://github.com/devops-maturity/devops-maturity)，该工具支持 Web UI 和 CLI，可自动计算你的成熟度得分。

### OpenSSF Best Practices 和 DevOps Maturity 有什么区别？

[OpenSSF Best Practices](https://www.bestpractices.dev/) 面向整个软件开发生命周期的开源项目，而 DevOps Maturity 专注于适用于开源和企业内部项目的 DevOps 实践。DevOps Maturity 提供 Web UI 和 CLI 两种自动化成熟度评分方式，而 OpenSSF Best Practices 仅提供基于 Web 的 SaaS 服务，不支持内部部署。

### DevOps Maturity Model 和 DevOps Maturity Specification 有什么区别？

DevOps Maturity Model 是一个概念框架，描述了 DevOps 采纳和成熟度的各个阶段，而 DevOps Maturity Specification 提供了详细、可操作的评估标准和指南，用于评估和改进 DevOps 实践。

### 如何为 DevOps Maturity Specification 做出贡献？

你可以通过提出新的评估标准、功能建议或报告问题来参与贡献。欢迎在 GitHub 上 [提交 Issue](https://github.com/devops-maturity/spec/issues) 或 [创建 Pull Request](https://github.com/devops-maturity/spec/pulls)。我们非常欢迎来自社区的参与！

### 如何在组织中应用 DevOps Maturity Specification？

你可以通过以下方式将 DevOps Maturity Specification 融入组织的 DevOps 实践中：

* 使用各项评估标准来衡量当前的 DevOps 成熟度水平。
* 按照推荐的标准逐步改进 DevOps 流程。
* 使用如 [devops-maturity](https://github.com/devops-maturity/devops-maturity) 这样的工具，自动计算成熟度得分并生成徽章。
