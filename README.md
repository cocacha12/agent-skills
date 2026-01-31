# Agent Skills

A collection of high-quality agent skills to extend the capabilities of AI coding agents like Antigravity.

## Core Principles

To ensure skills are reliable, efficient, and easy for agents to use, we follow these core principles:

- **Modularity**: Each skill should focus on a single, well-defined domain or objective.
- **Context Efficiency**: Instructions are optimized to provide the maximum value with minimum token overhead.
- **Universal Design**: Skills are designed to work across various agentic platforms and IDEs.
- **Verification Driven**: Every skill includes guidelines for verifying its own output.

## Skill Structure

All skills in this repository are located in the `skills/` directory and follow a standardized layout:

```text
skills/
└── [skill-name]/
    ├── SKILL.md       # Core instructions and metadata
    ├── metadata.json  # Structured discovery metadata
    ├── scripts/       # (Optional) Automation tools
    └── examples/      # (Optional) Reference implementations
```

## Anatomy of a Skill

Each skill is defined primarily by its `SKILL.md` file, which includes:

1. **YAML Frontmatter**: Defines the skill's name, description, version, and author.
2. **Goal & Scope**: Clearly states what the skill is for and when it should be used.
3. **Internal Logic**: Ste-by-step instructions or decision trees for the agent.
4. **Best Practices**: Guardrails and optimization tips.

## Installation

You can install any skill from this repository directly into your workspace using the `skills` CLI:

```bash
npx skills add https://github.com/cocacha12/agent-skills --skill [skill-name]
```

Example:
```bash
npx skills add https://github.com/cocacha12/agent-skills --skill skill-antigravity
```

## Available Skills

| Skill | Description |
| :--- | :--- |
| **[skill-antigravity](file:///skills/skill-antigravity/SKILL.md)** | Core management rules for creating and managing Antigravity Skills. |

---
*Maintained by Muze AI*
