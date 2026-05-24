# The DevOps Maturity Specification

[![DevOps Maturity](https://img.shields.io/badge/DevOps%20Maturity-Specification-yellow)](https://devops-maturity.github.io/)
[![Website](https://img.shields.io/website?url=https%3A%2F%2Fdevops-maturity.github.io&up_color=yellow)](https://devops-maturity.github.io/)

The DevOps Maturity specification is standardized to assess the maturity of DevOps practices. It is a set of criteria to help you measure and improve your DevOps maturity.

> DevOps Maturity is a **broad DevOps baseline assessment**. It does not replace specialized supply-chain security standards like [SLSA](https://slsa.dev/). See the [SLSA mapping](MAPPING-SLSA.md) for where the two frameworks overlap.

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
