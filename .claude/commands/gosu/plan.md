# Comprehensive Feature Planning Command

Perform comprehensive feature planning as an expert software architect and project manager. Analyze the current codebase, understand project patterns, and create detailed implementation plans with multi-phase task breakdown.

## Command Usage

```bash
claude gosu:plan <feature_description>
```

**Example:**
```bash
claude gosu:plan "user profile management with avatar upload and privacy settings"
claude gosu:plan "real-time chat system with message history and file sharing"
claude gosu:plan "advanced search functionality with filters and autocomplete"
```

## Phase 1: Technology Stack Detection & Codebase Analysis

**CRITICAL**: Before planning any feature, automatically detect and analyze the technology stack:

### Technology Stack Detection
Use the Task tool to identify:
- **Programming Languages**: Scan file extensions (.js, .ts, .py, .java, .cs, .go, .rb, .php, .kt, .swift, etc.)
- **Frameworks**: Identify by package files (package.json, requirements.txt, pom.xml, Cargo.toml, composer.json, etc.)
- **Web Frameworks**: Express, NestJS, Django, Flask, Spring Boot, Rails, Laravel, ASP.NET, Gin, etc.
- **Database Technologies**: SQL/NoSQL databases, ORMs, migration tools, connection libraries
- **Build Tools**: Webpack, Maven, Gradle, npm/yarn, pip, cargo, dotnet, etc.
- **Testing Frameworks**: Jest, Mocha, pytest, JUnit, NUnit, RSpec, PHPUnit, etc.
- **Package Managers**: npm, yarn, pip, maven, gradle, composer, cargo, nuget, etc.

### Adaptive Project Understanding
Based on detected technology stack:
1. **Read CLAUDE.md**: Always check project-specific guidelines, conventions, and requirements
2. **Architecture Pattern Analysis**: Understand patterns specific to detected framework/language
3. **Language-Specific Module Structure**: Analyze organization patterns for the detected stack
4. **Database Schema Review**: Use appropriate tools for detected database technology
5. **API Pattern Analysis**: Framework-specific endpoint and response patterns
6. **Authentication & Authorization**: Technology-specific security implementations
7. **Testing Strategy**: Framework-appropriate testing patterns and tools

### Language-Agnostic Codebase Pattern Recognition
Use Task tool to analyze patterns specific to detected technology:

**For Any Technology Stack:**
- **Module/Package Organization**: How features are structured based on language conventions
- **Naming Conventions**: Language-specific file, class, function naming patterns
- **Error Handling Patterns**: Exception handling patterns for the detected language/framework
- **Configuration Management**: Environment variables, config files, secrets handling per stack

**Technology-Specific Analysis:**
- **JavaScript/TypeScript/Node.js**: Module exports, async patterns, npm package structure
- **Python**: Package structure, virtual environments, requirements management, Django/Flask patterns
- **Java**: Package hierarchy, Maven/Gradle structure, Spring framework patterns, annotation usage
- **C#/.NET**: Namespace organization, project structure, dependency injection patterns
- **Go**: Package structure, module organization, goroutine patterns, dependency management
- **Ruby**: Gem structure, Rails conventions, module organization
- **PHP**: Namespace usage, Composer dependencies, framework-specific patterns (Laravel, Symfony)
- **Other Languages**: Adapt analysis to detected language-specific patterns

**Framework-Specific Patterns:**
- **Database Interaction**: ORM/query patterns appropriate to detected stack
- **API Design**: REST/GraphQL patterns specific to framework
- **Authentication**: Framework-specific auth patterns and middleware
- **Testing**: Testing framework conventions and patterns
- **Validation**: Input validation approaches for the technology stack

### Dependency & Integration Analysis
- **External Services**: Third-party integrations and APIs
- **Internal Dependencies**: Module interdependencies and coupling
- **Package Management**: Current dependencies and their purposes
- **Build & Deployment**: CI/CD patterns and deployment strategies

## Phase 2: Feature Requirements Analysis

### Deep Feature Understanding
**ULTRATHINK** the feature request by considering:

#### Functional Requirements
- **Core Functionality**: What exactly needs to be built
- **User Interactions**: How users will interact with the feature
- **Data Requirements**: What data needs to be stored, processed, retrieved
- **Business Logic**: Rules, validations, workflows, and processes
- **Integration Points**: How it connects with existing features
- **Performance Requirements**: Expected load, response times, scalability needs

#### Non-Functional Requirements
- **Security Considerations**: Authentication, authorization, data protection
- **Performance Impact**: Database queries, caching needs, optimization requirements
- **Scalability Factors**: How the feature will handle growth
- **Monitoring & Logging**: What needs to be tracked and logged
- **Error Handling**: Failure scenarios and recovery strategies
- **Testing Requirements**: Unit, integration, and end-to-end testing needs

#### Technical Constraints
- **Existing Architecture Alignment**: How to fit within current patterns
- **Database Schema Impact**: New tables, relationships, migrations
- **API Design Consistency**: Endpoint patterns, response formats
- **Frontend Compatibility**: If applicable, frontend integration requirements
- **Third-party Dependencies**: External services or libraries needed

## Phase 3: Detailed Implementation Planning

### Implementation Strategy
Create a comprehensive plan with:

#### Phase Breakdown
Organize implementation into logical phases:
1. **Foundation Phase**: Core infrastructure and data models
2. **Core Feature Phase**: Main functionality implementation
3. **Integration Phase**: Connect with existing systems
4. **Enhancement Phase**: Advanced features and optimizations
5. **Testing & Documentation Phase**: Comprehensive testing and documentation

#### Task & Subtask Structure
For each phase, create detailed tasks with:
- **Task Description**: Clear explanation of what needs to be done
- **Subtasks**: Granular steps with specific implementation details
- **Dependencies**: What must be completed before this task
- **Estimated Complexity**: High/Medium/Low complexity rating
- **Implementation Examples**: Code examples and patterns to follow
- **Acceptance Criteria**: How to know when the task is complete

### Detailed Task Planning Template

#### Database & Data Models (Adapt to Detected Stack)

**For Relational Databases (SQL):**
- **Migration Creation**: Database schema changes using detected migration tool
  - SQL Server: Entity Framework migrations, T-SQL scripts
  - PostgreSQL: Django migrations, Alembic, Flyway, Rails migrations
  - MySQL: Laravel migrations, Sequelize migrations, JPA/Hibernate
  - Example: `migration: create_user_profiles_table` (adapt to detected ORM)

**For NoSQL Databases:**
- **Schema Design**: Document/collection structure for detected NoSQL database
  - MongoDB: Collections and document schemas, Mongoose models
  - Cassandra: Column family design, CQL scripts
  - DynamoDB: Table design with partition/sort keys
  - Example: `UserProfile collection schema with validation rules`

**Entity/Model Definition** (Language-Specific):
- **JavaScript/TypeScript**: TypeScript interfaces, Mongoose schemas, Sequelize models
- **Python**: Django models, SQLAlchemy models, Pydantic schemas
- **Java**: JPA entities, Hibernate annotations, Spring Data models
- **C#**: Entity Framework models, Data annotations, DTOs
- **Go**: Struct definitions with GORM tags, validation tags
- **Ruby**: ActiveRecord models, validations, associations
- **PHP**: Eloquent models, Doctrine entities, validation rules

#### API Layer Implementation (Framework-Specific)

**Web Framework Patterns:**
- **Express.js/NestJS**: Controllers with decorators, middleware, route handlers
- **Django/Flask**: Views, serializers, URL patterns, middleware
- **Spring Boot**: Controllers, RestControllers, RequestMapping, ResponseEntity
- **ASP.NET Core**: Controllers, ActionResults, model binding, middleware
- **Rails**: Controllers, strong parameters, before_action filters
- **Laravel**: Controllers, resource routes, form requests, middleware
- **Gin/Echo (Go)**: Handler functions, middleware, route groups

**API Design Patterns** (Adapt to Detected Framework):
- Define endpoints following detected framework conventions
- Implement request validation using framework-specific validators
- Add error handling following established patterns
- Use appropriate response formatting for detected stack

#### Integration & Security (Technology-Specific)

**Authentication Integration:**
- **JWT-based**: Integrate with existing JWT implementation per framework
- **Session-based**: Use framework-specific session management
- **OAuth/SSO**: Implement using appropriate libraries for detected stack
- **Custom Auth**: Follow existing authentication patterns in codebase

**Framework-Specific Security:**
- **Node.js**: Passport.js, helmet, bcrypt, jsonwebtoken
- **Python**: Django auth, Flask-Login, PyJWT, passlib
- **Java**: Spring Security, JWT libraries, BCrypt
- **C#**: ASP.NET Identity, JWT Bearer, Data Protection API
- **Go**: JWT-go, bcrypt, custom middleware
- **Ruby**: Devise, Warden, JWT gems
- **PHP**: Laravel Auth, JWT-Auth, password hashing

#### Testing Implementation (Framework-Appropriate)

**Testing Frameworks by Technology:**
- **JavaScript/TypeScript**: Jest, Mocha, Chai, Supertest, Cypress
- **Python**: pytest, unittest, Django TestCase, Flask testing
- **Java**: JUnit, Mockito, Spring Boot Test, TestContainers
- **C#**: xUnit, NUnit, MSTest, Moq, ASP.NET Core TestHost
- **Go**: testing package, Testify, Ginkgo, Gomega
- **Ruby**: RSpec, Minitest, FactoryBot, Capybara
- **PHP**: PHPUnit, Mockery, Laravel Testing, Codeception

**Test Structure** (Language-Specific):
- Unit tests following detected framework conventions
- Integration tests using appropriate testing tools
- Mock implementations using framework-specific mocking libraries
- Test data setup using detected patterns (factories, fixtures, seeds)

## Phase 4: Priority & Dependency Management

### Priority Classification
**P0 (Critical Path - Implement First)**
- Core data models and database migrations
- Essential API endpoints for basic functionality
- Authentication and security integration
- Basic validation and error handling

**P1 (High Priority - Core Features)**
- Main feature functionality
- User interface integration points
- File handling and storage (if applicable)
- Core business logic implementation

**P2 (Medium Priority - Enhancements)**
- Advanced features and optimizations
- Additional validation and edge case handling
- Performance optimizations and caching
- Enhanced error messages and logging

**P3 (Low Priority - Nice to Have)**
- Advanced UI features
- Additional integrations
- Comprehensive documentation
- Monitoring and analytics integration

### Dependency Mapping
Create clear dependency chains:
- **Sequential Dependencies**: Tasks that must be completed in order
- **Parallel Opportunities**: Tasks that can be worked on simultaneously
- **Blocking Dependencies**: External dependencies that could delay progress
- **Risk Mitigation**: Alternative approaches for high-risk dependencies

## Phase 5: Implementation Plan Presentation & User Confirmation

### Comprehensive Plan Report
Present a detailed implementation plan including:

1. **Executive Summary**
   - Feature overview and scope
   - Total estimated complexity and timeline
   - Key technical decisions and rationale
   - Resource requirements and dependencies

2. **Technical Architecture**
   - How the feature fits into existing architecture
   - New components and their relationships
   - Database schema changes and impact
   - API design and integration points

3. **Detailed Implementation Phases**
   - Phase-by-phase breakdown with tasks and subtasks
   - Priority classification and dependencies
   - Implementation examples and code patterns
   - Testing strategy for each phase

4. **Risk Assessment**
   - Potential challenges and blockers
   - Mitigation strategies
   - Alternative implementation approaches
   - Integration complexity analysis

### User Confirmation & Implementation Options

**CRITICAL**: Always stop and ask for user approval before proceeding with implementation.

```
FEATURE PLANNING COMPLETE

Feature: [Feature Name]
Complexity: [High/Medium/Low]
Estimated Implementation: [X phases, Y tasks]

Planning Summary:
" Phase 1: [X] foundation tasks (database, core models)
" Phase 2: [X] core feature tasks (API, business logic)  
" Phase 3: [X] integration tasks (auth, file handling)
" Phase 4: [X] testing and documentation tasks

Would you like me to proceed with implementing this feature plan?

Options:
1. Yes - Create todo list and begin implementing Phase 1 (P0 tasks)
2. No - Stop here, planning only
3. Selective - Let me choose which phases/tasks to implement
4. Modify Plan - Adjust the plan before implementation
```

## Phase 6: Multi-Agent Implementation Strategy (Only if User Confirms)

### Implementation Complexity Analysis
When user approves implementation, determine optimal execution strategy:

#### Multi-Agent Feasibility Assessment
**Evaluate if multiple agents should be used based on:**
- **Task Count**: >12 implementation tasks across different areas
- **Component Distribution**: Tasks span >6 different modules or areas
- **Skill Diversity**: Mix of database, API, testing, and integration work
- **Task Independence**: Implementation tasks can be completed independently
- **Complexity Variation**: Mix of simple configuration and complex business logic

#### Agent Assignment Strategy
**If Multi-Agent is Feasible:**
- **Agent 1 (Database & Models)**: Database migrations, entities, data models
- **Agent 2 (API & Services)**: Controllers, services, business logic implementation
- **Agent 3 (Integration & Security)**: Authentication, file handling, third-party integrations
- **Agent 4 (Testing & Documentation)**: Unit tests, integration tests, API documentation

**If Single Agent is Optimal:**
- Complex interdependent feature requiring coordinated implementation
- Small feature with <8 implementation tasks
- Feature requiring careful orchestration across multiple existing modules
- High risk of conflicts between concurrent implementations

### Implementation Execution

#### Multi-Agent Coordination (If Determined Feasible)
```
DEPLOYING MULTI-AGENT FEATURE IMPLEMENTATION TEAM

Feature: [Feature Name]
Agent Distribution:
- Agent 1: [X] Database/Model tasks in migrations/, entities/
- Agent 2: [X] API/Service tasks in controllers/, services/
- Agent 3: [X] Integration tasks in auth/, middleware/, config/
- Agent 4: [X] Testing/Docs tasks in test/, docs/

Each agent will receive:
- Specific task assignments from the implementation plan
- Complete feature context and requirements
- Current codebase patterns and conventions
- Coordination guidelines to prevent conflicts
```

#### Single Agent Implementation (If Multi-Agent Not Feasible)
Create prioritized todo list and proceed with sequential implementation following the detailed plan.

### Implementation Verification & Summary
Once implementation is complete:

```
FEATURE IMPLEMENTATION COMPLETE

Feature: [Feature Name]
Implementation Summary:
- Phase 1 (Database): [X] migrations, [X] entities created
- Phase 2 (API): [X] endpoints, [X] services implemented
- Phase 3 (Integration): [X] auth integration, [X] file handling
- Phase 4 (Testing): [X] unit tests, [X] integration tests

Total Implementation: [X] tasks completed
Code Quality: Maintains project standards
Test Coverage: [X]% coverage added
Documentation: Updated API docs and README
```

## Advanced Planning Features

### Pattern Recognition & Consistency
- **Code Pattern Analysis**: Identify and follow existing patterns
- **Naming Convention Adherence**: Maintain consistent naming across the codebase
- **Architecture Alignment**: Ensure new feature aligns with existing architecture
- **API Consistency**: Follow established API design patterns and response formats

### Risk Assessment & Mitigation
- **Technical Risk Analysis**: Identify potential implementation challenges
- **Performance Impact Assessment**: Analyze impact on existing system performance
- **Security Consideration**: Identify security implications and mitigation strategies
- **Scalability Planning**: Consider future growth and scaling requirements

### Integration Planning
- **Existing Feature Integration**: How new feature connects with current functionality
- **Database Impact Assessment**: Schema changes and migration strategies
- **API Backward Compatibility**: Ensuring existing API consumers aren't broken
- **Frontend Integration Points**: If applicable, frontend development considerations

## Execution Instructions

```bash
claude gosu:plan "your feature description here"
```

**The AI will:**
1. **Detect Technology Stack**: Automatically identify programming languages, frameworks, databases, and tools
2. **Analyze Current Codebase**: Comprehensive understanding of language-specific patterns and architecture
3. **Read CLAUDE.md**: Follow project-specific guidelines and conventions
4. **ULTRATHINK Feature Requirements**: Deep analysis adapted to detected technology stack
5. **Create Technology-Specific Implementation Plan**: Phase-by-phase breakdown using appropriate tools and patterns
6. **Prioritize & Organize**: Logical ordering with framework-specific dependency mapping
7. **Present Plan & ASK FOR CONFIRMATION**: Stop and wait for user approval before implementation
8. **Implement Feature (Only if Approved)**: Execute plan with technology-appropriate agent coordination

**IMPORTANT**: The process will ALWAYS pause after presenting the comprehensive plan and ask the user whether to proceed with implementation. No code changes will be made without explicit user approval.

## Expected Adaptive Output

- **Technology Stack Detection**: "Detected Node.js/TypeScript with NestJS" or "Python/Django with PostgreSQL"
- **Codebase Analysis Report**: Understanding of language-specific architecture and patterns
- **Feature Requirements Analysis**: Comprehensive functional and technical requirements adapted to detected stack
- **Technology-Specific Implementation Plan**: Phase-by-phase breakdown using appropriate frameworks and tools
- **Priority & Dependency Map**: Logical implementation order respecting detected technology constraints
- **Risk Assessment**: Technology-specific challenges and mitigation strategies
- **Implementation Options**: Choice of how to proceed with framework-appropriate development

**Key Principle**: Always begin with automatic technology stack detection and thorough codebase analysis, then create a comprehensive, prioritized implementation plan that respects existing language-specific patterns while delivering the requested feature efficiently and maintainably using the most appropriate tools for the detected technology stack.