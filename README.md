# claude-skill-marketplace
> A curated collection of Claude skills to enhance your AI assistant capabilities

[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![Skills](https://img.shields.io/badge/skills-X-green.svg)](#available-skills)
[![Contributions Welcome](https://img.shields.io/badge/contributions-welcome-brightgreen.svg)](#contributing)

## 📋 Table of Contents

- [About](#about)
- [Quick Start](#quick-start)
- [Available Skills](#available-skills)
- [Installation](#installation)
- [Usage](#usage)
- [Skill Development](#skill-development)
- [Marketplace Structure](#marketplace-structure)
- [Support](#support)

## 🎯 About

This marketplace provides a centralized collection of Claude skills that extend Claude's capabilities across various domains including productivity, automation, data analysis, and more.

### What are Claude Skills?

Claude skills are modular extensions that provide Claude with:
- Specialized knowledge and best practices
- Domain-specific workflows and templates
- Custom tools and integrations
- Enhanced capabilities for specific tasks

## 🚀 Quick Start

### Prerequisites

- Claude Code installed and running
- Basic familiarity with command-line interfaces
- Git (for cloning repositories)

### Add This Marketplace

Add this marketplace to your Claude Code installation:

```bash
/plugin marketplace add yourusername/claude-skills-marketplace
```

Or using git URL:

```bash
/plugin marketplace add https://github.com/yourusername/claude-skills-marketplace.git
```

### Install a Skill

Browse and install skills interactively:

```bash
/plugin
```

Or install a specific skill:

```bash
/plugin install skill-name@claude-skills-marketplace
```

## 📦 Available Skills

### Development

| Skill                        | Description | Version | Category |
|------------------------------|-------------|--------|----------|
| [skill-creator](#)           | Guide for creating effective Claude Agent Skills. | 1.0.0  | Development |

## 💻 Installation

### Method 1: Add Marketplace (Recommended)

```bash
# Add the marketplace
/plugin marketplace add yourusername/claude-skills-marketplace

# Verify marketplace was added
/plugin marketplace list

# Browse and install skills
/plugin
```

### Method 2: Direct Skill Installation

If you know the specific skill you want:

```bash
/plugin install skill-name@claude-skills-marketplace
```

### Method 3: Team Configuration

For team-wide deployment, add to your project's `.claude/settings.json`:

```json
{
  "extraKnownMarketplaces": {
    "claude-skills-marketplace": {
      "source": {
        "source": "github",
        "repo": "yourusername/claude-skills-marketplace"
      }
    }
  },
  "enabledPlugins": [
    "skill-name-1",
    "skill-name-2"
  ]
}
```

## 📖 Usage

### Basic Usage

Once a skill is installed, Claude automatically has access to its capabilities. Simply interact with Claude naturally:

```
You: "Can you help me analyze this dataset?"
Claude: [Uses data-analysis-toolkit skill to provide specialized assistance]
```

### Skill-Specific Commands

Some skills may provide custom commands. Check individual skill documentation for details:

```bash
# List all installed plugins and their commands
/plugin list
```

### Update Skills

Keep your skills up to date:

```bash
# Update marketplace metadata
/plugin marketplace update claude-skills-marketplace

# Update specific skill
/plugin update skill-name
```

## 🛠️ Skill Development

### Creating a New Skill

1. **Create skill directory structure:**

```
skills/
└── your-skill-name/
    ├── SKILL.md          # Main skill documentation
    ├── README.md         # User-facing documentation
    ├── commands/         # Optional: Custom commands
    ├── agents/           # Optional: Specialized agents
    └── examples/         # Optional: Usage examples
```

2. **Write SKILL.md:**

This is the core file that Claude reads. Include:
- Overview and purpose
- Best practices and methodologies
- Examples and templates
- Configuration options

3. **Add to marketplace.json:**

```json
{
  "name": "your-skill-name",
  "source": "./skills/your-skill-name",
  "description": "Brief description of what your skill does",
  "version": "1.0.0",
  "author": {
    "name": "Your Name",
    "email": "your.email@example.com"
  },
  "license": "MIT",
  "keywords": ["relevant", "keywords"],
  "category": "appropriate-category"
}
```

### Testing Your Skill

Before submitting, test locally:

```bash
# Add local marketplace
/plugin marketplace add ./path/to/your/repo

# Install and test your skill
/plugin install your-skill-name@local-marketplace-name
```

### Skill Best Practices

- **Clear documentation**: Explain what the skill does and how to use it
- **Specific scope**: Focus on a well-defined problem or domain
- **Examples**: Provide concrete examples of usage
- **Versioning**: Use semantic versioning (MAJOR.MINOR.PATCH)
- **Dependencies**: Document any external requirements
- **Testing**: Include test cases or validation examples

## 📁 Marketplace Structure

```
claude-skills-marketplace/
├── .claude-plugin/
│   └── marketplace.json      # Marketplace catalog
├── skills/                   # Local skills directory
│   ├── skill-1/
│   │   ├── SKILL.md
│   │   └── README.md
│   └── skill-2/
│       ├── SKILL.md
│       └── README.md
├── examples/                 # Usage examples
├── README.md                 # This file
```

### Marketplace.json Schema

The marketplace catalog follows this structure:

```json
{
  "name": "marketplace-identifier",
  "owner": {
    "name": "Maintainer Name",
    "email": "contact@example.com"
  },
  "metadata": {
    "description": "Marketplace description",
    "version": "1.0.0",
    "pluginRoot": "./skills"
  },
  "plugins": [
    {
      "name": "skill-name",
      "source": "skill-location",
      "description": "Skill description",
      "version": "1.0.0",
      "author": {...},
      "license": "MIT",
      "keywords": [...],
      "category": "category-name"
    }
  ]
}
```

## 🆘 Support

### Getting Help

- **Issues**: Report bugs or request features via [GitHub Issues](https://github.com/yourusername/claude-skills-marketplace/issues)
- **Email**: Contact us at speedykrab98@gmail.com

### FAQ

**Q: How do I update an installed skill?**
A: Run `/plugin marketplace update claude-skills-marketplace` to refresh the marketplace, then `/plugin update skill-name`.

**Q: Can I use multiple marketplaces?**
A: Yes! You can add multiple marketplaces and install skills from any of them.

**Q: How do I remove a skill?**
A: Use `/plugin uninstall skill-name` to remove an installed skill.

**Q: Are these skills official Anthropic products?**
A: No, this is a community marketplace. Skills are contributed by various developers.

**Q: How do I report a security issue?**
A: Please email security@example.com with details. Do not post security issues publicly.


---