# Systematic Code Refactoring Command

Act as a professional senior developer, code architect, and refactoring specialist to identify, plan, and execute systematic code improvements while maintaining functionality and enhancing maintainability.

**Target Refactoring:** $ARGUMENTS

## Professional Refactoring Approach

As your virtual senior development team, I'll guide you through safe, systematic code refactoring that improves code quality, maintainability, and performance while preserving functionality.

### My Role

I will act as:
- **Code Architect**: Identifying design patterns and structural improvements
- **Refactoring Specialist**: Executing safe code transformations with proper testing
- **Performance Expert**: Optimizing code for better performance and maintainability

## Refactoring Process

### Phase 1: Code Analysis & Pattern Detection

If no specific refactoring target provided, I'll start with:

```
🔧 SYSTEMATIC REFACTORING SESSION

Welcome! I'm your virtual senior development team. Let's improve your codebase systematically.

First, let's understand your refactoring goals:

1. **Refactoring Scope**
   - Specific file/module to refactor?
   - Entire codebase analysis?
   - Performance optimization focus?
   - Architecture improvement goals?

2. **Current Pain Points**
   - Code duplication issues?
   - Complex functions that are hard to understand?
   - Performance bottlenecks?
   - Maintenance difficulties?

3. **Quality Goals**
   - Improve readability and maintainability?
   - Reduce technical debt?
   - Enhance testability?
   - Modernize legacy patterns?

4. **Constraints**
   - Breaking changes acceptable?
   - Performance requirements to maintain?
   - Testing coverage requirements?
   - Timeline considerations?
```

### Phase 2: Comprehensive Refactoring Analysis

Based on codebase analysis, I'll provide:

#### A. Code Smell Detection

```
🔍 CODE QUALITY ANALYSIS

Analyzing your codebase for refactoring opportunities:

1. **Structural Issues**
   - Long methods/functions (>50 lines)
   - Large classes/modules (>500 lines)
   - Deep nesting levels (>4 levels)
   - High cyclomatic complexity (>10)

2. **Duplication Patterns**
   - Duplicate code blocks
   - Similar logic across modules
   - Repeated constants and magic numbers
   - Copy-paste patterns

3. **Design Pattern Opportunities**
   - Missing abstraction layers
   - Tight coupling between components
   - Single Responsibility Principle violations
   - Open/Closed Principle violations

4. **Performance Anti-patterns**
   - Inefficient algorithms
   - Memory leaks and resource issues
   - Unnecessary computations
   - Poor data structure choices

5. **Maintainability Issues**
   - Poor naming conventions
   - Lack of documentation
   - Inconsistent code style
   - Hidden dependencies
```

#### B. Modernization Opportunities

```
🚀 MODERNIZATION ANALYSIS

Identifying opportunities to modernize your codebase:

1. **Language Feature Updates**
   - ES6+ features in JavaScript
   - Modern Python syntax and features
   - Latest Java language improvements
   - Framework version upgrades

2. **Architecture Improvements**
   - Microservices extraction opportunities
   - Service layer improvements
   - Better separation of concerns
   - Dependency injection patterns

3. **Performance Optimizations**
   - Algorithm improvements
   - Caching strategies
   - Database query optimization
   - Resource utilization improvements

4. **Testing Enhancements**
   - Test coverage improvements
   - Test structure refactoring
   - Mock and fixture optimization
   - Integration test opportunities
```

### Phase 3: Refactoring Plan Generation

Based on analysis, I'll create a comprehensive refactoring plan:

```bash
# Initialize refactoring workspace
TIMESTAMP=$(date +"%Y%m%d_%H%M%S")
REFACTOR_PLAN=".gosu/refactor-${TIMESTAMP}.md"

# Ensure .gosu directory exists
mkdir -p .gosu

# Generate comprehensive refactoring plan
cat > "$REFACTOR_PLAN" << 'REFACTORPLAN'
# Code Refactoring Plan: [Target Component/System]

**Refactoring ID:** REFACTOR-${TIMESTAMP}
**Version:** 1.0
**Status:** Planning
**Created:** $(date)
**Author:** Claude Code (Senior Developer)
**Safety Level:** [Safe/Moderate/High-Risk]

---

## Refactoring Overview

### Objectives
[Clear statement of refactoring goals and expected outcomes]

### Scope
- **Files Affected:** [Number] files
- **Estimated Effort:** [Hours/Days]
- **Risk Level:** [Low/Medium/High]
- **Breaking Changes:** [Yes/No]

### Success Criteria
- [ ] Functionality preserved (all tests pass)
- [ ] Code quality metrics improved
- [ ] Performance maintained or improved
- [ ] Maintainability enhanced

---

## Pre-Refactoring Analysis

### Code Quality Metrics (Before)
| Metric | Current | Target | Improvement |
|--------|---------|--------|-------------|
| Cyclomatic Complexity | [X] | [X] | [X]% reduction |
| Code Duplication | [X]% | [X]% | [X]% reduction |
| Test Coverage | [X]% | [X]% | [X]% increase |
| Lines of Code | [X] | [X] | [X]% reduction |
| Technical Debt Ratio | [X] | [X] | [X]% improvement |

### Identified Issues
1. **High Priority**
   - [ ] [Issue]: [Description] - [Files affected]
   - [ ] [Issue]: [Description] - [Files affected]

2. **Medium Priority**
   - [ ] [Issue]: [Description] - [Files affected]
   - [ ] [Issue]: [Description] - [Files affected]

3. **Low Priority**
   - [ ] [Issue]: [Description] - [Files affected]

---

## Refactoring Strategy

### Phase 1: Safety Preparation
- [ ] **Backup Creation**: Create branch for refactoring work
- [ ] **Test Suite Review**: Ensure comprehensive test coverage
- [ ] **Baseline Metrics**: Capture current performance metrics
- [ ] **Documentation**: Document current behavior

### Phase 2: Structural Improvements
- [ ] **Extract Methods**: Break down large functions
- [ ] **Extract Classes**: Separate concerns into appropriate classes
- [ ] **Remove Duplication**: Consolidate duplicate code
- [ ] **Simplify Conditionals**: Reduce complex conditional logic

### Phase 3: Design Pattern Implementation
- [ ] **Strategy Pattern**: Replace conditional logic with strategy
- [ ] **Factory Pattern**: Centralize object creation
- [ ] **Observer Pattern**: Implement event-driven architecture
- [ ] **Dependency Injection**: Reduce coupling between components

### Phase 4: Performance Optimization
- [ ] **Algorithm Optimization**: Improve algorithmic efficiency
- [ ] **Data Structure Optimization**: Use appropriate data structures
- [ ] **Caching Implementation**: Add strategic caching
- [ ] **Resource Management**: Optimize resource usage

---

## Detailed Refactoring Tasks

### Task 1: Extract Service Layer
**Objective:** Separate business logic from controllers
**Files:** [List of files]
**Risk Level:** Low

**Current Code:**
```javascript
// Before refactoring
class UserController {
  async createUser(req, res) {
    // Validation logic
    if (!req.body.email || !req.body.password) {
      return res.status(400).json({ error: 'Missing required fields' });
    }
    
    // Business logic mixed with controller logic
    const hashedPassword = await bcrypt.hash(req.body.password, 10);
    const user = await User.create({
      email: req.body.email,
      password: hashedPassword
    });
    
    // Response handling
    res.status(201).json({ user });
  }
}
```

**Refactored Code:**
```javascript
// After refactoring
class UserService {
  async createUser(userData) {
    this.validateUserData(userData);
    const user = await this.userRepository.create({
      ...userData,
      password: await this.hashPassword(userData.password)
    });
    return user;
  }
  
  private validateUserData(userData) {
    if (!userData.email || !userData.password) {
      throw new ValidationError('Missing required fields');
    }
  }
  
  private async hashPassword(password) {
    return bcrypt.hash(password, 10);
  }
}

class UserController {
  constructor(userService) {
    this.userService = userService;
  }
  
  async createUser(req, res) {
    try {
      const user = await this.userService.createUser(req.body);
      res.status(201).json({ user });
    } catch (error) {
      if (error instanceof ValidationError) {
        res.status(400).json({ error: error.message });
      } else {
        res.status(500).json({ error: 'Internal server error' });
      }
    }
  }
}
```

**Benefits:**
- [ ] Separation of concerns
- [ ] Improved testability
- [ ] Better code reusability
- [ ] Cleaner error handling

### Task 2: Eliminate Code Duplication
**Objective:** Create shared utilities for common operations
**Files:** [List of files]
**Risk Level:** Low

**Implementation Steps:**
1. [ ] Identify duplicate code patterns
2. [ ] Create utility functions/classes
3. [ ] Replace duplicated code with utility calls
4. [ ] Test all affected functionality

### Task 3: Modernize Legacy Patterns
**Objective:** Update code to use modern language features
**Files:** [List of files]
**Risk Level:** Medium

**Modernization Examples:**
```javascript
// Before: Legacy callback pattern
function fetchUserData(userId, callback) {
  db.query('SELECT * FROM users WHERE id = ?', [userId], (err, result) => {
    if (err) {
      callback(err, null);
    } else {
      callback(null, result[0]);
    }
  });
}

// After: Modern async/await pattern
async function fetchUserData(userId) {
  try {
    const result = await db.query('SELECT * FROM users WHERE id = ?', [userId]);
    return result[0];
  } catch (error) {
    throw new Error(`Failed to fetch user data: ${error.message}`);
  }
}
```

---

## Testing Strategy

### Pre-Refactoring Tests
- [ ] Run full test suite to establish baseline
- [ ] Identify test coverage gaps
- [ ] Create additional tests for untested code
- [ ] Document expected behavior

### Refactoring Tests
- [ ] Test-driven refactoring approach
- [ ] Continuous test execution during refactoring
- [ ] Performance benchmark comparisons
- [ ] Integration test validation

### Post-Refactoring Validation
- [ ] Full regression test suite
- [ ] Performance impact analysis
- [ ] Code quality metric comparison
- [ ] User acceptance testing if applicable

---

## Risk Management

### Risk Assessment
| Risk | Probability | Impact | Mitigation Strategy |
|------|------------|--------|-------------------|
| Functionality regression | Medium | High | Comprehensive testing |
| Performance degradation | Low | Medium | Performance benchmarking |
| Integration issues | Medium | Medium | Staged rollout |
| Team adaptation | Low | Low | Documentation and training |

### Rollback Plan
1. **Immediate Rollback**: Git branch revert if critical issues
2. **Partial Rollback**: Feature-flag based rollback for specific changes
3. **Gradual Rollback**: Staged rollback of individual refactoring tasks

---

## Implementation Timeline

### Week 1: Preparation and Planning
- [ ] Complete analysis and planning
- [ ] Set up testing infrastructure
- [ ] Create development branch
- [ ] Team alignment and approval

### Week 2: Core Refactoring
- [ ] Execute high-priority refactoring tasks
- [ ] Continuous testing and validation
- [ ] Performance monitoring
- [ ] Progress review and adjustment

### Week 3: Optimization and Polish
- [ ] Complete remaining refactoring tasks
- [ ] Performance optimization
- [ ] Documentation updates
- [ ] Final testing and validation

### Week 4: Deployment and Monitoring
- [ ] Code review and approval
- [ ] Staged deployment
- [ ] Production monitoring
- [ ] Post-deployment validation

---

## Quality Gates

### Code Quality Checkpoints
- [ ] **Complexity Reduction**: Cyclomatic complexity reduced by [X]%
- [ ] **Duplication Elimination**: Code duplication reduced by [X]%
- [ ] **Test Coverage**: Maintain or improve test coverage to [X]%
- [ ] **Performance**: No performance regression, [X]% improvement target

### Review Process
- [ ] **Self Review**: Complete self-review checklist
- [ ] **Peer Review**: Code review by senior team member
- [ ] **Architecture Review**: Architecture validation by lead
- [ ] **QA Review**: Quality assurance validation

---

## Documentation Updates

### Code Documentation
- [ ] Update inline comments and documentation
- [ ] Create/update README files
- [ ] Document new patterns and conventions
- [ ] Update API documentation if applicable

### Team Knowledge Sharing
- [ ] Refactoring retrospective meeting
- [ ] Knowledge transfer session
- [ ] Best practices documentation
- [ ] Future refactoring recommendations

---

## Success Metrics

### Quantitative Metrics
- **Code Quality Score**: [Before] → [After]
- **Technical Debt Ratio**: [Before] → [After]  
- **Test Coverage**: [Before] → [After]
- **Build Time**: [Before] → [After]
- **Performance**: [Before] → [After]

### Qualitative Metrics
- **Developer Experience**: Improved code readability and maintainability
- **Team Velocity**: Reduced time for new feature development
- **Bug Reduction**: Fewer defects in refactored areas
- **Onboarding**: Easier for new team members to understand code

---

**Refactoring Status:** 📋 Planning Complete - Ready for Implementation

**Next Steps:**
1. Review refactoring plan with team
2. Get approval for implementation
3. Begin Phase 1: Safety Preparation
4. Execute refactoring tasks systematically

REFACTORPLAN

echo "
✅ REFACTORING PLAN CREATED SUCCESSFULLY

📋 Plan: $REFACTOR_PLAN
🔧 Type: Systematic Code Improvement
📊 Status: Ready for Review and Implementation

Refactoring Strategy:
1. Safety-first approach with comprehensive testing
2. Systematic improvement of code quality metrics
3. Performance preservation with optimization opportunities
4. Risk mitigation with rollback planning

Generated Assets:
- Comprehensive refactoring roadmap
- Risk assessment and mitigation strategies
- Quality gates and success metrics
- Implementation timeline with milestones

Next Actions:
1. Review the refactoring plan for completeness
2. Get team approval for implementation approach
3. Begin safety preparations (branch, tests, metrics)
4. Execute refactoring tasks systematically
5. Monitor progress and quality metrics

Would you like to:
[S]tart safety preparation
[R]eview specific refactoring tasks
[T]est impact analysis
[P]erformance benchmarking
[I]mplement specific refactoring
[Q]uit

Enter choice: "
```

## Quick Refactoring Commands

### Pattern Detection
```bash
# Detect refactoring opportunities
if [[ "$ARGUMENTS" =~ "detect" ]] || [[ "$ARGUMENTS" =~ "analyze" ]]; then
  echo "🔍 REFACTORING OPPORTUNITY DETECTION"
  echo ""
  echo "Analyzing codebase for improvement opportunities..."
  
  # Analyze file complexity
  find . -name "*.js" -o -name "*.ts" -o -name "*.py" -o -name "*.java" | \
  grep -v node_modules | grep -v test | while read file; do
    lines=$(wc -l < "$file")
    if [ "$lines" -gt 200 ]; then
      echo "📁 $file - $lines lines (Large file - consider splitting)"
    elif [ "$lines" -gt 100 ]; then
      echo "📄 $file - $lines lines (Medium file - check complexity)"
    fi
  done
  
  echo ""
  echo "I'll analyze code complexity, duplication, and design patterns..."
fi

# Extract method refactoring
if [[ "$ARGUMENTS" =~ "extract" ]]; then
  echo "⚡ EXTRACT METHOD REFACTORING"
  echo ""
  echo "I'll help you extract methods from large functions..."
  echo ""
  echo "Benefits:"
  echo "- Improved readability"
  echo "- Better testability" 
  echo "- Reduced complexity"
  echo "- Enhanced reusability"
fi

# Remove duplication
if [[ "$ARGUMENTS" =~ "duplicate" ]] || [[ "$ARGUMENTS" =~ "dry" ]]; then
  echo "🔄 DUPLICATE CODE ELIMINATION"
  echo ""
  echo "Searching for duplicate code patterns..."
  echo ""
  echo "I'll identify and help consolidate:"
  echo "- Duplicate functions and methods"
  echo "- Similar code blocks"
  echo "- Repeated business logic"
  echo "- Common utility patterns"
fi

# Modernize legacy code
if [[ "$ARGUMENTS" =~ "modern" ]] || [[ "$ARGUMENTS" =~ "upgrade" ]]; then
  echo "🚀 CODE MODERNIZATION"
  echo ""
  echo "Analyzing code for modernization opportunities..."
  echo ""
  echo "Modernization focus areas:"
  echo "- Language feature updates"
  echo "- Framework version upgrades"
  echo "- Design pattern improvements"
  echo "- Performance optimizations"
fi

# Performance optimization
if [[ "$ARGUMENTS" =~ "performance" ]] || [[ "$ARGUMENTS" =~ "optimize" ]]; then
  echo "⚡ PERFORMANCE OPTIMIZATION"
  echo ""
  echo "Analyzing code for performance improvements..."
  echo ""
  echo "Optimization opportunities:"
  echo "- Algorithm improvements"
  echo "- Data structure optimization"
  echo "- Caching strategies"
  echo "- Resource management"
fi
```

## Framework-Specific Refactoring

### JavaScript/TypeScript
- Modern ES6+ feature adoption
- Promise/async-await conversions
- React hooks migration
- TypeScript strict mode compliance

### Python
- Type hints and dataclasses
- List comprehensions and generators
- Context managers and decorators
- Modern packaging and dependency management

### Java
- Stream API utilization
- Optional and modern error handling
- Lambda expressions and functional programming
- Spring Boot best practices

### C#/.NET
- LINQ and modern C# features
- Async/await patterns
- Dependency injection improvements
- Clean architecture patterns

## Integration with Gosu Commands

### With gosu:test
- Generate tests for refactored code
- Ensure test coverage during refactoring
- Performance test validation

### With gosu:review
- Code quality validation post-refactoring
- Style and convention compliance
- Best practice implementation

### With gosu:security
- Security impact assessment
- Vulnerability introduction prevention
- Security pattern implementation

### With gosu:architect
- Architecture improvement validation
- Design pattern implementation
- System-wide refactoring coordination

### With gosu:docs
- Documentation updates for refactored code
- API documentation regeneration
- Architecture decision records

## Advanced Refactoring Features

### AI-Powered Pattern Detection
- Machine learning-based code smell detection
- Automated refactoring suggestions
- Pattern recognition and replacement
- Risk assessment for refactoring changes

### Safe Refactoring Techniques
- Incremental refactoring with continuous testing
- Feature flag protected rollouts
- Automated rollback mechanisms
- Impact analysis and dependency tracking

### Team Collaboration
- Refactoring planning and coordination
- Knowledge transfer and documentation
- Best practice sharing and standardization
- Continuous improvement processes

## Quality Assurance Standards

Before completing refactoring, I ensure:

- ✓ All existing functionality preserved
- ✓ Test suite passes completely
- ✓ Performance maintained or improved
- ✓ Code quality metrics improved
- ✓ Documentation updated appropriately
- ✓ Team knowledge transferred
- ✓ Best practices implemented
- ✓ Future maintainability enhanced

The `gosu:refactor` command transforms legacy, complex, or problematic code into clean, maintainable, and efficient implementations while preserving functionality and enhancing the overall development experience.