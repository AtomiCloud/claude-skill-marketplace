---
name: skill-creator
description: Guide for creating effective Claude Agent Skills. Use when the user wants to create a new skill, needs help writing SKILL.md files, wants to understand skill structure, or asks about skill best practices, frontmatter fields, or skill discovery.
---

# Skill Creator

A comprehensive guide for creating effective Claude Agent Skills that extend Claude's capabilities.

## Documentation

This skill includes:
- **SKILL.md** (this file) - Complete guide on creating skills with concepts, instructions, and templates
- **[EXAMPLES.md](EXAMPLES.md)** - Two complete, production-ready skill examples (simple and multi-file)

## What are Agent Skills?

Agent Skills are modular capabilities that extend Claude's functionality through organized folders containing instructions, scripts, and resources. Skills are **model-invoked** - Claude autonomously decides when to use them based on the user's request and the skill's description.

## Quick Start: Create a Skill

### 1. Choose Skill Type

**Personal Skills** (`~/.claude/skills/`):
- Available across all your projects
- For individual workflows and preferences
- Experimental or personal productivity tools

**Project Skills** (`.claude/skills/`):
- Shared with your team via git
- For team workflows and conventions
- Project-specific expertise

**Plugin Skills**:
- Bundled with Claude Code plugins
- Distributed through plugin marketplaces
- Most professional distribution method

### 2. Create Skill Directory

```bash
# Personal skill
mkdir -p ~/.claude/skills/my-skill-name

# Project skill
mkdir -p .claude/skills/my-skill-name
```

### 3. Create SKILL.md

Every skill requires a `SKILL.md` file with YAML frontmatter and Markdown content.

## SKILL.md Structure

### Required Frontmatter Fields

```yaml
---
name: your-skill-name
description: Brief description of what this skill does and when to use it
---
```

**Field Requirements:**
- `name`: Lowercase letters, numbers, and hyphens only (max 64 characters)
- `description`: What the skill does AND when to use it (max 1024 characters)

### Optional Frontmatter Fields

```yaml
---
name: advanced-skill
description: Advanced skill with tool restrictions
allowed-tools: Read, Grep, Glob
---
```

**allowed-tools**: Restrict which tools Claude can use when skill is active
- Useful for read-only skills, security-sensitive workflows
- If not specified, Claude asks for permission normally
- Example tools: Read, Write, Edit, Grep, Glob, Bash

## Writing Effective SKILL.md Content

### Basic Template

```markdown
---
name: skill-name
description: What the skill does and when Claude should use it
---

# Skill Name

## Overview
Brief overview of the skill's purpose and capabilities.

## Instructions
Clear, step-by-step guidance for Claude:
1. First step with specific actions
2. Second step with examples
3. Third step with expected outcomes

## Examples
Show concrete usage examples with input and output.

## Best Practices
- Key principle 1
- Key principle 2
- Common pitfalls to avoid

## Requirements
List any dependencies, packages, or tools needed.
```

### Content Guidelines

**Be Specific and Actionable:**
- Provide step-by-step instructions
- Include concrete examples
- Show expected outputs
- Reference specific tools and commands

**Use Progressive Disclosure:**
- Keep SKILL.md focused on essentials
- Link to additional files for detailed reference
- Claude loads extra files only when needed

**Include Trigger Words:**
- Mention key terms users would say
- Include file extensions, technologies, or domains
- Help Claude discover when to activate the skill

## Adding Supporting Files

Create a multi-file skill structure:

```
my-skill/
├── SKILL.md           (required - main instructions)
├── REFERENCE.md       (optional - detailed API docs)
├── EXAMPLES.md        (optional - extended examples)
├── scripts/
│   └── helper.py      (optional - utility scripts)
└── templates/
    └── template.txt   (optional - reusable templates)
```

Reference these files from SKILL.md:

```markdown
For advanced usage, see [REFERENCE.md](REFERENCE.md).

Run the helper script:
```bash
python scripts/helper.py input.txt
```
```

## Writing Effective Descriptions

The description is CRITICAL for skill discovery. It must include:

1. **What the skill does** (capabilities)
2. **When to use it** (triggers)
3. **Key terms** (technologies, file types, domains)

### Examples

**❌ Too Vague:**
```yaml
description: Helps with documents
```

**✅ Specific and Discoverable:**
```yaml
description: Extract text and tables from PDF files, fill PDF forms, merge documents. Use when working with PDF files or when the user mentions PDFs, forms, or document extraction.
```

**❌ Missing Triggers:**
```yaml
description: Analyzes data
```

**✅ Clear Triggers:**
```yaml
description: Analyze Excel spreadsheets, create pivot tables, generate charts. Use when working with Excel files, spreadsheets, or analyzing tabular data in .xlsx format.
```

**❌ Too Broad:**
```yaml
description: For data tools
```

**✅ Focused Scope:**
```yaml
description: Analyze sales data in Excel files and CRM exports. Use for sales reports, pipeline analysis, and revenue tracking.
```

## Skill Examples by Complexity

For complete, production-ready examples with full code, see **[EXAMPLES.md](EXAMPLES.md)**, which includes:
- Simple single-file skill (Git commit helper)
- Multi-file skill with supporting documentation (Python project helper)

Below are minimal templates to get you started:

### Simple Skill Template

```yaml
---
name: skill-name
description: What it does, when to use it, with trigger keywords
---

# Skill Name

## Instructions
1. Step-by-step guidance
2. With clear actions
3. And expected outcomes

## Examples
Concrete usage example

## Requirements
Dependencies if any
```

### Skill with Tool Restrictions Template

```yaml
---
name: read-only-skill
description: Skill description with clear use cases
allowed-tools: Read, Grep, Glob
---

# Read-Only Skill

## Instructions
1. Use Read to examine files
2. Use Grep to search patterns
3. Use Glob to find files
4. Provide analysis without modifications
```

### Multi-File Skill Template

Structure:
```
skill-name/
├── SKILL.md           # Main instructions
├── REFERENCE.md       # Detailed reference
├── EXAMPLES.md        # Extended examples
└── scripts/           # Helper scripts
    └── helper.py
```

SKILL.md links to other files:
```markdown
For detailed reference, see [REFERENCE.md](REFERENCE.md).
For more examples, see [EXAMPLES.md](EXAMPLES.md).
```

## Testing Your Skill

### 1. Create the Skill
Write your SKILL.md with clear description and instructions.

### 2. Test Discovery
Ask questions that match your description:

```
# If description mentions "PDF files"
Can you help me extract text from this PDF?

# If description mentions "Excel spreadsheets"
Analyze this sales data spreadsheet
```

Claude should autonomously activate your skill - you don't explicitly invoke it.

### 3. Debug if Needed

**Claude doesn't use your skill?**
- Check description is specific enough
- Verify file path is correct
- Validate YAML syntax
- Ensure trigger words match user queries

**Check file exists:**
```bash
# Personal skill
ls ~/.claude/skills/my-skill/SKILL.md

# Project skill
ls .claude/skills/my-skill/SKILL.md
```

**View YAML frontmatter:**
```bash
cat SKILL.md | head -n 10
```

**Run in debug mode:**
```bash
claude --debug
```

## Best Practices

### Keep Skills Focused
One skill = one capability

**✅ Focused:**
- "PDF form filling"
- "Excel data analysis"
- "Git commit messages"

**❌ Too Broad:**
- "Document processing" (split into separate skills)
- "Data tools" (split by data type)

### Write Clear Descriptions
Include both WHAT and WHEN:

```yaml
description: Analyze Excel spreadsheets, create pivot tables, and generate charts. Use when working with Excel files, spreadsheets, or analyzing tabular data in .xlsx format.
```

### Use Progressive Disclosure
- Keep SKILL.md focused on essentials
- Link to detailed docs in separate files
- Claude loads additional content only when needed

### Document Dependencies
List required packages in description and instructions:

```yaml
description: PDF text extraction and form filling. Requires pypdf and pdfplumber packages.
```

```markdown
## Requirements
```bash
pip install pypdf pdfplumber
```
```

### Test with Real Users
- Have teammates use the skill
- Verify it activates when expected
- Check instructions are clear
- Gather feedback and iterate

## Common Issues & Solutions

### Issue: Skill Doesn't Activate

**Problem:** Description too vague
**Solution:** Add specific triggers and technologies

**Problem:** Wrong file location
**Solution:** Verify path (`~/.claude/skills/` or `.claude/skills/`)

**Problem:** Invalid YAML
**Solution:** Check syntax - opening/closing `---`, no tabs, correct indentation

### Issue: Multiple Skills Conflict

**Problem:** Similar descriptions confuse Claude
**Solution:** Use distinct trigger terms

Instead of:
```yaml
# Skill 1
description: For data analysis
# Skill 2  
description: For analyzing data
```

Use:
```yaml
# Skill 1
description: Analyze sales data in Excel files and CRM exports. Use for sales reports.
# Skill 2
description: Analyze log files and system metrics. Use for performance monitoring.
```

### Issue: Skill Has Errors

**Problem:** Missing dependencies
**Solution:** Claude auto-installs or asks permission - document requirements

**Problem:** Script permissions
**Solution:**
```bash
chmod +x .claude/skills/my-skill/scripts/*.py
```

**Problem:** Wrong path format
**Solution:** Use forward slashes: `scripts/helper.py` not `scripts\helper.py`

## Skill Naming Conventions

**Good Names:**
- `pdf-form-filler`
- `excel-pivot-tables`
- `git-commit-helper`
- `api-documentation-generator`

**Bad Names:**
- `PDFFormFiller` (no camelCase)
- `pdf_form_filler` (no underscores)
- `pdf form filler` (no spaces)
- `pdf-form-filler-v2-final-UPDATED` (keep it simple)

## Resources

- [Agent Skills Documentation](https://code.claude.com/docs/en/skills)
- [Best Practices Guide](https://docs.claude.com/en/docs/agents-and-tools/agent-skills/best-practices)
- [Plugin Development](https://code.claude.com/docs/en/plugins)
- [Agent Skills Blog Post](https://www.anthropic.com/engineering/equipping-agents-for-the-real-world-with-agent-skills)

## Quick Reference Card

```yaml
---
name: lowercase-with-hyphens
description: What it does + When to use it + Key trigger words
allowed-tools: Read, Write, Edit  # Optional
---

# Skill Title

## Instructions
1. Specific steps
2. With examples
3. And outcomes

## Examples
Concrete usage examples

## Requirements
Dependencies and tools needed
```

Remember: The description field is the most important part - it determines when Claude discovers and uses your skill!