# /breakdown - Implementation Task Manager Creation

**Purpose:** Transform a large IMPLEMENTATION.md file into a systematic task-manager structure with phases, tasks, and subtasks ready for execution.

**Usage:** `/breakdown <implementation-file> <project-name>`

**Example:** `/breakdown IMPLEMENTATION.md ui-ux-enhancements`

---

## Your Role

You are guiding the user through a **5-phase workflow** to create a complete task-manager structure from their IMPLEMENTATION.md file. This workflow includes strategic context compacts to maintain continuity across a multi-hour breakdown process.

**Key Principles:**
- Be systematic and thorough
- Compact at strategic points (after each phase in Phase 2 and Phase 4)
- Validate before moving to next phase
- Link everything (tasks → tests, tasks → research, tasks → code)
- Make subtasks actionable (2-4 hours each)

---

## Parameters Provided

- **implementation_file:** {{arg1}}
- **project_name:** {{arg2}}

**Validate:**
- implementation_file exists
- project_name is valid (lowercase, hyphens)

---

## Phase 1: Initialize Structure (30 minutes)

### Goal
Create the directory structure and README skeletons for all phases.

### Steps

**1.1: Parse Implementation File**
- Read the implementation file: `{{arg1}}`
- Identify all phases (look for "Phase X:", "Week X:", or similar headers)
- Extract phase names and numbers
- Typical count: 4-7 phases

**1.2: Create Directory Structure**
```bash
mkdir -p task-manager/
mkdir -p task-manager/phase-1-<name>/
mkdir -p task-manager/phase-2-<name>/
# ... for each phase detected
```

**1.3: Create README Skeletons**
- Create `task-manager/README.md` (use Master README Template below)
- Create `task-manager/phase-N-<name>/README.md` for each phase (use Phase README Template)
- Fill in phase names, but leave metrics empty (will populate later)

**1.4: Validation**
- Confirm directory structure created
- Confirm all phase folders exist
- Confirm README skeletons exist

**1.5: Checkpoint**
**OUTPUT TO USER:**
```
✅ Phase 1 Complete: Structure Initialized

Created:
- task-manager/ (root folder)
- X phase folders
- X+1 README skeletons

Next: Phase 2 (Extract Tasks)
This will take 4-6 hours with compacts between each phase.

Ready to proceed? (yes/no)
```

**WAIT for user confirmation before Phase 2.**

---

## Phase 2: Extract Tasks (Iterative with Compacts)

### Goal
Create task files for each phase by analyzing the implementation guide, research, and tests.

### Process: FOR EACH PHASE

**2.1: Context Gathering**
1. Read IMPLEMENTATION.md section for current phase
2. Read PLANNING.md to identify relevant ADRs for this phase
3. Read relevant ADRs (e.g., ADR-004 for Agents SDK phase)
4. Read research/documentation/INDEX.md to find relevant research chunks
5. Read TESTING.md section for this phase (identify test count)

**2.2: Task Identification**
- Analyze phase requirements from IMPLEMENTATION.md
- Break into 3-6 major tasks (not too many, not too few)
- Criteria for task boundaries:
  - Each task is 1-3 days of work
  - Each task has clear deliverable
  - Each task maps to tests in TESTING.md
  - Tasks have logical dependencies

**2.3: Task Creation**
For each task identified:
1. Create file: `task-manager/phase-N-<name>/task-N.M-<task-name>.md`
2. Use **Task File Template** (see below)
3. Fill in:
   - Overview (from IMPLEMENTATION.md)
   - Dependencies (which prior tasks block this?)
   - Success criteria (specific, measurable)
   - Research references (ADRs, research chunks, IMPLEMENTATION.md lines)
   - Test specifications (TESTING.md lines, file paths, test counts)
4. Leave "Implementation Steps" section empty (will fill in Phase 4)

**2.4: Phase README Update**
- Update `phase-N-<name>/README.md`
- Add task list table with all tasks
- Add file links to each task file
- Update dependencies section

**2.5: Checkpoint & Compact**
**OUTPUT TO USER:**
```
✅ Phase N Tasks Complete

Created:
- X task files for Phase N
- Updated phase-N README

Tasks in this phase:
1. Task N.1: <name> (2 days, 12 tests)
2. Task N.2: <name> (2 days, 8 tests)
3. Task N.3: <name> (1 day, 5 tests)

🔄 COMPACT CONTEXT NOW

After compact, I'll continue with Phase N+1.
Ready to compact? (yes/no)
```

**WAIT for user to compact and confirm before next phase.**

**Repeat 2.1-2.5 for ALL phases.**

### After ALL Phases Have Tasks

**OUTPUT TO USER:**
```
✅ Phase 2 Complete: All Tasks Extracted

Summary:
- Phase 1: X tasks
- Phase 2: Y tasks
- Phase 3: Z tasks
- ...
Total: XX tasks across Y phases

Next: Phase 3 (Flow Review)
This will take 1-2 hours to validate task flow and dependencies.

Ready to proceed? (yes/no)
```

**WAIT for user confirmation before Phase 3.**

---

## Phase 3: Flow Review (1-2 hours)

### Goal
Read all tasks sequentially, validate dependencies, identify gaps, ensure logical flow.

### Steps

**3.1: Sequential Task Read**
- Read ALL task files in order (1.1 → 1.2 → ... → last task)
- As you read, note:
  - Dependencies mentioned
  - Prerequisite knowledge/setup
  - Deliverables that enable future tasks

**3.2: Dependency Analysis**
- Create dependency map:
  - Which tasks are prerequisite for others?
  - Which tasks can run in parallel?
  - What is the critical path? (longest dependency chain)
- Check for circular dependencies (Task A needs B, B needs A) - FIX if found
- Check for orphan tasks (no dependencies, doesn't enable anything) - QUESTION if found

**3.3: Gap Analysis**
Check for missing tasks in these categories:
- **Error Handling:** Are error cases covered?
- **Testing:** Are test creation tasks explicit?
- **Documentation:** Are docs updates included?
- **Deployment:** Is staging/production deployment included?
- **Infrastructure:** Is setup (DB, Redis, etc.) covered?
- **Integration:** Are integration points between phases covered?

**3.4: Flow Validation**
Ask these questions:
- Does the sequence make logical sense?
- Should any tasks be reordered for better flow?
- Are any tasks too large? (>3 days → split)
- Are any tasks too small? (<0.5 days → merge)
- Do dependencies make sense? (Task 5.3 needs Task 2.1 - why?)

**3.5: Updates**
Based on analysis:
1. Add gap tasks if identified
2. Reorder tasks if better sequence found
3. Split large tasks if needed
4. Merge small tasks if beneficial
5. Update dependency sections in all affected task files
6. Update phase READMEs with task changes

**3.6: Checkpoint**
**OUTPUT TO USER:**
```
✅ Phase 3 Complete: Flow Reviewed

Findings:
- Dependencies validated: X task dependency relationships
- Critical path: Task A.B → C.D → E.F → G.H (N days)
- Gaps found: Y gap tasks added
  - Gap 1: <description>
  - Gap 2: <description>
- Reordering: Z tasks moved for better flow
  - Moved Task X.Y to earlier in phase (dependency reason)

Updated task count: XX tasks (was YY, added ZZ gaps)

Next: Phase 4 (Subtask Breakdown)
This will take 3-4 hours with compacts between each phase.

Ready to proceed? (yes/no)
```

**WAIT for user confirmation before Phase 4.**

---

## Phase 4: Subtask Breakdown (Iterative with Compacts)

### Goal
Break each task into actionable 2-4 hour subtasks with code file paths, test links, and validation steps.

### Process: FOR EACH PHASE

**4.1: Task Analysis**
For each task in current phase:
1. Read task file
2. Read IMPLEMENTATION.md section for detailed steps
3. Identify logical breakpoints (what can be done in 2-4 hours?)
4. Typical subtask count: 3-5 per task

**4.2: Subtask Creation Criteria**
Each subtask should:
- Be completable in 2-4 hours
- Have clear start and end points
- Produce verifiable output
- Link to specific code files to create/modify
- Link to specific tests to run
- Include validation command

**4.3: Subtask Documentation**
For each task, add "Implementation Steps" section:

```markdown
### Subtask X.Y.1: <Subtask Name>

**Duration:** 2-4 hours
**Status:** ⬜ Not Started

**Files to Create:**
- `src/path/to/new_file.py`

**Files to Modify:**
- `src/path/to/existing.py` (add function X)

**Steps:**
1. Specific step 1
2. Specific step 2
3. Specific step 3

**Code Example:**
```python
# Reference code from IMPLEMENTATION.md or research
```

**Validation:**
```bash
pytest tests/unit/test_specific.py::test_function -v
```

**Expected Result:**
- 5 tests passing
- Coverage >90% for new code
```

**4.4: File Path Linking**
- Link to specific src/ files from IMPLEMENTATION.md
- Link to specific test files from TESTING.md
- Include line numbers when helpful

**4.5: Phase Checkpoint & Compact**
**OUTPUT TO USER:**
```
✅ Phase N Subtasks Complete

Added:
- X subtasks to Task N.1
- Y subtasks to Task N.2
- Z subtasks to Task N.3

Total for Phase N: XX subtasks

🔄 COMPACT CONTEXT NOW

After compact, I'll continue with Phase N+1 subtasks.
Ready to compact? (yes/no)
```

**WAIT for user to compact and confirm before next phase.**

**Repeat 4.1-4.5 for ALL phases.**

### After ALL Phases Have Subtasks

**OUTPUT TO USER:**
```
✅ Phase 4 Complete: All Subtasks Added

Summary:
- Phase 1: X subtasks
- Phase 2: Y subtasks
- Phase 3: Z subtasks
- ...
Total: XXX subtasks across YY tasks

Next: Phase 5 (Master README)
This will take 30 minutes to create final navigation and metrics.

Ready to proceed? (yes/no)
```

**WAIT for user confirmation before Phase 5.**

---

## Phase 5: Master README Creation (30 minutes)

### Goal
Create comprehensive task-manager/README.md with navigation, metrics, and usage instructions.

### Steps

**5.1: Aggregate Metrics**
Count across all files:
- Total phases: X
- Total tasks: Y
- Total subtasks: Z
- Total tests: N (from TESTING.md)
- Estimated duration: M weeks

**5.2: Create Progress Table**
Build table showing all phases with:
- Phase number and name
- Task count
- Subtask count
- Test count
- Status (all start as ⬜)
- Progress (all start at 0%)

**5.3: Build Navigation**
- Links to all phase READMEs
- Quick jump links to critical path tasks
- External resources (PLANNING.md, IMPLEMENTATION.md, ADRs)

**5.4: Add Usage Instructions**
Include:
- How to use task manager during implementation
- How to mark tasks/subtasks complete
- How to update progress counters
- When to compact (between phases)
- How to use handoff format

**5.5: Add Dependencies Visualization**
Create simple text-based dependency diagram:
```
Phase 1 (Auth)
    ↓
Phase 2 (AI) ← requires auth
    ↓
Phase 3 (Design) ← requires features
```

**5.6: Final README**
- Use **Master README Template** (see below)
- Fill in all sections with aggregated data
- Save to `task-manager/README.md`

**5.7: Final Checkpoint**
**OUTPUT TO USER:**
```
✅ Phase 5 Complete: Task Manager Ready! 🎉

📊 Final Metrics:
- Phases: X
- Tasks: Y
- Subtasks: Z
- Tests: N
- Estimated Duration: M weeks
- Compacts Recommended: P (one per phase during implementation)

📁 Created Structure:
task-manager/
├── README.md (master navigation)
├── phase-1-<name>/ (X tasks, Y subtasks)
├── phase-2-<name>/ (X tasks, Y subtasks)
└── ...

✅ All tasks have:
- Dependencies documented
- Test specifications linked
- Research references
- Subtasks (2-4 hour chunks)
- Validation commands

🚀 Ready for Implementation!

Next Steps:
1. Review task-manager/README.md
2. Confirm approach makes sense
3. Begin implementation with /execute or manually

Location: task-manager/
```

---

## Templates

### Task File Template

```markdown
# Task X.Y: <Task Name>

**Phase:** X - <Phase Name>
**Status:** ⬜ Not Started
**Estimated Duration:** X days
**Assigned To:** (filled during execution)

---

## Overview

<1-2 paragraph description of what this task accomplishes>

<Why this task is important in the overall implementation>

---

## Dependencies

**Required Before Starting:**
- Task A.B: <Description> (must be complete)
- Task C.D: <Description> (must be complete)

**Enables After Completion:**
- Task E.F: <Description> (blocked until this is done)
- Task G.H: <Description> (blocked until this is done)

---

## Success Criteria

✅ Criterion 1 (specific, measurable)
✅ Criterion 2 (specific, measurable)
✅ Criterion 3 (specific, measurable)

---

## Research References

**Architecture Decisions:**
- ADR-00X: <Title> (Section: <specific section>)
  - Why relevant: <explanation>

**Technical Documentation:**
- research/documentation/<file>.md (Lines: XX-YY)
  - Key concepts: <summary>

**Implementation Guide:**
- IMPLEMENTATION.md (Lines: XXX-YYY)
  - Detailed steps reference

---

## Test Specifications

**Unit Tests:** (X tests)
- TESTING.md: Lines XX-YY
- File: `tests/unit/test_<name>.py`
- Coverage target: 90%+

**Integration Tests:** (Y tests)
- TESTING.md: Lines ZZ-AA
- File: `tests/integration/test_<name>.py`
- Coverage target: 85%+

**Total Tests:** X+Y tests

---

## Implementation Steps

### Subtask X.Y.1: <Subtask Name>

**Duration:** 2-4 hours
**Status:** ⬜ Not Started

**Files to Create:**
- `src/path/to/new_file.py`

**Files to Modify:**
- `src/path/to/existing_file.py` (lines XX-YY)

**Steps:**
1. Step 1 (specific action)
2. Step 2 (specific action)
3. Step 3 (specific action)

**Code Example:**
```python
# Example code from IMPLEMENTATION.md or research
```

**Validation:**
```bash
pytest tests/unit/test_<name>.py::test_specific -v
```

**Expected Result:**
- X tests passing
- Coverage >90%

---

### Subtask X.Y.2: <Subtask Name>

[Same structure]

---

## Troubleshooting

**Common Issues:**
- Issue 1: See TROUBLESHOOTING.md:Lines XX-YY
- Issue 2: See TROUBLESHOOTING.md:Lines ZZ-AA

---

## Progress Tracking

**Subtasks:** 0/N complete (0%)

- [ ] Subtask X.Y.1
- [ ] Subtask X.Y.2
- [ ] Subtask X.Y.3

**Tests:** 0/N passing (0%)

**Last Updated:** YYYY-MM-DD
```

### Phase README Template

```markdown
# Phase X: <Phase Name>

**Duration:** X weeks (Days 1-Y)
**Status:** ⬜ Not Started
**Progress:** 0/Z tasks complete (0%)

---

## Overview

<2-3 paragraph description from IMPLEMENTATION.md>

---

## Tasks

| Task | Name | Status | Duration | Dependencies | Tests | Subtasks |
|------|------|--------|----------|--------------|-------|----------|
| X.1 | <Name> | ⬜ | 2d | None | 12 | 4 |
| X.2 | <Name> | ⬜ | 2d | X.1 | 8 | 3 |
| X.3 | <Name> | ⬜ | 1d | X.1, X.2 | 5 | 2 |

**Totals:**
- Tasks: 0/3 complete (0%)
- Subtasks: 0/9 complete (0%)
- Tests: 0/25 passing (0%)

---

## Phase Dependencies

**Required Before Starting:**
- Phase Y complete

**Enables After Completion:**
- Phase Z

---

## Research Materials

- ADR-00X: <Title>
- research/documentation/<file>.md
- IMPLEMENTATION.md: Lines XXX-YYY

---

## Success Criteria

✅ All X tasks complete
✅ All Y tests passing
✅ Code coverage ≥80%
✅ Documentation updated

---

## Files

- [Task X.1: <Name>](task-X.1-<name>.md)
- [Task X.2: <Name>](task-X.2-<name>.md)
```

### Master README Template

```markdown
# Task Manager: {{arg2}}

**Project:** {{arg2}}
**Implementation Guide:** {{arg1}}
**Created:** {{current_date}}

---

## Progress Overview

**Overall Progress:** 0/Y tasks (0%) | 0/Z subtasks (0%)

| Phase | Name | Tasks | Subtasks | Tests | Status | Progress |
|-------|------|-------|----------|-------|--------|----------|
| 1 | <Name> | X | Y | Z | ⬜ | 0% |
| 2 | <Name> | X | Y | Z | ⬜ | 0% |

**Totals:**
- **Phases:** X
- **Tasks:** Y
- **Subtasks:** Z
- **Tests:** N
- **Estimated Duration:** M weeks

---

## Quick Navigation

### By Phase
- [Phase 1: <Name>](phase-1-<name>/README.md)
- [Phase 2: <Name>](phase-2-<name>/README.md)

### Critical Path
1. Task X.Y: <Name> (blocks...)
2. Task A.B: <Name> (blocks...)

---

## How to Use This Task Manager

### During Implementation

1. **Start with Phase 1**
   - Read phase-1-<name>/README.md
   - Begin with first task

2. **Work Through Tasks**
   - Open task file
   - Execute subtasks in order
   - Mark complete with ✅

3. **Update Progress**
   - Update task file
   - Update phase README
   - Update this master README

4. **Between Phases: COMPACT**
   - After completing phase
   - Compact context
   - Resume with next phase

---

## Dependencies Visualization

```
Phase 1
    ↓
Phase 2 ← requires Phase 1
    ↓
Phase 3 ← requires Phase 2
```

---

## Research Materials

- PLANNING.md
- IMPLEMENTATION.md
- TESTING.md
- TROUBLESHOOTING.md
- ADR-00X, ADR-00Y, etc.

---

## Checkpoints & Compacts

**Recommended:**
- After Phase 1 (Day X)
- After Phase 2 (Day Y)
- ...

**Total Compacts:** N

---

**Last Updated:** {{current_date}}
**Status:** Ready for Implementation ✅
```

---

## Summary

This command creates a complete task-manager structure with:
- Phase folders with READMEs
- Task files with subtasks
- Master README with navigation
- Full dependency tracking
- Test linkage
- Research references

**Total time:** 8-12 hours (saves 20-30 hours during implementation)

**Usage:** `/breakdown IMPLEMENTATION.md project-name`
