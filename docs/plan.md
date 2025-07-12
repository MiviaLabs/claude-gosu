# Feature Planning Command (`gosu:plan`)

Comprehensive feature planning and implementation roadmap creation by an expert software architect with intelligent multi-agent coordination for complex feature development.

## Overview

The plan command performs thorough feature analysis and creates detailed implementation roadmaps. It automatically detects your technology stack, analyzes existing codebase patterns, and creates phase-by-phase implementation plans with specific tasks, subtasks, and code examples.

## Usage

```bash
claude gosu:plan "feature description"
```

### Examples

```bash
# User management features
claude gosu:plan "user profile management with avatar upload and privacy settings"

# Real-time functionality
claude gosu:plan "real-time chat system with message history and file sharing"

# Search and filtering
claude gosu:plan "advanced search functionality with filters and autocomplete"

# Complex integrations
claude gosu:plan "payment processing system with multiple providers"
```

## What It Does

### 🔍 **Technology Stack Detection & Analysis**
- **Auto-detects technology stack** (languages, frameworks, databases, tools)
- **Analyzes existing codebase patterns** and architectural decisions
- **Reviews project guidelines** (always checks CLAUDE.md)
- **Identifies current module organization** and naming conventions
- **Understands existing API patterns** and authentication systems

### 🧠 **ULTRATHINK Feature Analysis**
- **Deep requirements analysis** - functional and non-functional requirements
- **Integration point identification** - how feature connects with existing systems
- **Performance and scalability considerations** - load, response times, growth planning
- **Security implications** - authentication, authorization, data protection needs
- **Technical constraint evaluation** - database impact, API design consistency

### 📋 **Comprehensive Implementation Planning**
- **Phase-by-phase breakdown** with logical dependencies
- **Detailed task and subtask definitions** with acceptance criteria
- **Technology-specific implementation examples** using detected stack
- **Priority classification** from P0 (Critical) to P3 (Nice-to-have)
- **Risk assessment** with mitigation strategies

## Technology-Specific Planning

The command automatically adapts its planning approach based on detected technologies:

### JavaScript/TypeScript/Node.js
- **Framework Integration**: Express.js, NestJS, Next.js patterns
- **Database Planning**: Mongoose schemas, Sequelize models, Prisma setup
- **API Design**: REST endpoints, GraphQL resolvers, middleware implementation
- **Testing Strategy**: Jest, Mocha, Cypress integration
- **Package Management**: npm/yarn dependency planning

### Python
- **Framework Integration**: Django models/views, Flask blueprints, FastAPI routers
- **Database Planning**: Django migrations, SQLAlchemy models, Pydantic schemas
- **API Design**: Django REST framework, Flask-RESTful, FastAPI endpoints
- **Testing Strategy**: pytest, Django TestCase, unittest integration
- **Package Management**: pip, Poetry, conda dependency planning

### Java
- **Framework Integration**: Spring Boot controllers/services, Maven/Gradle modules
- **Database Planning**: JPA entities, Hibernate mappings, Spring Data repositories
- **API Design**: RestController annotations, Spring Security integration
- **Testing Strategy**: JUnit, Mockito, Spring Boot Test setup
- **Package Management**: Maven, Gradle dependency management

### Other Languages
The command includes planning patterns for C#/.NET, Go, Ruby, PHP, and more, automatically adapting to your specific stack.

## Process Flow

1. **Technology Stack Detection**
   - Scans codebase for languages, frameworks, and tools
   - Identifies package managers, databases, and testing frameworks
   - Determines appropriate planning patterns

2. **Codebase Pattern Analysis**
   - Reviews existing module organization and naming conventions
   - Analyzes current API patterns and authentication systems
   - Understands database schema and relationship patterns
   - Checks CLAUDE.md for project-specific guidelines

3. **Feature Requirements Analysis**
   - ULTRATHINK approach to understand feature complexity
   - Identifies functional and non-functional requirements
   - Analyzes integration points with existing systems
   - Evaluates performance, security, and scalability needs

4. **Implementation Plan Creation**
   - Creates phase-by-phase breakdown with logical dependencies
   - Defines specific tasks with technology-appropriate examples
   - Prioritizes tasks from P0 (Critical) to P3 (Nice-to-have)
   - Includes risk assessment and mitigation strategies

5. **User Confirmation**
   - Presents comprehensive implementation plan
   - **Stops and asks for permission** before implementation
   - Offers multiple implementation options

6. **Intelligent Implementation** (if approved)
   - Determines optimal agent coordination strategy
   - Deploys specialized agents for complex features
   - Provides coordinated implementation summary

## Multi-Agent Coordination

For complex features with many implementation tasks, the command automatically deploys specialized agents:

### Agent Assignment Strategy
- **Agent 1 (Database & Models)**: Database migrations, entities, data models
- **Agent 2 (API & Services)**: Controllers, services, business logic implementation
- **Agent 3 (Integration & Security)**: Authentication, file handling, third-party integrations
- **Agent 4 (Testing & Documentation)**: Unit tests, integration tests, API documentation

### When Multi-Agent is Used
- **Task Count**: >12 implementation tasks across different areas
- **Component Distribution**: Tasks span >6 different modules or areas
- **Skill Diversity**: Mix of database, API, testing, and integration work
- **Task Independence**: Implementation tasks can be completed independently

## Persistent Task Management

### Plan File Creation & Storage
If you've run `gosu:init` to initialize the workspace, your plans are automatically saved for later resumption:

```bash
# Plan is saved to .gosu directory
.gosu/plan-20240712_143022.md

# Contains complete plan with:
- Executive summary and technical analysis
- Phase-by-phase task breakdown with checkboxes
- Implementation examples and acceptance criteria
- Risk assessment and recommendations
- Real-time progress tracking
```

### Integration with gosu:work
Resume planning and implementation across sessions:

```bash
# Resume saved plan
claude gosu:work plan-20240712_143022.md

# Or select interactively
claude gosu:work
# > 1. plan-20240712_143022.md (Implementation In Progress - 8/12 tasks completed)
```

### Progress Tracking
Plan files automatically track implementation progress:
- **Checkbox states**: `[x]` completed, `[ ]` pending
- **Phase tracking**: Progress within each implementation phase
- **Timestamps**: When tasks were completed
- **Status updates**: Current implementation state

## Command Options

After the feature planning analysis, you'll be prompted with:

```
📋 FEATURE PLANNING COMPLETE

Feature: User Profile Management
Complexity: Medium
Estimated Implementation: 4 phases, 18 tasks
Plan File: .gosu/plan-20240712_143022.md (if workspace initialized)

Planning Summary:
• Phase 1: 5 foundation tasks (database, core models)
• Phase 2: 6 core feature tasks (API, business logic)
• Phase 3: 4 integration tasks (auth, file handling)
• Phase 4: 3 testing and documentation tasks

Would you like me to proceed with implementing this feature plan?

Options:
1. Yes - Follow the saved plan and begin implementing Phase 1 (P0 tasks)
2. No - Stop here, planning only (plan saved for later use with gosu:work)
3. Selective - Let me choose which phases/tasks to implement
4. Modify Plan - Adjust the plan and update the saved file
5. Cancel Plan - Delete the plan file and stop
```

## Output Examples

### Feature Planning Report
```
📋 FEATURE ANALYSIS COMPLETE

Technology Stack: Node.js/TypeScript with NestJS
Feature: User Profile Management with Avatar Upload
Complexity: Medium (18 tasks across 4 phases)

Phase 1 - Foundation (P0 - Critical):
• Database Migration: Create user_profiles table with avatar_url, bio, privacy_settings
• UserProfile Entity: TypeScript interface with validation decorators
• Profile Repository: TypeORM repository with custom queries
• Basic Profile Service: CRUD operations with validation

Phase 2 - Core API (P1 - High):
• Profile Controller: GET, PUT /api/profiles endpoints with auth guards
• Avatar Upload Endpoint: POST /api/profiles/avatar with Multer configuration
• Profile Validation: class-validator DTOs for profile updates
• Privacy Settings: Service methods for managing user privacy levels

Phase 3 - Integration (P1 - High):
• Authentication Integration: JWT guard integration on profile endpoints
• File Storage Service: Local/S3 storage with file validation and resizing
• Profile Picture Processing: Image optimization and thumbnail generation
• Existing User Integration: Connect profiles with current user system

Phase 4 - Testing & Documentation (P2 - Medium):
• Unit Tests: Profile service and controller test suites with mocks
• Integration Tests: API endpoint tests with test database
• Swagger Documentation: OpenAPI specs for new profile endpoints
• Profile Feature Documentation: Usage guide and API examples

Risk Assessment:
• File upload security requires careful validation and storage configuration
• Profile privacy settings may impact existing user queries
• Image processing could affect server performance under load

Technology-Specific Recommendations:
• Use Multer with file type validation for secure uploads
• Implement sharp or imagemagick for image processing
• Add rate limiting to file upload endpoints
• Use TypeORM query builder for complex privacy filtering
```

### Multi-Agent Implementation
```
🚀 DEPLOYING MULTI-AGENT FEATURE IMPLEMENTATION TEAM

Feature: User Profile Management
Agent Distribution:
- Agent 1: 4 Database/Model tasks in migrations/, entities/, repositories/
- Agent 2: 6 API/Service tasks in controllers/, services/, dto/
- Agent 3: 4 Integration tasks in auth/, storage/, middleware/
- Agent 4: 4 Testing/Docs tasks in test/, docs/, swagger/

📋 MULTI-AGENT FEATURE IMPLEMENTATION COMPLETE

Results Summary:
- Agent 1 (Database): Created user_profiles table, UserProfile entity, repository with custom queries
- Agent 2 (API): Implemented profile CRUD endpoints, avatar upload, validation DTOs
- Agent 3 (Integration): Added JWT auth, file storage service, image processing pipeline
- Agent 4 (Testing): Created 15 unit tests, 8 integration tests, updated API documentation

Total Implementation: 18 tasks completed across 4 phases
Feature Status: Fully functional with comprehensive test coverage
Documentation: Updated API docs and feature guides
```

## Priority Classifications

### P0 (Critical Path - Implement First)
- **Core data models** and database migrations
- **Essential API endpoints** for basic functionality
- **Authentication integration** and security setup
- **Basic validation** and error handling

### P1 (High Priority - Core Features)
- **Main feature functionality** and business logic
- **File handling and storage** (if applicable)
- **User interface integration** points
- **Core business rules** implementation

### P2 (Medium Priority - Enhancements)
- **Advanced features** and optimizations
- **Additional validation** and edge case handling
- **Performance optimizations** and caching
- **Enhanced error messages** and logging

### P3 (Low Priority - Nice to Have)
- **Advanced UI features** and polish
- **Additional integrations** and third-party services
- **Comprehensive documentation** and guides
- **Monitoring and analytics** integration

## Best Practices

### When to Use
- **Before implementing new features** - Get comprehensive roadmap
- **For complex functionality** - Break down into manageable tasks
- **During architectural changes** - Plan integration with existing systems
- **For team coordination** - Create shared understanding of implementation

### Integration with Development Workflow
```bash
# Feature planning and implementation cycle
claude gosu:plan "notification system"

# Plan → Review → Security → Implementation
claude gosu:plan "feature" && claude gosu:review && claude gosu:security

# Cross-session workflow with persistence
claude gosu:plan "complex feature"    # Create plan file
# ... session ends ...
claude gosu:work                      # Resume implementation later
# ... continue work ...
claude gosu:work                      # Resume again until complete
```

### Task Completion & File Management
The plan command automatically manages task files throughout the implementation lifecycle:

**Automatic Progress Updates:**
```bash
# As tasks complete, plan file is updated in real-time
- [x] Create user migration - Completed: 2024-07-12 14:32:15
- [x] Implement UserProfile entity - Completed: 2024-07-12 14:45:22
- [ ] Add profile validation service
```

**Automatic Cleanup:**
```bash
# When all tasks reach 100% completion
🎉 Feature implementation completed successfully!
🗑️ Cleaning up completed plan file: .gosu/plan-20240712_143022.md
✅ Plan file deleted - implementation complete
```

**Manual Plan Management:**
- **Modify Plan**: Update plan content and save changes
- **Cancel Plan**: Delete plan file and stop work
- **Backup Plans**: Previous versions saved before modifications

### Planning Best Practices
The command helps ensure:
- **Technology consistency** - Uses existing patterns and frameworks
- **Architecture alignment** - Respects current system design
- **Code quality maintenance** - Follows established conventions
- **Security considerations** - Includes appropriate security measures
- **Testing strategy** - Plans comprehensive test coverage

## Technology-Specific Features

### Database Planning
- **SQL Databases**: Migration strategies, ORM integration, indexing plans
- **NoSQL Databases**: Schema design, collection structure, query optimization
- **Hybrid Approaches**: Multi-database strategies and data synchronization

### API Design Planning
- **REST APIs**: Endpoint design, response formats, error handling
- **GraphQL**: Schema design, resolver implementation, subscription planning
- **Real-time Features**: WebSocket integration, event streaming, notification systems

### Security Planning
- **Authentication**: Integration with existing auth systems
- **Authorization**: Role-based access control, permission systems
- **Data Protection**: Encryption, validation, input sanitization

## Related Commands

- [`gosu:init`](./init.md) - Initialize workspace for persistent task management (recommended first step)
- [`gosu:work`](./work.md) - Resume work on saved plan files across sessions
- [`gosu:review`](./review.md) - Code quality review after feature implementation
- [`gosu:security`](./security.md) - Security analysis to validate planned implementations

### Complete Development Lifecycle
```bash
# Initialize workspace
claude gosu:init

# Plan → Implement → Review → Secure
claude gosu:plan "feature"   # Create implementation plan
claude gosu:work             # Resume implementation across sessions
claude gosu:review           # Review implemented code
claude gosu:security         # Validate security of implementation
```

## Support

The plan command is part of the gosu suite. For general information, see the [main documentation](./README.md).