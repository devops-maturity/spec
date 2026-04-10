---
type: enterprise
draft: false
layout: single
title: "Enterprise Edition"
description: "Deployment, governance, API, licensing, and pricing for DevOps Maturity Enterprise."
---

# DevOps Maturity Enterprise

DevOps Maturity Assessment Enterprise (DMAE) is the commercial edition of the open-source DevOps Maturity project. It extends the core assessment workflow with multi-team governance, compliance features, enterprise reporting, and commercial license enforcement.

## What Enterprise Adds

- Multi-tenancy for organizations, teams, and departments
- Role-based access control (RBAC) for enterprise administration
- JWT authentication, browser sessions, and API key access
- Custom assessment criteria and industry-specific templates
- Advanced reporting, trend analysis, benchmark comparison, and data export
- Audit logging and outbound webhooks
- SSO and LDAP/Active Directory integration skeletons
- Vendor-issued license management with runtime policy enforcement

## Feature Matrix

| Feature | Open Source | Enterprise |
| --- | :---: | :---: |
| DevOps maturity assessment | ✅ | ✅ |
| Score levels (WIP -> GOLD) | ✅ | ✅ |
| Social OAuth (Google / GitHub) | ✅ | ✅ |
| Multi-tenancy (organizations) | ❌ | ✅ |
| Team / department management | ❌ | ✅ |
| Role-based access control (RBAC) | ❌ | ✅ |
| JWT authentication + API keys | ❌ | ✅ |
| Custom assessment criteria | ❌ | ✅ |
| Industry templates | ❌ | ✅ |
| Advanced reporting & trend analysis | ❌ | ✅ |
| Team benchmark comparison | ❌ | ✅ |
| Data export | ❌ | ✅ |
| Audit logging | ❌ | ✅ |
| Outbound webhooks | ❌ | ✅ |
| SSO (SAML / OIDC) skeleton | ❌ | ✅ |
| LDAP / Active Directory sync skeleton | ❌ | ✅ |
| License management | ❌ | ✅ |

## Quick Start

### 1. Install dependencies

```bash
pip install -e ".[dev]"
```

### 2. Create a signing keypair

This is a vendor-side step. Keep the private key offline.

```bash
dmae-enterprise generate-license-keypair \
  --private-key-out ./secrets/vendor-license-private.pem \
  --public-key-out ./secrets/license-public.pem
```

### 3. Issue a trial or paid license

```bash
dmae-enterprise issue-license \
  --private-key-file ./secrets/vendor-license-private.pem \
  --org acme-corp \
  --tier trial \
  --expires 2026-05-09
```

### 4. Configure the environment

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

### 5. Start the server

```bash
dmae-enterprise server
```

First-run setup from the browser will:

- accept the signed license key
- create the first `SUPER_ADMIN`
- create the first organization
- persist runtime license overrides for self-hosted restarts

### 6. Optional CLI bootstrap

```bash
dmae-enterprise bootstrap-admin \
  --username platform-admin \
  --email admin@example.com \
  --org-name "Acme Corp" \
  --org-slug acme
```

## UI Endpoints

- Setup UI: `http://localhost:8000/`
- Login UI: `http://localhost:8000/login`
- Invite accept UI: `http://localhost:8000/welcome?token=...`
- Password reset UI: `http://localhost:8000/reset-password?token=...`
- App landing page: `http://localhost:8000/app`
- Swagger UI: `http://localhost:8000/enterprise/docs`
- ReDoc: `http://localhost:8000/enterprise/redoc`
- Health check: `http://localhost:8000/health`

The browser workspace at `/app` includes:

- organization overview and effective limits
- license tier and feature visibility
- user listing, email invitation, password reset links, and account activation controls
- team listing and creation
- recent audit activity

## Runtime Enforcement

The server enforces commercial policy at runtime:

- `strict` mode refuses startup without a valid, unexpired license
- license tiers gate premium features such as webhooks, advanced reporting, export, and benchmark reporting
- user, team, and monthly assessment quotas are enforced at request time
- trial, starter, and enterprise tiers can each carry custom overrides for users, teams, and assessments

## Authentication And API Access

Login with email and password:

```bash
curl -X POST http://localhost:8000/enterprise/auth/login \
  -H "Content-Type: application/json" \
  -d '{"email":"admin@example.com","password":"secret"}'
```

Use the returned bearer token:

```bash
curl http://localhost:8000/enterprise/organizations \
  -H "Authorization: Bearer <access_token>"
```

Or use an API key when the current license includes `api_access`:

```bash
curl http://localhost:8000/enterprise/organizations \
  -H "X-API-Key: dmae_<your_api_key>"
```

Browser sessions use `HttpOnly` cookies. Invite acceptance and password reset flows issue one-time links that land on `/welcome` and `/reset-password`.

For local development, keep `EMAIL_DELIVERY_MODE=log` and the admin UI will show link previews after sending an invite or reset, plus recent delivery history in the Email Delivery panel. For production, switch to `EMAIL_DELIVERY_MODE=smtp`, configure SMTP settings, and set `EMAIL_BRAND_NAME` and `EMAIL_SUPPORT_ADDRESS` to match customer-facing emails.

## Key API Endpoints

| Endpoint | Description |
| --- | --- |
| `POST /enterprise/auth/login` | Authenticate and receive JWT tokens |
| `POST /enterprise/auth/session/login` | Authenticate and establish browser session cookies |
| `POST /enterprise/auth/refresh` | Refresh an access token |
| `GET /enterprise/email/settings` | Inspect effective email delivery configuration |
| `POST /enterprise/email/test` | Send a test email with the current delivery settings |
| `GET /enterprise/auth/action-link` | Inspect an invite or password reset link |
| `POST /enterprise/auth/action-link/consume` | Complete an invite or password reset |
| `POST /enterprise/organizations` | Create an organization |
| `POST /enterprise/organizations/{id}/teams` | Create a team |
| `POST /enterprise/organizations/{id}/users` | Create a user and send invite link |
| `POST /enterprise/organizations/{id}/users/{user_id}/invite-link` | Reissue an invite link |
| `POST /enterprise/organizations/{id}/users/{user_id}/reset-password` | Send a password reset link |
| `GET /enterprise/organizations/{id}/email-deliveries` | View invite/reset delivery outcomes |
| `POST /enterprise/organizations/{id}/email-deliveries/{delivery_id}/retry` | Retry a failed or previewed invite/reset email |
| `POST /enterprise/organizations/{id}/assessments` | Submit an assessment |
| `GET /enterprise/organizations/{id}/reports/summary` | Summary dashboard |
| `GET /enterprise/organizations/{id}/reports/trends` | Score trend over time |
| `GET /enterprise/organizations/{id}/reports/benchmark` | Team comparison |
| `GET /enterprise/organizations/{id}/reports/export` | Export assessments |
| `GET /enterprise/organizations/{id}/audit-logs` | View audit trail |
| `POST /enterprise/organizations/{id}/api-keys` | Generate API key |
| `POST /enterprise/organizations/{id}/webhooks` | Register webhook |

## Licensing And Pricing

The current commercial baseline is a simple B2B annual subscription model sold per organization, with seat bands instead of pure per-seat billing.

| Tier | Recommended packaging | Suggested starting price |
| --- | --- | --- |
| `trial` | 14-30 days, 10 users, 3 teams, 50 assessments/month | Free |
| `starter` | Up to 100 users, 20 teams, 500 assessments/month | USD 6,000/year |
| `enterprise` | Up to 500 users included, SSO/export/benchmark/priority support | From USD 18,000/year |

Recommended overage policy:

- Additional 100 users: +USD 2,000/year
- Additional 1000 assessments/month: +USD 1,500/year
- Premium onboarding or private support channel: quoted separately

Operational license policy:

- default enforcement mode is `strict`
- trial customers receive a signed `trial` license with an expiry date
- paying customers receive a signed `starter` or `enterprise` license
- renewals are handled by issuing a fresh key before expiry
- upgrades are handled by issuing a new key with a higher tier or larger limits

The runtime verifies licenses with an Ed25519 public key. Keep the private key offline and only distribute the public key to deployed environments.

## Customer Lifecycle

1. Generate a signing keypair once and store the private key offline.
2. Send the public key with the deployment package or bake it into the hosted environment.
3. Issue a `trial` key for evaluation.
4. When the customer converts, issue a `starter` or `enterprise` key with the agreed expiry and limits.
5. Before expiry, issue a renewal key and rotate `LICENSE_KEY`.

## Default Criteria Fallback

If the open-source submodule is not checked out, the enterprise service falls back to a built-in assessment criteria set so scoring still works in a standalone deployment.

## Get Started With Enterprise

Use Enterprise when you need centralized governance, private deployment, compliance-oriented reporting, and licensed commercial support around the DevOps Maturity workflow.

{{< enterprise-cta >}}
