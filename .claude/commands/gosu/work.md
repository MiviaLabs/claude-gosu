# Gosu Work Command

## Usage
```
gosu:work [filename]
```

**Target File:** $ARGUMENTS

## Description
Resume work on a previously saved task from the `.gosu` directory. If no filename is provided, lists available tasks and asks user to choose.

## Command Logic

### With Parameter - Resume Specific Task
```bash
claude gosu:work plan-20240712_143022.md
claude gosu:work review-20240712_151045.md  
claude gosu:work security-20240712_160315.md
```

### Without Parameter - Interactive Selection
```bash
claude gosu:work
```

## Implementation

### Step 1: Check .gosu Directory Existence
```bash
# Check if .gosu directory exists
if [ ! -d ".gosu" ]; then
  echo "L .gosu directory not found. Run 'claude gosu:init' first to initialize."
  exit 1
fi
```

### Step 2: Parameter Handling

#### If filename parameter is provided:
```bash
# Use $ARGUMENTS for filename
if [ -n "$ARGUMENTS" ]; then
  WORK_FILE=".gosu/$ARGUMENTS"
  if [ ! -f "$WORK_FILE" ]; then
    echo "❌ File not found: $WORK_FILE"
    echo "Available files:"
    ls -la .gosu/*.md 2>/dev/null || echo "No task files found in .gosu directory"
    exit 1
  fi
  echo "🔄 Resuming work on: $WORK_FILE"
```

#### If no parameter provided:
```bash
else
  # List available task files
  echo "📋 Available task files in .gosu directory:"
  echo ""

  TASK_FILES=($(ls .gosu/*.md 2>/dev/null))
  if [ ${#TASK_FILES[@]} -eq 0 ]; then
    echo "❌ No task files found in .gosu directory"
    echo "📝 Create a task first using: gosu:plan, gosu:review, or gosu:security"
    exit 1
  fi

# Display numbered list
for i in "${!TASK_FILES[@]}"; do
  FILE="${TASK_FILES[$i]}"
  BASENAME=$(basename "$FILE")
  
  # Extract task type and timestamp from filename
  TASK_TYPE=$(echo "$BASENAME" | cut -d'-' -f1)
  TIMESTAMP=$(echo "$BASENAME" | cut -d'-' -f2- | sed 's/\.md$//')
  
  # Get file creation date and status
  CREATED=$(stat -c %y "$FILE" 2>/dev/null | cut -d' ' -f1 || echo "unknown")
  STATUS=$(grep "Status:" "$FILE" | head -1 | cut -d':' -f2 | xargs || echo "unknown")
  
  echo "$((i+1)). $BASENAME"
  echo "   Type: $TASK_TYPE | Created: $CREATED | Status: $STATUS"
  echo ""
done

  echo "Enter the number of the task you want to work on (1-${#TASK_FILES[@]}):"
fi
```

### Step 3: Task Resume Logic

The AI will analyze the selected task file and determine the appropriate action:

#### For Plan Files (plan-*.md):
1. **Read the current plan status**
2. **Identify completed vs pending tasks** from checkbox states
3. **Resume implementation** from where it left off
4. **Update the plan file** with progress as tasks are completed

#### For Review Files (review-*.md):
1. **Read the current review status**
2. **Identify fixed vs pending issues** from checkbox states  
3. **Resume fixing issues** based on priority
4. **Update the review file** with fix progress

#### For Security Files (security-*.md):
1. **Read the current security status**
2. **Identify fixed vs pending vulnerabilities** from checkbox states
3. **Resume security fixes** based on severity
4. **Update the security file** with remediation progress

### Step 4: Status Analysis & Action Determination

```bash
# Analyze task file status
STATUS=$(grep "Status:" "$WORK_FILE" | head -1 | cut -d':' -f2 | xargs)
TASK_TYPE=$(basename "$WORK_FILE" | cut -d'-' -f1)

case "$STATUS" in
  "Planning Complete - Awaiting User Approval"|"Review Complete - Awaiting User Approval"|"Security Review Complete - Awaiting User Approval")
    echo "= Task is ready for implementation. Would you like to begin?"
    echo "Options:"
    echo "1. Yes - Begin implementation following the saved plan"
    echo "2. Review - Show me the plan/review/security report first"
    echo "3. Modify - Update the plan/review/security report"
    ;;
  "Implementation In Progress")
    echo "=� Task implementation is in progress. Resuming from last checkpoint..."
    # Continue implementation based on checkbox states
    ;;
  *)
    echo "=� Task status: $STATUS"
    echo "=� Analyzing task file to determine next steps..."
    ;;
esac
```

### Step 5: Implementation Resume

Based on the task type and status, the AI will:

1. **Parse the task file** to understand:
   - What has been completed (checked boxes: `- [x]`)
   - What is still pending (unchecked boxes: `- [ ]`)
   - Current implementation status and notes

2. **Create a focused todo list** with only the remaining tasks

3. **Begin implementation** following the original plan/review/security priorities

4. **Update the task file** in real-time as each item is completed:
   ```bash
   # Mark task as completed in the file
   sed -i 's/- \[ \] Task Name: Description/- \[x\] Task Name: Description - Completed: $(date)/' "$WORK_FILE"
   ```

5. **Add implementation notes** to track progress:
   ```bash
   echo "- Resumed work: $(date) - Continuing from checkpoint" >> "$WORK_FILE"
   ```

## Task File Status Tracking

### Plan Files Progress Tracking
- **Phase 1: Foundation** - Database, core models
- **Phase 2: Core Feature** - API, business logic  
- **Phase 3: Integration** - Auth, file handling
- **Phase 4: Testing & Documentation** - Tests, docs

### Review Files Progress Tracking
- **High Priority Issues** - Critical fixes
- **Medium Priority Issues** - Quality improvements
- **Low Priority Issues** - Style and minor optimizations

### Security Files Progress Tracking  
- **Critical Vulnerabilities** - Immediate security fixes
- **High Priority Issues** - Important security improvements
- **Medium/Low Priority** - Configuration hardening

## Example Usage Flow

```bash
# List available tasks
$ claude gosu:work
=� Available task files in .gosu directory:

1. plan-20240712_143022.md
   Type: plan | Created: 2024-07-12 | Status: Implementation In Progress

2. review-20240712_151045.md
   Type: review | Created: 2024-07-12 | Status: Review Complete - Awaiting User Approval

3. security-20240712_160315.md
   Type: security | Created: 2024-07-12 | Status: Security Review Complete - Awaiting User Approval

Enter the number of the task you want to work on (1-3): 1

# Resume specific task
=� Task implementation is in progress. Resuming from last checkpoint...
=� Analyzing plan-20240712_143022.md...
 Phase 1: Foundation (3/4 tasks completed)
� Phase 2: Core Feature (0/5 tasks completed)  
� Phase 3: Integration (0/3 tasks completed)
� Phase 4: Testing & Documentation (0/2 tasks completed)

<� Resuming with: Implement user validation service (Phase 1, Task 4)
```

## Integration with Existing Commands

The `gosu:work` command seamlessly integrates with the updated persistence-enabled commands:

- **gosu:plan** � creates plan files � **gosu:work** resumes implementation
- **gosu:review** � creates review files � **gosu:work** resumes fixing issues  
- **gosu:security** � creates security files � **gosu:work** resumes vulnerability fixes

This creates a complete task lifecycle:
1. **Plan/Review/Analyze** with persistence
2. **Pause** work at any time  
3. **Resume** later with full context
4. **Track progress** with real-time file updates
5. **Complete** tasks with full audit trail

## Advanced Features

### Progress Visualization
```bash
# Show progress summary
echo "=� Task Progress Summary:"
TOTAL_TASKS=$(grep -c "- \[ \]\|- \[x\]" "$WORK_FILE")
COMPLETED_TASKS=$(grep -c "- \[x\]" "$WORK_FILE")
PROGRESS=$((COMPLETED_TASKS * 100 / TOTAL_TASKS))
echo "Progress: $COMPLETED_TASKS/$TOTAL_TASKS tasks completed ($PROGRESS%)"
```

### File Cleanup
```bash
# Option to archive completed tasks
if [ "$PROGRESS" -eq 100 ]; then
  echo "<� Task completed! Would you like to archive this file?"
  echo "1. Yes - Move to .gosu/completed/"
  echo "2. No - Keep in .gosu/"
fi
```

### Task Completion & Cleanup

When a task reaches 100% completion, the `gosu:work` command automatically cleans up the task file:

```bash
# Automatic cleanup when task is 100% complete
if [ "$PROGRESS" -eq 100 ]; then
  echo "🎉 Task completed successfully!"
  echo "🗑️ Cleaning up completed task file: $WORK_FILE"
  rm "$WORK_FILE"
  echo "✅ Task file deleted - work complete"
fi
```

**Behavior:**
- **Automatic deletion** when all tasks are marked as completed (`[x]`)
- **Clean workspace** - no leftover files for finished work
- **Completion confirmation** with user feedback

### User Cancellation Handling

If a user wants to cancel work on a task:

```bash
# Option to cancel current work
echo "Would you like to cancel this task and delete the file?"
echo "1. Yes - Delete task file and stop"
echo "2. No - Keep task file for later"

if [ "$CHOICE" = "1" ]; then
  echo "🗑️ Canceling task and deleting file: $WORK_FILE"
  rm "$WORK_FILE"
  echo "❌ Task canceled and file deleted"
fi
```

This command creates a powerful task resumption system that maintains full context and progress tracking across AI sessions.