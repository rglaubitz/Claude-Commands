# Research, Document, Finalization Workflow

You are executing the **Research, Document, Finalization (RDF)** workflow - a comprehensive research-first implementation process.

## Workflow Overview

This workflow follows three phases:
1. **Research Phase** - Deep research using Exa and GitHub
2. **Documentation Phase** - Create implementation guides and research docs
3. **Finalization Phase** - Update plans, commit, and push

## Your Task

Execute the complete RDF workflow for the specified upgrade/feature.

### Phase 1: Research Phase

**Identify Research Questions:**

1. Read the upgrade's existing documentation (IMPROVEMENT-PLAN.md, README.md)
2. Identify critical questions that need research:
   - Are we using the LATEST versions of libraries/tools?
   - Are there BETTER alternatives to proposed solutions?
   - What are the 2025 BEST PRACTICES for the patterns we're using?
   - What training data or examples do we need?

3. For EACH research question, use:
   - **Exa (mcp__exa__web_search_exa)** for:
     - Official documentation
     - Technical articles and benchmarks
     - Best practices guides
   - **GitHub (mcp__github__)** for:
     - Latest version verification
     - Code examples from 1.5k+ star repos
     - Implementation patterns

4. **Source Quality Requirements:**
   - Tier 1: Official documentation (Anthropic, OpenAI, library maintainers)
   - Tier 2: Verified repositories (1.5k+ stars minimum)
   - Tier 3: Technical standards (RFCs, W3C specs)
   - NO sources below Tier 3

### Phase 2: Documentation Phase

**Create Complete Documentation:**

1. **Research Documents** (`research/documentation/[topic]/[analysis-name].md`):

   For each research question, create a comprehensive analysis document with:
   ```markdown
   # [Topic] Analysis

   **Research Date:** [Today's date]
   **Source Tier:** [Tier 1/2/3]
   **Decision:** [Clear recommendation]

   ## Executive Summary
   - Key findings (3-5 bullets)

   ## Research Context
   [What problem are we solving?]

   ## Options Comparison
   [Table comparing alternatives]

   ## Benchmark Results
   [Performance/cost/quality data]

   ## Decision Matrix
   [Weighted scoring if applicable]

   ## Final Recommendation
   [Clear decision with rationale]

   ## References
   - [Source 1 with URL]
   - [Source 2 with URL]

   **Research Quality:** ✅ Tier X
   **Last Updated:** [Date]
   **Recommendation:** APPROVED/REJECTED
   ```

2. **Implementation Guide** (`upgrades/[name]/IMPLEMENTATION-GUIDE.md`):

   Create step-by-step implementation guide with:
   - Pre-flight verification commands
   - Exact dependency versions (from research)
   - Phase-by-phase implementation with complete code examples
   - Testing strategies
   - Rollback procedures
   - Links to all research documents

3. **Supporting Files** (`upgrades/[name]/examples/`):

   Create any needed:
   - Training data (JSON/YAML)
   - Configuration examples
   - Helper scripts
   - Sample queries/inputs

4. **Update Master Plan** (`upgrades/[name]/IMPROVEMENT-PLAN.md`):

   Update with:
   - Links to new research documents
   - Latest library versions from research
   - Technology recommendations from research
   - Updated code examples using latest patterns
   - Cross-references to research in "Research Foundation" section

### Phase 3: Finalization Phase

**Commit and Push:**

1. **Review all created files** for:
   - Cross-references are correct
   - All research sources cited
   - Code examples are complete
   - Versions are latest

2. **Git operations:**
   ```bash
   git add research/documentation/[topic]/*.md
   git add upgrades/[name]/IMPLEMENTATION-GUIDE.md
   git add upgrades/[name]/examples/*
   git add upgrades/[name]/IMPROVEMENT-PLAN.md

   git commit -m "[Descriptive message following project style]"
   git push
   ```

3. **Commit Message Format:**
   ```
   [Action] [component] [summary]

   Implementation Documentation:
   - Item 1
   - Item 2

   Research Documentation:
   - Item 1
   - Item 2

   Key Changes:
   - Change 1
   - Change 2

   🤖 Generated with [Claude Code](https://claude.com/claude-code)

   Co-Authored-By: Claude <noreply@anthropic.com>
   ```

## Quality Standards

**Research Quality:**
- Minimum 3 sources per research question
- All Tier 1-2 sources (Tier 3 only if no alternatives)
- Official documentation prioritized
- Latest versions verified via GitHub/PyPI/npm

**Documentation Quality:**
- Complete code examples (no pseudocode)
- Exact version numbers
- Clear decision rationale
- All sources cited with URLs
- Cross-references between docs

**Implementation Quality:**
- Step-by-step instructions
- Pre-flight verification steps
- Testing strategies included
- Rollback procedures documented

## Tools Available

Use these MCP tools:
- `mcp__exa__web_search_exa` - Web research
- `mcp__exa__get_code_context_exa` - Code examples
- `mcp__github__search_code` - GitHub code search
- `mcp__github__get_file_contents` - Get file from repo (for version verification)
- `mcp__github__search_repositories` - Find example repos

Use these built-in tools:
- `Read` - Read existing docs
- `Write` - Create new docs
- `Edit` - Update existing docs
- `Glob` - Find files
- `Grep` - Search content
- `Bash` - Git operations
- `TodoWrite` - Track progress

## Execution Instructions

1. **Use TodoWrite** to create task list with all phases
2. **Execute Phase 1** - Research (mark each research question as you complete it)
3. **Execute Phase 2** - Documentation (mark each document as you create it)
4. **Execute Phase 3** - Finalization (commit and push)
5. **Mark all todos as completed** when done

## Success Criteria

- ✅ All research questions answered with Tier 1-2 sources
- ✅ Research documents created in `research/documentation/`
- ✅ Implementation guide created with complete examples
- ✅ Supporting files created (training data, configs)
- ✅ Master plan updated with research findings
- ✅ All files committed and pushed to git
- ✅ Cross-references verified

## Example Output Summary

At the end, provide a summary like:

```
## RDF Workflow Complete

### Files Created:
1. research/documentation/[topic]/[file1].md
2. research/documentation/[topic]/[file2].md
3. upgrades/[name]/IMPLEMENTATION-GUIDE.md
4. upgrades/[name]/examples/[file].json

### Key Findings:
- Finding 1
- Finding 2
- Finding 3

### Git Commit:
Commit: [hash] - "[message]"
Pushed to: origin/main

Ready for implementation Phase 1.
```

---

**Now execute this workflow for the specified upgrade/feature. Ask the user for the upgrade name if not provided, then begin Phase 1.**
