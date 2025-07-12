# Initialization Command (`gosu:init`)

Initialize Gosu workspace for persistent task management with automatic gitignore configuration.

## Overview

The init command sets up the Gosu workspace by creating the `.gosu` directory and configuring git to ignore it. This enables persistent task management across all other gosu commands (`gosu:plan`, `gosu:review`, `gosu:security`) and allows resuming work with `gosu:work`.

## Usage

```bash
claude gosu:init
```

## What It Does

### 🗂️ **Workspace Initialization**
- **Creates `.gosu` directory** in the project root for persistent task storage
- **Updates `.gitignore`** to exclude `.gosu` from version control (if git repository)
- **Creates `.gitignore`** with `.gosu` entry if the file doesn't exist (if git repository)
- **Safe operation** - won't overwrite existing directories or duplicate gitignore entries

### 📁 **Directory Structure Created**
```
project-root/
├── .gosu/                  # Created by gosu:init
│   ├── plan-YYYYMMDD_HHMMSS.md     # Created by gosu:plan
│   ├── review-YYYYMMDD_HHMMSS.md   # Created by gosu:review
│   └── security-YYYYMMDD_HHMMSS.md # Created by gosu:security
├── .gitignore              # Updated by gosu:init
└── ... (your project files)
```

## Process Flow

1. **Directory Creation**
   - Creates `.gosu` directory in current working directory
   - Directory serves as persistent storage for task files
   - Safe operation - skips if directory already exists

2. **Git Integration** (if git repository detected)
   - Checks if `.gitignore` exists
   - Adds `.gosu` entry if not already present
   - Creates `.gitignore` with `.gosu` entry if file doesn't exist
   - Prevents task files from being committed to version control

3. **Workspace Ready**
   - Enables persistent task management for other gosu commands
   - Prepares environment for task resumption with `gosu:work`

## When to Use

### First Time Setup
```bash
# Initialize gosu workspace in any project
cd your-project/
claude gosu:init
```

### Required Before Using
The init command should be run before using persistent features:
- **Before `gosu:plan`** - To enable plan file persistence
- **Before `gosu:review`** - To enable review file persistence  
- **Before `gosu:security`** - To enable security report persistence
- **Required for `gosu:work`** - Workspace needed for task resumption

### Git Repository Benefits
For git repositories, initialization provides:
- **Automatic gitignore management** - Prevents committing temporary task files
- **Team workspace isolation** - Each developer has their own `.gosu` directory
- **Clean repository** - Task management files stay local

## Integration with Other Commands

### Persistent Task Management
After initialization, all gosu commands gain persistence:

```bash
# Initialize workspace (one time)
claude gosu:init

# Plan feature with persistence
claude gosu:plan "user authentication system"
# Creates: .gosu/plan-20240712_143022.md

# Review code with persistence  
claude gosu:review
# Creates: .gosu/review-20240712_151045.md

# Security audit with persistence
claude gosu:security
# Creates: .gosu/security-20240712_160315.md

# Resume any saved task
claude gosu:work
# Lists available task files for resumption
```

### File Persistence Benefits
With `.gosu` directory:
- **Task continuity** - Resume work across AI sessions
- **Progress tracking** - Checkbox progress in task files
- **Context preservation** - Full task context and implementation notes
- **Audit trail** - Complete history of analysis and implementation

## Command Details

### Git Repository Detection
```bash
# Checks for git repository
if [ -d ".git" ]; then
  # Git repository detected - manage .gitignore
fi
```

### Gitignore Management
```bash
# If .gitignore exists
if [ -f ".gitignore" ]; then
  # Add .gosu entry if not present
  if ! grep -q "^\.gosu$" .gitignore; then
    echo ".gosu" >> .gitignore
  fi
# If .gitignore doesn't exist
else
  # Create .gitignore with .gosu entry
  echo ".gosu" > .gitignore
fi
```

### Directory Creation
```bash
# Create .gosu directory safely
mkdir -p .gosu
```

## Output Examples

### Successful Initialization
```
🏗️ GOSU WORKSPACE INITIALIZATION

✅ Created .gosu directory
✅ Updated .gitignore (added .gosu entry)

Gosu workspace ready for persistent task management!

Available commands:
- claude gosu:plan "feature description"  # Feature planning with persistence
- claude gosu:review                      # Code review with persistence  
- claude gosu:security                    # Security audit with persistence
- claude gosu:work                        # Resume saved tasks

Next steps:
1. Run any gosu command to create task files
2. Use gosu:work to resume tasks across sessions
```

### Already Initialized
```
🏗️ GOSU WORKSPACE CHECK

✅ .gosu directory already exists
✅ .gitignore already contains .gosu entry

Gosu workspace is already initialized and ready!

Use gosu:work to see available tasks.
```

### Non-Git Project
```
🏗️ GOSU WORKSPACE INITIALIZATION

✅ Created .gosu directory
ℹ️ No git repository detected - .gitignore not modified

Gosu workspace ready for persistent task management!
Note: In a git repository, .gosu would be automatically added to .gitignore
```

## Best Practices

### Team Development
```bash
# Each developer initializes their own workspace
cd shared-project/
claude gosu:init  # Creates local .gosu directory

# .gosu is in .gitignore - no conflicts between team members
git status  # .gosu directory not shown
```

### Project Setup Integration
```bash
# Add to project setup documentation
git clone project-repo
cd project-repo
npm install  # or your package manager
claude gosu:init  # Initialize gosu workspace
```

### Maintenance
The `.gosu` directory is self-managing:
- **Task files** created automatically by other gosu commands
- **Cleanup** handled by `gosu:work` when tasks complete
- **No manual maintenance** required after initialization

## Safety Features

### Non-Destructive Operation
- **Safe directory creation** - Uses `mkdir -p` (won't fail if exists)
- **Gitignore preservation** - Only adds entry, never removes existing content
- **Duplicate prevention** - Checks before adding gitignore entries
- **Existing file respect** - Won't overwrite any existing files

### Error Handling
- **Permission checks** - Validates write permissions
- **Path validation** - Ensures valid directory creation
- **Git detection** - Safely handles non-git projects

## Related Commands

- [`gosu:work`](./work.md) - Resume saved tasks (requires initialization)
- [`gosu:plan`](./plan.md) - Feature planning with persistence (enhanced after init)
- [`gosu:review`](./review.md) - Code review with persistence (enhanced after init)
- [`gosu:security`](./security.md) - Security audit with persistence (enhanced after init)

## Support

The init command is part of the gosu suite. For general information, see the [main documentation](../README.md).