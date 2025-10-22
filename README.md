# Claude Commands 🤖

**Professional slash commands for Claude Code** - Automate research, documentation, and workflow optimization.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Claude Code](https://img.shields.io/badge/Claude-Code-blue.svg)](https://claude.ai/code)

---

## 🎯 What Are Claude Commands?

Slash commands are reusable workflow automations for [Claude Code](https://claude.ai/code). They turn complex multi-step processes into single commands that Claude executes autonomously.

**Instead of:**
```
"Research library X, compare alternatives, create docs, update plans, commit changes..."
```

**Just type:**
```
/rdf my-feature
```

And Claude handles the rest.

---

## 📚 Available Commands

### 🏗️ Implementation Task Breakdown

**Command:** `/breakdown <implementation-file> <project-name>`

**What it does:**
- **Phase 1: Initialize** - Create directory structure and README skeletons
- **Phase 2: Extract Tasks** - Analyze implementation guide and create task files (with compacts)
- **Phase 3: Flow Review** - Validate dependencies and identify gaps
- **Phase 4: Subtask Breakdown** - Break tasks into 2-4 hour actionable chunks (with compacts)
- **Phase 5: Master README** - Create navigation and progress tracking

**When to use:**
- Multi-week implementation projects (4-7 weeks)
- Large implementation guides (1,000+ lines)
- Need systematic progress tracking
- Complex dependency management
- Team handoffs during long projects

**Quality guarantees:**
- ✅ Tasks linked to test specifications
- ✅ Subtasks are 2-4 hour actionable chunks
- ✅ Dependencies validated (no circular deps)
- ✅ Gap analysis (error handling, deployment, etc.)
- ✅ Research integration (ADRs, docs)
- ✅ Critical path identification

**Example:**
```bash
/breakdown IMPLEMENTATION.md ui-ux-enhancements
```

**Output:** Complete task-manager structure with phases, tasks, subtasks, and progress tracking.

**[Full Documentation →](commands/breakdown.md)**

---

### 🔬 Research, Document, Finalize (RDF)

**Command:** `/rdf` or `/research-document-finalize`

**What it does:**
- **Phase 1: Research** - Deep research using Exa and GitHub
- **Phase 2: Documentation** - Create implementation guides and research docs
- **Phase 3: Finalization** - Update plans, commit, and push

**When to use:**
- Starting implementation of a planned upgrade
- Need to verify latest versions and alternatives
- Want comprehensive research-backed documentation
- Need implementation guide with complete examples

**Quality guarantees:**
- ✅ All sources are Tier 1-2 (official docs, 1.5k+ star repos)
- ✅ Latest versions verified via GitHub/PyPI/npm
- ✅ Complete code examples (no pseudocode)
- ✅ Cross-referenced documentation
- ✅ Git commit and push included

**Example:**
```bash
/rdf authentication-system
```

**[Full Documentation →](commands/research-document-finalize/)**

---

## 🚀 Quick Start

### 1. Install Commands

Copy command files to your Claude Code commands directory:

```bash
# On macOS/Linux
cp -r commands/* ~/.claude/commands/

# On Windows
copy commands\* %USERPROFILE%\.claude\commands\
```

### 2. Use a Command

In Claude Code, just type the command:

```
/rdf my-feature-name
```

### 3. Let Claude Work

Claude will:
1. Research using Exa and GitHub
2. Create comprehensive documentation
3. Commit and push to git

That's it! 🎉

---

## 📖 Command Catalog

| Command | Purpose | Phase | Status |
|---------|---------|-------|--------|
| **[Breakdown](/commands/breakdown.md)** | Transform implementation guides into task hierarchies | Planning → Execution | ✅ Stable |
| **[RDF](/commands/research-document-finalize/)** | Research, Document, Finalize workflow | Research → Implementation | ✅ Stable |
| *More coming soon...* | | | 🚧 |

---

## 🏗️ Command Structure

Each command directory contains:

```
commands/
└── [command-name]/
    ├── command.md              # Main command prompt
    ├── alias.md                # Short alias (optional)
    ├── README.md               # Documentation
    └── examples/
        ├── input-example.md    # Example inputs
        └── output-example.md   # Expected outputs
```

---

## 💡 Use Cases

### Software Development
- **Research-first implementation** - Verify latest versions before coding
- **Comprehensive documentation** - Auto-generate implementation guides
- **Best practices verification** - Check 2025 standards for patterns

### Research & Analysis
- **Multi-source research** - Aggregate from official docs, repos, articles
- **Source quality control** - Only Tier 1-2 sources (official docs, verified repos)
- **Decision documentation** - Track rationale with citations

### Team Workflows
- **Consistent documentation** - Same format every time
- **Git automation** - Auto-commit with proper messages
- **Knowledge sharing** - Reproducible research process

---

## 🎓 Real-World Example

**Project:** Apex Memory System Query Router Upgrade

**Challenge:**
- Need to verify semantic-router library version
- Compare Claude vs OpenAI for query rewriting
- Research async best practices
- Create implementation guide with examples

**Solution:**
```bash
/rdf query-router
```

**Result:**
- ✅ Researched and verified semantic-router 0.1.11 (latest)
- ✅ Compared Claude 3.5 Sonnet vs GPT-4 (Claude 67% cheaper, better quality)
- ✅ Researched async patterns (full async 2× faster)
- ✅ Created 3 research documents with citations
- ✅ Created implementation guide with complete examples
- ✅ Created training data (48 example queries)
- ✅ Committed and pushed to GitHub

**Time saved:** 4-6 hours of manual research and documentation

**[See the full example →](examples/rdf-query-router-example.md)**

---

## 🛠️ Requirements

- **Claude Code** - [Get it here](https://claude.ai/code)
- **MCP Servers** (for research commands):
  - Exa (web search)
  - GitHub (code search, version verification)
- **Git** - For commit/push automation

---

## 🤝 Contributing

We welcome contributions! Whether it's:
- 🆕 New commands
- 📖 Documentation improvements
- 🐛 Bug fixes
- 💡 Ideas for new workflows

**[See CONTRIBUTING.md for guidelines →](CONTRIBUTING.md)**

---

## 📝 License

MIT License - See [LICENSE](LICENSE) for details

---

## 🌟 Featured Command: RDF Workflow

The **Research, Document, Finalize (RDF)** workflow is our flagship command.

**Created from real-world use:**
- Built while upgrading the Apex Memory System query router
- Automated a 4-6 hour manual process
- Maintains research quality standards (Tier 1-2 sources only)
- Produces production-ready documentation

**What makes it special:**
- **Autonomous execution** - From research to git push
- **Quality guaranteed** - Official docs, verified repos only
- **Complete output** - Research docs, implementation guides, examples
- **Git integration** - Proper commit messages and push

**Try it:**
```bash
/rdf your-feature-name
```

---

## 🎯 Roadmap

**Coming Soon:**
- 🔄 `/code-review` - Automated code review with best practices
- 📊 `/benchmark` - Performance testing and comparison
- 🐛 `/debug-session` - Systematic debugging workflow
- 📚 `/api-docs` - Auto-generate API documentation
- 🧪 `/test-suite` - Create comprehensive test suites

**Have an idea?** [Open an issue](https://github.com/rglaubitz/Claude-Commands/issues)

---

## 📚 Learn More

- **[Command Documentation](commands/)** - Detailed guides for each command
- **[Examples](examples/)** - Real-world usage examples
- **[Contributing Guide](CONTRIBUTING.md)** - How to add commands
- **[Claude Code Docs](https://docs.claude.com/claude-code)** - Official documentation

---

## 💬 Support

- **Issues:** [GitHub Issues](https://github.com/rglaubitz/Claude-Commands/issues)
- **Discussions:** [GitHub Discussions](https://github.com/rglaubitz/Claude-Commands/discussions)

---

**Built with ❤️ for the Claude Code community**

**Star ⭐ this repo if you find it useful!**
