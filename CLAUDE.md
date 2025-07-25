# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Claude Gosu is a collection of advanced Claude Code commands for comprehensive code analysis and improvement. This is a command package that provides seven main commands:

- `gosu:init` - Initialize workspace for persistent task management
- `gosu:plan` - Feature planning with implementation roadmaps
- `gosu:review` - Code quality review with intelligent improvements  
- `gosu:security` - Comprehensive cybersecurity analysis and vulnerability fixes
- `gosu:spec` - Comprehensive feature specification creation with stakeholder analysis
- `gosu:jira` - JIRA issue management through MCP integration  
- `gosu:work` - Resume work on previously saved tasks

## Architecture

### Command Structure
Each command follows a standardized workflow:
1. Technology stack auto-detection
2. Comprehensive analysis phase
3. Stop and ask for user confirmation before making changes
4. Intelligent multi-agent coordination for complex tasks
5. Priority-based implementation (Critical → High → Medium → Low)

### Multi-Agent Coordination
Commands automatically determine when to deploy multiple specialized agents based on:
- Issue count and complexity (>10-15 issues typically triggers multi-agent)
- File distribution across codebase
- Task independence and technology diversity

### Documentation Structure
- `/docs/init.md` - Workspace initialization command documentation
- `/docs/plan.md` - Feature planning command documentation
- `/docs/review.md` - Code quality review command documentation  
- `/docs/security.md` - Detailed security command documentation
- `/docs/spec.md` - Feature specification command documentation
- `/docs/jira.md` - JIRA MCP integration command documentation
- `/docs/work.md` - Task resumption command documentation
- `/docs/jira-mcp-integration.md` - Comprehensive JIRA MCP setup and usage guide
- `README.md` - Main project documentation and usage examples

## Development Commands

Based on package.json analysis:
- **Test**: `npm test` (currently placeholder - "Error: no test specified")
- **No build/lint commands defined** - this is a command package, not a traditional codebase

## Key Features

### Language Agnostic
All commands automatically detect and adapt to any programming language or technology stack:
- JavaScript/TypeScript/Node.js, Python, Java, C#/.NET, Go, Ruby, PHP, etc.

### User Control & Safety
- Commands always analyze first, then stop for user confirmation
- No changes made without explicit user approval
- Multiple implementation options: Yes/No/Selective/High Priority Only
- Persistent task management with cross-session continuity
- Automatic progress tracking and file cleanup

### Technology-Specific Analysis
Each command adapts its analysis patterns based on detected stack:
- Framework-specific security patterns
- Language-specific code quality rules
- Technology-appropriate best practices

## Command Usage Patterns

```bash
# Initialize workspace (first time)
claude gosu:init

# Feature specification creation
claude gosu:spec "user profile management system"

# Feature planning and implementation
claude gosu:plan "feature description"

# Code quality review  
claude gosu:review

# Security audit
claude gosu:security

# JIRA issue management
claude gosu:jira "create task 'Fix login bug' in ROS"

# Resume any saved task
claude gosu:work

# Combined workflow with persistence
claude gosu:init && claude gosu:spec "feature" && claude gosu:plan "feature" && claude gosu:review && claude gosu:security

# Cross-session workflow with specifications
claude gosu:spec "feature"  # Create comprehensive specification
# ... session ends ...
claude gosu:work            # Resume specification work
claude gosu:plan "feature"  # Create implementation plan
# ... session ends ...
claude gosu:work            # Resume exactly where left off
```

## Persistent Task Management

### Workspace Initialization
Commands support persistent task management through the `.gosu` directory:
```bash
# Initialize workspace
claude gosu:init
# Creates .gosu/ directory and updates .gitignore
```

### Task File Structure
After initialization, commands create persistent task files:
```
.gosu/
├── spec-YYYYMMDD_HHMMSS.md      # Feature specifications
├── plan-YYYYMMDD_HHMMSS.md      # Feature implementation plans
├── review-YYYYMMDD_HHMMSS.md    # Code quality reviews
└── security-YYYYMMDD_HHMMSS.md  # Security audit reports
```

### Task Resumption
Work can be resumed across sessions with full context:
```bash
# Resume any saved task
claude gosu:work

# Resume specific task
claude gosu:work spec-20240712_143022.md
claude gosu:work plan-20240712_143022.md
```

### Progress Tracking
Task files include:
- **Checkbox progress tracking** (`[x]` completed, `[ ]` pending)
- **Implementation notes** and timestamps
- **Status indicators** and completion state
- **Automatic cleanup** when tasks reach 100% completion

## Project Type
This is a command definition package, not a traditional application. The commands are designed to be invoked within other codebases to provide analysis and improvement capabilities with optional persistent task management.