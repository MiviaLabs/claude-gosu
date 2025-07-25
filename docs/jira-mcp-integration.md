# JIRA MCP Integration

This document provides comprehensive information about the JIRA MCP (Model Context Protocol) integration, enabling seamless issue management and workflow automation through Claude Code.

## Overview

The JIRA MCP integration allows developers and project managers to interact with JIRA issues directly through Claude Code using natural language commands. This integration streamlines project management workflows by providing a conversational interface to JIRA's project management capabilities.

## Table of Contents

- [Setup and Configuration](#setup-and-configuration)
- [Authentication](#authentication)
- [Available Commands](#available-commands)
- [Usage Examples](#usage-examples)
- [Project Context](#project-context)
- [Best Practices](#best-practices)
- [Troubleshooting](#troubleshooting)
- [Advanced Features](#advanced-features)

## Setup and Configuration

### 1. Install JIRA MCP

First, install the JIRA MCP client:

```bash
npx -p mcp-remote@latest mcp-remote-client https://mcp.atlassian.com/v1/sse
```

### 2. Add to Claude Code

Add the JIRA MCP to your Claude Code configuration:

```bash
claude mcp add JIRA npx mcp-remote https://mcp.atlassian.com/v1/sse
```

### 3. Configuration

The integration can be configured to work with your JIRA project with the following example settings:

- **Project Key**: Your project key (e.g., PROJ)
- **Cloud ID**: Your Atlassian cloud instance ID
- **Available Issue Types**: Task, Epic, Subtask (varies by project configuration)

## Authentication

The JIRA MCP integration uses Atlassian's authentication system. Ensure you have proper permissions for your JIRA project before using the commands.

## Available Commands

### Quick Commands Reference

Use these commands with Claude Code's `/gosu:jira` slash command:

#### User & Projects
- `get user info` - Get current Jira user information
- `list projects` - Show all visible Jira projects
- `show project PROJ` - Get details for specific project

#### Issue Management
- `search issues in PROJ` - Find issues in your project
- `get issue PROJ-123` - Get details for specific issue
- `create task "Fix login bug"` - Create new task (unassigned by default)
- `add comment to PROJ-123 "Fixed in latest build"` - Add comment to issue

#### Advanced Search
- `search "project = PROJ AND status = Open"` - Custom JQL search
- `find my assigned issues` - Search issues assigned to current user
- `list recent issues` - Show recently created issues

### MCP Functions

The following MCP functions are available for programmatic access:

#### Core Functions
- `mcp__JIRA__atlassianUserInfo` - Get current user info
- `mcp__JIRA__getVisibleJiraProjects` - List accessible projects
- `mcp__JIRA__getJiraProjectIssueTypesMetadata` - Get project issue types

#### Issue Management
- `mcp__JIRA__searchJiraIssuesUsingJql` - Search with JQL
- `mcp__JIRA__getJiraIssue` - Get issue details by key/ID
- `mcp__JIRA__createJiraIssue` - Create new issue
- `mcp__JIRA__editJiraIssue` - Update existing issue
- `mcp__JIRA__addCommentToJiraIssue` - Add comment to issue

#### Workflow
- `mcp__JIRA__getTransitionsForJiraIssue` - Get available transitions
- `mcp__JIRA__transitionJiraIssue` - Change issue status
- `mcp__JIRA__lookupJiraAccountId` - Find user by email/name

## Usage Examples

### Basic Issue Management

```bash
# Get user information
claude "/gosu:jira get user info"

# List all projects
claude "/gosu:jira list projects"

# Search for open issues
claude "/gosu:jira search issues project = PROJ AND status = Open"

# Create a new task (unassigned by default)
claude "/gosu:jira create task 'Implement user authentication' in PROJ"

# Get specific issue details
claude "/gosu:jira get issue PROJ-123"

# Add a comment to an issue
claude "/gosu:jira add comment to PROJ-123 'Testing completed successfully'"
```

### Advanced Workflow Management

```bash
# Create task with assignment
claude "/gosu:jira create task 'Database optimization' assigned to john.doe@example.com"

# Search for recently updated issues
claude "/gosu:jira search 'project = PROJ AND updated >= -7d'"

# Find all issues assigned to current user
claude "/gosu:jira find my assigned issues"
```

## Project Context

### Available Projects
- **PROJ** (Example Project) - Software project with Task, Epic, Subtask issue types

### Issue Types
- **Task** - Standard work items
- **Epic** - Large features or initiatives
- **Subtask** - Smaller components of tasks

### Status Workflow
- **To Do** (ID: 11) - New items
- **In Progress** (ID: 21) - Active work
- **DRAFT** (ID: 3) - Draft items
- **IN REVIEW** (ID: 2) - Under review
- **Done** (ID: 31) - Completed items

## Best Practices

### Task Assignment
- **Default Behavior**: All tasks are created unassigned unless explicitly specified
- **Assignment During Creation**: Include assignment information in the command
- **Assignment After Creation**: Use edit commands to update assignee field

### Epic and Task Relationships
- **Issue**: Subtasks cannot be directly created under Epics in this project configuration
- **Solution**: Create regular Tasks instead of Subtasks and link them appropriately
- Use the `parent` parameter for true parent-child relationships

### Status Transitions
1. Always check available transitions before attempting to change status
2. Use transition ID (not name) in transition commands
3. Verify permissions before attempting status changes

## Troubleshooting

### Common Issues and Solutions

#### Epic Linking Problems
**Error**: `"parentId": "Given parent work item does not belong to appropriate hierarchy."`

**Solution**:
1. Create the task normally with `mcp__JIRA__createJiraIssue`
2. Link it to the epic using `mcp__JIRA__editJiraIssue` with the parent field
3. Use the Epic's numeric ID (e.g., "10067"), not the key (e.g., "PROJ-2")

#### Custom Fields
**Issue**: Custom fields like epic links may not be available on creation screens

**Solution**:
1. Create the issue first with basic fields
2. Use `mcp__JIRA__editJiraIssue` to add custom field values
3. Check project metadata with `mcp__JIRA__getJiraProjectIssueTypesMetadata`

#### Permission Issues
**Issue**: Unable to create or modify issues

**Solution**:
1. Verify user permissions in your JIRA project
2. Check with project administrators for proper access levels
3. Ensure authentication is properly configured

## Advanced Features

### JQL (JIRA Query Language) Support
The integration supports full JQL queries for complex searches:

```bash
# Complex search example
claude "/gosu:jira search 'project = PROJ AND assignee = currentUser() AND status in (\"To Do\", \"In Progress\") ORDER BY priority DESC'"
```

### Batch Operations
For multiple operations, chain commands or use the programmatic API:

```bash
# Create multiple related tasks
claude "/gosu:jira create task 'Setup database schema' in PROJ"
claude "/gosu:jira create task 'Implement API endpoints' in PROJ"
claude "/gosu:jira create task 'Add unit tests' in PROJ"
```

### Integration with Development Workflow
Combine JIRA commands with development tasks:

```bash
# Create issue, work on code, then update status
claude "/gosu:jira create task 'Fix authentication bug' in PROJ"
# ... development work ...
claude "/gosu:jira add comment to PROJ-XXX 'Fix implemented and tested'"
```

## Security Considerations

- Never share authentication tokens or credentials
- Verify permissions before making changes to issues
- Use appropriate access levels for team members
- Regularly review and audit JIRA permissions

## Related Documentation

- [Project Management Workflows](PROJECT-MANAGEMENT.md)
- [Development Guide](DEVELOPMENT.md)
- [CI/CD Integration](CICD.md)
- [Team Collaboration](COLLABORATION.md)

## Support

For issues with JIRA MCP integration:

1. Check the [Troubleshooting](#troubleshooting) section
2. Review Atlassian MCP documentation
3. Contact the development team
4. Report bugs via GitHub Issues

---

*This integration is part of the comprehensive project management suite, designed to streamline development workflows and enhance team productivity.*