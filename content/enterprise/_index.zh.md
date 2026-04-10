---
type: enterprise
draft: false
layout: single
title: "企业版"
description: "DevOps 成熟度企业版的部署、治理、API、许可与定价说明。"
---

# DevOps 成熟度企业版

DevOps Maturity Assessment Enterprise（DMAE）是 DevOps Maturity 开源项目的商业版本。它在核心评估流程之上增加了多团队治理、合规能力、企业级报表和商业许可证运行时控制。

## 企业版新增能力

- 面向组织、团队和部门的多租户模型
- 面向企业管理场景的基于角色访问控制（RBAC）
- JWT 鉴权、浏览器会话和 API Key 访问
- 自定义评估标准和行业模板
- 高级报表、趋势分析、团队基准对比和数据导出
- 审计日志和出站 Webhook
- SSO 与 LDAP / Active Directory 集成骨架
- 由供应商签发的许可证管理与运行时策略校验

## 功能矩阵

| 功能 | 开源版 | 企业版 |
| --- | :---: | :---: |
| DevOps 成熟度评估 | ✅ | ✅ |
| 评分等级（WIP -> GOLD） | ✅ | ✅ |
| 社交 OAuth（Google / GitHub） | ✅ | ✅ |
| 多租户（组织） | ❌ | ✅ |
| 团队 / 部门管理 | ❌ | ✅ |
| 基于角色的访问控制（RBAC） | ❌ | ✅ |
| JWT 鉴权 + API Key | ❌ | ✅ |
| 自定义评估标准 | ❌ | ✅ |
| 行业模板 | ❌ | ✅ |
| 高级报表与趋势分析 | ❌ | ✅ |
| 团队基准对比 | ❌ | ✅ |
| 数据导出 | ❌ | ✅ |
| 审计日志 | ❌ | ✅ |
| 出站 Webhook | ❌ | ✅ |
| SSO（SAML / OIDC）骨架 | ❌ | ✅ |
| LDAP / Active Directory 同步骨架 | ❌ | ✅ |
| 许可证管理 | ❌ | ✅ |

## 快速开始

### 1. 安装依赖

```bash
pip install -e ".[dev]"
```

### 2. 生成许可证签名密钥对

这是供应商侧步骤，私钥应离线保管。

```bash
dmae-enterprise generate-license-keypair \
  --private-key-out ./secrets/vendor-license-private.pem \
  --public-key-out ./secrets/license-public.pem
```

### 3. 签发试用或正式许可证

```bash
dmae-enterprise issue-license \
  --private-key-file ./secrets/vendor-license-private.pem \
  --org acme-corp \
  --tier trial \
  --expires 2026-05-09
```

### 4. 配置环境变量

```env
JWT_SECRET_KEY=change-me-before-production
DATABASE_URL=sqlite:///./enterprise.db
LICENSE_KEY=<vendor-issued-license>
LICENSE_PUBLIC_KEY_FILE=./secrets/license-public.pem
LICENSE_ENFORCEMENT_MODE=strict
DMAE_RUNTIME_CONFIG_FILE=./.dmae/runtime-config.json
PUBLIC_APP_URL=http://localhost:8000
EMAIL_DELIVERY_MODE=log
EMAIL_BRAND_NAME=DMAE Enterprise
EMAIL_SUPPORT_ADDRESS=support@dmae.local
```

### 5. 启动服务

```bash
dmae-enterprise server
```

首次通过浏览器初始化时会：

- 接收签名许可证
- 创建首个 `SUPER_ADMIN`
- 创建首个组织
- 持久化自托管部署重启后仍可用的运行时许可证配置

### 6. 可选的 CLI 引导

```bash
dmae-enterprise bootstrap-admin \
  --username platform-admin \
  --email admin@example.com \
  --org-name "Acme Corp" \
  --org-slug acme
```

## UI 入口

- 初始化页面：`http://localhost:8000/`
- 登录页面：`http://localhost:8000/login`
- 邀请接受页面：`http://localhost:8000/welcome?token=...`
- 密码重置页面：`http://localhost:8000/reset-password?token=...`
- 应用首页：`http://localhost:8000/app`
- Swagger UI：`http://localhost:8000/enterprise/docs`
- ReDoc：`http://localhost:8000/enterprise/redoc`
- 健康检查：`http://localhost:8000/health`

`/app` 浏览器工作台包含：

- 组织概览和生效中的资源配额
- 当前许可证等级及功能可见性
- 用户列表、邮件邀请、密码重置链接和账户激活控制
- 团队列表与创建
- 最近审计活动

## 运行时控制

服务在运行时会强制执行商业策略：

- `strict` 模式下，没有有效且未过期许可证时将拒绝启动
- 许可证等级会控制高级功能，例如 webhook、高级报表、导出和 benchmark 报表
- 用户数、团队数和每月评估次数会在请求时校验
- `trial`、`starter` 和 `enterprise` 都可以带有用户、团队和评估额度的自定义覆盖

## 鉴权与 API 访问

通过邮箱和密码登录：

```bash
curl -X POST http://localhost:8000/enterprise/auth/login \
  -H "Content-Type: application/json" \
  -d '{"email":"admin@example.com","password":"secret"}'
```

使用返回的 Bearer Token：

```bash
curl http://localhost:8000/enterprise/organizations \
  -H "Authorization: Bearer <access_token>"
```

当当前许可证包含 `api_access` 时，也可以使用 API Key：

```bash
curl http://localhost:8000/enterprise/organizations \
  -H "X-API-Key: dmae_<your_api_key>"
```

浏览器会话使用 `HttpOnly` Cookie。邀请接受和密码重置流程会生成一次性链接，分别落到 `/welcome` 和 `/reset-password`。

本地开发建议保留 `EMAIL_DELIVERY_MODE=log`，这样管理界面会显示邀请或重置邮件的链接预览和投递历史。生产环境则应切换到 `EMAIL_DELIVERY_MODE=smtp`，配置 SMTP 参数，并设置 `EMAIL_BRAND_NAME` 与 `EMAIL_SUPPORT_ADDRESS`。

## 关键 API 接口

| 接口 | 说明 |
| --- | --- |
| `POST /enterprise/auth/login` | 登录并返回 JWT Token |
| `POST /enterprise/auth/session/login` | 登录并建立浏览器会话 Cookie |
| `POST /enterprise/auth/refresh` | 刷新访问令牌 |
| `GET /enterprise/email/settings` | 查看当前邮件投递配置 |
| `POST /enterprise/email/test` | 发送测试邮件 |
| `GET /enterprise/auth/action-link` | 查看邀请或重置链接状态 |
| `POST /enterprise/auth/action-link/consume` | 完成邀请接受或密码重置 |
| `POST /enterprise/organizations` | 创建组织 |
| `POST /enterprise/organizations/{id}/teams` | 创建团队 |
| `POST /enterprise/organizations/{id}/users` | 创建用户并发送邀请链接 |
| `POST /enterprise/organizations/{id}/users/{user_id}/invite-link` | 重新签发邀请链接 |
| `POST /enterprise/organizations/{id}/users/{user_id}/reset-password` | 发送密码重置链接 |
| `GET /enterprise/organizations/{id}/email-deliveries` | 查看邀请/重置邮件投递结果 |
| `POST /enterprise/organizations/{id}/email-deliveries/{delivery_id}/retry` | 重试失败或仅预览的邮件投递 |
| `POST /enterprise/organizations/{id}/assessments` | 提交一次评估 |
| `GET /enterprise/organizations/{id}/reports/summary` | 汇总看板 |
| `GET /enterprise/organizations/{id}/reports/trends` | 评分趋势 |
| `GET /enterprise/organizations/{id}/reports/benchmark` | 团队对比 |
| `GET /enterprise/organizations/{id}/reports/export` | 导出评估数据 |
| `GET /enterprise/organizations/{id}/audit-logs` | 查看审计日志 |
| `POST /enterprise/organizations/{id}/api-keys` | 生成 API Key |
| `POST /enterprise/organizations/{id}/webhooks` | 注册 Webhook |

## 许可与定价

当前商业基线是按组织销售的 B2B 年度订阅模型，采用席位区间，而不是纯按 seat 单价计费。

| 套餐 | 建议打包方式 | 建议起售价 |
| --- | --- | --- |
| `trial` | 14-30 天，10 用户，3 团队，每月 50 次评估 | 免费 |
| `starter` | 最多 100 用户，20 团队，每月 500 次评估 | USD 6,000/年 |
| `enterprise` | 默认含 500 用户，含 SSO / 导出 / benchmark / 优先支持 | USD 18,000/年起 |

建议的超额策略：

- 每增加 100 用户：+USD 2,000/年
- 每增加 1000 次/月评估：+USD 1,500/年
- 高级导入实施或私有支持通道：单独报价

运行许可证策略：

- 默认强制模式是 `strict`
- 试用客户会拿到带到期时间的签名 `trial` 许可证
- 付费客户会拿到签名 `starter` 或 `enterprise` 许可证
- 续费通过到期前签发新许可证完成
- 升级通过签发更高套餐或更大额度的新许可证完成

运行时使用 Ed25519 公钥验证许可证。私钥应离线保管，只向部署环境分发公钥。

## 客户生命周期

1. 只生成一次签名密钥对，并将私钥离线保存。
2. 将公钥随部署包提供，或直接内置到托管环境中。
3. 为评估阶段签发 `trial` 许可证。
4. 客户转化后，按约定的到期时间和额度签发 `starter` 或 `enterprise` 许可证。
5. 到期前重新签发续费许可证，并轮换 `LICENSE_KEY`。

## 默认标准回退

如果开源子模块没有检出，企业版服务会回退到内置评估标准，保证独立部署时依然可以完成评分。

## 开始使用企业版

当你需要集中治理、私有部署、面向合规的报表能力，以及围绕 DevOps Maturity 工作流的商业支持时，就应该使用企业版。

{{< enterprise-cta >}}
