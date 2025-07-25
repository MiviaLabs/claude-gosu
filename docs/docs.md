# gosu:docs - Intelligent Documentation Generation & Maintenance

Act as a professional technical writer, documentation architect, and knowledge management specialist to create, maintain, and enhance comprehensive documentation that stays current with AI-driven code changes.

## Overview

The `gosu:docs` command ensures your project has comprehensive, accurate, and maintainable documentation that evolves with your codebase and supports both developers and end-users. This command acts as your virtual documentation team.

## Usage

```bash
# Interactive mode - comprehensive documentation analysis
claude gosu:docs

# Generate API documentation
claude gosu:docs "generate API documentation"

# Update README and project documentation
claude gosu:docs "update README"

# Create user guides and tutorials
claude gosu:docs "create user guide"

# Developer documentation
claude gosu:docs "developer documentation"

# Audit existing documentation
claude gosu:docs "audit documentation"
```

## Key Features

### 1. Professional Documentation Team Approach

Claude Code acts as your virtual documentation team:

- **Technical Writer**: Creating clear, comprehensive documentation for all audiences
- **Documentation Architect**: Designing documentation structure and maintenance strategies
- **Knowledge Manager**: Ensuring documentation stays current and accessible

### 2. Comprehensive Documentation Coverage

#### Multi-Audience Content
- **End Users**: Installation guides, tutorials, feature documentation
- **Developers**: API documentation, contributing guides, architecture overviews
- **Stakeholders**: Project overviews, roadmaps, business documentation
- **Support Teams**: Troubleshooting guides, FAQ sections, common issues

#### Documentation Types
- **API Documentation**: Auto-generated from code with examples and interactive elements
- **User Guides**: Step-by-step tutorials and feature walkthroughs
- **Developer Documentation**: Setup guides, contributing guidelines, architecture docs
- **Project Documentation**: README files, changelogs, release notes

### 3. Intelligent Documentation Generation

#### Automated Content Creation
- **Code Analysis**: Extract documentation from code comments and structure
- **API Discovery**: Automatically document endpoints, parameters, and responses
- **Example Generation**: Create realistic usage examples and code samples
- **Schema Documentation**: Generate documentation from data models and schemas

#### Content Optimization
- **Clarity Analysis**: Ensure documentation is clear and understandable
- **Completeness Checking**: Identify missing documentation sections
- **Consistency Validation**: Maintain consistent style and formatting
- **Accuracy Verification**: Ensure documentation matches current code

### 4. Documentation Maintenance Automation

#### Automated Updates
- **Sync Detection**: Identify when code changes require documentation updates
- **Link Validation**: Regular checking and fixing of broken links
- **Content Freshness**: Automated detection and flagging of outdated content
- **Example Validation**: Ensure code examples continue to work

#### Quality Assurance
- **Style Consistency**: Automated style and tone checking
- **Technical Accuracy**: Validation of technical content and examples
- **Accessibility Compliance**: Ensure documentation meets accessibility standards
- **Multi-language Support**: Internationalization and localization capabilities

## Documentation Process

### Phase 1: Documentation Audit
1. **Current State Analysis**: Assess existing documentation quality and coverage
2. **Gap Identification**: Find missing or outdated documentation sections
3. **Audience Analysis**: Understand documentation needs for different user types
4. **Priority Assessment**: Rank documentation tasks by impact and urgency

### Phase 2: Content Strategy
1. **Information Architecture**: Design logical documentation structure
2. **Content Planning**: Plan comprehensive content creation and updates
3. **Style Guide**: Establish consistent tone, style, and formatting standards
4. **Maintenance Strategy**: Set up automated maintenance and update processes

### Phase 3: Content Creation
1. **Automated Generation**: Generate documentation from code and specifications
2. **Manual Enhancement**: Add context, examples, and user-focused content
3. **Review and Editing**: Ensure quality, accuracy, and clarity
4. **Integration**: Integrate with existing documentation systems and workflows

### Phase 4: Deployment & Maintenance
1. **Publishing**: Deploy documentation to appropriate platforms
2. **Monitoring**: Track usage, feedback, and effectiveness
3. **Continuous Updates**: Maintain currency with code changes
4. **User Feedback**: Collect and incorporate user feedback for improvements

## Framework-Specific Documentation

### JavaScript/TypeScript
- **JSDoc Integration**: Extract and enhance JSDoc comments
- **TypeScript Interfaces**: Document type definitions and interfaces
- **React Components**: Component documentation with prop types and examples
- **Node.js APIs**: Express.js route documentation and middleware guides

### Python
- **Docstring Enhancement**: Improve and standardize Python docstrings
- **Sphinx Integration**: Generate comprehensive Sphinx documentation
- **FastAPI Documentation**: Automatic OpenAPI documentation generation
- **Package Documentation**: PyPI-ready package documentation

### Java
- **Javadoc Enhancement**: Improve Javadoc comments and generation
- **Spring Boot Documentation**: Auto-document REST APIs and configurations
- **Maven Integration**: Generate documentation as part of build process
- **Architecture Documentation**: Document Spring application architecture

### Go
- **Godoc Integration**: Enhance Go package documentation
- **API Documentation**: Document HTTP handlers and middleware
- **Module Documentation**: Go module and package documentation
- **Example Programs**: Generate comprehensive usage examples

## Output Format

The command creates comprehensive documentation plans in `.gosu/docs-YYYYMMDD_HHMMSS.md` format with:

- **Documentation Strategy**: Objectives, scope, and target audiences
- **Content Architecture**: Logical organization and navigation structure
- **Generation Plan**: Automated and manual content creation strategies
- **Quality Standards**: Style guides and consistency requirements
- **Maintenance Workflow**: Automated update and validation processes
- **Success Metrics**: Usage tracking and effectiveness measurement

## Integration with Other Commands

### With gosu:spec
- **Requirements Documentation**: Convert specifications into user documentation
- **Traceability**: Maintain links between requirements and documentation
- **Stakeholder Communication**: Generate stakeholder-ready documentation

### With gosu:plan
- **Implementation Documentation**: Document development decisions and progress
- **Architectural Decisions**: Create and maintain Architecture Decision Records (ADRs)
- **Project Documentation**: Generate project status and timeline documentation

### With gosu:test
- **Testing Documentation**: Document testing procedures and requirements
- **Coverage Reports**: Generate and maintain test coverage documentation
- **Quality Documentation**: Document quality assurance processes and standards

### With gosu:refactor
- **Change Documentation**: Document refactoring decisions and impacts
- **API Changes**: Update documentation for modified interfaces
- **Migration Guides**: Create guides for breaking changes and updates

### With gosu:architect
- **System Documentation**: Generate comprehensive system architecture documentation
- **Design Documentation**: Document technical decisions and trade-offs
- **Integration Guides**: Create documentation for system integrations

## Advanced Features

### AI-Powered Content Enhancement
- **Natural Language Generation**: Generate human-readable descriptions from code
- **Content Optimization**: Improve clarity and readability of existing content
- **Translation Support**: Multi-language documentation generation
- **Context-Aware Examples**: Generate relevant, realistic usage examples

### Interactive Documentation
- **Live Examples**: Executable code examples within documentation
- **API Explorers**: Interactive API testing interfaces
- **Progressive Disclosure**: Layered information presentation
- **Search Optimization**: Enhanced search functionality and discovery

### Analytics and Optimization
- **Usage Tracking**: Monitor which documentation sections are most accessed
- **User Journey Analysis**: Understand how users navigate documentation
- **Feedback Integration**: Collect and analyze user feedback systematically
- **Content Performance**: Measure documentation effectiveness and impact

## Best Practices

### When to Use gosu:docs

- **New project setup**: Create comprehensive initial documentation
- **API changes**: Update documentation for interface modifications
- **Feature releases**: Document new features and capabilities
- **Onboarding improvement**: Enhance developer and user onboarding experiences
- **Compliance requirements**: Meet documentation standards and regulations

### Documentation Workflow Integration

```bash
# Complete documentation workflow
claude gosu:docs "audit current state"         # Assessment
claude gosu:docs "generate missing docs"       # Content creation
claude gosu:docs "setup automation"            # Maintenance automation
claude gosu:docs "deploy and monitor"          # Publishing and tracking
```

### Quality Assurance Standards

Before completing documentation:

- ✓ Content accuracy verified against current codebase
- ✓ Consistent style and tone maintained throughout
- ✓ Proper navigation and structure implemented
- ✓ All examples tested and working correctly
- ✓ Links validated and functional
- ✓ Accessibility standards met
- ✓ Mobile-friendly presentation ensured
- ✓ Search optimization implemented

## Benefits for Agentic Development

The `gosu:docs` command is essential for agentic development because it:

1. **Maintains Knowledge**: Preserves understanding as AI agents modify code
2. **Enables Collaboration**: Provides clear communication between AI agents and human developers
3. **Supports Onboarding**: Helps new team members understand AI-generated or modified code
4. **Reduces Support Load**: Comprehensive documentation reduces questions and support requests
5. **Ensures Compliance**: Maintains documentation standards required for enterprise environments
6. **Facilitates Adoption**: Well-documented features see higher adoption and successful usage

## Documentation Formats and Platforms

### Supported Formats
- **Markdown**: Standard markdown with enhanced features
- **HTML**: Static site generation with modern styling
- **PDF**: Professional document export for distribution
- **Interactive**: Web-based interactive documentation

### Platform Integration
- **GitHub Pages**: Automated deployment and hosting
- **GitLab Pages**: CI/CD integration for documentation updates
- **Netlify/Vercel**: Modern hosting with preview deployments
- **Custom Platforms**: Integration with existing documentation systems

The command transforms documentation from a maintenance burden into an automated, intelligent system that enhances development productivity and user success while staying current with rapid development cycles.