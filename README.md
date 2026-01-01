# Simple Skills

A collection of Claude Code skills for various tools and services.

## What are Claude Code Skills?

Claude Code skills are markdown files that teach Claude how to perform specific tasks. Skills are automatically invoked by Claude when they match your request based on the skill's description.

## Available Skills

### Gitea
**Location:** `gitea/`
**Description:** Interact with Gitea (self-hosted Git service) using the Gitea API for repository, issue, and pull request management.

## Installation

### Personal Installation (Available Across All Projects)
```bash
# Copy skills to your personal Claude skills directory
cp -r gitea ~/.claude/skills/
```

### Project Installation (Available Only in This Repository)
```bash
# Copy skills to project's Claude skills directory
cp -r gitea .claude/skills/
```

## Usage

Once installed, Claude will automatically use these skills when you make requests that match their descriptions. For example:

- "Create a new repository on my Gitea instance"
- "List all issues in my Gitea repository"
- "Create a pull request on Gitea"

## Structure

Each skill follows this structure:

```
skill-name/
├── SKILL.md              # Main skill file with metadata and instructions
└── ...                   # Additional supporting files (optional)
```

## Creating New Skills

To add a new skill to this collection:

1. Create a new directory with the skill name (lowercase, hyphens only)
2. Create a `SKILL.md` file with:
   - YAML metadata (name, description, optional allowed-tools)
   - Markdown instructions for Claude
3. Test the skill by installing it and asking Claude to perform related tasks

### Example SKILL.md Structure

```yaml
---
name: your-skill-name
description: Brief description of what this skill does and when to use it
allowed-tools: Bash, Read, Write
---

# Your Skill Name

## Instructions
Clear, step-by-step guidance for Claude.
```

## Contributing

Feel free to add new skills to this collection! Each skill should:
- Have a clear, specific purpose
- Include comprehensive instructions
- Follow the standard skill format
- Be well-documented

## Resources

- [Claude Code Documentation](https://docs.anthropic.com/claude/docs)
- [Creating Custom Skills](https://docs.anthropic.com/claude/docs/custom-skills)
