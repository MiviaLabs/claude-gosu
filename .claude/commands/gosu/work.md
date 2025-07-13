# Gosu Work Command

## Usage
```
gosu:work [filename]
```

**Target File:** $ARGUMENTS

## Description
Resume work on a previously saved task from the `.gosu` directory. If no filename is provided, lists available tasks and asks user to choose.

## Command
```bash
#!/bin/bash

# Gosu Work Command - Resume work on previously saved tasks
# Usage: gosu:work [filename]

set -e

ARGUMENTS="$ARGUMENTS"

# Step 1: Check .gosu Directory Existence
if [ ! -d ".gosu" ]; then
  echo "❌ .gosu directory not found. Run 'claude gosu:init' first to initialize."
  exit 1
fi

# Step 2: Parameter Handling
if [ -n "$ARGUMENTS" ]; then
  # Use $ARGUMENTS for filename
  WORK_FILE=".gosu/$ARGUMENTS"
  if [ ! -f "$WORK_FILE" ]; then
    echo "❌ File not found: $WORK_FILE"
    echo "Available files:"
    ls -la .gosu/*.md 2>/dev/null || echo "No task files found in .gosu directory"
    exit 1
  fi
  echo "🔄 Resuming work on: $WORK_FILE"
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
  read -r CHOICE
  
  # Validate choice
  if ! [[ "$CHOICE" =~ ^[0-9]+$ ]] || [ "$CHOICE" -lt 1 ] || [ "$CHOICE" -gt ${#TASK_FILES[@]} ]; then
    echo "❌ Invalid choice. Please enter a number between 1 and ${#TASK_FILES[@]}"
    exit 1
  fi
  
  # Set the work file based on choice
  WORK_FILE="${TASK_FILES[$((CHOICE-1))]}"
  echo "🔄 Resuming work on: $WORK_FILE"
fi

# Step 3: Analyze task file status
STATUS=$(grep "Status:" "$WORK_FILE" | head -1 | cut -d':' -f2 | xargs || echo "unknown")
TASK_TYPE=$(basename "$WORK_FILE" | cut -d'-' -f1)

echo ""
echo "📊 Task Analysis:"
echo "   File: $(basename "$WORK_FILE")"
echo "   Type: $TASK_TYPE"
echo "   Status: $STATUS"

# Step 4: Progress Analysis
TOTAL_TASKS=$(grep -c "- \[ \]\|- \[x\]" "$WORK_FILE" 2>/dev/null || echo "0")
COMPLETED_TASKS=$(grep -c "- \[x\]" "$WORK_FILE" 2>/dev/null || echo "0")

if [ "$TOTAL_TASKS" -gt 0 ]; then
  PROGRESS=$((COMPLETED_TASKS * 100 / TOTAL_TASKS))
  echo "   Progress: $COMPLETED_TASKS/$TOTAL_TASKS tasks completed ($PROGRESS%)"
  
  # Check if task is 100% complete
  if [ "$PROGRESS" -eq 100 ]; then
    echo ""
    echo "🎉 Task completed successfully!"
    echo "🗑️ Cleaning up completed task file: $WORK_FILE"
    rm "$WORK_FILE"
    echo "✅ Task file deleted - work complete"
    exit 0
  fi
else
  echo "   Progress: No tasks found"
fi

echo ""

# Step 5: Status-based Action Determination
case "$STATUS" in
  "Planning Complete - Awaiting User Approval"|"Review Complete - Awaiting User Approval"|"Security Review Complete - Awaiting User Approval")
    echo "✅ Task is ready for implementation. Would you like to begin?"
    echo "Options:"
    echo "1. Yes - Begin implementation following the saved plan"
    echo "2. Review - Show me the plan/review/security report first"
    echo "3. Modify - Update the plan/review/security report"
    echo "4. Cancel - Exit without changes"
    echo ""
    echo "Enter your choice (1-4):"
    read -r ACTION_CHOICE
    
    case "$ACTION_CHOICE" in
      "1")
        echo "🚀 Beginning implementation..."
        # Update status to Implementation In Progress
        sed -i "s/Status: $STATUS/Status: Implementation In Progress/" "$WORK_FILE"
        echo "- Resumed work: $(date) - Beginning implementation" >> "$WORK_FILE"
        ;;
      "2")
        echo "📖 Displaying task file content:"
        echo "==========================================="
        cat "$WORK_FILE"
        echo "==========================================="
        exit 0
        ;;
      "3")
        echo "✏️ Opening task file for modification: $WORK_FILE"
        echo "Please modify the file and run the command again."
        exit 0
        ;;
      "4")
        echo "❌ Cancelled"
        exit 0
        ;;
      *)
        echo "❌ Invalid choice. Exiting."
        exit 1
        ;;
    esac
    ;;
  "Implementation In Progress")
    echo "🔄 Task implementation is in progress. Resuming from last checkpoint..."
    echo "- Resumed work: $(date) - Continuing from checkpoint" >> "$WORK_FILE"
    ;;
  *)
    echo "📋 Task status: $STATUS"
    echo "🔍 Analyzing task file to determine next steps..."
    echo "- Work session: $(date) - Analyzing current state" >> "$WORK_FILE"
    ;;
esac

echo ""
echo "📝 Task File Content:"
echo "==========================================="
cat "$WORK_FILE"
echo ""
echo "==========================================="

# Step 6: Show pending tasks
echo ""
echo "⏳ Pending Tasks:"
grep "- \[ \]" "$WORK_FILE" 2>/dev/null | head -5 | sed 's/^/   /' || echo "   No pending tasks found"

if [ "$(grep -c "- \[ \]" "$WORK_FILE" 2>/dev/null || echo "0")" -gt 5 ]; then
  MORE_TASKS=$(($(grep -c "- \[ \]" "$WORK_FILE") - 5))
  echo "   ... and $MORE_TASKS more tasks"
fi

echo ""
echo "🎯 Ready to continue implementation!"
echo "💡 Tip: As you complete tasks, update the checkboxes in $WORK_FILE"
echo "🔄 Run 'gosu:work $(basename "$WORK_FILE")' again to check progress"
```

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

## Features

This command provides a complete task management system:

- **📋 Interactive Selection:** Lists available task files with metadata when no parameter provided
- **📊 Progress Tracking:** Shows completion percentage with checkbox analysis (`- [ ]` vs `- [x]`)
- **🔄 Status Management:** Handles different task states (Planning Complete, Implementation In Progress, etc.)
- **🎯 Context Restoration:** Displays task content and pending items for full context
- **🗑️ Automatic Cleanup:** Deletes completed task files (100% progress)
- **⚡ Smart Actions:** Provides contextual options based on task status

## Task Integration

Works seamlessly with other gosu commands:
- **gosu:plan** → creates plan files → **gosu:work** resumes implementation
- **gosu:review** → creates review files → **gosu:work** resumes fixing issues  
- **gosu:security** → creates security files → **gosu:work** resumes vulnerability fixes

## Example Output

```
📋 Available task files in .gosu directory:

1. plan-implementation-20240712_143022.md
   Type: plan | Created: 2024-07-12 | Status: Implementation In Progress

2. security-review-20240712_160315.md
   Type: security | Created: 2024-07-12 | Status: Security Review Complete

📊 Task Analysis:
   File: security-review-20240712_160315.md
   Type: security
   Status: Security Review Complete
   Progress: 7/10 tasks completed (70%)

⏳ Pending Tasks:
   - [ ] Implement rate limiting protection
   - [ ] Add security monitoring system
   - [ ] Update dependency vulnerabilities
```