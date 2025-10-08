# Research, Document, Finalize (RDF) Command

**Automate comprehensive research-first implementation workflows**

---

## 📋 Overview

The RDF command automates the complete research-to-implementation pipeline that many developers follow manually. It's designed for teams and individuals who value research-backed decisions and comprehensive documentation.

**Command:** `/research-document-finalize` or `/rdf`

**Time saved:** 4-6 hours per feature/upgrade

**Quality level:** Production-ready documentation with cited sources

---

## 🎯 What It Does

### Phase 1: Research 📚

**Automatic research using:**
- **Exa AI** - Web search for official docs, articles, benchmarks
- **GitHub API** - Version verification, code examples from verified repos

**Research questions answered:**
1. Are we using the **LATEST versions** of libraries/tools?
2. Are there **BETTER alternatives** to proposed solutions?
3. What are the **2025 BEST PRACTICES** for patterns we're using?
4. What **training data or examples** do we need?

**Source quality standards:**
- ✅ Tier 1: Official documentation (Anthropic, OpenAI, framework maintainers)
- ✅ Tier 2: Verified repositories (1.5k+ stars minimum)
- ✅ Tier 3: Technical standards (RFCs, W3C specifications)
- ❌ NO sources below Tier 3

### Phase 2: Documentation 📝

**Auto-generated documentation:**

1. **Research Analysis Documents** (`research/documentation/[topic]/`)
   - Executive summary with key findings
   - Options comparison table
   - Benchmark results (performance, cost, quality)
   - Decision matrix with weighted scoring
   - Final recommendation with rationale
   - All sources cited with URLs

2. **Implementation Guide** (`upgrades/[name]/IMPLEMENTATION-GUIDE.md`)
   - Pre-flight verification commands
   - Exact dependency versions from research
   - Phase-by-phase implementation with complete code examples
   - Testing strategies
   - Rollback procedures
   - Links to all research documents

3. **Supporting Files** (`upgrades/[name]/examples/`)
   - Training data (JSON/YAML)
   - Configuration examples
   - Helper scripts
   - Sample queries/inputs

4. **Updated Master Plan** (`upgrades/[name]/IMPROVEMENT-PLAN.md`)
   - Latest library versions
   - Technology recommendations
   - Updated code examples
   - Cross-references to research

### Phase 3: Finalization ✅

**Git automation:**
1. Review all created files for completeness
2. `git add` all documentation
3. `git commit` with descriptive message
4. `git push` to remote
5. Provide completion summary

---

## 🚀 Usage

### Basic Usage

```bash
/rdf authentication-system
```

### Without Parameter

```bash
/rdf
```

Claude will prompt: "What upgrade/feature are you researching?"

### In Practice

```bash
You: /rdf query-router-upgrade

Claude: Executing RDF workflow for query-router-upgrade...

[Phase 1: Research]
✅ Researching semantic-router library (GitHub → v0.1.11 latest)
✅ Comparing Claude vs OpenAI for query rewriting (Exa → Claude superior)
✅ Researching async best practices (Official docs → full async 2× faster)

[Phase 2: Documentation]
✅ Created research/documentation/query-routing/semantic-router-analysis.md
✅ Created research/documentation/query-routing/claude-vs-openai-query-rewriting.md
✅ Created research/documentation/query-routing/async-best-practices-2025.md
✅ Created upgrades/query-router/IMPLEMENTATION-GUIDE.md
✅ Created upgrades/query-router/examples/training-queries.json (48 examples)
✅ Updated upgrades/query-router/IMPROVEMENT-PLAN.md

[Phase 3: Finalization]
✅ Committed: "Add query router implementation documentation and research"
✅ Pushed to origin/main

## RDF Workflow Complete ✅

Ready for implementation Phase 1.
```

---

## 📊 Real-World Example

**Project:** Apex Memory System - Query Router Upgrade

**Context:**
- Upgrading query routing system
- Need to verify latest library versions
- Compare LLM providers for query rewriting
- Research async/await best practices

**Input:**
```bash
/rdf query-router
```

**Output:**

### Research Documents Created (3 files, ~15,000 words):

1. **`semantic-router-analysis.md`**
   - Verified aurelio-labs/semantic-router v0.1.11 (not 0.0.40)
   - Compared to LangChain Router, LlamaIndex Router, custom BERT
   - Decision: semantic-router is best-in-class (2× faster, purpose-built)
   - Sources: GitHub repo, official docs, comparison benchmarks

2. **`claude-vs-openai-query-rewriting.md`**
   - Compared Claude 3.5 Sonnet vs GPT-4 Turbo vs GPT-4o
   - Benchmarks: instruction following, decomposition quality, speed, cost
   - Decision: Claude 3.5 Sonnet (67% lower cost, better quality)
   - Sources: Anthropic docs, OpenAI docs, production metrics

3. **`async-best-practices-2025.md`**
   - Compared full async vs sync wrappers vs hybrid approach
   - Benchmarks: 2× throughput, 4× better latency with full async
   - Decision: Full async/await conversion (FastAPI async-native)
   - Sources: Python official docs, FastAPI docs, real-world benchmarks

### Implementation Documentation Created:

4. **`IMPLEMENTATION-GUIDE.md`** (~600 lines)
   - Pre-flight verification (Neo4j version, Redis memory check)
   - Dependency installation (semantic-router==0.1.11, anthropic==0.39.0, etc.)
   - Phase 1-4 implementation with complete code examples
   - Testing strategies (unit tests, integration tests)
   - Rollback procedures

5. **`training-queries.json`** (48 example queries)
   - 12 graph queries (connections, relationships)
   - 12 temporal queries (history, trends, changes)
   - 12 semantic queries (similarity, meaning)
   - 12 metadata queries (filters, structured data)

### Master Plan Updated:

6. **`IMPROVEMENT-PLAN.md`** (updated)
   - Added research document cross-references
   - Updated library versions (0.0.40 → 0.1.11)
   - Added Claude API recommendation
   - Updated code examples with latest patterns

### Git Operations:

```bash
Commit: f2af155 - "Add query router implementation documentation and research"

Implementation Documentation:
- Add IMPLEMENTATION-GUIDE.md with comprehensive step-by-step instructions
- Add training-queries.json with 48 example queries across 4 intent types
- Update IMPROVEMENT-PLAN.md with latest library versions and Claude API

Research Documentation:
- Add semantic-router-analysis.md (v0.1.11, best-in-class comparison)
- Add claude-vs-openai-query-rewriting.md (Claude 3.5 Sonnet superior)
- Add async-best-practices-2025.md (full async conversion recommended)

Key Changes:
- Semantic Router: Upgraded from 0.0.40 to 0.1.11 (latest)
- Query Rewriting: Use Claude 3.5 Sonnet (67% lower cost than GPT-4)
- Async Pattern: Full async/await conversion (no sync wrappers)

Pushed to: origin/main
```

**Time saved:** ~6 hours of manual research and documentation

---

## 🛠️ Requirements

### Software

- **Claude Code** - [Download here](https://claude.ai/code)
- **Git** - For commit/push automation
- **Python 3.9+** (if researching Python projects)

### MCP Servers (Required)

The command uses these MCP servers:

1. **Exa** - For web research
   ```bash
   # Add via Claude Code MCP settings
   claude mcp add exa https://mcp.exa.ai/mcp
   ```

2. **GitHub** - For code search and version verification
   ```bash
   # Add via Claude Code MCP settings
   claude mcp add github npx -y @modelcontextprotocol/server-github
   ```

### Project Structure (Optional)

RDF works best with this structure, but can adapt:

```
your-project/
├── research/
│   └── documentation/
│       └── [topic]/           # Research docs go here
├── upgrades/
│   └── [name]/
│       ├── IMPROVEMENT-PLAN.md
│       ├── IMPLEMENTATION-GUIDE.md (created)
│       └── examples/          (created)
└── .git/                      # Git repo required
```

---

## 📐 Quality Standards

### Research Quality

**Minimum requirements:**
- ✅ 3+ sources per research question
- ✅ All Tier 1-2 sources (official docs, verified repos 1.5k+ stars)
- ✅ Latest versions verified via GitHub/PyPI/npm
- ✅ Performance/cost/quality benchmarks included
- ✅ Decision rationale documented

**What you get:**
- Comprehensive comparison tables
- Benchmark data (speed, cost, quality)
- Weighted decision matrices
- Clear recommendations with citations

### Documentation Quality

**Implementation guides include:**
- ✅ Complete code examples (no pseudocode or TODOs)
- ✅ Exact version numbers (e.g., `semantic-router==0.1.11`)
- ✅ Pre-flight verification steps
- ✅ Testing strategies (unit, integration, e2e)
- ✅ Rollback procedures
- ✅ Cross-references to research docs

**Research documents include:**
- ✅ Executive summary (3-5 key findings)
- ✅ Research context (problem statement)
- ✅ Options comparison (table format)
- ✅ Benchmarks (performance, cost, quality)
- ✅ Decision matrix (weighted scoring)
- ✅ Final recommendation (clear decision + rationale)
- ✅ References (all sources with URLs)

---

## 🎓 Use Cases

### Software Engineering

**Scenario:** Upgrading a core system component

```bash
/rdf authentication-system-upgrade
```

**What RDF does:**
- Researches OAuth2, JWT, session-based auth (latest standards)
- Compares Auth0 vs Keycloak vs custom (cost, features, complexity)
- Finds 2025 best practices for token management
- Creates implementation guide with security considerations
- Generates example configs and integration code

**Output:**
- Research docs with security benchmarks
- Implementation guide with code examples
- Migration strategy from old auth system
- Testing strategy for auth flows
- Rollback procedure if deployment fails

---

### Library Selection

**Scenario:** Choosing between multiple libraries

```bash
/rdf caching-library-selection
```

**What RDF does:**
- Verifies latest versions (Redis, Memcached, Valkey)
- Compares performance benchmarks
- Researches 2025 caching patterns
- Finds production examples from verified repos
- Documents trade-offs

**Output:**
- Comparison table (speed, memory, features)
- Cost analysis (infrastructure, maintenance)
- Decision matrix with scoring
- Implementation guide for chosen library
- Migration path from current solution

---

### Best Practices Research

**Scenario:** Modernizing code patterns

```bash
/rdf async-migration-python
```

**What RDF does:**
- Researches Python async/await best practices (2025)
- Finds migration patterns from sync to async
- Locates production examples
- Documents performance improvements
- Identifies common pitfalls

**Output:**
- Before/after code comparison
- Migration guide (phase-by-phase)
- Performance benchmarks
- Testing strategy for async code
- Troubleshooting guide

---

## ⚙️ Installation

### Step 1: Install Command Files

Copy to your Claude Code commands directory:

**macOS/Linux:**
```bash
cp command.md ~/.claude/commands/research-document-finalize.md
cp alias.md ~/.claude/commands/rdf.md
```

**Windows:**
```powershell
copy command.md %USERPROFILE%\.claude\commands\research-document-finalize.md
copy alias.md %USERPROFILE%\.claude\commands\rdf.md
```

### Step 2: Verify Installation

In Claude Code, type:
```
/rdf
```

You should see Claude respond with: "Executing RDF workflow..."

### Step 3: Configure MCP Servers

Ensure Exa and GitHub MCP servers are configured in Claude Code settings.

---

## 🔧 Customization

### Modify Research Questions

Edit `command.md` and change the research questions:

```markdown
2. Identify critical questions that need research:
   - Are we using the LATEST versions of libraries/tools?
   - Are there BETTER alternatives to proposed solutions?
   - Your custom question here...
```

### Change Output Structure

Modify documentation paths in Phase 2:

```markdown
1. **Research Documents** (`research/documentation/[topic]/[analysis-name].md`):
   # Change to your preferred path
```

### Adjust Commit Message Format

Update Phase 3 commit message template:

```markdown
3. **Commit Message Format:**
   ```
   [Your project format here]
   ```
```

---

## 📈 Success Metrics

**From real-world usage (Apex Memory System project):**

| Metric | Before RDF | After RDF | Improvement |
|--------|-----------|-----------|-------------|
| **Research time** | 4-6 hours | 30 minutes | 8-12× faster |
| **Documentation quality** | Variable | Consistent | 100% complete |
| **Source quality** | Mixed | Tier 1-2 only | Verified |
| **Version accuracy** | Often outdated | Always latest | 100% current |
| **Missing pieces** | Frequent (examples, tests) | None | Complete |
| **Rework needed** | 20-30% | <5% | 4-6× less |

---

## 🐛 Troubleshooting

### "Command not found"

**Check installation:**
```bash
ls ~/.claude/commands/ | grep rdf
```

Should show:
- `research-document-finalize.md`
- `rdf.md`

**Fix:** Re-copy command files to `~/.claude/commands/`

---

### "Exa/GitHub MCP server not available"

**Symptom:** Claude says "I don't have access to Exa" or "GitHub search failed"

**Fix:** Configure MCP servers in Claude Code settings:
```bash
# Exa
claude mcp add exa https://mcp.exa.ai/mcp

# GitHub
claude mcp add github npx -y @modelcontextprotocol/server-github
```

---

### "Git operations failed"

**Common causes:**
1. Not in a git repository
2. Uncommitted changes blocking push
3. No write permissions

**Fix:**
```bash
# Verify git repo
git status

# Commit any pending changes
git add .
git commit -m "WIP"

# Verify remote
git remote -v
```

---

### Research returns low-quality sources

**Symptom:** Claude finds sources below Tier 3 (blog posts, random repos)

**Fix:** The command explicitly blocks Tier 4+ sources. If you see low-quality:
1. Check that Exa MCP server is properly configured
2. Try more specific research questions
3. Manually guide: "Only use official documentation"

---

## 💡 Pro Tips

### 1. Let It Run Fully

**Don't interrupt the workflow.** RDF is designed to be fully autonomous. Interrupting mid-phase can leave incomplete documentation.

**Best practice:**
```bash
/rdf my-feature
# ☕ Go get coffee, let it complete
```

### 2. Provide Context in Existing Docs

RDF reads existing documentation. Help it by providing context:

**Good setup:**
```markdown
# IMPROVEMENT-PLAN.md

## Problem Statement
We need to upgrade our authentication system...

## Current Implementation
Using JWT tokens with...

## Goals
- Improve security
- Add MFA support
```

**Result:** RDF knows what to research (MFA providers, JWT best practices, etc.)

---

### 3. Review Research Before Implementation

**After RDF completes:**
1. Read the research documents (5-10 minutes)
2. Validate the recommendations
3. Adjust if needed

**Remember:** RDF provides recommendations, but **you** make final decisions.

---

### 4. Use for New Projects Too

**Not just upgrades!** Use RDF for greenfield projects:

```bash
/rdf new-microservice-architecture
```

RDF will research:
- Latest microservices patterns (2025)
- Best frameworks and libraries
- Deployment strategies
- Testing approaches

---

## 🤝 Contributing

Found a bug? Have an improvement? **We welcome contributions!**

**See:** [CONTRIBUTING.md](../../CONTRIBUTING.md)

---

## 📜 License

MIT License - See [LICENSE](../../LICENSE) for details

---

## 🌟 Star History

**Star this repo** if RDF saves you time! ⭐

---

**Created by:** [@rglaubitz](https://github.com/rglaubitz)
**First used:** October 7, 2025
**Project:** [Apex Memory System](https://github.com/rglaubitz/Apex-Memory-System-Development)

**🚀 Try it today:**
```bash
/rdf your-next-feature
```
