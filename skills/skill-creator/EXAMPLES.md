# Skill Examples

Two complete examples demonstrating different skill patterns.

---

## Example 1: Simple Single-File Skill

**Git Commit Message Helper** - Generate clear, conventional commit messages

### Directory Structure

```
git-commit-helper/
└── SKILL.md
```

### SKILL.md Content

This skill has frontmatter with `name` and `description`, followed by instructions.

**Key sections:**
- Instructions for generating commits
- Commit type definitions (feat, fix, docs, etc)
- Example output format
- Best practices

**Description field:**
> Generate conventional commit messages from git diffs. Use when writing commit messages, reviewing staged changes, or when user mentions git, commits, or version control.

**Instructions tell Claude to:**
1. Ask user to run `git diff --staged`
2. Analyze what changed and why
3. Generate message in format: `type(scope): description`
4. Include bullet points explaining changes
5. Reference issue numbers

**Example output the skill produces:**

```
feat(auth): add user login endpoint

- Implement POST /api/login with JWT authentication
- Add password hashing with bcrypt
- Include input validation for email and password

Closes #42
```

**Commit types defined:**
- `feat` - New feature
- `fix` - Bug fix
- `docs` - Documentation changes
- `style` - Code formatting
- `refactor` - Code restructuring
- `test` - Adding tests
- `chore` - Maintenance tasks

---

## Example 2: Multi-File Skill

**Python Project Helper** - Guide on Python project structure and setup

### Directory Structure

```
python-helper/
├── SKILL.md
└── STRUCTURE-GUIDE.md
```

### SKILL.md Content

Main file with quick setup guide and references to detailed docs.

**Description field:**
> Help set up Python projects with proper structure and virtual environments. Use when user asks about Python project setup, structure, or virtual environments.

**Key sections:**
- Quick Setup Guide (commands for creating project)
- Install Dependencies (pip commands)
- Project Structure overview
- Common Commands (testing, formatting, type checking)
- Link to STRUCTURE-GUIDE.md for details

**Setup commands it provides:**

```bash
mkdir my-project
cd my-project
python -m venv venv
source venv/bin/activate
mkdir src tests
touch README.md requirements.txt .gitignore
```

**Common commands it teaches:**

```bash
# Run tests
pytest tests/

# Format code
black src/

# Type check
mypy src/
```

### STRUCTURE-GUIDE.md Content

Supporting file with detailed project layout examples.

**Includes three structure patterns:**

1. **Simple Script Project** - For single-file scripts
2. **Application Project** - For multi-module applications
3. **Package Project** - For distributable packages

**Example structure shown:**

```
my-app/
├── src/
│   ├── __init__.py
│   ├── main.py
│   └── utils/
├── tests/
├── requirements.txt
└── README.md
```

**Explains important files:**
- `requirements.txt` - Package dependencies
- `README.md` - Project documentation
- `.gitignore` - Files to exclude from git
- `__init__.py` - Marks directory as Python package

---

## Key Differences

| Aspect | Example 1 (Git Helper) | Example 2 (Python Helper) |
|--------|------------------------|---------------------------|
| **Files** | Single SKILL.md | SKILL.md + STRUCTURE-GUIDE.md |
| **Complexity** | Simple | Multi-file |
| **Pattern** | All-in-one | Progressive disclosure |
| **Best for** | Focused single tasks | Complex multi-part guidance |

## What Makes These Good Skills

**Both examples demonstrate:**

✅ **Clear descriptions** with trigger words (git, commits, Python, project setup)

✅ **Specific use cases** so Claude knows when to activate

✅ **Step-by-step instructions** that are easy to follow

✅ **Concrete examples** showing actual output

✅ **Proper structure** with frontmatter and organized content

**The multi-file example shows:**

✅ **Progressive disclosure** - Quick guide in main file, details in supporting file

✅ **File references** - SKILL.md links to STRUCTURE-GUIDE.md

✅ **Organized information** - Separates quick reference from comprehensive guide