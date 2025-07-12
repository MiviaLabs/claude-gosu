# Comprehensive Security Review Command

Perform a comprehensive cybersecurity analysis of any codebase as an expert security researcher. First determine the technology stack, then adapt your security analysis methodology accordingly.

## Phase 1: Technology Stack Detection

**CRITICAL**: Before beginning security analysis, use the Task tool to identify:

### Language & Framework Detection
- **Programming Languages**: Scan file extensions (.js, .py, .java, .cs, .go, .rb, .php, etc.)
- **Frameworks**: Identify by package files (package.json, requirements.txt, pom.xml, Cargo.toml, etc.)
- **Runtime Environments**: Node.js, Python, .NET, JVM, Go runtime, etc.
- **Database Technologies**: SQL/NoSQL databases, ORMs, connection libraries
- **Web Frameworks**: Express, Django, Spring, Rails, Laravel, etc.
- **Build Tools**: Webpack, Maven, Gradle, npm scripts, etc.

### Technology-Specific Security Focus
Based on detected stack, prioritize relevant security patterns:
- **JavaScript/Node.js**: Prototype pollution, eval() usage, npm vulnerabilities
- **Python**: Pickle deserialization, SQL injection, Django/Flask specific issues
- **Java**: Deserialization, XML processing, Spring Security configurations
- **C#/.NET**: Deserialization, SQL injection, authentication bypasses
- **Go**: Buffer overflows, concurrency issues, HTTP handler security
- **Ruby**: Rails mass assignment, YAML deserialization, gem vulnerabilities
- **PHP**: Include vulnerabilities, SQL injection, session management
- **Others**: Adapt analysis to specific language security patterns

## Phase 2: Adaptive Security Analysis

### Universal Security Vulnerability Categories
Analyze ALL codebases for these core issues, adapting techniques per language:

#### 1. Injection Vulnerabilities
**Adapt per technology:**
- **SQL Databases**: Look for string concatenation in queries vs parameterized queries
- **NoSQL**: Check for MongoDB injection, ElasticSearch injection
- **Command Injection**: OS command execution patterns per language
- **Code Injection**: eval(), exec(), deserialization patterns
- **Template Injection**: Framework-specific template engines

#### 2. Authentication & Authorization
**Language-agnostic patterns:**
- Hardcoded credentials in source code
- Weak password policies and storage
- Session management implementation
- JWT/token handling security
- Access control bypass possibilities
- Multi-factor authentication gaps

#### 3. Data Protection & Cryptography
**Universal security checks:**
- Sensitive data exposure in logs/errors
- Weak cryptographic implementations
- Insecure random number generation
- Certificate and key management
- Encryption key storage and rotation
- PII handling and data privacy

#### 4. Input Validation & Output Encoding
**Adapt validation patterns per language:**
- Input sanitization techniques
- Output encoding for XSS prevention
- Buffer overflow possibilities (C/C++/Go)
- Type confusion vulnerabilities
- Boundary checks and validation

#### 5. Configuration & Infrastructure
**Technology-neutral analysis:**
- Environment variable security
- Configuration file exposure
- Default credentials usage
- File permission issues
- Container security (if applicable)
- CI/CD pipeline vulnerabilities

## Phase 3: Language-Specific Deep Dive

**DYNAMIC ADAPTATION**: Based on Phase 1 detection, focus on:

### If JavaScript/Node.js Detected:
- npm audit for dependency vulnerabilities
- Prototype pollution patterns
- eval() and Function() constructor usage
- Express.js security middleware
- JWT implementation security
- Async/await error handling

### If Python Detected:
- pip security vulnerabilities
- Pickle/YAML deserialization
- Django/Flask security settings
- SQL injection in ORM usage
- Template injection (Jinja2)
- Import statement security

### If Java Detected:
- Maven/Gradle dependency vulnerabilities
- XML processing vulnerabilities (XXE)
- Deserialization gadget chains
- Spring Security configurations
- JDBC SQL injection
- Log4j and logging security

### If C#/.NET Detected:
- NuGet package vulnerabilities
- Deserialization vulnerabilities
- Entity Framework security
- ASP.NET security configurations
- XML processing security
- Authentication bypass patterns

### [Continue for other languages as detected]

## Phase 4: Vulnerability Prioritization & Reporting

### Risk-Based Priority Classification
**CRITICAL (Immediate Action Required)**
- Remote code execution
- Authentication bypass
- Sensitive data exposure
- Administrative privilege escalation

**HIGH (Fix Within 1 Week)**
- Local privilege escalation
- Cross-site scripting
- SQL injection
- Insecure direct object references

**MEDIUM (Fix Within 1 Month)**
- Information disclosure
- CSRF vulnerabilities
- Security misconfigurations
- Weak cryptography

**LOW (Fix When Possible)**
- Missing security headers
- Verbose error messages
- Minor configuration issues

### Comprehensive Security Report Structure

#### Executive Summary
- **Technology Stack Identified**: Languages, frameworks, databases
- **Total Vulnerabilities**: Count by severity level
- **Most Critical Issues**: Top 5 requiring immediate attention
- **Security Posture Rating**: Overall assessment
- **Compliance Status**: Against relevant standards

#### Technology-Specific Findings
For each detected technology:
- **Framework Security Assessment**
- **Language-Specific Vulnerabilities**
- **Dependency Security Analysis**
- **Configuration Security Review**

#### Detailed Vulnerability Analysis
For each finding:
- **Severity & Impact**: Risk level and business impact
- **Location**: Exact file and line references
- **Vulnerability Type**: Category and CWE mapping
- **Technical Details**: How the vulnerability works
- **Exploitation Scenario**: Attack vector description
- **Remediation**: Step-by-step fix instructions
- **Prevention**: How to avoid similar issues

#### Security Recommendations
- **Immediate Actions**: Critical fixes required now
- **Technology-Specific Improvements**: Framework security enhancements
- **Development Process**: Secure coding practices
- **Infrastructure Security**: Deployment and configuration hardening
- **Monitoring & Detection**: Security logging and alerting

## Phase 5: Security Report & User Confirmation

### Security Assessment Completion
After completing the comprehensive security analysis:

1. **Present Complete Security Report** including:
   - Executive summary with vulnerability counts
   - Detailed findings with severity levels
   - Technology-specific security recommendations
   - Risk assessment and compliance status

2. **STOP and Ask User for Confirmation**
   
   **CRITICAL**: Do NOT proceed with implementation automatically. Instead, present the findings and ask:

   ```
   🔒 SECURITY REVIEW COMPLETE
   
   Found [X] security issues:
   - [X] Critical vulnerabilities
   - [X] High priority issues  
   - [X] Medium priority issues
   - [X] Low priority issues
   
   Would you like me to proceed with implementing fixes for the security vulnerabilities found?
   
   Options:
   1. Yes - Create todo list and begin implementing critical fixes
   2. No - Stop here, review only
   3. Selective - Let me choose which issues to fix
   ```

3. **Wait for User Response** before proceeding to Phase 6

## Phase 6: Multi-Agent Implementation Strategy (Only if User Confirms)

### Step 1: Analyze Implementation Complexity
When user approves fixes, first determine the optimal implementation strategy:

#### Multi-Agent Feasibility Assessment
**Evaluate if multiple agents should be used based on:**
- **Issue Count**: >10 security issues across different categories
- **File Distribution**: Issues span >5 different files or modules
- **Technology Diversity**: Multiple languages/frameworks requiring different expertise
- **Issue Independence**: Vulnerabilities can be fixed independently without conflicts
- **Complexity Variation**: Mix of simple and complex fixes requiring different skill levels

#### Agent Assignment Strategy
**If Multi-Agent is Feasible:**
- **Agent 1 (Critical Security)**: P0 critical vulnerabilities, authentication issues
- **Agent 2 (Injection & Validation)**: SQL injection, XSS, input validation fixes
- **Agent 3 (Configuration & Infrastructure)**: Security headers, configuration hardening
- **Agent 4 (Dependencies & Documentation)**: Dependency updates, security documentation

**If Single Agent is Optimal:**
- Complex interdependent fixes
- Small codebase with <5 security issues
- Single technology stack with related vulnerabilities
- Risk of conflicts between concurrent fixes

### Step 2: Implementation Execution

#### Multi-Agent Coordination (If Determined Feasible)
```
🤖 DEPLOYING MULTI-AGENT SECURITY TEAM

Agent Distribution:
- Agent 1: [X] Critical vulnerabilities in [files]
- Agent 2: [X] Injection fixes in [files] 
- Agent 3: [X] Configuration hardening in [files]
- Agent 4: [X] Dependencies and docs in [files]

Each agent will receive:
- Specific vulnerability assignments
- Current codebase context
- Technology stack information
- Security best practices for their domain
```

**For each agent, provide context:**
- Complete security assessment findings
- Assigned vulnerability details
- Technology-specific security guidelines
- File modification coordination to avoid conflicts

#### Single Agent Implementation (If Multi-Agent Not Feasible)
Create prioritized todo list and proceed with sequential fixes:

**P0 (Critical - Fix Immediately)**
- Critical vulnerabilities requiring hotfixes
- Exposed credentials or keys
- Remote code execution flaws

**P1 (High - Fix This Sprint)**
- Authentication/authorization bypasses
- SQL injection vulnerabilities
- XSS vulnerabilities

**P2 (Medium - Next Sprint)**
- Configuration hardening
- Security header implementation
- Input validation improvements

**P3 (Low - Backlog)**
- Code quality improvements
- Security documentation
- Monitoring enhancements

### Step 3: Coordination & Summary

#### Multi-Agent Completion Summary
Once all agents complete their tasks:
```
🔒 MULTI-AGENT SECURITY IMPLEMENTATION COMPLETE

Results Summary:
- Agent 1 (Critical): Fixed [X] critical vulnerabilities
- Agent 2 (Injection): Resolved [X] injection issues
- Agent 3 (Config): Hardened [X] configuration items
- Agent 4 (Dependencies): Updated [X] dependencies, added docs

Total Security Improvements: [X] vulnerabilities resolved
Remaining Issues: [X] items requiring manual review
Security Posture: Improved from [Previous] to [Current]
```

#### Implementation Verification
- **Conflict Resolution**: Check for any conflicting changes between agents
- **Testing Recommendations**: Suggest security testing for implemented fixes
- **Monitoring Setup**: Recommend security monitoring for addressed vulnerabilities
- **Follow-up Actions**: List any remaining manual security tasks

### If User Chooses "Selective" - Guided Implementation
Ask user to specify which priority levels or specific vulnerabilities to fix, then apply the same multi-agent analysis for the selected subset.

### If User Chooses "No" - Report Only
End the process after delivering the security report. Do not create todo lists or make any code changes.

## Execution Instructions

```bash
claude gosu:security
```

**The AI will:**
1. **Detect Technology Stack**: Identify languages, frameworks, databases
2. **Adapt Analysis Approach**: Focus on technology-specific vulnerabilities
3. **Perform Comprehensive Scan**: Universal + language-specific security analysis
4. **Generate Tailored Report**: Results relevant to the detected technology stack
5. **Present Findings & ASK FOR CONFIRMATION**: Stop and wait for user decision
6. **Implement Fixes (Only if Approved)**: Create action plan and fix vulnerabilities

**IMPORTANT**: The process will ALWAYS pause after the security report and ask the user whether to proceed with implementing fixes. No code changes will be made without explicit user approval.

## Expected Adaptive Output

- **Stack Detection Report**: "Detected Node.js/Express with MongoDB" or "Java/Spring Boot with PostgreSQL"
- **Technology-Focused Analysis**: Security assessment tailored to identified stack
- **Language-Specific Vulnerabilities**: Issues relevant to detected programming languages
- **Framework Security Review**: Security assessment for identified frameworks
- **Prioritized Action Plan**: Todo list with technology-appropriate remediation steps

**Key Principle**: Always begin with technology detection, then adapt all subsequent security analysis to be relevant and actionable for the specific technology stack discovered.