# gosu:jira - JIRA MCP Integration Command

Execute JIRA operations using MCP tools with natural language commands. This command provides seamless integration with JIRA for issue management, project tracking, and team collaboration through Claude Code.

## Overview

The `gosu:jira` command enables developers and project managers to interact with JIRA issues directly through Claude Code using natural language commands. This integration streamlines project management workflows by providing a conversational interface to JIRA's comprehensive project management capabilities.

## Usage

```bash
# Interactive mode - guided JIRA operations
claude gosu:jira

# Direct mode - execute specific JIRA command
claude gosu:jira "create task 'Fix login bug' in PROJ"
```

## Quick Commands Reference

### User & Projects

- `get user info` - Get current JIRA user information
- `list projects` - Show all visible JIRA projects
- `show project PROJ` - Get details for specific project

### Issue Management

- `search issues in PROJ` - Find issues in your project
- `get issue PROJ-123` - Get details for specific issue
- `create task "Fix login bug"` - Create new task (unassigned by default)
- `add comment to PROJ-123 "Fixed in latest build"` - Add comment to issue

### Advanced Search

- `search "project = PROJ AND status = Open"` - Custom JQL search
- `find my assigned issues` - Search issues assigned to current user
- `list recent issues` - Show recently created issues

## Available MCP Functions

The command leverages the following MCP functions for programmatic access:

### Core Functions

- `mcp__JIRA__atlassianUserInfo` - Get current user info
- `mcp__JIRA__getVisibleJiraProjects` - List accessible projects
- `mcp__JIRA__getJiraProjectIssueTypesMetadata` - Get project issue types

### Issue Management

- `mcp__JIRA__searchJiraIssuesUsingJql` - Search with JQL
- `mcp__JIRA__getJiraIssue` - Get issue details by key/ID
- `mcp__JIRA__createJiraIssue` - Create new issue
- `mcp__JIRA__editJiraIssue` - Update existing issue
- `mcp__JIRA__addCommentToJiraIssue` - Add comment to issue

### Workflow Management

- `mcp__JIRA__getTransitionsForJiraIssue` - Get available transitions
- `mcp__JIRA__transitionJiraIssue` - Change issue status
- `mcp__JIRA__lookupJiraAccountId` - Find user by email/name

## Task Assignment Guidelines

### Default Behavior

All tasks are created **unassigned** unless explicitly specified otherwise.

### Assignment Options

**During Creation:**
```bash
# Assign to specific user
claude gosu:jira "create task 'Fix bug' assigned to john.doe@example.com"

# Assign to current user
claude gosu:jira "create task 'Feature work' for current user"
```

**After Creation:**
Use edit commands to update the assignee field of existing issues.

## Common Patterns & Solutions

### Epic and Task Relationships

**Issue:** Subtasks cannot be directly created under Epics in some project configurations.

**Solution:** 
1. Create a regular Task instead of Subtask
2. Use the `parent` parameter only for true parent-child relationships
3. Epic linking may require additional fields not available on creation screen

### Linking Tasks to Epics

**Method 1: Link existing task to epic**
```bash
# Use mcp__JIRA__editJiraIssue with parent field
{"parent": {"id": "EPIC_ID"}}
```

**Method 2: Create task under epic**
1. Create the task normally with `mcp__JIRA__createJiraIssue`
2. Link it to the epic using `mcp__JIRA__editJiraIssue`

**Important Notes:**
- Use the Epic's numeric ID (e.g., "10067"), not the key (e.g., "PROJ-2")
- The parent field requires object format: `{"id": "numeric_id"}`
- Epic linking works through parent-child hierarchy

### Status Transitions

**Best Practice:**
1. Always check available transitions before attempting status change
2. Use `mcp__JIRA__getTransitionsForJiraIssue` to get available transitions
3. Use transition ID (not name) in `mcp__JIRA__transitionJiraIssue`

**Example Available Statuses:**
- To Do (ID: 11)
- In Progress (ID: 21)
- DRAFT (ID: 3)
- IN REVIEW (ID: 2)
- Done (ID: 31)

### Custom Fields

**Issue:** Custom fields like epic links may not be available on creation screens.

**Solution:**
1. Create the issue first with basic fields
2. Use `mcp__JIRA__editJiraIssue` to add custom field values
3. Check project metadata with `mcp__JIRA__getJiraProjectIssueTypesMetadata`

## Setup and Configuration

### Prerequisites

1. **Install JIRA MCP:**
   ```bash
   npx -p mcp-remote@latest mcp-remote-client https://mcp.atlassian.com/v1/sse
   ```

2. **Add to Claude Code:**
   ```bash
   claude mcp add JIRA npx mcp-remote https://mcp.atlassian.com/v1/sse
   ```

3. **Authentication:**
   Ensure proper JIRA permissions for your project before using commands.

### Project Configuration

The integration can be configured for any JIRA project:

- **Project Key:** Your project identifier (e.g., PROJ)
- **Cloud ID:** Your Atlassian cloud instance ID
- **Issue Types:** Task, Epic, Subtask (varies by project)

## Usage Examples

### Basic Operations

```bash
# Get user information
claude gosu:jira "get user info"

# List all projects
claude gosu:jira "list projects"

# Search for open issues
claude gosu:jira "search issues project = PROJ AND status = Open"

# Create new task
claude gosu:jira "create task 'Implement user authentication' in PROJ"

# Get issue details
claude gosu:jira "get issue PROJ-123"

# Add comment
claude gosu:jira "add comment to PROJ-123 'Testing completed successfully'"
```

### Advanced Workflow

```bash
# Create task with assignment
claude gosu:jira "create task 'Database optimization' assigned to john.doe@example.com"

# Search with custom JQL
claude gosu:jira "search 'project = PROJ AND updated >= -7d'"

# Find assigned issues
claude gosu:jira "find my assigned issues"
```

## Integration with Development Workflow

### Combined with Other Gosu Commands

```bash
# Create specification and JIRA task
claude gosu:spec "user authentication system"
claude gosu:jira "create epic 'User Authentication' in PROJ"

# Plan implementation and create subtasks
claude gosu:plan "user authentication system"
# ... create related tasks in JIRA based on plan ...

# Track progress through JIRA
claude gosu:jira "add comment to PROJ-123 'Implementation started'"
# ... development work ...
claude gosu:jira "transition PROJ-123 to 'In Progress'"
```

### Cross-Team Collaboration

```bash
# Create tasks for different teams
claude gosu:jira "create task 'API endpoint design' assigned to backend-team@company.com"
claude gosu:jira "create task 'UI mockups' assigned to design-team@company.com"
claude gosu:jira "create task 'Integration testing' assigned to qa-team@company.com"
```

## Best Practices

### Task Creation
- **Default unassigned:** Tasks are unassigned unless explicitly specified
- **Clear descriptions:** Use descriptive task titles and detailed descriptions
- **Proper project context:** Always specify the correct project key

### Status Management
- **Check transitions:** Always verify available status transitions
- **Use IDs:** Use transition/status IDs rather than names
- **Update regularly:** Keep issue status current with actual progress

### Team Collaboration
- **Consistent naming:** Use consistent task naming conventions
- **Regular updates:** Add progress comments regularly
- **Proper assignment:** Assign tasks to appropriate team members

## Troubleshooting

### Common Issues

**Epic Linking Problems:**
- Error: "Given parent work item does not belong to appropriate hierarchy"
- Solution: Use numeric Epic ID, not key; create task first, then link

**Permission Issues:**
- Verify user permissions in JIRA project
- Check with project administrators for access levels
- Ensure proper authentication configuration

**Custom Field Problems:**
- Create issue with basic fields first
- Use edit commands to add custom field values
- Check project metadata for available fields

## Advanced Features

### JQL Query Support
Full JIRA Query Language support for complex searches:

```bash
claude gosu:jira "search 'project = PROJ AND assignee = currentUser() AND status in (\"To Do\", \"In Progress\") ORDER BY priority DESC'"
```

### Batch Operations
Chain commands for multiple operations:

```bash
# Create multiple related tasks
claude gosu:jira "create task 'Setup database schema' in PROJ"
claude gosu:jira "create task 'Implement API endpoints' in PROJ"
claude gosu:jira "create task 'Add unit tests' in PROJ"
```

The `gosu:jira` command provides comprehensive JIRA integration for seamless project management within your development workflow.