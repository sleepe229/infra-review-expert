# InfraSec Review Expert

**Expert skills for AI agents** — infrastructure and security review with a senior DevOps/SRE lens. Covers Dockerfile, Terraform, Kubernetes, CI/CD and related configs.

## What’s in the repo

- **SKILL.md** — Main skill: role, priorities (P0–P4), output format.
- **skills/*.md** — Domain checklists: Dockerfile, Terraform, Kubernetes.
- **security-patterns/** — CVE, CIS, secrets (reference for the agent).
- **knowledge-base/** — Compliance mapping (CIS, NIST, PCI-DSS, SOC2).
- **.cursor/rules/** — Cursor: rule for infra files.
- **.claude/** — Claude Code: project memory + path-specific rule.

## Quick start (for agents)

1. Follow **SKILL.md** when the user asks for infra/security/DevOps review.
2. Use the right checklist: **skills/dockerfile-expert.md**, **skills/terraform-expert.md**, **skills/kubernetes-expert.md**.
3. Output findings with `[P0|P1|P2|P3|P4]`, rule_id, file:line, message, remediation (or patch).

**Cursor** — rule in `.cursor/rules/infra-review-expert.mdc`.  
**Claude Code** — `.claude/CLAUDE.md` and `.claude/rules/infra-review-expert.md`.

## Priority

| P0 BLOCKER | P1 CRITICAL | P2 HIGH | P3 MEDIUM | P4 LOW |
|------------|--------------|---------|-----------|--------|
| CVE, secrets, root, 0.0.0.0/0 | Privilege escalation, missing limits | Performance, HEALTHCHECK | Best practices | Formatting |

## License

MIT
