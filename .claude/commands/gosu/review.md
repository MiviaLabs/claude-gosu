# Comprehensive Code Review Command

Perform a comprehensive code quality review as an expert software engineer. First determine the technology stack, then adapt your review methodology accordingly. Focus on recently modified files when available via git, otherwise review the entire codebase.

## Phase 1: Review Scope Detection

**CRITICAL**: Before beginning code review, determine the review scope:

### Git-Based Review Scope (Preferred)
If git is available, check for recent changes:
1. **Check git availability**: Verify if project is a git repository
2. **Identify modified files**: 
   - Unstaged changes (`git diff --name-only`)
   - Staged changes (`git diff --cached --name-only`)
   - Recently modified files (`git diff HEAD~1 --name-only`)
3. **Focus review on changed files**: Prioritize recently modified code for review

### Fallback to Full Codebase Review
If no git available OR no modified files found:
- Perform comprehensive review of entire codebase
- Prioritize main source directories and critical files
- Focus on core application logic and configuration files

### Technology Stack Detection
Simultaneously identify the technology stack:
- **Programming Languages**: Scan file extensions (.js, .ts, .py, .java, .cs, .go, .rb, .php, etc.)
- **Frameworks**: Identify by package files (package.json, requirements.txt, pom.xml, etc.)
- **Build Tools**: Detect build configurations and dependency managers
- **Database Technologies**: Identify ORMs, connection libraries, migration files
- **Testing Frameworks**: Locate test files and testing configurations

## Phase 2: Adaptive Code Quality Analysis

### Universal Code Quality Categories
Analyze ALL codebases for these core quality issues, adapting techniques per language:

#### 1. Code Structure & Architecture
**Language-agnostic patterns:**
- Single Responsibility Principle violations
- Tight coupling between modules/classes
- Missing abstraction layers
- Circular dependencies
- Inconsistent architectural patterns
- Poor separation of concerns

#### 2. Code Readability & Maintainability
**Universal quality checks:**
- Function/method complexity (cyclomatic complexity)
- Excessive nesting levels
- Long parameter lists
- Unclear variable and function naming
- Missing or inadequate documentation
- Code duplication and repeated patterns
- Magic numbers and hardcoded values

#### 3. Error Handling & Robustness
**Adapt per technology:**
- Incomplete error handling
- Generic exception catching
- Missing input validation
- Lack of defensive programming
- Resource leak possibilities
- Graceful degradation gaps

#### 4. Performance & Efficiency
**Technology-neutral analysis:**
- Inefficient algorithms and data structures
- Unnecessary loops and iterations
- Memory usage patterns
- Database query optimization
- Caching implementation
- Resource management

#### 5. Testing & Quality Assurance
**Universal testing practices:**
- Test coverage gaps
- Missing unit tests for critical logic
- Integration test completeness
- Test code quality and maintainability
- Mock usage appropriateness
- Test data management

#### 6. Code Style & Conventions
**Adapt to language standards:**
- Inconsistent formatting and indentation
- Naming convention violations
- Language-specific style guide adherence
- Import/dependency organization
- Comment style and documentation standards

## Phase 3: Language-Specific Deep Dive

**DYNAMIC ADAPTATION**: Based on detected technology stack:

### If JavaScript/TypeScript/Node.js Detected:
- ESLint/TSLint rule violations
- Type safety issues (TypeScript)
- Async/await vs Promise usage patterns
- Memory leak patterns (closures, event listeners)
- Package.json dependency management
- Jest/Mocha test quality

### If Python Detected:
- PEP 8 style guide compliance
- Type hints usage (Python 3.5+)
- List comprehension optimization
- Exception handling patterns
- Virtual environment setup
- pytest/unittest test quality

### If Java Detected:
- Clean Code principles adherence
- Design pattern implementation
- Stream API usage (Java 8+)
- Exception hierarchy design
- Maven/Gradle dependency management
- JUnit test coverage

### If C#/.NET Detected:
- SOLID principles implementation
- Async/await pattern usage
- LINQ optimization
- Exception handling best practices
- NuGet package management
- Unit test quality (NUnit/xUnit)

### [Continue for other languages as detected]

## Phase 4: Issue Prioritization & Classification

### Priority-Based Classification

#### **HIGH PRIORITY (Fix Immediately)**
- Critical bugs and logic errors
- Security vulnerabilities
- Performance bottlenecks
- Breaking changes or regressions
- Code that could cause system failures

#### **MEDIUM PRIORITY (Fix This Sprint)**
- Code quality violations affecting maintainability
- Missing error handling
- Test coverage gaps
- Architecture violations
- Documentation gaps

#### **LOW PRIORITY (Fix When Possible)**
- Style guide violations
- Minor performance optimizations
- Code organization improvements
- Non-critical refactoring opportunities
- Enhancement suggestions

### Comprehensive Code Review Report Structure

#### Executive Summary
- **Technology Stack Identified**: Languages, frameworks, testing tools
- **Review Scope**: Files reviewed (modified vs full codebase)
- **Total Issues Found**: Count by priority level
- **Code Quality Score**: Overall assessment (A-F scale)
- **Most Critical Issues**: Top 5 requiring immediate attention

#### File-by-File Analysis
For each reviewed file:
- **File Quality Rating**: Individual assessment
- **Issues Found**: Categorized by priority
- **Complexity Metrics**: Cyclomatic complexity, lines of code
- **Maintainability Index**: Readability and maintainability score

#### Detailed Issue Analysis
For each finding:
- **Priority Level**: High/Medium/Low
- **Issue Category**: Architecture, Performance, Style, etc.
- **Location**: Exact file and line references
- **Description**: Clear explanation of the issue
- **Impact**: Why this matters for code quality
- **Solution**: Step-by-step fix recommendations
- **Best Practice**: How to prevent similar issues

#### Code Quality Recommendations
- **Immediate Actions**: High priority fixes
- **Architecture Improvements**: Structural enhancements
- **Development Process**: Code review and quality practices
- **Tooling Suggestions**: Linters, formatters, analysis tools
- **Team Standards**: Coding conventions and guidelines

## Phase 5: Code Review Report & File Persistence

### Code Quality Assessment Completion & Memory Persistence
After completing the comprehensive code review:

**CRITICAL**: Before presenting the findings, check if `.gosu` directory exists and save the review to a file.

```bash
# Check if .gosu directory exists, if not, skip file creation
if [ -d ".gosu" ]; then
  TIMESTAMP=$(date +"%Y%m%d_%H%M%S")
  REVIEW_FILE=".gosu/review-${TIMESTAMP}.md"
  
  # Save the complete review to file for persistent memory
  cat > "$REVIEW_FILE" << 'EOF'
# Code Quality Review Report - [Project Name]

**Created:** $(date)
**Status:** Review Complete - Awaiting User Approval
**File ID:** review-${TIMESTAMP}
**Quality Score:** [A-F]

## Executive Summary
- Technology Stack: [Detected stack]
- Review Scope: [Files reviewed]
- Total Issues Found: [Count by priority]
- Most Critical Issues: [Top 5]

## Detailed Findings

### HIGH PRIORITY (Fix Immediately)
- [ ] Issue 1: [Description] - File: [location]
- [ ] Issue 2: [Description] - File: [location]

### MEDIUM PRIORITY (Fix This Sprint)
- [ ] Issue 1: [Description] - File: [location]
- [ ] Issue 2: [Description] - File: [location]

### LOW PRIORITY (Fix When Possible)
- [ ] Issue 1: [Description] - File: [location]
- [ ] Issue 2: [Description] - File: [location]

## Code Quality Recommendations
[Immediate actions and improvements]

## Implementation Progress
[Space for tracking fix progress]
EOF
  
  echo "📋 Review saved to: $REVIEW_FILE"
fi
```

1. **Present Complete Code Review Report** including:
   - Executive summary with issue counts and quality score
   - Detailed findings with priority levels
   - Technology-specific recommendations
   - Code quality metrics and assessments

2. **STOP and Ask User for Confirmation**
   
   **CRITICAL**: Do NOT proceed with implementation automatically. Instead, present the findings and ask:

   ```
   CODE REVIEW COMPLETE
   
   Code Quality Score: [A-F]
   Review File: .gosu/review-[TIMESTAMP].md (if .gosu directory exists)
   
   Found [X] code quality issues:
   - [X] High priority issues (fix immediately)
   - [X] Medium priority issues (fix this sprint)
   - [X] Low priority issues (fix when possible)
   
   Would you like me to proceed with implementing fixes for the code quality issues found?
   
   Options:
   1. Yes - Follow the saved review and begin implementing high priority fixes
   2. No - Stop here, review only (review saved for later use with gosu:work)
   3. Selective - Let me choose which issues to fix
   4. High Priority Only - Fix only critical issues
   5. Modify Review - Adjust the findings and update the saved file
   6. Cancel Review - Delete the review file and stop
   ```

3. **Wait for User Response** before proceeding to Phase 6

### Review Refinement Handling

If user chooses "Modify Review", update the saved review file:
```bash
# Update review file with refinements
if [ -f "$REVIEW_FILE" ]; then
  cp "$REVIEW_FILE" "${REVIEW_FILE}.backup"
  # Update the review content based on user feedback
  # Add refinement log
  echo "\n## Review Refinements\n- Refined: $(date) - [Refinement details]" >> "$REVIEW_FILE"
fi
```

If user chooses "Cancel Review", delete the review file:
```bash
# Cancel review and clean up file
if [ -f "$REVIEW_FILE" ]; then
  echo "🗑️ Canceling review and deleting file: $REVIEW_FILE"
  rm "$REVIEW_FILE"
  echo "❌ Review canceled and file deleted"
fi
```

## Phase 6: Multi-Agent Implementation Strategy (Only if User Confirms)

### Step 1: Analyze Implementation Complexity
When user approves fixes, first determine the optimal implementation strategy:

#### Multi-Agent Feasibility Assessment
**Evaluate if multiple agents should be used based on:**
- **Issue Count**: >15 code quality issues across different categories
- **File Distribution**: Issues span >8 different files or modules
- **Issue Type Diversity**: Mix of architecture, performance, testing, and style issues
- **Issue Independence**: Code improvements can be made independently without conflicts
- **Complexity Variation**: Mix of simple style fixes and complex architectural changes

#### Agent Assignment Strategy
**If Multi-Agent is Feasible:**
- **Agent 1 (Architecture & Performance)**: High priority architectural issues, performance bottlenecks
- **Agent 2 (Error Handling & Testing)**: Error handling improvements, test coverage gaps
- **Agent 3 (Code Style & Organization)**: Style guide violations, code organization improvements
- **Agent 4 (Documentation & Best Practices)**: Documentation gaps, best practice implementations

**If Single Agent is Optimal:**
- Complex interdependent refactoring
- Small codebase with <8 code quality issues
- Issues requiring coordinated changes across multiple files
- Risk of merge conflicts between concurrent improvements

### Step 2: Implementation Execution with Review Tracking

**IMPORTANT**: If implementing, always reference and update the saved review file to track progress.

```bash
# Update review file with implementation start
if [ -f "$REVIEW_FILE" ]; then
  sed -i 's/Status: Review Complete - Awaiting User Approval/Status: Implementation In Progress/' "$REVIEW_FILE"
  echo "\n## Implementation Log\n- Started: $(date)" >> "$REVIEW_FILE"
fi
```

#### Multi-Agent Coordination (If Determined Feasible)
```
🔧 DEPLOYING MULTI-AGENT CODE QUALITY TEAM

Agent Distribution:
- Agent 1: [X] Architecture/Performance issues in [files]
- Agent 2: [X] Error handling/Testing improvements in [files]
- Agent 3: [X] Style/Organization fixes in [files]
- Agent 4: [X] Documentation/Best practices in [files]

Each agent will receive:
- Specific issue assignments
- Current codebase context
- Technology stack information
- Code quality standards for their domain
```

**For each agent, provide context:**
- Complete code review findings
- Assigned issue details with priority levels
- Technology-specific coding standards
- File modification coordination to prevent conflicts

#### Single Agent Implementation (If Multi-Agent Not Feasible)
Create prioritized todo list and proceed with sequential fixes following the saved review.

**Issue Fix Tracking**: After completing each fix, update the review file:
```bash
# Mark completed issues in review file
sed -i 's/- \[ \] Issue X: Description/- \[x\] Issue X: Description - Fixed: $(date)/' "$REVIEW_FILE"
echo "- Fixed Issue X: [Description] at $(date)" >> "$REVIEW_FILE"
```

Prioritized implementation order:

**P0 (High Priority - Fix Immediately)**
- Critical bugs and logic errors
- Security vulnerabilities
- Performance bottlenecks
- Breaking changes

**P1 (Medium Priority - Fix This Sprint)**
- Code quality violations
- Missing error handling
- Architecture improvements
- Test coverage gaps

**P2 (Low Priority - Fix When Possible)**
- Style guide violations
- Code organization improvements
- Minor optimizations
- Documentation enhancements

### Step 3: Coordination & Summary

#### Multi-Agent Completion Summary
Once all agents complete their tasks:
```
📋 MULTI-AGENT CODE QUALITY IMPLEMENTATION COMPLETE

Results Summary:
- Agent 1 (Architecture): Improved [X] architectural issues, optimized [X] performance bottlenecks
- Agent 2 (Error/Testing): Enhanced [X] error handlers, added [X] test cases
- Agent 3 (Style/Organization): Fixed [X] style violations, reorganized [X] code structures
- Agent 4 (Documentation): Updated [X] documentation sections, implemented [X] best practices

Total Code Quality Improvements: [X] issues resolved
Code Quality Score: Improved from [Previous] to [Current]
Remaining Items: [X] items for future consideration
```

#### Implementation Verification
- **Conflict Resolution**: Check for any conflicting changes between agents
- **Code Quality Metrics**: Measure improvement in maintainability and readability
- **Testing Verification**: Ensure all tests pass after improvements
- **Integration Check**: Verify code still functions correctly after changes
- **Follow-up Actions**: List any remaining code quality recommendations

**File Cleanup**: After successful code quality implementation completion:
```bash
# Mark review as completed and clean up
if [ -f "$REVIEW_FILE" ]; then
  echo "🗑️ Cleaning up completed review file: $REVIEW_FILE"
  rm "$REVIEW_FILE"
  echo "✅ Review file deleted - code quality improvements complete"
fi
```

### If User Chooses "High Priority Only"
Apply the same multi-agent analysis but focus only on critical issues that could cause system problems.

### If User Chooses "Selective" - Guided Implementation
Ask user to specify which priority levels or specific issues to fix, then apply the same multi-agent analysis for the selected subset.

### If User Chooses "No" - Report Only
End the process after delivering the code review report. Do not create todo lists or make any code changes.

## Execution Instructions

```bash
claude gosu:review
```

**The AI will:**
1. **Detect Review Scope**: Check git for modified files vs full codebase review
2. **Identify Technology Stack**: Determine languages, frameworks, tools
3. **Adapt Review Approach**: Focus on technology-specific quality patterns
4. **Perform Comprehensive Analysis**: Code quality assessment with metrics
5. **Generate Quality Report**: Results with prioritized recommendations
6. **Present Findings & ASK FOR CONFIRMATION**: Stop and wait for user decision
7. **Implement Fixes (Only if Approved)**: Create action plan and improve code quality

**IMPORTANT**: The process will ALWAYS pause after the code review report and ask the user whether to proceed with implementing fixes. No code changes will be made without explicit user approval.

## Expected Adaptive Output

- **Review Scope Report**: "Reviewing 5 modified files" or "Full codebase review (47 files)"
- **Technology Stack Report**: "Node.js/TypeScript with NestJS framework"
- **Code Quality Assessment**: Detailed analysis with quality metrics
- **Technology-Focused Recommendations**: Improvements relevant to detected stack
- **Prioritized Action Plan**: Todo list with technology-appropriate fixes

**Key Principle**: Always begin with scope and technology detection, then adapt all subsequent code review analysis to be relevant and actionable for the specific codebase and recent changes.