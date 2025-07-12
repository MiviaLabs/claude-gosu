# Code Review Command (`gosu:review`)

Comprehensive code quality review by an expert software engineer with intelligent multi-agent coordination for code improvements.

## Overview

The review command performs a thorough code quality analysis, intelligently focusing on recently modified files (via git) or the entire codebase. It automatically adapts its review methodology to your technology stack.

## Usage

```bash
claude gosu:review
```

## What It Does

### 🎯 **Smart Review Scope**
- **Git-based focus**: Prioritizes recently modified files (unstaged/staged changes)
- **Fallback to full codebase**: Reviews entire project if no git or no recent changes
- **Intelligent file prioritization**: Focuses on core application logic and critical files

### 📊 **Comprehensive Quality Analysis**
- **Code structure & architecture** - SOLID principles, coupling, abstraction layers
- **Readability & maintainability** - Complexity metrics, naming conventions, documentation
- **Error handling & robustness** - Exception handling, defensive programming, graceful degradation
- **Performance & efficiency** - Algorithms, memory usage, database optimization
- **Testing & quality assurance** - Test coverage, test quality, mock usage
- **Code style & conventions** - Language-specific style guides, formatting consistency

### 🏆 **Quality Scoring**
- **A-F Grade Scale**: Overall codebase quality assessment
- **File-by-file metrics**: Individual quality ratings
- **Complexity analysis**: Cyclomatic complexity, maintainability index
- **Improvement tracking**: Before/after quality comparisons

## Technology-Specific Analysis

The command automatically adapts its review approach based on detected technologies:

### JavaScript/TypeScript/Node.js
- ESLint/TSLint rule violations
- Type safety issues (TypeScript)
- Async/await vs Promise usage patterns
- Memory leak patterns (closures, event listeners)
- Jest/Mocha test quality

### Python
- PEP 8 style guide compliance
- Type hints usage (Python 3.5+)
- List comprehension optimization
- Exception handling patterns
- pytest/unittest test quality

### Java
- Clean Code principles adherence
- Design pattern implementation
- Stream API usage (Java 8+)
- Exception hierarchy design
- JUnit test coverage

### C#/.NET
- SOLID principles implementation
- Async/await pattern usage
- LINQ optimization
- Exception handling best practices
- Unit test quality (NUnit/xUnit)

## Process Flow

1. **Review Scope Detection**
   - Checks git for recently modified files
   - Falls back to full codebase review if needed
   - Identifies technology stack and frameworks

2. **Adaptive Quality Analysis**
   - Applies universal code quality patterns
   - Uses language-specific analysis techniques
   - Generates complexity and maintainability metrics

3. **Issue Prioritization & Classification**
   - **High Priority**: Critical bugs, security issues, performance bottlenecks
   - **Medium Priority**: Code quality violations, missing error handling, architecture issues
   - **Low Priority**: Style violations, minor optimizations, enhancement suggestions

4. **User Confirmation**
   - Presents comprehensive code review report
   - **Stops and asks for permission** before making changes
   - Offers multiple implementation options

5. **Intelligent Implementation** (if approved)
   - Determines optimal agent coordination strategy
   - Deploys specialized agents for complex improvements
   - Provides coordinated summary of enhancements

## Multi-Agent Coordination

For large codebases with many quality issues, the command automatically deploys specialized agents:

### Agent Assignment Strategy
- **Agent 1 (Architecture & Performance)**: Architectural issues, performance bottlenecks
- **Agent 2 (Error Handling & Testing)**: Error handling improvements, test coverage gaps
- **Agent 3 (Code Style & Organization)**: Style violations, code organization improvements
- **Agent 4 (Documentation & Best Practices)**: Documentation gaps, best practice implementations

### When Multi-Agent is Used
- **Issue Count**: >15 code quality issues across different categories
- **File Distribution**: Issues span >8 different files or modules
- **Issue Type Diversity**: Mix of architecture, performance, testing, and style issues
- **Complexity Variation**: Mix of simple style fixes and complex architectural changes

## Command Options

After the code review analysis, you'll be prompted with:

```
📋 CODE REVIEW COMPLETE

Code Quality Score: B+
Reviewing 8 modified files

Found 23 code quality issues:
- 3 High priority issues (fix immediately)
- 12 Medium priority issues (fix this sprint)
- 8 Low priority issues (fix when possible)

Would you like me to proceed with implementing fixes?

Options:
1. Yes - Create todo list and begin implementing high priority fixes
2. No - Stop here, review only
3. Selective - Let me choose which issues to fix
4. High Priority Only - Fix only critical issues
```

## Output Examples

### Code Quality Report
```
📋 CODE QUALITY ANALYSIS COMPLETE

Technology Stack: Node.js/TypeScript with NestJS
Review Scope: 8 modified files (git-based)
Code Quality Score: B+ (Good, with room for improvement)

High Priority Issues (3):
- Circular dependency detected (src/users/users.module.ts ↔ src/auth/auth.module.ts)
- Missing error handling in async function (src/payments/payments.service.ts:45)
- Performance bottleneck: N+1 query pattern (src/orders/orders.service.ts:123)

Medium Priority Issues (12):
- Function complexity too high (src/users/users.service.ts:67 - complexity: 15)
- Missing unit tests for critical business logic (src/payments/payments.service.ts)
- Inconsistent naming convention (src/utils/helper.functions.ts)
- Magic numbers should be constants (src/config/app.config.ts:23)

Low Priority Issues (8):
- Missing JSDoc comments (src/auth/auth.service.ts)
- Inconsistent import ordering (src/users/users.controller.ts)
- Long parameter list (src/orders/orders.service.ts:89)

Recommendations:
- Refactor circular dependencies using dependency injection patterns
- Implement comprehensive error handling with proper logging
- Optimize database queries using eager loading or caching
- Add unit tests with >80% coverage for business logic
```

### Multi-Agent Implementation
```
🔧 DEPLOYING MULTI-AGENT CODE QUALITY TEAM

Agent Distribution:
- Agent 1: 3 Architecture/Performance issues in users/, orders/, payments/
- Agent 2: 5 Error handling/Testing improvements in services/, controllers/
- Agent 3: 8 Style/Organization fixes across multiple files
- Agent 4: 4 Documentation/Best practices in utils/, config/

📋 MULTI-AGENT CODE QUALITY IMPLEMENTATION COMPLETE

Results Summary:
- Agent 1 (Architecture): Resolved circular dependencies, optimized N+1 queries, improved performance
- Agent 2 (Error/Testing): Added error handling, implemented 15 unit tests, improved robustness
- Agent 3 (Style/Organization): Fixed naming conventions, organized imports, extracted constants
- Agent 4 (Documentation): Added JSDoc comments, created best practices guide, updated README

Total Code Quality Improvements: 20 issues resolved
Code Quality Score: Improved from B+ to A-
Remaining Items: 3 items for future consideration
```

## Priority Classifications

### High Priority (Fix Immediately)
- **Critical bugs and logic errors** - Issues that could cause system failures
- **Security vulnerabilities** - Potential security risks
- **Performance bottlenecks** - Code that significantly impacts performance
- **Breaking changes or regressions** - Issues that break existing functionality

### Medium Priority (Fix This Sprint)
- **Code quality violations** - Issues affecting long-term maintainability
- **Missing error handling** - Incomplete exception and error management
- **Test coverage gaps** - Missing tests for critical functionality
- **Architecture violations** - Deviations from established patterns

### Low Priority (Fix When Possible)
- **Style guide violations** - Formatting and convention inconsistencies
- **Minor performance optimizations** - Small efficiency improvements
- **Code organization improvements** - Better structure and organization
- **Enhancement suggestions** - Nice-to-have improvements

## Best Practices

### When to Use
- **Before submitting pull requests** - Ensure code quality standards
- **After major refactoring** - Validate structural changes
- **When code quality metrics decline** - Proactive quality maintenance
- **For new team member reviews** - Educational code review process
- **Regular maintenance** - Weekly or bi-weekly quality checks

### Integration with Development Workflow
```bash
# Before committing changes
git add . && claude gosu:review

# Focus on recent changes only
claude gosu:review  # Automatically focuses on git changes

# Full codebase review (periodic)
git stash && claude gosu:review  # Reviews entire codebase

# Combined with security review
claude gosu:review && claude gosu:security
```

### Git Integration Benefits
The command intelligently uses git to:
- **Focus on recent changes** - Reviews only modified files for efficiency
- **Track improvement over time** - Compares current vs previous versions
- **Optimize review scope** - Avoids reviewing unchanged, already-reviewed code
- **Support iterative development** - Perfect for agile development cycles

## Quality Metrics

### Code Quality Score (A-F)
- **A (90-100%)**: Excellent code quality, minimal issues
- **B (80-89%)**: Good quality with minor improvements needed
- **C (70-79%)**: Acceptable quality, some issues to address
- **D (60-69%)**: Below standard, significant improvements needed
- **F (<60%)**: Poor quality, major refactoring required

### Complexity Metrics
- **Cyclomatic Complexity**: Measures code complexity and decision points
- **Maintainability Index**: Combines complexity, lines of code, and documentation
- **Technical Debt Ratio**: Estimated time to fix issues vs development time

## Related Commands

- [`gosu:security`](./security.md) - Security-focused analysis that complements code quality review
- Use both commands together for comprehensive code health assessment

## Support

The review command is part of the gosu suite. For general information, see the [main documentation](./README.md).