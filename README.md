# InfraSec Review Expert

A comprehensive infra review skill for AI agents. Performs structured reviews with a senior DevOps/SRE lens, covering architecture, security, performance, and quality across infrastructure code and configs.

## Installation

**Cursor** — Copy `.cursor/rules/infra-review-expert.mdc` into your project's `.cursor/rules/`.

**Claude Code** — Copy `.claude/` (CLAUDE.md + rules/) into your project root.

**Or** clone this repo and symlink/copy the rules into your project.

## Features

- **Dockerfile Security** — ADD vs COPY (CVE), root USER, apt cache poisoning, secrets in layers, curl/wget without checksum
- **Terraform Security** — IAM least privilege, 0.0.0.0/0 ingress, publicly_accessible DB, S3 backend encryption, secrets in state
- **Kubernetes Security** — securityContext (runAsNonRoot, runAsUser), hostNetwork/hostPID, RBAC least privilege, missing resources/limits
- **Compliance Mapping** — CIS, NIST, PCI-DSS, SOC2 references for findings
- **Secrets Detection** — AWS keys, private keys, tokens (reference patterns in security-patterns/)

## Usage

When you ask for **infra review**, **security review**, or **DevOps review**, the agent follows SKILL.md and the domain checklists. Works automatically when you open or edit Dockerfile, `*.tf`, `k8s/**/*.yaml`, CI configs (if rules are installed).

## Workflow

1. **Scope** — Identify changed/opened infra files (Dockerfile, Terraform, K8s, CI)
2. **Dockerfile** — Apply dockerfile-expert.md (ADD/COPY, USER, apt, downloads, HEALTHCHECK)
3. **Terraform** — Apply terraform-expert.md (IAM, security groups, RDS, backend, null_resource)
4. **Kubernetes** — Apply kubernetes-expert.md (securityContext, RBAC, resources, host namespaces)
5. **Output** — Findings by severity (P0–P4) with rule_id, file:line, message, remediation
6. **Fix** — Agent suggests patches or step-by-step remediation for P0/P1

## Severity Levels

| Level | Name      | Action              |
|-------|-----------|---------------------|
| P0    | BLOCKER   | Must block merge    |
| P1    | CRITICAL  | Fix before prod     |
| P2    | HIGH      | Fix or follow-up    |
| P3    | MEDIUM    | Best practice       |
| P4    | LOW       | Optional / style    |

## Structure

```
infra-review-expert/
├── SKILL.md                 # Main skill definition
├── skills/
│   ├── dockerfile-expert.md # Dockerfile checklist
│   ├── terraform-expert.md  # Terraform checklist
│   └── kubernetes-expert.md # Kubernetes checklist
├── security-patterns/       # Reference for agent
│   ├── cve-patterns.json
│   ├── cis-benchmarks.yaml
│   └── secrets-patterns.toml
├── knowledge-base/
│   ├── compliance-mapping.yaml
│   └── aws-security.json
├── .cursor/rules/           # Cursor integration
│   └── infra-review-expert.mdc
└── .claude/                 # Claude Code integration
    ├── CLAUDE.md
    └── rules/infra-review-expert.md
```

## References

Each checklist provides detailed prompts and anti-patterns:

- **dockerfile-expert.md** — ADD vs COPY, USER root, apt-get cleanup, curl/wget checksums, HEALTHCHECK, .dockerignore
- **terraform-expert.md** — IAM Resource/actions wildcards, cidr_blocks 0.0.0.0/0, publicly_accessible, backend encrypt, null_resource triggers
- **kubernetes-expert.md** — runAsNonRoot, runAsUser, allowPrivilegeEscalation, hostNetwork, resources, RBAC verbs, ClusterRoleBinding vs RoleBinding

## License

MIT
