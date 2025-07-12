# Task Resumption Command (`gosu:work`)

Resume work on previously saved tasks with full context preservation and progress tracking.

## Overview

The work command provides seamless task resumption across AI sessions. It allows you to pause work on any gosu task (`gosu:plan`, `gosu:review`, `gosu:security`) and resume later with complete context, progress tracking, and intelligent continuation.

## Usage

```bash
# Interactive task selection (lists all available tasks)
claude gosu:work

# Resume specific task file directly
claude gosu:work plan-20240712_143022.md
claude gosu:work review-20240712_151045.md  
claude gosu:work security-20240712_160315.md
```

## What It Does

### 🔄 **Intelligent Task Resumption**
- **Context preservation** - Full analysis context maintained across sessions
- **Progress tracking** - Checkbox states track completed vs pending tasks
- **Smart continuation** - Resumes from exact point where work was interrupted
- **Status analysis** - Determines appropriate next steps based on task state

### 📋 **Interactive Task Management**
- **Task file discovery** - Automatically finds all available task files
- **Status reporting** - Shows completion progress and current state
- **Priority resumption** - Continues with highest priority pending tasks
- **Real-time updates** - Updates task files as work progresses

### 🧹 **Automatic Cleanup**
- **Completion detection** - Automatically detects when all tasks are finished
- **File cleanup** - Removes completed task files automatically
- **Workspace maintenance** - Keeps `.gosu` directory clean and organized

## Prerequisites

### Required Setup
```bash
# Initialize gosu workspace first
claude gosu:init

# Create task files with other gosu commands
claude gosu:plan "feature description"    # Creates plan files
claude gosu:review                        # Creates review files
claude gosu:security                      # Creates security files
```

### Directory Structure
```
.gosu/
├── plan-20240712_143022.md      # Feature implementation plan
├── review-20240712_151045.md    # Code quality review
└── security-20240712_160315.md  # Security audit report
```

## Process Flow

### 1. Workspace Validation
- **Checks `.gosu` directory existence** - Ensures proper initialization
- **Suggests `gosu:init`** if workspace not found
- **Validates file access** - Confirms read/write permissions

### 2. Task Discovery & Selection
- **Scans for task files** - Finds all `.md` files in `.gosu` directory
- **Interactive listing** - Displays available tasks with metadata
- **Status analysis** - Shows completion progress and current state
- **User selection** - Prompts for task choice or accepts filename parameter

### 3. Task Analysis & Resumption
- **Context reconstruction** - Rebuilds full task context from saved file
- **Progress assessment** - Identifies completed vs pending tasks
- **Priority determination** - Focuses on highest priority pending items
- **Intelligent continuation** - Resumes with appropriate next steps

### 4. Implementation & Tracking
- **Real-time progress updates** - Marks tasks complete as they finish
- **File synchronization** - Keeps task file current with progress
- **Status logging** - Adds implementation notes and timestamps
- **Completion detection** - Monitors for task completion

### 5. Cleanup & Completion
- **Automatic file deletion** - Removes task files when 100% complete
- **Completion confirmation** - Notifies user of successful completion
- **Workspace maintenance** - Keeps directory clean and organized

## Interactive Task Selection

### Available Tasks Display
```
🔄 Available task files in .gosu directory:

1. plan-20240712_143022.md
   Type: plan | Created: 2024-07-12 | Status: Implementation In Progress
   Progress: 8/12 tasks completed (67%)

2. review-20240712_151045.md
   Type: review | Created: 2024-07-12 | Status: Review Complete - Awaiting User Approval
   Progress: 0/15 issues fixed (0%)

3. security-20240712_160315.md
   Type: security | Created: 2024-07-12 | Status: Security Review Complete - Awaiting User Approval
   Progress: 0/8 vulnerabilities fixed (0%)

Enter the number of the task you want to work on (1-3):
```

### Task Selection Options
- **Number selection** - Choose from numbered list
- **Direct filename** - Specify exact filename as parameter
- **Status-based filtering** - Focus on specific task types or states
- **Progress-based priority** - Automatically suggest next logical task

## Task Type Resumption

### Plan Files (`plan-*.md`)
**Resumption Process:**
1. **Read current plan status** and implementation progress
2. **Identify completed vs pending tasks** from checkbox states (`[x]` vs `[ ]`)
3. **Resume implementation** from highest priority pending task
4. **Update plan file** with progress as tasks complete
5. **Phase-by-phase continuation** following original implementation roadmap

**Example Resumption:**
```
🔄 Resuming plan-20240712_143022.md...

📋 PLAN ANALYSIS
Feature: User Profile Management System
Status: Implementation In Progress

Progress Summary:
✅ Phase 1: Foundation (4/4 tasks completed)
✅ Phase 2: Core Feature (3/5 tasks completed)  
⏳ Phase 3: Integration (0/3 tasks completed)
⏳ Phase 4: Testing & Documentation (0/2 tasks completed)

🔄 Resuming with: Implement avatar upload validation (Phase 2, Task 4)

Creating todo list with remaining 7 tasks...
```

### Review Files (`review-*.md`)
**Resumption Process:**
1. **Read current review status** and fix progress
2. **Identify fixed vs pending issues** from checkbox states
3. **Resume fixing issues** based on priority level (High → Medium → Low)
4. **Update review file** with fix progress and timestamps
5. **Priority-driven continuation** focusing on critical issues first

**Example Resumption:**
```
🔄 Resuming review-20240712_151045.md...

📋 CODE REVIEW ANALYSIS
Code Quality Score: B+ → Target: A-
Status: Implementation In Progress

Progress Summary:
✅ High Priority Issues (2/3 fixed) 
⏳ Medium Priority Issues (0/8 fixed)
⏳ Low Priority Issues (0/5 fixed)

🔄 Resuming with: Fix circular dependency in auth module (High Priority)

Creating todo list with remaining 11 issues...
```

### Security Files (`security-*.md`)
**Resumption Process:**
1. **Read current security status** and remediation progress
2. **Identify fixed vs pending vulnerabilities** from checkbox states
3. **Resume security fixes** based on severity (Critical → High → Medium → Low)
4. **Update security file** with remediation progress and notes
5. **Risk-driven continuation** prioritizing highest impact vulnerabilities

**Example Resumption:**
```
🔄 Resuming security-20240712_160315.md...

🔒 SECURITY ANALYSIS
Security Posture: C+ → Target: A-
Status: Implementation In Progress

Progress Summary:
✅ Critical Vulnerabilities (1/2 fixed)
⏳ High Priority Issues (0/4 fixed)
⏳ Medium Priority Issues (0/3 fixed)

🔄 Resuming with: Fix SQL injection in user search (Critical)

Creating todo list with remaining 6 vulnerabilities...
```

## Progress Tracking & File Updates

### Real-Time Progress Updates
```bash
# Mark task as completed in task file
sed -i 's/- \[ \] Task Description/- \[x\] Task Description - Completed: $(date)/' "$WORK_FILE"

# Add implementation notes
echo "- Resumed work: $(date) - Implementation notes..." >> "$WORK_FILE"

# Update status in file header
sed -i 's/Status: Implementation In Progress/Status: Phase 2 Complete/' "$WORK_FILE"
```

### Progress Visualization
```
🔄 Task Progress Summary:
Progress: 8/12 tasks completed (67%)

✅ Phase 1: Foundation (4/4 complete)
✅ Phase 2: Core Feature (3/5 complete) 
⏳ Phase 3: Integration (0/3 complete)
⏳ Phase 4: Testing & Documentation (0/2 complete)

Next: Continue Phase 2 implementation
```

## Completion & Cleanup

### Automatic Task Completion
When all tasks reach 100% completion:

```
🎉 TASK COMPLETED SUCCESSFULLY!

Feature: User Profile Management System
Total Tasks: 12/12 completed (100%)
Implementation Time: 2 hours 34 minutes

✅ All phases completed successfully
✅ All tests passing
✅ Documentation updated

🗑️ Cleaning up completed task file: .gosu/plan-20240712_143022.md
✅ Task file deleted - work complete
```

### Manual Cleanup Options
```bash
# Option to cancel and delete incomplete tasks
echo "Would you like to cancel this task and delete the file?"
echo "1. Yes - Delete task file and stop"
echo "2. No - Keep task file for later"

if [ "$CHOICE" = "1" ]; then
  echo "🗑️ Canceling task and deleting file: $WORK_FILE"
  rm "$WORK_FILE"
  echo "❌ Task canceled and file deleted"
fi
```

## Command Options & Examples

### Interactive Mode
```bash
# Show available tasks and prompt for selection
claude gosu:work

# Output shows all available tasks with progress
# User selects by number or filename
```

### Direct Task Resumption
```bash
# Resume specific task by filename
claude gosu:work plan-20240712_143022.md

# Resume most recent task of specific type
claude gosu:work $(ls -t .gosu/plan-*.md | head -1)

# Resume oldest pending task
claude gosu:work $(ls .gosu/*.md | head -1)
```

### Status-Based Selection
```bash
# Resume tasks by status patterns
claude gosu:work  # Lists all with status information
# User can see which tasks are "In Progress" vs "Awaiting Approval"
```

## Error Handling & Validation

### Missing Workspace
```
❌ .gosu directory not found. Run 'claude gosu:init' first to initialize.
```

### No Task Files
```
📁 No task files found in .gosu directory
ℹ️ Create a task first using: gosu:plan, gosu:review, or gosu:security
```

### Invalid File
```
❌ File not found: .gosu/invalid-task.md

Available files:
- plan-20240712_143022.md
- review-20240712_151045.md
```

## Integration with Other Commands

### Task Creation Commands
Commands that create task files:
- **`gosu:plan`** → Creates `plan-YYYYMMDD_HHMMSS.md`
- **`gosu:review`** → Creates `review-YYYYMMDD_HHMMSS.md`  
- **`gosu:security`** → Creates `security-YYYYMMDD_HHMMSS.md`

### Workflow Integration
```bash
# Complete development lifecycle with resumption
claude gosu:plan "new feature"     # Plan and start implementation
# ... work session ends ...
claude gosu:work                   # Resume planning/implementation

claude gosu:review                 # Review implemented code
# ... work session ends ...
claude gosu:work                   # Resume code quality improvements

claude gosu:security               # Security audit
# ... work session ends ...
claude gosu:work                   # Resume security fixes
```

## Best Practices

### When to Use
- **Interrupted work sessions** - Resume exactly where you left off
- **Large feature implementations** - Break work across multiple sessions  
- **Code quality improvement cycles** - Fix issues incrementally
- **Security remediation projects** - Address vulnerabilities systematically
- **Team handoffs** - Transfer work context between developers

### Workflow Patterns
```bash
# Daily development pattern
morning:   claude gosu:work        # Resume yesterday's work
midday:    # Continue working...
evening:   # Work automatically saves progress

next_day:  claude gosu:work        # Continue from exact stopping point
```

### File Management
- **Automatic cleanup** - Completed tasks are automatically removed
- **Manual cleanup** - Option to cancel and delete incomplete tasks
- **Progress preservation** - All work is saved incrementally
- **Context maintenance** - Full task context preserved between sessions

## Related Commands

- [`gosu:init`](./init.md) - Initialize workspace (required prerequisite)
- [`gosu:plan`](./plan.md) - Feature planning that creates resumable task files
- [`gosu:review`](./review.md) - Code review that creates resumable task files
- [`gosu:security`](./security.md) - Security audit that creates resumable task files

## Support

The work command is part of the gosu suite. For general information, see the [main documentation](../README.md).