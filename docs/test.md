# gosu:test - Intelligent Test Generation & Quality Assurance

Act as a professional test engineer and quality assurance lead to create comprehensive testing strategies, generate intelligent tests, and ensure code quality through systematic test management.

## Overview

The `gosu:test` command provides comprehensive testing solutions that enable safe agentic development by creating robust test suites, analyzing coverage, and maintaining test quality. This command acts as your virtual test engineering team.

## Usage

```bash
# Interactive mode - comprehensive testing analysis
claude gosu:test

# Generate tests for specific component
claude gosu:test "generate tests for UserService"

# Coverage analysis
claude gosu:test "coverage analysis"

# Fix failing tests
claude gosu:test "fix failing tests"

# Performance testing
claude gosu:test "performance testing"

# Test maintenance
claude gosu:test "cleanup and optimize"
```

## Key Features

### 1. Professional Test Engineering Approach

Claude Code acts as your virtual test team:

- **Test Engineer**: Creating comprehensive test suites with proper patterns and best practices
- **QA Lead**: Ensuring test quality, coverage, and maintenance strategies
- **Test Architect**: Designing testing frameworks and CI/CD integration

### 2. Intelligent Test Generation

- **Auto-Discovery**: Finds untested functions and coverage gaps automatically
- **Smart Generation**: Creates unit, integration, and end-to-end tests
- **Framework Detection**: Supports Jest, Vitest, pytest, JUnit, Go test, and more
- **Pattern Recognition**: Learns from existing test patterns in your codebase

### 3. Comprehensive Testing Strategy

#### Test Types Supported
- **Unit Tests**: Function-level testing with proper mocking
- **Integration Tests**: Component interaction and API testing
- **End-to-End Tests**: Complete user journey validation
- **Performance Tests**: Load testing and benchmark creation
- **Security Tests**: Vulnerability and penetration testing

#### Framework Support
- **JavaScript/TypeScript**: Jest, Vitest, Mocha with React Testing Library
- **Python**: pytest, unittest with fixtures and comprehensive mocks
- **Java**: JUnit with Mockito and Spring Boot testing configurations
- **Go**: Native go test with table-driven test patterns
- **Auto-detection**: Intelligently detects your project's testing framework

### 4. Coverage Analysis & Optimization

- **Real-time Coverage**: Analyze current test coverage with detailed reports
- **Gap Identification**: Identify untested code paths and critical functions
- **Quality Metrics**: Track test reliability, speed, and maintainability
- **Performance Monitoring**: Optimize slow-running tests and flaky test detection

### 5. CI/CD Integration

- **Pipeline Configuration**: Generate CI/CD testing configurations
- **Quality Gates**: Set up coverage thresholds and quality checkpoints
- **Automated Reporting**: Test result dashboards and notifications
- **Deployment Safety**: Ensure tests pass before deployment

## Testing Process

### Phase 1: Test Strategy Analysis
1. **Framework Detection**: Automatically identify testing tools and patterns
2. **Coverage Assessment**: Analyze current test coverage and identify gaps
3. **Quality Evaluation**: Review existing test quality and reliability
4. **Strategy Planning**: Develop comprehensive testing strategy

### Phase 2: Test Generation
1. **Unit Test Creation**: Generate tests for individual functions and methods
2. **Integration Testing**: Create tests for component interactions
3. **Mock Generation**: Automatic creation of mocks and test fixtures
4. **Data Factory Creation**: Generate realistic test data and scenarios

### Phase 3: Quality Assurance
1. **Test Validation**: Ensure generated tests are comprehensive and reliable
2. **Performance Testing**: Create load tests and performance benchmarks
3. **Security Testing**: Generate security-focused test scenarios
4. **Maintenance Planning**: Set up automated test maintenance workflows

## Output Format

The command creates comprehensive test plans in `.gosu/test-YYYYMMDD_HHMMSS.md` format with:

- **Test Strategy Overview**: Objectives, scope, and success criteria
- **Generated Test Suites**: Complete test implementations for all frameworks
- **Coverage Analysis**: Detailed coverage reports and improvement plans
- **Performance Benchmarks**: Load testing scenarios and performance targets
- **CI/CD Integration**: Pipeline configurations and quality gates
- **Maintenance Strategy**: Automated test maintenance and monitoring

## Integration with Other Commands

### With gosu:plan
- Include test implementation tasks in feature development plans
- Generate test estimates and timeline integration
- Create testing milestones and deliverables

### With gosu:review
- Analyze test quality during code reviews
- Suggest test improvements and optimizations
- Validate test coverage for new features

### With gosu:security
- Generate security-focused test scenarios
- Test authentication and authorization flows
- Validate input sanitization and data protection

### With gosu:refactor
- Update tests for refactored code
- Maintain test coverage during code improvements
- Optimize test performance and reliability

### With gosu:architect
- Design testing strategies for system architecture
- Create integration testing approaches
- Validate non-functional requirements through testing

## Advanced Features

### AI-Powered Test Generation
- **Pattern Learning**: Analyze existing test patterns to generate consistent tests
- **Edge Case Detection**: Automatically identify and test edge cases
- **Realistic Data**: Generate test data based on actual data models
- **Scenario Creation**: Create realistic integration test scenarios

### Test Quality Analysis
- **Flaky Test Detection**: Identify and suggest fixes for unreliable tests
- **Redundancy Analysis**: Find and eliminate duplicate test coverage
- **Performance Optimization**: Optimize test execution speed and efficiency
- **Coverage Optimization**: Ensure meaningful coverage of critical code paths

### Continuous Testing Integration
- **Pipeline Automation**: Generate complete CI/CD testing workflows
- **Quality Monitoring**: Track test trends and quality metrics over time
- **Failure Analysis**: Automatic analysis of test failures and suggestions
- **Deployment Gates**: Automated quality gates for safe deployments

## Best Practices

### When to Use gosu:test

- **Before major code changes**: Establish safety nets for refactoring
- **New feature development**: Ensure comprehensive test coverage
- **CI/CD setup**: Create robust testing pipelines
- **Quality improvement**: Systematically improve test coverage and quality
- **Performance validation**: Establish performance benchmarks and monitoring

### Testing Workflow Integration

```bash
# Complete testing workflow
claude gosu:test "analyze current coverage"     # Assessment
claude gosu:test "generate missing tests"       # Implementation
claude gosu:test "performance benchmarks"       # Optimization
claude gosu:test "ci/cd integration"           # Automation
```

### Quality Assurance Standards

Before completing test implementation:

- ✓ Generated tests follow framework best practices
- ✓ Tests cover happy paths, edge cases, and error scenarios
- ✓ Performance tests include realistic load scenarios
- ✓ Tests are maintainable and readable
- ✓ Mock strategies are appropriate and effective
- ✓ Test data is realistic but safe for all environments
- ✓ CI/CD integration is properly configured
- ✓ Coverage targets are achievable and meaningful

## Benefits for Agentic Development

The `gosu:test` command is essential for agentic development because it:

1. **Provides Safety**: Comprehensive tests enable AI agents to make changes confidently
2. **Ensures Quality**: Automated test generation maintains consistent code quality
3. **Enables Automation**: CI/CD integration supports continuous development workflows
4. **Reduces Risk**: Early detection of regressions and issues before production
5. **Documents Behavior**: Tests serve as executable specifications and documentation
6. **Supports Refactoring**: Enables safe code improvements with confidence

The command transforms testing from a manual overhead into an intelligent, automated process that provides the safety net essential for effective agentic development workflows.