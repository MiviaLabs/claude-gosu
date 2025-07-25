# Gosu Commands

> **⚡ Optimized for Claude Code Max** - These commands work best with a Claude Code Max subscription for enhanced performance and capabilities.

Gosu is a collection of advanced Claude Code commands for comprehensive agentic development. These commands provide expert-level architecture design, code quality review, intelligent testing, and systematic improvements with multi-agent coordination - enabling safe and effective AI-driven development workflows.

## Available Commands

| Command | Description | Documentation |
|---------|-------------|---------------|
| `gosu:init` | Initialize workspace for persistent task management | [Details](./docs/init.md) |
| `gosu:spec` | Professional PM/BA/Tech Lead guided feature specification creation | [Details](./docs/spec.md) |
| `gosu:plan` | Comprehensive feature planning with implementation roadmaps | [Details](./docs/plan.md) |
| `gosu:review` | Code quality review with intelligent improvements | [Details](./docs/review.md) |
| `gosu:security` | Comprehensive cybersecurity analysis and vulnerability fixes | [Details](./docs/security.md) |
| `gosu:test` | Intelligent test generation, coverage analysis, and quality assurance | [Details](./docs/test.md) |
| `gosu:refactor` | Systematic code refactoring with pattern detection and modernization | [Details](./docs/refactor.md) |
| `gosu:docs` | Intelligent documentation generation and maintenance | [Details](./docs/docs.md) |
| `gosu:architect` | System architecture design and technical decision guidance | [Details](./docs/architect.md) |
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

# Intelligent test generation and coverage analysis
claude gosu:test "generate tests for UserService"
# OR coverage analysis
claude gosu:test "coverage analysis"

# Systematic code refactoring
claude gosu:refactor "extract service layer from controllers"
# OR detect refactoring opportunities
claude gosu:refactor

# Documentation generation and maintenance
claude gosu:docs "generate API documentation"
# OR update all documentation
claude gosu:docs

# System architecture design
claude gosu:architect "design microservices architecture"
# OR interactive architecture session
claude gosu:architect

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
claude gosu:work test-20240712_143022.md
claude gosu:work refactor-20240712_143022.md
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
Multiple commands feature Claude Code acting as specialized professionals:

**gosu:spec** - Virtual PM/BA/Tech Lead team:
- **Project Manager** - Scope definition and resource planning
- **Business Analyst** - Requirements gathering and success criteria
- **Technical Lead** - Architecture assessment and feasibility analysis

**gosu:test** - Virtual Test Engineering team:
- **Test Engineer** - Comprehensive test suite creation
- **QA Lead** - Quality assurance and coverage analysis
- **Test Architect** - Testing framework and CI/CD integration

**gosu:refactor** - Virtual Senior Developer team:
- **Code Architect** - Pattern detection and design improvement
- **Refactoring Specialist** - Safe code transformation
- **Performance Expert** - Optimization and modernization

**gosu:architect** - Virtual Architecture team:
- **Solution Architect** - System design and technology selection
- **Technical Architect** - Implementation guidance and best practices
- **Enterprise Architect** - Scalability and integration planning

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

# Test generation and coverage
claude gosu:test "comprehensive test suite"

# Code refactoring opportunities
claude gosu:refactor

# Documentation updates
claude gosu:docs

# Architecture review
claude gosu:architect "validate current architecture"

# JIRA integration for issue tracking
claude gosu:jira "create task 'Implement notifications' in PROJ"

# Resume interrupted work
claude gosu:work

# Complete agentic development cycle
claude gosu:init && claude gosu:architect "system design" && claude gosu:spec "feature" && claude gosu:plan "feature" && claude gosu:test "comprehensive tests" && claude gosu:review && claude gosu:refactor && claude gosu:docs && claude gosu:security

# Generate team productivity report
claude gosu:summary 14
```

### When to Use Each Command

- **Init (`gosu:init`)**: First time setup, enable persistent task management
- **Spec (`gosu:spec`)**: Professional specification creation with PM/BA/Tech Lead guidance
- **Plan (`gosu:plan`)**: Before implementing new features, architectural changes, complex functionality
- **Review (`gosu:review`)**: Before PRs, after refactoring, regular code quality maintenance
- **Security (`gosu:security`)**: Before deployments, after adding user input features, compliance audits
- **Test (`gosu:test`)**: Generate comprehensive tests, analyze coverage, ensure quality
- **Refactor (`gosu:refactor`)**: Systematic code improvements, pattern detection, modernization
- **Docs (`gosu:docs`)**: Generate and maintain documentation, keep content current
- **Architect (`gosu:architect`)**: System design, architecture decisions, technical guidance
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
├── security-20240712_160315.md  # Security audit report
├── test-20240712_160530.md      # Test implementation plan
├── refactor-20240712_161045.md  # Refactoring roadmap
└── architect-20240712_161530.md # Architecture design document
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
claude gosu:work test-20240712_160530.md     # Continue test implementation
claude gosu:work refactor-20240712_161045.md # Continue refactoring work
claude gosu:work architect-20240712_161530.md # Continue architecture design
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

## Agentic Development Workflows

The gosu commands enable sophisticated AI-driven development patterns:

### Complete Feature Development Lifecycle

```bash
# 1. Architecture & Planning Phase
claude gosu:architect "design user authentication system"
claude gosu:spec "multi-factor authentication feature"
claude gosu:plan "implement OAuth2 with MFA"

# 2. Development & Quality Assurance Phase
claude gosu:test "generate authentication test suite"
claude gosu:review "analyze security patterns"
claude gosu:refactor "optimize authentication flow"

# 3. Documentation & Security Phase
claude gosu:docs "generate API documentation"
claude gosu:security "comprehensive security audit"

# 4. Project Management & Deployment
claude gosu:jira "create deployment tasks"
claude gosu:summary "generate release report"
```

### Agentic Code Improvement Pipeline

```bash
# Systematic codebase improvement
claude gosu:architect "evaluate current architecture"    # Assess system design
claude gosu:refactor "detect improvement opportunities"  # Identify refactoring needs
claude gosu:test "ensure comprehensive coverage"         # Safety net creation
claude gosu:review "validate improvements"              # Quality assurance
claude gosu:docs "update technical documentation"       # Knowledge preservation
claude gosu:security "validate security posture"       # Security validation
```

### Cross-Session Development Continuity

```bash
# Session 1: Architecture and Specification
claude gosu:init
claude gosu:architect "microservices e-commerce platform"
claude gosu:spec "payment processing service"
# ... session ends, work automatically saved ...

# Session 2: Implementation Planning
claude gosu:work  # Resume previous work
claude gosu:plan "implement payment service"
claude gosu:test "payment service test strategy"
# ... session ends ...

# Session 3: Quality and Documentation
claude gosu:work  # Continue from where left off
claude gosu:review "payment service code quality"
claude gosu:docs "payment API documentation"
claude gosu:security "payment security audit"
```

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