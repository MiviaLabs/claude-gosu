# Gosu Summary Command

**Generate comprehensive work summary reports with team productivity analysis**

The `gosu:summary` command analyzes git history and GitHub activity to create detailed reports of work completed by each contributor over a specified time period, providing both technical insights and management-focused analytics.

## Usage

```bash
claude gosu:summary [days]
```

### Parameters

- `days` (optional): Number of days to look back from today (default: 7)

### Examples

```bash
# Generate report for last 7 days (default)
claude gosu:summary

# Generate report for last 30 days
claude gosu:summary 30

# Generate quarterly report (90 days)
claude gosu:summary 90

# Sprint retrospective (14 days)
claude gosu:summary 14
```

## Output Structure

### Executive Summary (Manager-Focused)

#### Project Health Overview
- High-level narrative of team productivity and overall code growth
- Development velocity assessment with activity level categorization
- Team collaboration metrics and contributor balance analysis

#### Work Distribution Analysis
- Breakdown of feature development vs maintenance work
- Percentage analysis of different commit types (features, fixes, refactoring)
- Risk identification and recommendations for process improvements

#### Key Development Areas
- Intelligence about which parts of the codebase are most active
- Categorized analysis of backend, database, testing, and infrastructure work
- Project focus area identification with file change metrics

#### Development Timeline
- Daily commit activity visualization with ASCII bars
- Pattern analysis for planning and resource allocation
- Historical trend identification

### Individual Contributor Analysis

#### Personal Accomplishments
- AI-generated summary of each person's major contributions
- Intelligent commit message analysis with contextual categorization:
  - **API Development**: REST endpoints and controller implementations
  - **Database Schema**: Migrations, entities, and data model work
  - **Type System**: TypeScript interfaces and type definitions
  - **Architecture**: Module structure and dependency injection
  - **Business Logic**: Core application services and functionality

#### Technical Impact Assessment
- Code contribution metrics (lines added/deleted, files changed)
- Productivity scoring with intelligent interpretation
- File-based analysis showing areas of focused development
- Commit frequency and consistency patterns

#### Work Narrative Generation
The command provides intelligent analysis of actual code changes rather than just commit messages:

- **Feature Analysis**: Identifies API endpoints, database work, architecture changes
- **Bug Fix Categorization**: Validates validation fixes, security patches, error handling
- **Refactoring Impact**: Code organization, performance optimizations, quality improvements

### Pull Request Information

When GitHub CLI (`gh`) is available, the report includes:
- **Merged Pull Requests**: PRs merged in the time period with author attribution
- **Created Pull Requests**: New PRs created with current status tracking

### Report Persistence

#### Automatic Saving
- Reports are automatically saved to `.gosu/` directory (if it exists after running `gosu:init`)
- Filename format: `work-summary-YYYY-MM-DD-to-YYYY-MM-DD-Xdays.md`
- Historical tracking for trend analysis and comparison

#### File Structure
```
.gosu/
├── work-summary-2024-07-01-to-2024-07-07-7days.md
├── work-summary-2024-07-01-to-2024-07-31-30days.md
└── work-summary-2024-06-01-to-2024-08-31-90days.md
```

## Key Features

### Language Agnostic Analysis
The command automatically adapts its analysis patterns based on detected technology stack:
- **JavaScript/TypeScript**: Controllers, services, modules, DTOs
- **Python**: Classes, functions, Django models, Flask routes
- **Java**: Spring controllers, entities, repositories
- **C#/.NET**: Controllers, services, models, configurations
- **Go**: Handlers, structs, interfaces, packages
- And more...

### Intelligent Categorization
Commit analysis goes beyond simple message parsing:

#### Code Content Analysis
- Examines actual diff content to understand what changed
- Identifies patterns like `@Controller`, `CREATE TABLE`, `interface {}` 
- Categorizes work based on technical implementation details

#### Smart Grouping
- Groups similar work across team members
- Identifies project-wide initiatives and technical debt reduction
- Recognizes architectural improvements and infrastructure work

#### Context-Aware Narratives
- Generates human-readable summaries of technical accomplishments
- Explains the business impact of code changes
- Provides actionable insights for project management

### Management Insights

#### Risk Analysis
- **High Bug Fix Ratio**: Alerts when fixes exceed feature development
- **Single Contributor Risk**: Identifies knowledge sharing gaps
- **Work Distribution**: Flags unbalanced workload across team members
- **Documentation Gap**: Highlights missing documentation work

#### Productivity Metrics
- Lines of code per commit analysis with intelligent interpretation
- Commit frequency patterns and consistency tracking
- Team collaboration effectiveness measurement
- Development velocity categorization (Very High/High/Moderate/Low)

#### Recommendations
- Process improvement suggestions based on commit patterns
- Resource allocation recommendations for balanced team workload
- Quality assurance insights based on testing and documentation activity

## Use Cases

### Sprint Reviews & Retrospectives
```bash
# Generate 2-week sprint summary
claude gosu:summary 14
```
Perfect for sprint retrospectives, showing individual contributions and team velocity.

### Manager Updates & Status Reports
```bash
# Monthly team productivity report
claude gosu:summary 30
```
Comprehensive overview for stakeholder updates with executive summary and metrics.

### Performance Reviews
```bash
# Quarterly individual contribution analysis
claude gosu:summary 90
```
Detailed individual contributor analysis with technical impact assessment.

### Project Health Monitoring
```bash
# Weekly team health check
claude gosu:summary 7
```
Regular monitoring of development patterns, code quality trends, and team balance.

### Release Planning
```bash
# Feature development cycle analysis
claude gosu:summary 45
```
Understanding development velocity and capacity for future sprint planning.

## Sample Output Structure

```markdown
# Work Summary Report
**Period:** 2024-07-15 to 2024-07-21 (7 days)
**Generated:** 2024-07-21 15:30:45

## Contributors Summary

### John Smith (john@company.com)

**Statistics:**
- Commits: 12
- Lines added: 456
- Lines deleted: 78
- Files changed: 24

**Work Narrative:**
📍 **API Development**: Enhanced user authentication endpoints
   └ Implemented new REST endpoints and controller logic
🐛 **Security Fix**: Fixed JWT token validation vulnerability
   └ Corrected authentication and authorization issues
🔧 **Code Quality**: Refactored user service for better maintainability
   └ Enhanced code structure and readability

**Technical Impact:**
⚙️  **Service Layer**: Developed business logic in auth.service.ts (5 modifications)
🎯 **API Layer**: Enhanced REST endpoints in auth.controller.ts (3 modifications)

**Impact & Metrics:**
- Code contribution: +456/-78 lines across 24 files
- Commit frequency: 12 commits over 7 days (avg: 12 per week)
- Productivity level: Medium (38 lines per commit)

---

## Executive Summary

**Project Narrative:**
During this 7-day development cycle, the team accomplished significant progress across multiple technical areas.

The development effort heavily focused on **API expansion**, with 8 new endpoints and controller implementations that enhance the system's integration capabilities.

**Database infrastructure** saw substantial improvements with 3 schema enhancements, strengthening the data layer foundation.

**Quantitative Summary:**
The team collectively contributed 45 commits, adding 1,247 lines while removing 234 lines, resulting in a net codebase growth of 1,013 lines across 89 files.

**Development Velocity:**
- Activity Level: High (6 commits/day average)
- Team Collaboration: 15 commits per contributor on average
- Code Volume: 416 lines added per contributor on average
```

## Integration with Other Commands

### Workflow Integration
```bash
# Initialize workspace first
claude gosu:init

# After development cycles, generate reports
claude gosu:summary 14

# Use with other commands for comprehensive analysis
claude gosu:review && claude gosu:security && claude gosu:summary 30
```

### Cross-Session Usage
The summary command integrates seamlessly with persistent task management:
- Reports are saved alongside other task files in `.gosu/`
- Historical reports provide context for ongoing work
- Can be used to track progress on tasks created by other commands

## Prerequisites

### Required Tools
- **Git**: Repository with commit history
- **Claude Code**: For command execution

### Optional Enhancements
- **GitHub CLI (`gh`)**: Enables pull request information in reports
- **Initialized Workspace**: `.gosu/` directory for report persistence (via `gosu:init`)

## Technical Implementation

### Intelligent Analysis Engine
The command uses sophisticated bash scripting with:
- Git log parsing with statistical analysis
- Diff content examination for contextual understanding
- Pattern matching for technology stack detection
- Dynamic categorization based on code patterns

### Performance Optimizations
- Efficient git operations with limited output processing
- Parallel analysis of multiple contributors
- Smart caching of repository statistics
- Optimized file pattern matching for large repositories

### Output Formatting
- Clean Markdown formatting for readability
- ASCII visualization for timeline data
- Structured sections for easy parsing
- Consistent emoji usage for visual categorization

The `gosu:summary` command transforms raw git history into actionable insights, making it an essential tool for team leads, project managers, and individual contributors who need comprehensive visibility into development progress and team productivity.