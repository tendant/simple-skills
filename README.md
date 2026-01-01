# Simple Skills

A collection of Claude Code skills for various tools and services.

## What are Claude Code Skills?

Claude Code skills are markdown files that teach Claude how to perform specific tasks. Skills are automatically invoked by Claude when they match your request based on the skill's description.

## Available Skills

### Gitea
**Location:** `gitea/`
**Description:** Interact with Gitea (self-hosted Git service) using the Gitea API for repository, issue, and pull request management.

## Quick Start

```bash
# Install all skills from GitHub
git clone https://github.com/tendant/simple-skills.git /tmp/simple-skills
cp -r /tmp/simple-skills/*/ ~/.claude/skills/
rm -rf /tmp/simple-skills

# Restart Claude Code to load the new skills
```

## Installation

### Option 1: Install from GitHub (Recommended)

Clone the repository and install skills directly from GitHub:

```bash
# Clone the repository to a temporary location
git clone https://github.com/tendant/simple-skills.git /tmp/simple-skills

# Install all skills to your personal Claude skills directory
cp -r /tmp/simple-skills/*/  ~/.claude/skills/

# Or install specific skills only
cp -r /tmp/simple-skills/gitea ~/.claude/skills/

# Clean up
rm -rf /tmp/simple-skills
```

### Option 2: Install from Local Clone

If you've already cloned this repository:

```bash
# Install all skills to your personal Claude skills directory
cp -r */  ~/.claude/skills/

# Or install specific skills only
cp -r gitea ~/.claude/skills/
```

### Option 3: Project-Specific Installation

To make skills available only in a specific project:

```bash
# From the cloned repository
mkdir -p /path/to/your/project/.claude/skills
cp -r gitea /path/to/your/project/.claude/skills/

# Or from within your project directory
git clone https://github.com/tendant/simple-skills.git /tmp/simple-skills
mkdir -p .claude/skills
cp -r /tmp/simple-skills/gitea .claude/skills/
rm -rf /tmp/simple-skills
```

> **Note:** After installing or updating skills, restart Claude Code for the changes to take effect.

## Updating Skills

To update your installed skills with the latest versions from GitHub:

```bash
# Pull the latest changes
git clone https://github.com/tendant/simple-skills.git /tmp/simple-skills

# Update all skills
cp -r /tmp/simple-skills/*/ ~/.claude/skills/

# Or update specific skills
cp -r /tmp/simple-skills/gitea ~/.claude/skills/

# Clean up
rm -rf /tmp/simple-skills

# Restart Claude Code to load the updates
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

We welcome contributions! To add a new skill:

1. Fork the repository at https://github.com/tendant/simple-skills
2. Create a new directory with the skill name (lowercase, hyphens only)
3. Add a `SKILL.md` file following the standard format
4. Test the skill locally
5. Submit a pull request

Each skill should:
- Have a clear, specific purpose
- Include comprehensive instructions
- Follow the standard skill format
- Be well-documented
- Include usage examples

## Resources

- [Claude Code Documentation](https://docs.anthropic.com/claude/docs)
- [Creating Custom Skills](https://docs.anthropic.com/claude/docs/custom-skills)
