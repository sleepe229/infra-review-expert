# InfraSec Review Expert — Project memory

This project provides **expert skills for AI agents** that perform infrastructure and security review (Dockerfile, Terraform, Kubernetes, CI/CD).

## When doing infra or security review

- Follow the role and process in **SKILL.md** (project root). See @../SKILL.md for the full skill.
- Use the right checklist from **skills/**:
  - Dockerfile / Containerfile → **skills/dockerfile-expert.md**
  - Terraform (.tf, .tfvars) → **skills/terraform-expert.md**
  - Kubernetes YAML / Helm → **skills/kubernetes-expert.md**
- Output findings with **P0–P4**, rule_id, file:line, message, and remediation (or patch).
- Use **security-patterns/** and **knowledge-base/** when citing CVE, CIS, or compliance.

## Project layout

- **SKILL.md** — Main InfraSec Review Expert skill (role, priorities, output format).
- **skills/*.md** — Domain expert checklists (agent skills); **skills/*.py** — optional scripted checks.
- **security-patterns/** — CVE, CIS, secrets reference.
- **knowledge-base/** — Compliance mapping (CIS, NIST, PCI-DSS, SOC2).
- **runner/** — Optional Python CLI for CI.

Apply the skill with a senior DevOps lens; avoid false positives on intentional patterns.
