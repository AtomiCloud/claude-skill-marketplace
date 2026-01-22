# Skill Creator

> A comprehensive guide for creating effective Claude Agent Skills

## What is This?

This skill teaches Claude how to create high-quality Agent Skills. It's a meta-skill - a skill about making skills!

## What You Get

- **SKILL.md** - Complete guide on creating skills with templates and best practices
- **EXAMPLES.md** - 2 complete skill examples (simple and multi-file)

## When to Use

This skill activates when you:
- Want to create a new Claude skill
- Need help writing SKILL.md files
- Ask about skill structure or best practices
- Mention frontmatter fields or skill discovery
- Need examples of different skill types

## What It Covers

### Core Concepts
- What Agent Skills are and how they work
- Skill types (personal, project, plugin)
- Directory structure and file organization
- YAML frontmatter requirements

### Writing Effective Skills
- SKILL.md structure and templates
- Writing discoverable descriptions
- Using progressive disclosure
- Tool restrictions with `allowed-tools`
- Supporting files and scripts

### Best Practices
- Keeping skills focused
- Writing clear descriptions with triggers
- Testing and debugging
- Sharing with teams
- Version management

### Complete Examples
1. **Simple Skills** - Git commit helper, documentation generator
2. **Tool-Restricted Skills** - Read-only code reviewer, data analyzer
3. **Multi-File Skills** - PDF processing suite with supporting docs
4. **Domain-Specific** - API docs, test generators

## Quick Start

Just ask Claude things like:
- "Help me create a skill for [specific purpose]"
- "How do I write a good skill description?"
- "Show me an example of a [type] skill"
- "What's the structure for SKILL.md?"
- "How do I test my skill?"

## Files in This Skill

```
skill-creator/
├── SKILL.md              # Main guide (concepts + templates)
├── EXAMPLES.md           # 2 complete skill examples
└── README.md             # This file
```

## Key Takeaways

1. **Description is Critical**: The description field determines when Claude uses your skill
2. **Be Specific**: Include what it does, when to use it, and trigger keywords
3. **Keep Focused**: One skill = one capability
4. **Test Thoroughly**: Ask questions matching your description
5. **Use Progressive Disclosure**: Keep SKILL.md focused, link to detailed docs

## Installation

### As a Personal Skill
```bash
mkdir -p ~/.claude/skills/skill-creator
# Copy all files to this directory
```

### As a Project Skill
```bash
mkdir -p .claude/skills/skill-creator
# Copy all files to this directory
git add .claude/skills/
git commit -m "Add skill-creator skill"
```

### From Plugin Marketplace
```bash
/plugin marketplace add [marketplace-url]
/plugin install skill-creator
```

## Example Usage

**User:** "I want to create a skill that helps me write better commit messages"

**Claude will:**
1. Read this skill's documentation
2. Ask clarifying questions about requirements
3. Generate appropriate SKILL.md structure
4. Include proper frontmatter with good description
5. Provide instructions and examples
6. Suggest testing approaches

## Requirements

None - this skill uses only markdown documentation that Claude reads.

## Contributing

Have suggestions for improving skill creation guidance? Update the SKILL.md file with:
- Better examples
- Clearer explanations
- Additional best practices
- More troubleshooting tips

## Version History

- v1.0.0 (2025-01-22): Initial release
    - Complete skill creation guide
    - 7 example skills
    - Quick reference card
    - Troubleshooting section

## License

MIT License - Feel free to use and adapt this skill for your needs.

## Related Resources

- [Claude Code Skills Documentation](https://code.claude.com/docs/en/skills)
- [Agent Skills Best Practices](https://docs.claude.com/en/docs/agents-and-tools/agent-skills/best-practices)
- [Plugin Development Guide](https://code.claude.com/docs/en/plugins)
- [Agent Skills Blog Post](https://www.anthropic.com/engineering/equipping-agents-for-the-real-world-with-agent-skills)

---

**Made for the Claude Skills community**