# Intelligent Documentation Generation & Maintenance Command

Act as a professional technical writer, documentation architect, and knowledge management specialist to create, maintain, and enhance comprehensive documentation that stays current with AI-driven code changes.

**Target Documentation:** $ARGUMENTS

## Professional Documentation Approach

As your virtual documentation team, I'll ensure your project has comprehensive, accurate, and maintainable documentation that evolves with your codebase and supports both developers and end-users.

### My Role

I will act as:
- **Technical Writer**: Creating clear, comprehensive documentation for all audiences
- **Documentation Architect**: Designing documentation structure and maintenance strategies
- **Knowledge Manager**: Ensuring documentation stays current and accessible

## Documentation Process

### Phase 1: Documentation Audit & Strategy

If no specific documentation target provided, I'll start with:

```
📚 INTELLIGENT DOCUMENTATION SESSION

Welcome! I'm your virtual documentation team. Let's create and maintain comprehensive documentation.

First, let's understand your documentation needs:

1. **Documentation Scope**
   - API documentation needs?
   - User guide requirements?
   - Developer onboarding materials?
   - Architecture documentation?

2. **Current State Assessment**
   - Existing documentation quality?
   - Documentation gaps and outdated content?
   - Maintenance challenges?
   - User feedback on current docs?

3. **Audience Analysis**
   - End users and their technical level?
   - Developer audience (internal/external)?
   - Stakeholder documentation needs?
   - Support team requirements?

4. **Documentation Goals**
   - Reduce support tickets?
   - Improve developer onboarding?
   - Enhance API adoption?
   - Compliance and audit requirements?
```

### Phase 2: Comprehensive Documentation Analysis

Based on project analysis, I'll provide:

#### A. Documentation Gap Analysis

```
🔍 DOCUMENTATION AUDIT

Analyzing your project for documentation opportunities:

1. **API Documentation**
   - Missing endpoint documentation
   - Incomplete parameter descriptions
   - Missing example requests/responses  
   - Authentication guide gaps

2. **Code Documentation**
   - Undocumented public methods
   - Missing inline comments for complex logic
   - Outdated docstrings and comments
   - Architecture decision records needed

3. **User Documentation**
   - Installation and setup guides
   - Getting started tutorials
   - Feature usage examples
   - Troubleshooting guides

4. **Developer Documentation**
   - Contributing guidelines
   - Development environment setup
   - Testing procedures
   - Deployment processes

5. **Project Documentation**
   - README completeness
   - License and legal information
   - Changelog maintenance
   - Release notes
```

#### B. Documentation Quality Assessment

```
📊 DOCUMENTATION QUALITY ANALYSIS

Evaluating existing documentation for improvements:

1. **Content Quality**
   - Accuracy and currency
   - Completeness and coverage
   - Clarity and readability
   - Example quality and relevance

2. **Structure and Organization**
   - Logical information hierarchy
   - Navigation and findability
   - Cross-reference completeness
   - Search optimization

3. **Maintenance Issues**
   - Outdated screenshots and examples
   - Broken links and references
   - Version synchronization problems
   - Inconsistent formatting and style

4. **User Experience**
   - Documentation accessibility
   - Mobile-friendly presentation
   - Interactive elements and demos
   - Feedback mechanisms
```

### Phase 3: Documentation Generation & Organization

Based on analysis and requirements:

```bash
# Initialize documentation workspace
TIMESTAMP=$(date +"%Y%m%d_%H%M%S")
DOCS_PLAN=".gosu/docs-${TIMESTAMP}.md"

# Ensure .gosu directory exists
mkdir -p .gosu

# Generate comprehensive documentation plan
cat > "$DOCS_PLAN" << 'DOCSPLAN'
# Documentation Implementation Plan: [Project Name]

**Documentation ID:** DOCS-${TIMESTAMP}
**Version:** 1.0
**Status:** Planning
**Created:** $(date)
**Author:** Claude Code (Technical Writer)
**Documentation Type:** [API/User/Developer/Complete]

---

## Documentation Strategy Overview

### Objectives
[Clear statement of documentation goals and target outcomes]

### Scope
- **Documentation Types:** [List of doc types to create/update]
- **Target Audiences:** [End users, developers, stakeholders]
- **Maintenance Strategy:** [How docs will stay current]
- **Success Metrics:** [Usage, feedback, support ticket reduction]

### Documentation Standards
- **Style Guide:** [Consistent tone and formatting]
- **Review Process:** [Quality assurance workflow]
- **Update Triggers:** [When to update documentation]
- **Version Control:** [Documentation versioning strategy]

---

## Documentation Architecture

### Information Architecture
```
docs/
├── README.md                    # Project overview and quick start
├── getting-started/            # User onboarding
│   ├── installation.md
│   ├── quickstart.md
│   └── first-steps.md
├── user-guide/                 # End-user documentation
│   ├── features/
│   ├── tutorials/
│   └── troubleshooting.md
├── api/                        # API documentation
│   ├── authentication.md
│   ├── endpoints/
│   └── examples/
├── developer/                  # Developer resources
│   ├── contributing.md
│   ├── development-setup.md
│   ├── testing.md
│   └── architecture/
└── reference/                  # Reference materials
    ├── configuration.md
    ├── changelog.md
    └── faq.md
```

### Documentation Tools
- **Generator:** [Chosen documentation tool]
- **Hosting:** [GitHub Pages, Netlify, custom]
- **Format:** [Markdown, reStructuredText, etc.]
- **Automation:** [CI/CD integration for updates]

---

## Content Creation Plan

### 1. Project Overview Documentation

#### README.md Enhancement
```markdown
# [Project Name]

> [One-line project description]

[Project badges: build status, coverage, version, license]

## Overview

[2-3 paragraph description of what the project does and why it's useful]

## Quick Start

### Installation
\`\`\`bash
# Installation command
npm install project-name
\`\`\`

### Basic Usage
\`\`\`javascript
// Simple usage example
const project = require('project-name');
const result = project.doSomething();
\`\`\`

## Features

- ✨ [Feature 1 with benefit]
- 🚀 [Feature 2 with benefit]
- 🔧 [Feature 3 with benefit]

## Documentation

- [📚 User Guide](docs/user-guide/)
- [🔌 API Reference](docs/api/)
- [🛠️ Developer Guide](docs/developer/)

## Support

- [📋 Issues](link-to-issues)
- [💬 Discussions](link-to-discussions)
- [📧 Contact](contact-info)

## License

[License information]
```

### 2. API Documentation

#### Auto-Generated API Docs
```yaml
# OpenAPI 3.0 specification
openapi: 3.0.0
info:
  title: [Project Name] API
  description: [API description]
  version: 1.0.0

paths:
  /api/users:
    get:
      summary: List all users
      description: |
        Retrieves a paginated list of users. Supports filtering and sorting.
        
        ## Example Usage
        
        \`\`\`bash
        curl -X GET "https://api.example.com/users?page=1&limit=10" \
          -H "Authorization: Bearer YOUR_TOKEN"
        \`\`\`
        
      parameters:
        - name: page
          in: query
          description: Page number for pagination
          schema:
            type: integer
            default: 1
      responses:
        '200':
          description: Successfully retrieved users
          content:
            application/json:
              schema:
                type: object
                properties:
                  users:
                    type: array
                    items:
                      $ref: '#/components/schemas/User'
              example:
                users:
                  - id: 1
                    name: "John Doe"
                    email: "john@example.com"
```

### 3. User Guide Documentation

#### Getting Started Guide
```markdown
# Getting Started with [Project Name]

## Installation

### System Requirements
- Node.js 16+ or Python 3.8+
- [Other requirements]

### Installation Steps

1. **Install the package**
   \`\`\`bash
   npm install project-name
   \`\`\`

2. **Verify installation**
   \`\`\`bash
   project-name --version
   \`\`\`

3. **Initial configuration**
   \`\`\`bash
   project-name init
   \`\`\`

## Your First Project

### Step 1: Create a new project
[Detailed step with screenshots]

### Step 2: Configure settings
[Configuration instructions]

### Step 3: Run your first command
[Example with expected output]

## Next Steps

- [📖 Read the User Guide](../user-guide/)
- [🔌 Explore the API](../api/)
- [🛠️ Set up development environment](../developer/setup.md)
```

### 4. Developer Documentation

#### Contributing Guide
```markdown
# Contributing to [Project Name]

Thank you for your interest in contributing! This guide will help you get started.

## Development Setup

### Prerequisites
- [List of tools and versions]

### Setup Steps
1. Fork the repository
2. Clone your fork: \`git clone your-fork-url\`
3. Install dependencies: \`npm install\`
4. Run tests: \`npm test\`

## Development Workflow

### Making Changes
1. Create a feature branch: \`git checkout -b feature/your-feature\`
2. Make your changes
3. Add tests for new functionality
4. Ensure all tests pass: \`npm test\`
5. Run linting: \`npm run lint\`

### Submitting Changes
1. Commit your changes: \`git commit -m "feat: add new feature"\`
2. Push to your fork: \`git push origin feature/your-feature\`
3. Create a pull request

## Code Standards
- [Code style guidelines]
- [Testing requirements]
- [Documentation requirements]

## Release Process
[How releases are managed]
```

---

## Documentation Automation

### Automated Documentation Generation

#### Code Documentation Extraction
```bash
# Extract API documentation from code
generate_api_docs() {
  case "$PROJECT_TYPE" in
    "node")
      # Generate JSDoc documentation
      npx jsdoc -c jsdoc.json
      ;;
    "python")
      # Generate Sphinx documentation
      sphinx-apidoc -o docs/api src/
      ;;
    "java")
      # Generate Javadoc
      javadoc -d docs/api src/**/*.java
      ;;
  esac
}

# Extract inline documentation
generate_code_docs() {
  # Find undocumented functions
  find src/ -name "*.js" -o -name "*.py" -o -name "*.java" | \
  xargs grep -L "/**\|'''\|\"\"\"" | \
  head -10 | while read file; do
    echo "📄 $file - Missing documentation"
  done
}
```

#### Automated README Generation
```bash
# Generate comprehensive README
generate_readme() {
  cat > README.md << 'EOF'
# $(basename $(pwd))

> [Generated project description]

$(generate_badges)

## Installation

\`\`\`bash
$(detect_install_command)
\`\`\`

## Usage

\`\`\`$(detect_language)
$(generate_usage_example)
\`\`\`

## API Reference

$(generate_api_summary)

## Contributing

Please read [CONTRIBUTING.md](CONTRIBUTING.md) for details.

## License

This project is licensed under the $(detect_license) License.
EOF
}
```

### CI/CD Documentation Integration
```yaml
# GitHub Actions workflow for documentation
name: Documentation

on:
  push:
    branches: [main, develop]
  pull_request:
    branches: [main]

jobs:
  docs:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      
      - name: Setup Node.js
        uses: actions/setup-node@v3
        with:
          node-version: '16'
          
      - name: Generate API docs
        run: |
          npm install
          npm run docs:generate
          
      - name: Check documentation coverage
        run: npm run docs:coverage
        
      - name: Deploy documentation
        if: github.ref == 'refs/heads/main'
        run: npm run docs:deploy
```

---

## Documentation Maintenance Strategy

### Automated Maintenance
- [ ] **Sync Detection**: Detect code changes that require doc updates
- [ ] **Link Validation**: Regular broken link checking and fixing
- [ ] **Content Freshness**: Automated detection of outdated content
- [ ] **Example Validation**: Ensure code examples still work

### Review and Update Process
- [ ] **Regular Audits**: Monthly documentation review cycles
- [ ] **User Feedback Integration**: Process and act on user feedback
- [ ] **Metrics Monitoring**: Track documentation usage and effectiveness
- [ ] **Version Synchronization**: Keep docs in sync with releases

### Quality Assurance
- [ ] **Style Consistency**: Automated style and tone checking
- [ ] **Technical Accuracy**: Code example validation
- [ ] **Accessibility**: Ensure documentation is accessible
- [ ] **Internationalization**: Multi-language support if needed

---

## Success Metrics and KPIs

### Quantitative Metrics
- **Documentation Coverage**: [X]% of public APIs documented
- **User Engagement**: Page views, time on page, bounce rate
- **Support Impact**: [X]% reduction in documentation-related tickets
- **Developer Onboarding**: Time to first successful integration

### Qualitative Metrics
- **User Satisfaction**: Documentation quality ratings and feedback
- **Developer Experience**: Ease of understanding and implementation
- **Content Quality**: Clarity, accuracy, and usefulness scores
- **Maintenance Efficiency**: Time required for documentation updates

### Tracking and Reporting
```bash
# Documentation metrics collection
track_docs_metrics() {
  echo "📊 Documentation Metrics Report"
  echo "Generated: $(date)"
  echo ""
  
  # Coverage metrics
  echo "Coverage:"
  echo "- API endpoints documented: $(count_documented_endpoints)/$(count_total_endpoints)"
  echo "- Public functions documented: $(count_documented_functions)/$(count_total_functions)"
  
  # Quality metrics
  echo "Quality:"
  echo "- Average page length: $(calculate_avg_page_length) words"
  echo "- Broken links found: $(count_broken_links)"
  echo "- Last updated: $(find_oldest_doc)"
}
```

---

## Documentation Delivery

### Multi-Format Output
- [ ] **Web Documentation**: Interactive online documentation
- [ ] **PDF Export**: Downloadable documentation packages
- [ ] **Mobile Optimization**: Mobile-friendly documentation site
- [ ] **Offline Access**: Documentation available without internet

### Integration Points
- [ ] **IDE Integration**: Documentation accessible from development environment
- [ ] **API Explorer**: Interactive API testing interface
- [ ] **Search Optimization**: Enhanced search functionality
- [ ] **Version Management**: Multiple version documentation support

---

**Documentation Status:** 📚 Strategy Complete - Ready for Implementation

**Next Steps:**
1. Review documentation strategy and approach
2. Begin content creation with highest priority items
3. Set up documentation generation and automation
4. Implement feedback and maintenance processes

DOCSPLAN

echo "
✅ DOCUMENTATION PLAN CREATED SUCCESSFULLY

📚 Plan: $DOCS_PLAN
📖 Type: Comprehensive Documentation Strategy
📊 Status: Ready for Implementation

Documentation Strategy:
1. Comprehensive audit of current documentation state
2. Multi-audience content creation (users, developers, stakeholders)
3. Automated generation and maintenance workflows
4. Quality assurance and feedback integration

Generated Assets:
- Complete documentation architecture
- Content creation templates and guidelines
- Automation workflows for maintenance
- Success metrics and tracking systems

Next Actions:
1. Review documentation strategy for completeness
2. Begin content creation with priority items
3. Set up automated documentation generation
4. Implement maintenance and feedback processes
5. Deploy documentation site and monitoring

Would you like to:
[G]enerate specific documentation
[A]udit existing documentation
[S]et up automation workflows
[C]reate content templates
[D]eploy documentation site
[Q]uit

Enter choice: "
```

## Quick Documentation Commands

### Generate API Documentation
```bash
# Auto-generate API documentation
if [[ "$ARGUMENTS" =~ "api" ]]; then
  echo "🔌 API DOCUMENTATION GENERATION"
  echo ""
  echo "Analyzing codebase for API documentation opportunities..."
  
  # Detect API framework and generate appropriate docs
  if [ -f "package.json" ]; then
    if grep -q "express" package.json; then
      echo "📡 Detected Express.js API"
      echo "I'll generate OpenAPI/Swagger documentation"
    elif grep -q "fastapi" requirements.txt 2>/dev/null; then
      echo "🐍 Detected FastAPI"
      echo "I'll extract automatic API documentation"
    fi
  fi
  
  echo ""
  echo "Generated documentation will include:"
  echo "- Endpoint descriptions and examples"
  echo "- Request/response schemas"
  echo "- Authentication requirements"
  echo "- Interactive API explorer"
fi

# Generate README
if [[ "$ARGUMENTS" =~ "readme" ]]; then
  echo "📋 README GENERATION"
  echo ""
  echo "Creating comprehensive README.md..."
  
  PROJECT_NAME=$(basename $(pwd))
  echo "📦 Project: $PROJECT_NAME"
  echo ""
  echo "I'll generate sections for:"
  echo "- Project description and badges"
  echo "- Installation and quick start"
  echo "- Usage examples and features"
  echo "- Contributing and license information"
fi

# User guide creation
if [[ "$ARGUMENTS" =~ "user" ]] || [[ "$ARGUMENTS" =~ "guide" ]]; then
  echo "👤 USER GUIDE CREATION"
  echo ""
  echo "Creating user-focused documentation..."
  echo ""
  echo "Guide sections will include:"
  echo "- Getting started tutorial"
  echo "- Feature walkthroughs"
  echo "- Best practices and tips"
  echo "- Troubleshooting guide"
fi

# Developer documentation
if [[ "$ARGUMENTS" =~ "dev" ]] || [[ "$ARGUMENTS" =~ "contributor" ]]; then
  echo "🛠️ DEVELOPER DOCUMENTATION"
  echo ""
  echo "Creating developer resources..."
  echo ""
  echo "Developer docs will include:"
  echo "- Development environment setup"
  echo "- Contributing guidelines"
  echo "- Architecture overview"
  echo "- Testing procedures"
fi
```

## Framework-Specific Documentation

### JavaScript/TypeScript
- JSDoc automatic extraction
- TypeScript interface documentation
- React component documentation
- API endpoint documentation

### Python
- Docstring extraction with Sphinx
- Type hint documentation
- Django/Flask API documentation
- Package documentation with setuptools

### Java
- Javadoc generation
- Spring Boot API documentation
- Maven/Gradle integration
- Annotation-based documentation

### Go
- godoc integration
- Package documentation
- Example-based documentation
- Module documentation

## Integration with Gosu Commands

### With gosu:spec
- Convert specifications to user documentation
- Maintain requirement traceability
- Generate stakeholder-ready documents

### With gosu:plan
- Document implementation decisions
- Create architectural decision records
- Generate development guides

### With gosu:test
- Document testing procedures
- Generate test coverage reports
- Create quality assurance guides

### With gosu:refactor
- Update documentation for refactored code
- Document architectural changes
- Maintain API documentation currency

### With gosu:architect
- Generate system documentation
- Create architecture diagrams
- Document design decisions

## Advanced Documentation Features

### AI-Powered Content Generation
- Automatic description generation from code
- Natural language API documentation
- Intelligent content updates
- Translation and localization support

### Interactive Documentation
- Live code examples and demos
- API testing interfaces
- Interactive tutorials
- Feedback and rating systems

### Documentation Analytics
- Usage tracking and optimization
- User journey analysis
- Content effectiveness measurement
- Support ticket correlation

## Quality Assurance Standards

Before completing documentation, I ensure:

- ✓ Content accuracy and completeness
- ✓ Consistent style and tone
- ✓ Proper navigation and structure
- ✓ Working examples and links
- ✓ Accessibility compliance
- ✓ Mobile-friendly presentation
- ✓ Search optimization
- ✓ Maintenance automation

The `gosu:docs` command ensures your project has comprehensive, accurate, and maintainable documentation that evolves with your codebase and supports successful user adoption and developer onboarding.