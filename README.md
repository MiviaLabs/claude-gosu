# Gosu Commands

> **⚡ Optimized for Claude Code Max** - These commands work best with a Claude Code Max subscription for enhanced performance and capabilities.

Gosu is a collection of advanced Claude Code commands for comprehensive code analysis and improvement. These commands provide expert-level security auditing and code quality review with intelligent multi-agent coordination.

## Available Commands

| Command | Description | Documentation |
|---------|-------------|---------------|
| `gosu:security` | Comprehensive cybersecurity analysis and vulnerability fixes | [Details](./docs/security.md) |
| `gosu:review` | Code quality review with intelligent improvements | [Details](./docs/review.md) |
| `gosu:plan` | Comprehensive feature planning with implementation roadmaps | [Details](./docs/plan.md) |

## Quick Start

All gosu commands follow the same pattern:

```bash
claude gosu:<command>
```

### Basic Usage Examples

```bash
# Security audit of your codebase
claude gosu:security

# Code quality review
claude gosu:review

# Feature planning and implementation
claude gosu:plan "user profile management with avatar upload"
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
# Before committing changes
claude gosu:review

# Before production deployment
claude gosu:security

# Planning new features
claude gosu:plan "real-time notifications system"

# Complete development cycle
claude gosu:plan "feature" && claude gosu:review && claude gosu:security
```

### When to Use Each Command

- **Security (`gosu:security`)**: Before deployments, after adding user input features, compliance audits
- **Review (`gosu:review`)**: Before PRs, after refactoring, regular code quality maintenance
- **Plan (`gosu:plan`)**: Before implementing new features, architectural changes, complex functionality

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