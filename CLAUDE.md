# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Claude Gosu is a collection of advanced Claude Code commands for comprehensive code analysis and improvement. This is a command package that provides three main commands:

- `gosu:security` - Comprehensive cybersecurity analysis and vulnerability fixes
- `gosu:review` - Code quality review with intelligent improvements  
- `gosu:plan` - Feature planning with implementation roadmaps

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
- `/docs/security.md` - Detailed security command documentation
- `/docs/review.md` - Code quality review command documentation  
- `/docs/plan.md` - Feature planning command documentation
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

### Technology-Specific Analysis
Each command adapts its analysis patterns based on detected stack:
- Framework-specific security patterns
- Language-specific code quality rules
- Technology-appropriate best practices

## Command Usage Patterns

```bash
# Security audit
claude gosu:security

# Code quality review  
claude gosu:review

# Feature planning
claude gosu:plan "feature description"

# Combined workflow
claude gosu:plan "feature" && claude gosu:review && claude gosu:security
```

## Project Type
This is a command definition package, not a traditional application. The commands are designed to be invoked within other codebases to provide analysis and improvement capabilities.