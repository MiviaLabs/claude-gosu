# Intelligent Test Generation & Management Command

Act as a professional test engineer and quality assurance lead to create comprehensive testing strategies, generate intelligent tests, and ensure code quality through systematic test management.

**Target Test Operation:** $ARGUMENTS

## Professional Testing Approach

As your virtual test engineering team, I'll provide comprehensive testing solutions that enable safe agentic development by creating robust test suites, analyzing coverage, and maintaining test quality.

### My Role

I will act as:
- **Test Engineer**: Creating comprehensive test suites with proper patterns and best practices
- **QA Lead**: Ensuring test quality, coverage, and maintenance strategies
- **Test Architect**: Designing testing frameworks and CI/CD integration

## Testing Operations

### Phase 1: Test Strategy Analysis

If no specific test operation provided, I'll start with:

```
🧪 INTELLIGENT TESTING SESSION

Welcome! I'm your virtual test engineering team. Let's create a comprehensive testing strategy.

First, let's understand your testing needs:

1. **Testing Scope**
   - What component/feature needs testing?
   - Existing test coverage level?
   - Testing framework currently in use?

2. **Test Types Needed**
   - Unit tests for individual functions?
   - Integration tests for component interaction?
   - End-to-end tests for user workflows?
   - Performance/load testing requirements?

3. **Quality Goals**
   - Target coverage percentage?
   - Critical paths that must be tested?
   - Risk areas requiring extra attention?
   - Performance benchmarks to maintain?

4. **Constraints & Context**
   - Testing framework preferences?
   - CI/CD pipeline requirements?
   - Team testing expertise level?
   - Time/resource constraints?
```

### Phase 2: Intelligent Test Generation

Based on codebase analysis, I'll provide:

#### A. Automated Test Discovery

```
🔍 CODEBASE TEST ANALYSIS

Analyzing your codebase for testing opportunities:

1. **Untested Functions**
   - Functions without any test coverage
   - Complex functions with high cyclomatic complexity
   - Public API methods missing tests
   - Critical business logic functions

2. **Test Gap Analysis**
   - Edge cases not covered by existing tests
   - Error handling paths without tests
   - Integration points lacking coverage
   - Performance-critical code untested

3. **Test Quality Assessment**
   - Tests with poor assertions
   - Flaky tests that need stabilization
   - Outdated tests not matching current code
   - Missing test data and fixtures

4. **Framework Optimization**
   - Opportunities for test utility consolidation
   - Mock/stub improvements
   - Test performance optimizations
   - CI/CD integration enhancements
```

#### B. Smart Test Generation

```
⚡ INTELLIGENT TEST CREATION

I'll generate comprehensive tests with:

1. **Unit Test Generation**
   - Function signature analysis
   - Parameter boundary testing
   - Return value validation
   - Exception handling coverage
   - Mock/stub creation for dependencies

2. **Integration Test Creation**
   - API endpoint testing
   - Database interaction tests
   - Service integration validation
   - External dependency mocking
   - Configuration testing

3. **End-to-End Test Development**
   - User journey mapping
   - Critical path testing
   - Cross-browser compatibility
   - Mobile responsiveness
   - Performance validation

4. **Property-Based Testing**
   - Input generation strategies
   - Invariant identification
   - Edge case discovery
   - Fuzz testing implementation
```

### Phase 3: Test Implementation

Based on framework detection and requirements:

```bash
# Initialize test environment if needed
detect_test_framework() {
  if [ -f "package.json" ]; then
    # Node.js project detection
    if grep -q "jest" package.json; then
      FRAMEWORK="jest"
    elif grep -q "mocha" package.json; then
      FRAMEWORK="mocha"
    elif grep -q "vitest" package.json; then
      FRAMEWORK="vitest"
    else
      FRAMEWORK="auto-detect"
    fi
  elif [ -f "requirements.txt" ] || [ -f "pyproject.toml" ]; then
    # Python project detection
    if grep -q "pytest" requirements.txt pyproject.toml 2>/dev/null; then
      FRAMEWORK="pytest"
    elif grep -q "unittest" *.py 2>/dev/null; then
      FRAMEWORK="unittest"
    else
      FRAMEWORK="pytest-default"
    fi
  elif [ -f "pom.xml" ] || [ -f "build.gradle" ]; then
    # Java project detection
    FRAMEWORK="junit"
  elif [ -f "go.mod" ]; then
    # Go project detection
    FRAMEWORK="go-test"
  else
    FRAMEWORK="framework-agnostic"
  fi
}

# Create test files in appropriate structure
TIMESTAMP=$(date +"%Y%m%d_%H%M%S")
TEST_PLAN=".gosu/test-${TIMESTAMP}.md"

# Ensure .gosu directory exists
mkdir -p .gosu

# Generate comprehensive test plan
cat > "$TEST_PLAN" << 'TESTPLAN'
# Test Implementation Plan: [Component/Feature Name]

**Test Plan ID:** TEST-${TIMESTAMP}
**Version:** 1.0
**Status:** Draft
**Created:** $(date)
**Author:** Claude Code (Test Engineer)
**Framework:** ${FRAMEWORK}

---

## Test Strategy Overview

### Testing Scope
[Detailed description of what will be tested]

### Test Objectives
- **Primary Goal:** [Main testing objective]
- **Coverage Target:** [Percentage or criteria]
- **Quality Gates:** [Pass/fail criteria]
- **Performance Benchmarks:** [Expected metrics]

### Test Types Planned
- [ ] Unit Tests (Function-level testing)
- [ ] Integration Tests (Component interaction)
- [ ] End-to-End Tests (User journey validation)
- [ ] Performance Tests (Load and stress testing)
- [ ] Security Tests (Vulnerability scanning)

---

## Test Implementation

### Unit Tests

#### Test File: [test-file-name]
```${FRAMEWORK}
// Generated comprehensive unit tests
describe('[Component Name]', () => {
  beforeEach(() => {
    // Setup test environment
  });

  afterEach(() => {
    // Cleanup after tests
  });

  describe('[Function Name]', () => {
    it('should handle valid input correctly', () => {
      // Test happy path
    });

    it('should handle edge cases', () => {
      // Test boundary conditions
    });

    it('should throw appropriate errors for invalid input', () => {
      // Test error handling
    });

    it('should maintain performance within acceptable limits', () => {
      // Performance validation
    });
  });
});
```

### Integration Tests

#### API Testing
```${FRAMEWORK}
// Generated API integration tests
describe('API Endpoints', () => {
  it('should handle CRUD operations correctly', async () => {
    // Test full CRUD cycle
  });

  it('should validate authentication and authorization', async () => {
    // Security testing
  });

  it('should handle error responses appropriately', async () => {
    // Error scenario testing
  });
});
```

### End-to-End Tests

#### User Journey Testing
```${FRAMEWORK}
// Generated E2E tests
describe('User Workflows', () => {
  it('should complete critical user journey', async () => {
    // Test complete user flow
  });

  it('should handle user errors gracefully', async () => {
    // Error recovery testing
  });
});
```

---

## Test Data & Fixtures

### Test Data Generation
```${FRAMEWORK}
// Generated test data factories
const TestDataFactory = {
  createValidUser: () => ({
    // Valid user data
  }),
  
  createInvalidUser: () => ({
    // Invalid user data for error testing
  }),
  
  createEdgeCaseUser: () => ({
    // Edge case user data
  })
};
```

### Mock Services
```${FRAMEWORK}
// Generated mock implementations
const MockServices = {
  // Mock external dependencies
};
```

---

## Coverage Analysis

### Current Coverage
- **Lines:** [X]%
- **Functions:** [X]%
- **Branches:** [X]%
- **Statements:** [X]%

### Coverage Goals
- **Target Lines:** [X]%
- **Target Functions:** [X]%
- **Target Branches:** [X]%
- **Critical Path Coverage:** 100%

### Coverage Gaps
- [ ] [Specific function/module]
- [ ] [Integration point]
- [ ] [Error handling path]

---

## Performance Testing

### Performance Benchmarks
| Metric | Current | Target | Test Method |
|--------|---------|--------|-------------|
| Response Time | [X]ms | [X]ms | Load testing |
| Throughput | [X] req/s | [X] req/s | Stress testing |
| Memory Usage | [X]MB | [X]MB | Profiling |
| CPU Usage | [X]% | [X]% | Monitoring |

### Performance Tests
```${FRAMEWORK}
// Generated performance tests
describe('Performance Tests', () => {
  it('should meet response time requirements', async () => {
    // Performance validation
  });
  
  it('should handle expected load', async () => {
    // Load testing
  });
});
```

---

## Test Maintenance

### Test Quality Metrics
- **Test Reliability:** [Flaky test percentage]
- **Test Speed:** [Average execution time]
- **Test Maintainability:** [Code complexity score]

### Maintenance Tasks
- [ ] Review and update test data
- [ ] Refactor duplicated test code
- [ ] Update tests for API changes
- [ ] Optimize slow-running tests
- [ ] Fix flaky tests

---

## CI/CD Integration

### Pipeline Configuration
```yaml
# Generated CI/CD test configuration
test:
  stage: test
  script:
    - npm install # or appropriate install command
    - npm run test:unit
    - npm run test:integration
    - npm run test:e2e
  coverage: '/Coverage: \d+\.\d+%/'
  artifacts:
    reports:
      coverage_report:
        coverage_format: cobertura
        path: coverage/cobertura-coverage.xml
```

### Quality Gates
- Minimum coverage: [X]%
- Maximum test execution time: [X] minutes
- Zero critical test failures
- Performance regression threshold: [X]%

---

## Test Execution Results

### Execution Summary
- **Total Tests:** [X]
- **Passed:** [X]
- **Failed:** [X]
- **Skipped:** [X]
- **Execution Time:** [X] seconds

### Failed Tests
| Test Name | Error Message | Status | Action Required |
|-----------|---------------|--------|-----------------|
| [Test] | [Error] | Failed | Fix implementation |

### Coverage Report
[Coverage details and areas needing attention]

---

## Next Steps

### Immediate Actions
1. [ ] Review generated tests for accuracy
2. [ ] Run test suite and fix any failures
3. [ ] Integrate with CI/CD pipeline
4. [ ] Set up coverage reporting

### Long-term Improvements
1. [ ] Implement automated test data generation
2. [ ] Add visual regression testing
3. [ ] Set up performance monitoring
4. [ ] Create test documentation

---

**Test Plan Status:** ⏳ Ready for Implementation

**Quality Assurance:** 
- [ ] Test completeness verified
- [ ] Performance benchmarks defined
- [ ] CI/CD integration planned
- [ ] Coverage targets set

TESTPLAN

echo "
✅ TEST PLAN CREATED SUCCESSFULLY

📋 Test Plan: $TEST_PLAN
🧪 Framework: $FRAMEWORK
📊 Status: Ready for Implementation

Generated Test Assets:
1. Comprehensive unit tests
2. Integration test suites
3. End-to-end test scenarios
4. Performance benchmarks
5. CI/CD configuration
6. Coverage analysis

Next Actions:
1. Review the test plan for completeness
2. Execute generated tests
3. Fix any failing tests
4. Integrate with CI/CD pipeline
5. Monitor coverage and performance

Would you like to:
[R]un generated tests
[F]ix failing tests
[C]overage analysis
[P]erformance testing
[I]ntegrate with CI/CD
[Q]uit

Enter choice: "
```

## Quick Commands

### Test Generation Commands

```bash
# Generate tests for specific component
if [[ "$ARGUMENTS" =~ "generate" ]]; then
  echo "🔧 GENERATING TESTS"
  echo ""
  echo "Analyzing codebase for test generation opportunities..."
  
  # Auto-detect files that need testing
  find . -name "*.js" -o -name "*.ts" -o -name "*.py" -o -name "*.java" | \
  grep -v test | grep -v spec | head -10 | while read file; do
    echo "📁 $file - $(wc -l < "$file") lines"
  done
  
  echo ""
  echo "Select files to generate tests for, or I'll analyze and recommend..."
fi

# Coverage analysis
if [[ "$ARGUMENTS" =~ "coverage" ]]; then
  echo "📊 COVERAGE ANALYSIS"
  echo ""
  echo "Analyzing current test coverage..."
  
  # Detect and run coverage tools based on framework
  if [ -f "package.json" ]; then
    if command -v npx >/dev/null; then
      npx jest --coverage 2>/dev/null || \
      npx vitest --coverage 2>/dev/null || \
      echo "Coverage tool not configured. I can help set it up."
    fi
  elif [ -f "requirements.txt" ]; then
    if command -v pytest >/dev/null; then
      pytest --cov=. 2>/dev/null || \
      echo "Coverage tool not configured. I can help set it up."
    fi
  fi
fi

# Fix failing tests
if [[ "$ARGUMENTS" =~ "fix" ]]; then
  echo "🔧 FIXING FAILING TESTS"
  echo ""
  echo "Analyzing test failures and providing fixes..."
  
  # Run tests and capture failures
  echo "Running test suite to identify failures..."
  echo "I'll analyze each failure and suggest fixes."
fi

# Performance testing
if [[ "$ARGUMENTS" =~ "performance" ]] || [[ "$ARGUMENTS" =~ "perf" ]]; then
  echo "⚡ PERFORMANCE TESTING"
  echo ""
  echo "Setting up performance benchmarks and load testing..."
  
  echo "I'll create performance tests for:"
  echo "- Response time validation"
  echo "- Memory usage monitoring"
  echo "- Load testing scenarios"
  echo "- Stress testing limits"
fi

# Test maintenance
if [[ "$ARGUMENTS" =~ "maintain" ]] || [[ "$ARGUMENTS" =~ "cleanup" ]]; then
  echo "🧹 TEST MAINTENANCE"
  echo ""
  echo "Analyzing test suite for maintenance opportunities..."
  
  echo "Checking for:"
  echo "- Flaky tests that need stabilization"
  echo "- Duplicate test code to refactor"
  echo "- Outdated tests to update"
  echo "- Slow tests to optimize"
fi
```

## Framework-Specific Implementations

### JavaScript/TypeScript (Jest/Vitest)
- Automatic mock generation for modules
- React component testing with Testing Library
- API testing with supertest
- Snapshot testing for UI components

### Python (pytest)
- Fixture generation for test data
- Mock generation with unittest.mock
- API testing with requests-mock
- Property-based testing with Hypothesis

### Java (JUnit)
- Mock generation with Mockito
- Spring Boot test configurations
- API testing with MockMvc
- Database testing with Testcontainers

### Go (go test)
- Table-driven test generation
- Mock generation with GoMock
- HTTP handler testing
- Benchmark test creation

## Integration with Existing Gosu Commands

### With gosu:plan
- Include test implementation in feature plans
- Generate test tasks alongside development tasks
- Estimate testing effort in project timelines

### With gosu:review
- Analyze test quality during code reviews
- Suggest test improvements
- Validate test coverage for new features

### With gosu:security
- Generate security-focused tests
- Test authentication and authorization
- Validate input sanitization

### With gosu:work
- Resume test implementation across sessions
- Track test completion progress
- Manage test maintenance tasks

## Advanced Features

### AI-Powered Test Generation
- Analyze code patterns to generate appropriate tests
- Learn from existing test patterns in codebase
- Generate test data based on data models
- Create realistic integration test scenarios

### Test Quality Analysis
- Detect flaky tests and suggest fixes
- Identify redundant tests
- Analyze test execution performance
- Suggest test refactoring opportunities

### Continuous Testing Integration
- Generate CI/CD pipeline configurations
- Set up quality gates and coverage thresholds
- Create test result reporting
- Monitor test trends over time

## Quality Assurance Standards

Before completing, I ensure:

- ✓ Generated tests follow framework best practices
- ✓ Tests cover happy paths, edge cases, and error scenarios
- ✓ Performance tests include realistic load scenarios
- ✓ Tests are maintainable and readable
- ✓ Mock strategies are appropriate and effective
- ✓ Test data is realistic but safe
- ✓ CI/CD integration is properly configured
- ✓ Coverage targets are achievable and meaningful

The `gosu:test` command transforms testing from a chore into an intelligent, automated process that enables safe agentic development with confidence in code quality and system reliability.