# Gosu Commands

> **⚡ Optimized for Claude Code Max** - These commands work best with a Claude Code Max subscription for enhanced performance and capabilities.

Gosu is a collection of advanced Claude Code commands for comprehensive code analysis and improvement. These commands provide expert-level security auditing and code quality review with intelligent multi-agent coordination.

## Available Commands

| Command | Description | Documentation |
|---------|-------------|---------------|
| `gosu:init` | Initialize workspace for persistent task management | [Details](./docs/init.md) |
| `gosu:spec` | Professional PM/BA/Tech Lead guided feature specification creation | [Details](./docs/spec.md) |
| `gosu:plan` | Comprehensive feature planning with implementation roadmaps | [Details](./docs/plan.md) |
| `gosu:review` | Code quality review with intelligent improvements | [Details](./docs/review.md) |
| `gosu:security` | Comprehensive cybersecurity analysis and vulnerability fixes | [Details](./docs/security.md) |
| `gosu:jira` | JIRA issue management through MCP integration | [Details](./docs/jira.md) |
| `gosu:summary` | Generate comprehensive work summary reports with team productivity analysis | [Details](./docs/summary.md) |
| `gosu:work` | Resume work on previously saved tasks | [Details](./docs/work.md) |

## Quick Start

All gosu commands follow the same pattern:

```bash
claude gosu:<command>
```

### Basic Usage Examples

```bash
# Initialize workspace (first time setup)
claude gosu:init

# Feature specification creation
claude gosu:spec "user profile management with avatar upload"
# OR interactive mode
claude gosu:spec

# Feature planning and implementation
claude gosu:plan "user profile management with avatar upload"
# OR interactive mode
claude gosu:plan

# Code quality review
claude gosu:review

# Security audit of your codebase
claude gosu:security

# JIRA issue management
claude gosu:jira "create task 'Fix login bug' in PROJ"
# OR interactive mode for guided operations
claude gosu:jira

# Generate work summary report (last 7 days)
claude gosu:summary
# OR for custom time period
claude gosu:summary 30

# Resume any saved task
claude gosu:work
# OR resume specific task
claude gosu:work spec-20240712_143022.md
claude gosu:work plan-20240712_143022.md
```

## Key Features

### Language Agnostic
All commands automatically detect and adapt to any programming language or technology stack:
- JavaScript/TypeScript/Node.js
- Python (Django, Flask)
- Java (Spring, Maven)
- C#/.NET
- Go, Ruby, PHP, and more

### Intelligent Multi-Agent Coordination
Commands automatically determine when to use multiple agents based on:
- Issue count and complexity
- File distribution across the codebase
- Task independence
- Technology diversity

### Professional Expertise
The `gosu:spec` command features Claude Code acting as your virtual:
- **Project Manager** - Scope definition and resource planning
- **Business Analyst** - Requirements gathering and success criteria
- **Technical Lead** - Architecture assessment and feasibility analysis

### User Control
All commands follow the same safe workflow:
1. Complete full analysis first
2. Present comprehensive findings
3. **Stop and ask for confirmation** before making changes
4. Offer options: Yes (full implementation), No (report only), Selective (choose specific fixes)

### Comprehensive Reporting
Each command provides:
- Executive summary with metrics
- Detailed findings with exact file/line references
- Priority-based classification (Critical/High/Medium/Low)
- Technology-specific recommendations
- Actionable improvement plans

## Command Options

When prompted after analysis, you can choose:

1. **Yes** - Create todo list and implement all priority fixes
2. **No** - Stop here, report only (no code changes)
3. **Selective** - Choose which specific issues to fix
4. **High Priority Only** - Fix only critical issues

## Best Practices

### Workflow Integration
```bash
# First time setup
claude gosu:init

# Feature specification creation
claude gosu:spec "real-time notifications system"

# Planning new features
claude gosu:plan "real-time notifications system"

# Before committing changes
claude gosu:review

# Before production deployment
claude gosu:security

# JIRA integration for issue tracking
claude gosu:jira "create task 'Implement notifications' in PROJ"

# Resume interrupted work
claude gosu:work

# Complete development cycle with persistence
claude gosu:init && claude gosu:spec "feature" && claude gosu:plan "feature" && claude gosu:review && claude gosu:security

# Generate team productivity report
claude gosu:summary 14
```

### When to Use Each Command

- **Init (`gosu:init`)**: First time setup, enable persistent task management
- **Spec (`gosu:spec`)**: Professional specification creation with PM/BA/Tech Lead guidance
- **Plan (`gosu:plan`)**: Before implementing new features, architectural changes, complex functionality
- **Review (`gosu:review`)**: Before PRs, after refactoring, regular code quality maintenance
- **Security (`gosu:security`)**: Before deployments, after adding user input features, compliance audits
- **JIRA (`gosu:jira`)**: Issue management, task creation, project tracking, team collaboration
- **Summary (`gosu:summary`)**: Team productivity reports, sprint reviews, manager updates
- **Work (`gosu:work`)**: Resume interrupted tasks, continue work across sessions

## Advanced Features

### Multi-Agent Coordination Example
For complex projects, commands may deploy multiple specialized agents:

```
> DEPLOYING MULTI-AGENT TEAM

Agent Distribution:
- Agent 1: Critical issues in auth/, api/
- Agent 2: Validation fixes in controllers/, middleware/
- Agent 3: Configuration hardening in config/, docker/
- Agent 4: Dependencies and documentation
```

Each agent works independently with specific expertise, then provides a coordinated summary of all improvements.

## Persistent Task Files

After initialization with `gosu:init`, task files are saved in the `.gosu` directory:

```
.gosu/
├── spec-20240712_143022.md      # Feature specification document
├── plan-20240712_143022.md      # Feature implementation plan
├── review-20240712_151045.md    # Code quality review
└── security-20240712_160315.md  # Security audit report
```

**Task File Features:**
- **Checkbox progress tracking** - `[x]` completed, `[ ]` pending
- **Implementation notes** - Progress logs and timestamps
- **Status indicators** - Current phase and completion state
- **Context preservation** - Full analysis and implementation details

**Resume Examples:**
```bash
# List all available tasks
claude gosu:work

# Resume specific task types
claude gosu:work spec-20240712_143022.md     # Continue feature specification
claude gosu:work plan-20240712_143022.md     # Continue feature implementation
claude gosu:work review-20240712_151045.md   # Continue code quality fixes
claude gosu:work security-20240712_160315.md # Continue security remediation
```

**Cross-Session Workflow:**
```bash
# Start feature development
claude gosu:spec "user authentication"  # Create specification
# ... session ends ...

# Resume later
claude gosu:work                         # Resume specification work
claude gosu:plan "user authentication"  # Create implementation plan
# ... session ends ...

# Continue with development
claude gosu:work                         # Resume planning/implementation
claude gosu:review                       # Start code review  
# ... session ends ...

# Continue quality improvements
claude gosu:work                         # Resume review fixes
claude gosu:security                     # Security audit
# ... session ends ...

# Finish security work
claude gosu:work                         # Resume security fixes
```

## JIRA MCP Configuration

The gosu commands include comprehensive JIRA MCP integration for seamless issue management through Claude Code.

### Quick Setup

```bash
# Install JIRA MCP client
npx -p mcp-remote@latest mcp-remote-client https://mcp.atlassian.com/v1/sse

# Add to Claude Code MCP
claude mcp add JIRA npx mcp-remote https://mcp.atlassian.com/v1/sse
```

### Usage Examples

```bash
# Create a new task
claude "/gosu:jira create task 'Implement user authentication' in PROJ"

# Search for open issues
claude "/gosu:jira search issues project = PROJ AND status = Open"

# Add comment to issue
claude "/gosu:jira add comment to PROJ-123 'Testing completed successfully'"
```

For comprehensive documentation, configuration options, and advanced usage, see [JIRA MCP Integration Guide](docs/jira-mcp-integration.md).

## Examples

See real-world examples of command outputs and task files:

- **[Feature Planning Example](./examples/plan-20250713_110206.md)** - Complete feature implementation plan with progress tracking

## Support

For detailed information about each command, see the individual documentation files linked above.

## Acknowledgments

This project was developed and tested with resources from:

- **[MiviaLabs](https://mivialabs.com)** - Enterprise AI development services company that provided Claude Code resources and testing environments for development
- **[Rimthan](https://rimthan.com)** - Contributing partner organization that supported the creation and refinement of these commands

Special thanks to both organizations for enabling the development of these advanced Claude Code commands through their support and resources.

## Author

**Maciej Lisowski**  
[LinkedIn](https://www.linkedin.com/in/maclisowski/)

## License

MIT License - see the [LICENSE](LICENSE) file for details.