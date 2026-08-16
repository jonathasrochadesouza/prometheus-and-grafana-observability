# AGENTS.md


## Technology Stack

- Prometheus
- Grafana

## Context
-> ai/

- Skills in 'ai/skills/' folder
- Agents and subagents in 'ai/agents/' folder

### Skills
-> ai/skills/

- committing-changes: When asked to create a Git commit or commit staged changes, read and follow `ai/skills/committing-changes/SKILL.md` before taking action.
- java-best-practices: When implementing, refactoring, debugging, testing, or reviewing Java, Spring Boot, Maven, JUnit, or Mockito code, read and follow `ai/skills/java-best-practices/SKILL.md` before taking action.
- terraform-best-practices: When implementing, refactoring, debugging, testing, or reviewing Terraform configuration, modules, state workflows, plans, or infrastructure CI, read and follow `ai/skills/terraform-best-practices/SKILL.md` before taking action.

### Agents
-> ai/agents/

### Rules
-> ai/instructions/repository-rules.md

## Infrastructure Safety

- Kiro must never execute Terraform commands that modify infrastructure or state, including `apply`, `destroy`, `import`, state mutation, workspace changes, or backend migration. Only the user may perform these operations.
- Kiro may run non-mutating checks such as `terraform fmt` and `terraform validate`. Run `terraform plan` only when the user explicitly requests it.
