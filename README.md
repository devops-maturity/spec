# The DevOps Maturity Specification

[![DevOps Maturity](https://img.shields.io/badge/DevOps%20Maturity-Specification-yellow)](https://devops-maturity.github.io/)
[![Website](https://img.shields.io/website?url=https%3A%2F%2Fdevops-maturity.github.io&up_color=yellow)](https://devops-maturity.github.io/)

The DevOps Maturity specification is standardized to assess the maturity of DevOps practices. It is a set of criteria to help you measure and improve your DevOps maturity.

> DevOps Maturity is a **broad DevOps baseline assessment**. It does not replace specialized supply-chain security standards like [SLSA](https://slsa.dev/). See the [SLSA mapping](MAPPING-SLSA.md) for where the two frameworks overlap.

## How it compares

DevOps Maturity is a **breadth-first, automatable baseline** across the whole delivery lifecycle. Adjacent frameworks go deeper but narrower, or measure outcomes rather than practices — they complement it rather than compete with it.

| Framework | Primary focus | Best for |
|---|---|---|
| **DevOps Maturity** | DevOps **practices & controls** in place (build, quality, security, supply chain, analysis, reporting) | A fast, broad baseline + shareable badge for OSS **and** internal repos |
| [DORA metrics](https://dora.dev/) | Delivery **outcomes** (deploy frequency, lead time, MTTR, change-fail rate) | Tracking delivery performance once practices exist |
| [OpenSSF Scorecard](https://securityscorecards.dev/) | OSS security **health** (repo-level heuristics) | Hardening the security posture of a public repo |
| [OpenSSF Best Practices](https://www.bestpractices.dev/) | OSS best-practice **badge** (web SaaS, self-attested) | Earning a recognized OSS badge |
| [SLSA](https://slsa.dev/) | Supply-chain **integrity** (provenance & attestation) | Deep, verifiable supply-chain assurance |

**What makes it different:** breadth beyond security; automatable end-to-end (YAML in, JSON/badge out, [GitHub Action](https://github.com/devops-maturity/devops-maturity-action) in CI); AI-powered auto-assessment from repo metadata; and CLI / self-hostable web UI that works on private repos with no SaaS lock-in.

See the full comparison and "when to use which" on the [specification site](https://devops-maturity.github.io/).

## Schema

The assessment file format is defined by a [JSON Schema](schema/devops-maturity.schema.json). Criteria accept both simple boolean values and structured objects with evidence, verification metadata, and rationale:

```yaml
# Simple boolean — quick self-assessment
D101: true
D202: false

# Structured — auditable evidence
D403:
  status: true
  evidence:
    - type: workflow
      path: .github/workflows/release.yml
    - type: artifact-signature
      tool: cosign
  verified_by: devops-maturity-action
  verified_at: "2026-05-24T00:00:00Z"
  rationale: "Release workflow signs artifacts with Cosign keyless signing"
```

## 🎉 Show Your Support

If you find this useful, consider giving it a ⭐️ on [GitHub](https://github.com/devops-maturity/spec)! Your support helps others discover and adopt the spec.

## 🛡 Badges!

Let others know your project follows the DevOps Maturity specification. Add this badge to your repository README:

```markdown
[![DevOps Maturity](https://img.shields.io/badge/DevOps%20Maturity-Specification-yellow)](https://devops-maturity.github.io/)
```

## Additional Documents

- **[MAPPING-SLSA.md](MAPPING-SLSA.md)** — Maps DevOps Maturity criteria to SLSA requirements
- **[schema/devops-maturity.schema.json](schema/devops-maturity.schema.json)** — JSON Schema for the assessment YAML format

## 🤝 Contributing

We welcome contributions from the community!  
If you'd like to help improve the DevOps Maturity Specification — whether it's fixing a typo, improving the questions, or proposing a new maturity dimension — please check out our [contributing guidelines](CONTRIBUTING.md).

No contribution is too small. Thank you for helping us grow! 💛
