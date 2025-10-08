# Contributing to Claude Commands

Thank you for your interest in contributing! This guide will help you add new commands or improve existing ones.

---

## 🎯 Ways to Contribute

- 🆕 **Add new commands** - Share your workflows with the community
- 📖 **Improve documentation** - Make guides clearer, add examples
- 🐛 **Fix bugs** - Report or fix issues
- 💡 **Suggest ideas** - Open issues with command proposals
- ⭐ **Share feedback** - Let us know how commands work for you

---

## 🚀 Quick Start

### 1. Fork the Repository

Click **Fork** at https://github.com/rglaubitz/Claude-Commands

### 2. Clone Your Fork

```bash
git clone https://github.com/YOUR-USERNAME/Claude-Commands.git
cd Claude-Commands
```

### 3. Create a Branch

```bash
git checkout -b feature/my-new-command
```

### 4. Make Your Changes

See sections below for guidelines.

### 5. Commit and Push

```bash
git add .
git commit -m "Add [command-name] command"
git push origin feature/my-new-command
```

### 6. Create Pull Request

Go to GitHub and create a PR from your fork.

---

## 📂 Command Structure

Each command should follow this structure:

```
commands/
└── [command-name]/
    ├── command.md              # Main command prompt (required)
    ├── alias.md                # Short alias (optional but recommended)
    ├── README.md               # Comprehensive documentation (required)
    └── examples/
        ├── input-example.md    # Example inputs (recommended)
        └── output-example.md   # Expected outputs (recommended)
```

---

## 📝 Creating a New Command

### Step 1: Create Command Directory

```bash
mkdir -p commands/my-command/examples
```

### Step 2: Create `command.md`

This is the **main prompt** that Claude Code executes.

**Template:**
```markdown
# [Command Name]

[Brief description of what this command does]

## Overview

[1-2 paragraphs explaining the purpose]

## Workflow

1. **Step 1 Name**
   - Detailed instructions
   - What Claude should do

2. **Step 2 Name**
   - More instructions
   - Expected behavior

## Quality Standards

**Requirements:**
- Requirement 1
- Requirement 2

## Tools Available

Use these tools:
- `Tool1` - Purpose
- `Tool2` - Purpose

## Execution Instructions

1. Do X
2. Then Y
3. Finally Z

## Success Criteria

- ✅ Criterion 1
- ✅ Criterion 2

## Example Output

```
Expected output format
```

---

**Now execute this workflow...**
```

**Key principles:**
- Be **specific and detailed**
- Use **clear section headers**
- Provide **examples**
- Define **success criteria**
- List **available tools**

### Step 3: Create `alias.md` (Optional)

Short alias for convenience.

**Template:**
```markdown
# [Short Name] - [Full Name]

**Alias for:** `/[command-name]`

[One sentence description]

## Usage

```bash
/[alias] <parameters>
```

---

See `/[command-name]` for full documentation.
```

**Example:**
```markdown
# RDF - Research, Document, Finalize

**Alias for:** `/research-document-finalize`

Execute the complete Research, Document, Finalization workflow.

## Usage

```bash
/rdf <feature-name>
```

---

See `/research-document-finalize` for full documentation.
```

### Step 4: Create `README.md`

Comprehensive documentation for users.

**Template sections:**

```markdown
# [Command Name]

[Tagline]

---

## 📋 Overview

[What it does, why it's useful]

## 🎯 What It Does

[Detailed breakdown]

## 🚀 Usage

[Usage examples]

## 📊 Real-World Example

[Complete example from actual use]

## 🛠️ Requirements

[What users need to install/configure]

## 📐 Quality Standards

[What output looks like]

## 🎓 Use Cases

[When to use this command]

## ⚙️ Installation

[How to install]

## 🔧 Customization

[How to modify for their needs]

## 📈 Success Metrics

[Results users can expect]

## 🐛 Troubleshooting

[Common issues and fixes]

## 💡 Pro Tips

[Best practices]

## 🤝 Contributing

[Link to this file]

## 📜 License

[MIT]
```

**See [`commands/research-document-finalize/README.md`](commands/research-document-finalize/README.md) for a complete example.**

### Step 5: Add Examples

Create example files showing:
- **Input:** What user types
- **Output:** What Claude produces

**Example structure:**
```
examples/
├── input-example.md     # User command + context
└── output-example.md    # Complete output
```

---

## ✅ Command Quality Checklist

Before submitting, ensure:

### Functionality
- [ ] Command executes successfully in Claude Code
- [ ] Handles edge cases (missing parameters, errors)
- [ ] Uses appropriate MCP tools (if needed)
- [ ] Produces consistent output

### Documentation
- [ ] `command.md` is clear and specific
- [ ] `README.md` is comprehensive
- [ ] Examples are included
- [ ] Installation instructions are clear

### Code Quality
- [ ] Follows project structure
- [ ] Markdown is properly formatted
- [ ] Links work correctly
- [ ] No spelling errors

### User Experience
- [ ] Command is intuitive to use
- [ ] Error messages are helpful
- [ ] Output is well-formatted
- [ ] Success criteria are clear

---

## 📖 Documentation Guidelines

### Writing Style

- **Be concise:** Users want quick answers
- **Be specific:** Avoid vague instructions
- **Use examples:** Show, don't just tell
- **Format well:** Use headers, lists, code blocks

### Code Examples

**Good:**
```python
# Complete, working example
def process_data(data: List[str]) -> Dict[str, int]:
    """Process data and return counts."""
    return {item: len(item) for item in data}
```

**Bad:**
```python
# Vague, incomplete
def process_data(data):
    # Do something
    return result
```

### Markdown Formatting

Use:
- `##` for main sections
- `###` for subsections
- ` ``` ` for code blocks
- `**bold**` for emphasis
- `[links](urls)` for references

---

## 🧪 Testing Your Command

### Local Testing

1. **Copy to commands directory:**
   ```bash
   cp commands/my-command/command.md ~/.claude/commands/my-command.md
   cp commands/my-command/alias.md ~/.claude/commands/mc.md  # if alias
   ```

2. **Test in Claude Code:**
   ```
   /my-command test-input
   ```

3. **Verify output:**
   - Executes without errors
   - Produces expected results
   - Handles edge cases

### Quality Check

Run through the checklist above before submitting.

---

## 🎨 Naming Conventions

### Command Names

- Use **lowercase** with **hyphens**: `research-document-finalize`
- Be **descriptive**: Avoid abbreviations
- Keep **short**: 2-4 words

**Good:**
- `code-review`
- `benchmark-performance`
- `generate-tests`

**Bad:**
- `CR` (too short, not descriptive)
- `CodeReviewWithAutomatedFixes` (too long, camelCase)

### Alias Names

- 2-4 characters
- Easy to remember
- Related to command

**Examples:**
- `/rdf` → research-document-finalize
- `/cr` → code-review
- `/bench` → benchmark-performance

---

## 🔧 MCP Tool Usage

If your command uses MCP tools:

### Document Requirements

In `README.md`, list required MCP servers:

```markdown
## Requirements

### MCP Servers

1. **[Server Name]** - What it's used for
   ```bash
   claude mcp add [server] [command]
   ```
```

### Handle Missing Tools

In `command.md`, handle cases where tools aren't available:

```markdown
## Execution Instructions

1. **Check for required tools**
   - If Exa is not available, inform user and skip web research
   - If GitHub is not available, try alternative methods

2. **Graceful degradation**
   - Provide helpful error messages
   - Suggest alternatives
```

---

## 📋 Pull Request Guidelines

### PR Title

Format: `[Type] Brief description`

**Types:**
- `feat:` New command
- `docs:` Documentation improvements
- `fix:` Bug fixes
- `refactor:` Code refactoring
- `test:` Adding tests

**Examples:**
- `feat: Add code-review command`
- `docs: Improve RDF installation instructions`
- `fix: Handle missing MCP servers gracefully`

### PR Description

Include:

```markdown
## What This PR Does

[Brief description]

## Command Name

`/[command-name]` or `/[alias]`

## Changes Made

- Change 1
- Change 2

## Testing

- [x] Tested locally
- [x] Documentation reviewed
- [x] Examples work

## Screenshots (if applicable)

[Screenshots of command output]
```

### Review Process

1. **Submit PR** - We'll review within 48 hours
2. **Address feedback** - Make requested changes
3. **Get approval** - Maintainer approves
4. **Merge** - Your command is live!

---

## 🏆 Recognition

Contributors get:
- ✅ Listed in command README as creator
- ✅ Mentioned in release notes
- ✅ Contributor badge in repo

---

## 💬 Getting Help

- **Questions:** [GitHub Discussions](https://github.com/rglaubitz/Claude-Commands/discussions)
- **Bugs:** [GitHub Issues](https://github.com/rglaubitz/Claude-Commands/issues)
- **Ideas:** [GitHub Discussions - Ideas](https://github.com/rglaubitz/Claude-Commands/discussions/categories/ideas)

---

## 📜 Code of Conduct

We follow the [Contributor Covenant Code of Conduct](https://www.contributor-covenant.org/version/2/1/code_of_conduct/).

**TL;DR:**
- Be respectful
- Be inclusive
- Be constructive

---

## 🎓 Learning Resources

### Claude Code Documentation

- [Official Docs](https://docs.claude.com/claude-code)
- [Slash Commands Guide](https://docs.claude.com/claude-code/slash-commands)
- [MCP Servers](https://docs.claude.com/claude-code/mcp)

### Markdown Guides

- [GitHub Markdown Guide](https://guides.github.com/features/mastering-markdown/)
- [CommonMark Spec](https://commonmark.org/)

---

## 🚀 Example Contribution Flow

**Scenario:** You want to add a `/code-review` command

**Steps:**

1. **Fork and clone**
   ```bash
   git clone https://github.com/YOUR-USERNAME/Claude-Commands.git
   cd Claude-Commands
   git checkout -b feat/code-review
   ```

2. **Create structure**
   ```bash
   mkdir -p commands/code-review/examples
   ```

3. **Create files**
   ```bash
   touch commands/code-review/command.md
   touch commands/code-review/alias.md
   touch commands/code-review/README.md
   touch commands/code-review/examples/input-example.md
   touch commands/code-review/examples/output-example.md
   ```

4. **Write command** (see templates above)

5. **Test locally**
   ```bash
   cp commands/code-review/command.md ~/.claude/commands/code-review.md
   # Test in Claude Code
   ```

6. **Commit and push**
   ```bash
   git add commands/code-review/
   git commit -m "feat: Add code-review command"
   git push origin feat/code-review
   ```

7. **Create PR** on GitHub

8. **Celebrate!** 🎉 You've contributed!

---

## 📊 What Makes a Good Command?

### ✅ Good Command Characteristics

- **Solves a real problem** - Addresses actual pain points
- **Saves time** - Automates multi-step processes
- **Repeatable** - Works consistently every time
- **Well-documented** - Easy for others to use
- **High quality** - Produces reliable output

### ❌ Avoid

- **Too specific** - Only works for one project
- **Too vague** - Doesn't provide clear instructions
- **Duplicate** - Already exists in the repo
- **Incomplete** - Missing documentation or examples

---

## 🌟 Command Ideas (We'd Love to See!)

- `/test-suite` - Generate comprehensive test suites
- `/benchmark` - Performance testing and comparison
- `/debug-session` - Systematic debugging workflow
- `/api-docs` - Auto-generate API documentation
- `/security-audit` - Security best practices review
- `/refactor` - Code refactoring with tests
- `/migration` - Migrate between frameworks/versions

**Have an idea?** [Open a discussion!](https://github.com/rglaubitz/Claude-Commands/discussions/new)

---

## 📬 Contact

- **Maintainer:** [@rglaubitz](https://github.com/rglaubitz)
- **Issues:** https://github.com/rglaubitz/Claude-Commands/issues
- **Discussions:** https://github.com/rglaubitz/Claude-Commands/discussions

---

**Thank you for contributing!** 🎉

Every command added helps the Claude Code community become more productive.

**Star ⭐ the repo** if you find it useful!
