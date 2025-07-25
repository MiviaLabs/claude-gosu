# gosu:refactor - Systematic Code Refactoring & Improvement

Act as a professional senior developer, code architect, and refactoring specialist to identify, plan, and execute systematic code improvements while maintaining functionality and enhancing maintainability.

## Overview

The `gosu:refactor` command provides systematic code refactoring solutions that improve code quality, maintainability, and performance while preserving functionality. This command acts as your virtual senior development team to guide safe, effective refactoring.

## Usage

```bash
# Interactive mode - comprehensive refactoring analysis
claude gosu:refactor

# Extract methods from large functions
claude gosu:refactor "extract service layer from controllers"

# Detect refactoring opportunities
claude gosu:refactor "detect patterns"

# Modernize legacy code
claude gosu:refactor "modernize legacy patterns"

# Performance optimization
claude gosu:refactor "optimize performance"

# Remove code duplication
claude gosu:refactor "eliminate duplication"
```

## Key Features

### 1. Professional Refactoring Team Approach

Claude Code acts as your virtual senior development team:

- **Code Architect**: Identifying design patterns and structural improvements
- **Refactoring Specialist**: Executing safe code transformations with proper testing
- **Performance Expert**: Optimizing code for better performance and maintainability

### 2. Intelligent Code Analysis

- **Code Smell Detection**: Automatically identify design issues and anti-patterns
- **Pattern Recognition**: Detect opportunities for design pattern implementation
- **Complexity Analysis**: Identify overly complex code that needs simplification
- **Duplication Detection**: Find and consolidate duplicate code across the codebase

### 3. Safe Refactoring Methodology

#### Safety-First Approach
- **Test-Driven Refactoring**: Ensure comprehensive test coverage before changes
- **Incremental Changes**: Small, manageable refactoring steps
- **Continuous Validation**: Test execution after each refactoring step
- **Rollback Planning**: Clear rollback strategies for each refactoring

#### Systematic Improvement
- **Priority-Based**: Address critical issues first, then improvements
- **Measurable Goals**: Define specific quality metrics to achieve
- **Documentation**: Document all changes and architectural decisions
- **Review Process**: Built-in code review and validation steps

### 4. Comprehensive Refactoring Types

#### Structural Refactoring
- **Extract Method**: Break down large functions into smaller, focused methods
- **Extract Class**: Separate concerns into appropriate classes
- **Move Method**: Reorganize methods into more appropriate locations
- **Inline Method**: Eliminate unnecessary indirection

#### Design Pattern Implementation
- **Strategy Pattern**: Replace conditional logic with strategy objects
- **Factory Pattern**: Centralize object creation logic
- **Observer Pattern**: Implement event-driven architecture
- **Dependency Injection**: Reduce coupling between components

#### Performance Optimization
- **Algorithm Improvement**: Optimize inefficient algorithms
- **Data Structure Optimization**: Use more appropriate data structures
- **Caching Implementation**: Add strategic caching layers
- **Resource Management**: Optimize memory and CPU usage

#### Modernization
- **Language Feature Updates**: Adopt modern language features
- **Framework Upgrades**: Update to modern framework patterns
- **API Modernization**: Improve API design and consistency
- **Documentation Updates**: Ensure documentation matches code changes

## Refactoring Process

### Phase 1: Analysis & Planning
1. **Code Quality Assessment**: Analyze current code quality metrics
2. **Issue Identification**: Detect code smells and improvement opportunities
3. **Priority Ranking**: Rank issues by impact and implementation difficulty
4. **Refactoring Strategy**: Develop systematic improvement plan

### Phase 2: Safety Preparation
1. **Test Coverage Analysis**: Ensure adequate test coverage exists
2. **Baseline Metrics**: Capture current performance and quality metrics
3. **Backup Strategy**: Create safe rollback points
4. **Impact Assessment**: Analyze potential risks and dependencies

### Phase 3: Systematic Implementation
1. **Incremental Changes**: Execute refactoring in small, safe steps
2. **Continuous Testing**: Validate functionality after each change
3. **Quality Monitoring**: Track improvement in quality metrics
4. **Documentation Updates**: Keep documentation current with changes

### Phase 4: Validation & Optimization
1. **Final Testing**: Comprehensive test suite execution
2. **Performance Validation**: Ensure performance is maintained or improved
3. **Code Review**: Thorough review of all changes
4. **Knowledge Transfer**: Document improvements and lessons learned

## Framework-Specific Refactoring

### JavaScript/TypeScript
- **Modern ES6+ Features**: Arrow functions, destructuring, async/await
- **React Optimization**: Hooks migration, component optimization
- **TypeScript Migration**: Add type safety to JavaScript code
- **Bundle Optimization**: Code splitting and performance improvements

### Python
- **Type Hints**: Add comprehensive type annotations
- **Modern Python**: List comprehensions, context managers, dataclasses
- **Framework Updates**: Django/Flask modernization patterns
- **Performance**: Asyncio adoption, efficient data structures

### Java
- **Modern Java**: Stream API, Optional, lambda expressions
- **Spring Boot**: Best practices and modern patterns
- **Design Patterns**: Implement appropriate GoF patterns
- **Performance**: JVM optimization and memory management

### C#/.NET
- **Modern C#**: LINQ, async/await, pattern matching
- **Dependency Injection**: Implement DI containers and patterns
- **Clean Architecture**: Layered architecture implementation
- **Performance**: Memory optimization and async patterns

## Output Format

The command creates comprehensive refactoring plans in `.gosu/refactor-YYYYMMDD_HHMMSS.md` format with:

- **Refactoring Strategy**: Objectives, scope, and systematic approach
- **Code Quality Analysis**: Current metrics and improvement targets
- **Detailed Tasks**: Step-by-step refactoring instructions with code examples
- **Risk Assessment**: Potential issues and mitigation strategies
- **Testing Strategy**: Comprehensive validation approach
- **Implementation Timeline**: Phased approach with milestones

## Integration with Other Commands

### With gosu:test
- **Safety Net**: Ensure comprehensive tests before refactoring
- **Validation**: Test all functionality after refactoring changes
- **Regression Prevention**: Catch issues introduced during refactoring

### With gosu:review
- **Quality Validation**: Review code quality improvements
- **Best Practices**: Ensure refactored code follows standards
- **Knowledge Sharing**: Document refactoring patterns and decisions

### With gosu:security
- **Security Impact**: Assess security implications of refactoring
- **Vulnerability Prevention**: Ensure refactoring doesn't introduce vulnerabilities
- **Access Control**: Validate security patterns in refactored code

### With gosu:architect
- **Architecture Alignment**: Ensure refactoring supports overall architecture
- **Design Consistency**: Maintain architectural patterns and decisions
- **System Impact**: Consider system-wide effects of refactoring

### With gosu:docs
- **Documentation Updates**: Keep documentation current with refactored code
- **API Documentation**: Update API docs for interface changes
- **Architecture Records**: Document architectural decisions made during refactoring

## Advanced Features

### AI-Powered Refactoring Analysis
- **Pattern Detection**: Machine learning-based detection of improvement opportunities
- **Risk Assessment**: Automated analysis of refactoring risks and complexity
- **Impact Prediction**: Predict the effects of proposed refactoring changes
- **Optimization Suggestions**: AI-driven recommendations for performance improvements

### Automated Refactoring Tools
- **Safe Transformations**: Automated execution of low-risk refactoring operations
- **Code Generation**: Generate boilerplate code for common patterns
- **Migration Assistance**: Automated help with framework and language migrations
- **Quality Metrics**: Real-time tracking of code quality improvements

### Team Collaboration Features
- **Refactoring Planning**: Coordinate refactoring efforts across team members
- **Knowledge Transfer**: Share refactoring patterns and best practices
- **Progress Tracking**: Monitor refactoring progress and success metrics
- **Review Integration**: Built-in code review workflows for refactoring changes

## Best Practices

### When to Use gosu:refactor

- **Before major feature additions**: Clean up code before adding new functionality
- **Technical debt reduction**: Systematically address accumulated technical debt
- **Performance optimization**: Improve code performance and efficiency
- **Legacy modernization**: Update old code to use modern patterns and practices
- **Code quality improvement**: Enhance maintainability and readability

### Refactoring Workflow Integration

```bash
# Complete refactoring workflow
claude gosu:refactor "analyze opportunities"    # Assessment
claude gosu:test "ensure coverage"              # Safety preparation
claude gosu:refactor "implement improvements"   # Execution
claude gosu:review "validate quality"          # Validation
claude gosu:docs "update documentation"        # Documentation
```

### Quality Assurance Standards

Before completing refactoring:

- ✓ All existing functionality preserved and tested
- ✓ Code quality metrics show measurable improvement
- ✓ Performance maintained or improved
- ✓ Test suite passes completely with no regressions
- ✓ Documentation updated to reflect changes
- ✓ Team knowledge transferred appropriately
- ✓ Architectural consistency maintained
- ✓ Security considerations addressed

## Benefits for Agentic Development

The `gosu:refactor` command is crucial for agentic development because it:

1. **Maintains Code Quality**: Systematic improvement prevents technical debt accumulation
2. **Enables Safe Changes**: Provides frameworks for AI agents to improve code safely
3. **Preserves Functionality**: Ensures refactoring doesn't break existing features
4. **Improves Maintainability**: Makes code easier for AI agents to understand and modify
5. **Optimizes Performance**: Systematically improves code efficiency and speed
6. **Modernizes Codebase**: Keeps code current with best practices and modern patterns

The command transforms refactoring from a risky, manual process into a systematic, safe, and measurable improvement workflow that enables continuous code quality enhancement in agentic development environments.