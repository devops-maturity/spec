# DevOps Maturity ↔ SLSA Mapping

This document maps DevOps Maturity criteria to relevant [SLSA (Supply-chain Levels for Software Artifacts)](https://slsa.dev/) concepts, helping teams understand where the two frameworks overlap.

## Relationship

DevOps Maturity is a **broader DevOps baseline assessment**, not a supply-chain security standard. It covers build, test, security, supply chain, analysis, and reporting — a wider surface than SLSA's focused scope on artifact integrity and provenance.

**DevOps Maturity does not replace SLSA.** SLSA provides a rigorous, verifiable supply-chain integrity framework. DevOps Maturity can help teams assess their readiness across the full DevOps spectrum, and the supply-chain-related criteria map naturally to SLSA requirements.

## Criteria Mapping

| DevOps Maturity | Description | SLSA Direction |
|---|---|---|
| **D401** Documented Build Process | Build steps are version-controlled and documented | Build process transparency — a prerequisite for Build Track reproducibility |
| **D402** CI/CD as Code | Pipelines and infrastructure defined as code | Build process definition — SLSA requires the build process to be defined and verifiable |
| **D403** Artifact Signing | Build artifacts are cryptographically signed | Artifact integrity / provenance distribution — aligns with SLSA's requirement for signed attestations |
| **D404** Dependency Pinning | All dependencies pinned to exact versions | Reproducibility support — reduces supply-chain attack surface |
| **D405** SBOM Generation | Automatically generate Software Bill of Materials | Supply-chain transparency — complements SLSA provenance with dependency inventory |
| **D603** Compliance Mapping & Auditability | Map controls to standards, provide audit-ready reports | Verified properties / audit evidence — supports the consumption and verification side |

## Where They Diverge

SLSA provides detailed requirements that go beyond DevOps Maturity:

- **Build Track** (Levels 1–3): Defines specific requirements for hermetic builds, isolated environments, parameterless builds, and ephemeral builders.
- **Source Track**: Covers source integrity protections (two-person review, branch protection, verified history).
- **Attestation Format**: SLSA defines standardized in-toto attestation formats (provenance, VSA).
- **Verification**: SLSA specifies policy-based verification of attestations.

DevOps Maturity covers areas SLSA does not:

- **Quality** (D2xx): Unit testing, functional testing, code coverage, accessibility.
- **Analysis** (D5xx): Static analysis, dynamic analysis, linting.
- **Reporting** (D6xx): Notifications, attached reports.
- **Security Scanning** (D3xx): Vulnerability and license scanning.

## Practical Path

A team can use DevOps Maturity as a **first-step health check** to identify gaps across the entire DevOps lifecycle. Once the supply-chain security criteria (D4xx) are addressed, SLSA provides the next level of rigor — with verifiable attestations, signed provenance, and policy-based enforcement.

For teams already pursuing SLSA compliance, DevOps Maturity can serve as a **companion assessment** covering the broader practices that SLSA does not address.
