---
draft: false
aliases: ["/zh/"]
layout: single
---

# DevOps 成熟度规范

## 概述

### 什么是 DevOps 成熟度规范？

DevOps 成熟度规范是一套用于帮助组织评估和改进 DevOps 实践的指南和标准。它通过结构化的方法，覆盖基础、质量、安全、供应链安全、分析和报告等关键领域，旨在对齐最佳实践，并为 DevOps 社区持续改进提供框架。

## 关键要点

- **目标**：帮助组织和团队评估 DevOps 实践，对齐最佳实践，并推动持续改进。
- **范围**：涵盖 DevOps 的关键领域，包括构建、测试、安全、供应链、分析和报告。
- **成熟度等级**：通过清晰的可视化徽章（见[徽章等级](#徽章等级)）跟踪进展，提供直观易懂的概览。
- **评分方式**：评估项分为必选（🟢）和可选（🟡），实现清晰且可操作的评估。
- **工具支持**：可结合 [devops-maturity](https://github.com/devops-maturity/devops-maturity) 工具，通过 Web UI 或 CLI 自动化评分。

---

## 规范

| **类别**  | **代码**[^1] | **评估项**[^2]               | **要求**[^3] |
|-----------|----------|---------------------------------|----------|
| 基础      | D101     | 分支构建        | 🟢       |
|           | D102     | PR 构建         | 🟢       |
|           | D103     | 干净环境构建     | 🟡       |
| 质量      | D201     | 单元测试        | 🟢       |
|           | D202     | 功能测试        | 🟢       |
|           | D203     | 性能测试        | 🟡       |
|           | D204     | 代码覆盖率      | 🟡       |
|           | D205     | 可访问性测试    | 🟡       |
| 安全      | D301     | 漏洞扫描        | 🟢       |
|           | D302     | 许可证扫描      | 🟡       |
| 供应链安全 | D401     | 构建过程文档化  | 🟢       |
|           | D402     | CI/CD 代码化    | 🟢       |
|           | D403     | 制品签名        | 🟡       |
|           | D404     | 依赖锁定        | 🟡       |
|           | D405     | SBOM 生成       | 🟡       |
| 分析      | D501     | 静态代码分析    | 🟡       |
|           | D502     | 动态代码分析    | 🟡       |
|           | D503     | 代码风格检查    | 🟡       |
| 报告      | D601     | 通知与告警      | 🟢       |
|           | D602     | 附加报告        | 🟡       |
|           | D603     | 合规映射与可审计性 | 🟡       |

[^1]: 评估项 ID 代码是分配给特定评估项的唯一标识符。更多详情见[代码说明](#评估项代码说明)。
[^2]: 每个评估项的详细信息可在[评估项详情](#评估项详情)部分找到。
[^3]: 要求等级：🟢 必选（权重：1），🟡 可选（权重：0.5）。

_提出新的评估项？_ 请[提交 issue](https://github.com/devops-maturity/spec/issues)。

## 徽章等级

你的得分将获得以下徽章之一：

| 等级    | 分数范围   | 徽章 |
|---------|-----------|------|
| WIP     | 0 - 29    | ![WIP](https://img.shields.io/badge/DevOps%20Maturity-WIP-red.svg)   |
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
| D102     | PR 构建            | 支持对 Pull Request（PR）进行自动构建，可在合并前进行验证。|
| D103     | 干净环境构建       | 确保构建在隔离且可复现的环境（如容器或虚拟机）中运行，避免受前次运行影响。|
| D201     | 单元测试           | 支持执行单元或组件级测试，验证各独立功能或模块。|
| D202     | 功能测试           | 支持运行功能、集成或端到端（E2E）测试，验证系统行为和交互。|
| D203     | 性能测试           | 支持负载、压力和可扩展性测试，评估系统在高压下的响应和稳定性。|
| D204     | 代码覆盖率         | 支持测试覆盖率测量，包括行、分支和函数覆盖率等指标，用于评估测试有效性。|
| D205     | 可访问性测试       | 支持符合如 WCAG 等标准的可访问性测试，确保残障人士可用性。|
| D301     | 漏洞扫描           | 使用 Snyk、Trivy 或 SonarQube 等工具对源代码、容器或基础设施进行已知安全漏洞扫描。|
| D302     | 许可证扫描         | 检查开源依赖的许可证合规性和法律风险，避免未授权或不兼容的使用。|
| D401     | 构建过程文档化     | CI/CD 构建步骤实现版本控制并有文档说明。|
| D402     | CI/CD 代码化       | 流水线和基础设施以代码形式定义（IaC、PaC）。|
| D403     | 制品签名           | 构建产物进行加密签名，确保真实性和完整性。|
| D404     | 依赖锁定           | 所有依赖均锁定为精确版本，确保可复现构建。|
| D405     | SBOM 生成          | 自动生成并管理软件材料清单（SBOM），如 SPDX 或 CycloneDX 格式。|
| D501     | 静态代码分析       | 使用 SonarQube、Polaris 等工具进行静态分析，检测代码缺陷和安全隐患。|
| D502     | 动态代码分析       | 在测试环境下运行应用，检测运行时漏洞、内存泄漏或行为异常。|
| D503     | 代码风格检查       | 使用 ESLint、Prettier 或 pre-commit 钩子检查代码风格和一致性。|
| D601     | 通知与告警         | 在关键 CI/CD 事件时通知相关人员，如邮件或 Slack。|
| D602     | 附加报告           | CI/CD 运行生成并附加结构化测试和分析报告。|
| D603     | 合规映射与可审计性 | 映射控制到合规标准（如 SLSA、NIST、ISO 20243），并生成可审计报告。|

{{< /details >}}

---

## 常见问题解答

### OpenSSF Best Practices 和 DevOps Maturity 有什么区别？

[OpenSSF Best Practices](https://www.bestpractices.dev/) 面向整个软件开发生命周期的开源项目，而 DevOps Maturity 专注于适用于开源和企业内部项目的 DevOps 实践。DevOps Maturity 提供 Web UI 和 CLI 两种自动化成熟度评分方式，而 OpenSSF Best Practices 仅提供基于 Web 的 SaaS 服务，不支持内部部署。

### DevOps Maturity Model 和 DevOps Maturity Specification 有什么区别？

DevOps Maturity Model 是一个概念框架，描述了 DevOps 采纳和成熟度的各个阶段，而 DevOps Maturity Specification 提供了详细、可操作的评估标准和指南，用于评估和改进 DevOps 实践。

### 如何为 DevOps Maturity Specification 做出贡献？

你可以通过提出新的评估标准、功能建议或报告问题来参与贡献。欢迎在 GitHub 上 [提交 Issue](https://github.com/devops-maturity/spec/issues) 或 [创建 Pull Request](https://github.com/devops-maturity/spec/pulls)。我们非常欢迎来自社区的参与！

### 如何在组织中应用 DevOps Maturity Specification？

你可以通过以下方式将 DevOps Maturity Specification 融入组织的 DevOps 实践中：

- 使用各项评估标准来衡量当前的 DevOps 成熟度水平。
- 按照推荐的标准逐步改进 DevOps 流程。
- 使用如 [devops-maturity](https://github.com/devops-maturity/devops-maturity) 这样的工具，自动计算成熟度得分并生成徽章。
