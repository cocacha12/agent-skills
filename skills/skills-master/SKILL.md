---
name: skills-master
description: Provides core knowledge and instructions for creating, documenting, and managing Antigravity Skills. Use this skill when the user asks to create a new skill, update metadata, or understand the skill system.
---

# Antigravity Skills Master

This skill empowers Antigravity agents to extend their own capabilities through the creation and management of modular skills.

## What are Skills?
Skills are reusable packages of knowledge stored in the workspace. They enable agents to handle specific tasks with high precision using pre-vetted instructions, scripts, and examples.

## Skill Structure
Skills are organized in folders within `.agent/skills/`:
- `SKILL.md`: (Required) The core instruction set with YAML frontmatter.
- `scripts/`: (Optional) Custom scripts for task automation.
- `examples/`: (Optional) Reference implementations.
- `resources/`: (Optional) Static assets or templates.

## Creating a New Skill
1. **Identify the Scope**: Ensure the skill addresses a single, well-defined task.
2. **Create the Folder**: `.agent/skills/<skill-name>/`
3. **Draft the `SKILL.md`**:
   - Start with YAML frontmatter (name and description).
   - Write instructions in clear, actionable markdown.
   - Include checklists and decision-making logic.
4. **Define the Description**: The description is critical for discovery. Use third-person and specific keywords.

## Managing Skills
- **Discovery**: The agent scans skill descriptions during task planning.
- **Activation**: The agent reads the full `SKILL.md` when a match is found.
- **Updates**: Refine instructions based on execution feedback to improve future performance.

## Best Practices
- **Focused & Modular**: Avoid monolithic skills.
- **Progressive Disclosure**: Keep instructions concise; link to external resources or scripts for depth.
- **Self-Correction**: Include common pitfalls and how to avoid them.
