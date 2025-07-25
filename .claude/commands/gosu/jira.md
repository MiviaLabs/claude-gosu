# JIRA MCP Command

Execute JIRA operations using MCP tools with natural language commands.

**Target Command:** $ARGUMENTS

## Quick Commands

### User & Projects

- `get user info` - Get current Jira user information
- `list projects` - Show all visible Jira projects
- `show project PROJ` - Get details for specific project

### Issues

- `search issues in PROJ` - Find issues in your project
- `get issue PROJ-123` - Get details for specific issue
- `create task "Fix login bug"` - Create new task in default project (unassigned by default)
- `add comment to PROJ-123 "Fixed in latest build"` - Add comment to issue

### Advanced Search

- `search "project = PROJ AND status = Open"` - Custom JQL search
- `find my assigned issues` - Search issues assigned to current user
- `list recent issues` - Show recently created issues

## Available MCP Functions

### Core Functions

- `mcp__JIRA__atlassianUserInfo` - Get current user info
- `mcp__JIRA__getVisibleJiraProjects` - List accessible projects
- `mcp__JIRA__getJiraProjectIssueTypesMetadata` - Get project issue types

### Issue Management

- `mcp__JIRA__searchJiraIssuesUsingJql` - Search with JQL
- `mcp__JIRA__getJiraIssue` - Get issue details by key/ID
- `mcp__JIRA__createJiraIssue` - Create new issue (unassigned by default unless explicitly specified)
- `mcp__JIRA__editJiraIssue` - Update existing issue
- `mcp__JIRA__addCommentToJiraIssue` - Add comment to issue

### Workflow

- `mcp__JIRA__getTransitionsForJiraIssue` - Get available transitions
- `mcp__JIRA__transitionJiraIssue` - Change issue status
- `mcp__JIRA__lookupJiraAccountId` - Find user by email/name

## Task Assignment Guidelines

**Default Behavior:** All tasks are created unassigned unless explicitly specified otherwise.

**To assign during creation:** Include assignment information in the command:
- `create task "Fix bug" assigned to john.doe@example.com`
- `create task "Feature work" for current user`

**To assign after creation:** Use edit commands to update assignee field.

## Common Issue Patterns & Solutions

### Epic and Task Relationships

**Issue:** Subtasks cannot be directly created under Epics in this project configuration.

**Solution:** When requested to create subtasks under epics:
1. Create a regular Task instead of Subtask
2. Use the `parent` parameter only for true parent-child relationships (not epic-task)
3. Epic linking may require additional fields that aren't available on the creation screen

**Example Error:**
```
"parentId": "Given parent work item does not belong to appropriate hierarchy."
```

### Linking Tasks to Epics

**Method 1: Link existing task to epic**
Use `mcp__JIRA__editJiraIssue` with the `parent` field:
```json
{"parent": {"id": "EPIC_ID"}}
```

**Method 2: Create task directly under epic**
When creating a task that should belong to an epic:
1. First create the task normally with `mcp__JIRA__createJiraIssue`
2. Then link it to the epic using `mcp__JIRA__editJiraIssue`

**Important Notes:**
- Use the Epic's numeric ID (e.g., "10067"), not the key (e.g., "PROJ-2")
- The parent field requires an object format: `{"id": "numeric_id"}`
- Epic linking works through parent-child hierarchy, not custom fields

**Example:**
```bash
# Create task
claude "/gosu:jira create task 'Database optimization' in PROJ"

# Link PROJ-3 to Epic PROJ-2 (ID: 10067)
{"parent": {"id": "10067"}}
```

### Status Transitions

**Best Practice:** Always check available transitions before attempting to change status:
1. Use `mcp__JIRA__getTransitionsForJiraIssue` to get available transitions
2. Use the transition ID (not name) in `mcp__JIRA__transitionJiraIssue`

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
2. Use `mcp__JIRA__editJiraIssue` to add custom field values if needed
3. Check project metadata with `mcp__JIRA__getJiraProjectIssueTypesMetadata` for available fields

## Examples

```bash
# Get user info
claude "/gosu:jira get user info"

# List projects
claude "/gosu:jira list projects"

# Search for open tasks
claude "/gosu:jira search issues project = PROJ AND status = Open"

# Create new task (unassigned by default)
claude "/gosu:jira create task 'Implement user authentication' in PROJ"

# Get issue details
claude "/gosu:jira get issue PROJ-123"

# Add comment
claude "/gosu:jira add comment to PROJ-123 'Testing completed successfully'"
```
