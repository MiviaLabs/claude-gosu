# Security Review Command (`gosu:security`)

Comprehensive cybersecurity analysis of any codebase by an expert security researcher with intelligent multi-agent coordination for vulnerability fixes.

## Overview

The security command performs a thorough security audit of your codebase, automatically adapting to your technology stack to identify vulnerabilities, security misconfigurations, and potential attack vectors.

## Usage

```bash
claude gosu:security
```

## What It Does

### 🔍 **Comprehensive Security Analysis**
- **Auto-detects technology stack** (languages, frameworks, databases)
- **Universal vulnerability scanning** (injection attacks, authentication flaws, data protection issues)
- **Language-specific security patterns** (adapted to detected technologies)
- **Configuration security review** (environment variables, security headers, permissions)
- **Dependency vulnerability analysis** (known CVEs in third-party packages)

### 📊 **Risk Assessment & Prioritization**
- **Critical**: Remote code execution, authentication bypass, sensitive data exposure
- **High**: Privilege escalation, XSS, SQL injection, insecure direct object references
- **Medium**: Information disclosure, CSRF, security misconfigurations, weak cryptography
- **Low**: Missing security headers, verbose error messages, minor configuration issues

## Technology-Specific Security Focus

The command automatically adapts its analysis based on detected technologies:

### JavaScript/Node.js
- npm audit for dependency vulnerabilities
- Prototype pollution patterns
- eval() and Function() constructor usage
- Express.js security middleware
- JWT implementation security

### Python
- pip security vulnerabilities
- Pickle/YAML deserialization
- Django/Flask security settings
- SQL injection in ORM usage
- Template injection (Jinja2)

### Java
- Maven/Gradle dependency vulnerabilities
- XML processing vulnerabilities (XXE)
- Deserialization gadget chains
- Spring Security configurations
- Log4j and logging security

### Other Languages
The command includes security patterns for C#/.NET, Go, Ruby, PHP, and more, automatically adapting to your specific stack.

## Process Flow

1. **Technology Stack Detection**
   - Scans file extensions and configuration files
   - Identifies frameworks, databases, and build tools
   - Determines appropriate security analysis patterns

2. **Security Vulnerability Analysis**
   - Injection vulnerabilities (SQL, NoSQL, Command, Code, Template)
   - Authentication & authorization flaws
   - Data protection & cryptography issues
   - Input validation & output encoding gaps
   - Configuration & infrastructure security

3. **Risk Assessment & Reporting**
   - Prioritizes findings by severity and impact
   - Maps vulnerabilities to OWASP Top 10 and CWE standards
   - Provides detailed remediation instructions
   - Creates technology-specific security recommendations

4. **User Confirmation**
   - Presents comprehensive security report
   - **Stops and asks for permission** before making changes
   - Offers implementation options

5. **Intelligent Implementation** (if approved)
   - Determines optimal agent coordination strategy
   - Deploys specialized agents for complex fixes
   - Provides coordinated summary of improvements

## Multi-Agent Coordination

For complex codebases with many security issues, the command automatically deploys specialized agents:

### Agent Assignment Strategy
- **Agent 1 (Critical Security)**: Critical vulnerabilities, authentication issues
- **Agent 2 (Injection & Validation)**: SQL injection, XSS, input validation fixes
- **Agent 3 (Configuration & Infrastructure)**: Security headers, configuration hardening
- **Agent 4 (Dependencies & Documentation)**: Dependency updates, security documentation

### When Multi-Agent is Used
- **Issue Count**: >10 security issues across different categories
- **File Distribution**: Issues span >5 different files or modules
- **Technology Diversity**: Multiple languages/frameworks requiring different expertise
- **Issue Independence**: Vulnerabilities can be fixed independently without conflicts

## Persistent Task Management

### Security Report Creation & Storage
If you've run `gosu:init` to initialize the workspace, your security audits are automatically saved for later resumption:

```bash
# Security report is saved to .gosu directory
.gosu/security-20240712_160315.md

# Contains complete security analysis with:
- Executive summary and security posture assessment
- Detailed vulnerability findings by severity level
- Technology-specific security recommendations
- Compliance status and remediation roadmap
- Real-time fix progress tracking
```

### Integration with gosu:work
Resume security remediation across sessions:

```bash
# Resume saved security work
claude gosu:work security-20240712_160315.md

# Or select interactively
claude gosu:work
# > 3. security-20240712_160315.md (Implementation In Progress - 3/8 vulnerabilities fixed)
```

### Progress Tracking
Security files automatically track remediation progress:
- **Checkbox states**: `[x]` fixed, `[ ]` pending
- **Severity tracking**: Progress within each severity level (Critical → High → Medium → Low)
- **Timestamps**: When vulnerabilities were resolved
- **Security posture improvements**: Before/after security rating

## Command Options

After the security analysis, you'll be prompted with:

```
🔒 SECURITY REVIEW COMPLETE

Security File: .gosu/security-20240712_160315.md (if workspace initialized)

Found 12 security issues:
- 2 Critical vulnerabilities
- 4 High priority issues  
- 5 Medium priority issues
- 1 Low priority issue

Would you like me to proceed with implementing fixes for the security vulnerabilities found?

Options:
1. Yes - Follow the saved security report and begin implementing critical fixes
2. No - Stop here, review only (report saved for later use with gosu:work)
3. Selective - Let me choose which issues to fix
4. Modify Report - Adjust the findings and update the saved file
5. Cancel Security Review - Delete the security file and stop
```

## Output Examples

### Security Assessment Report
```
🔒 SECURITY ANALYSIS COMPLETE

Technology Stack: Node.js/TypeScript with NestJS
Security Posture: C+ (Needs Improvement)

Critical Issues (2):
- SQL Injection in user query endpoint (src/users/users.service.ts:45)
- Hardcoded JWT secret in configuration (src/config/auth.config.ts:12)

High Priority Issues (4):
- Missing input validation on file upload (src/upload/upload.controller.ts:23)
- XSS vulnerability in comment display (src/comments/comments.service.ts:67)
- Insecure direct object reference (src/users/users.controller.ts:89)
- Missing rate limiting on authentication endpoints (src/auth/auth.controller.ts:34)

Recommendations:
- Implement parameterized queries for all database interactions
- Move secrets to environment variables with proper validation
- Add comprehensive input validation using class-validator
- Implement helmet.js for security headers
```

### Multi-Agent Implementation
```
🤖 DEPLOYING MULTI-AGENT SECURITY TEAM

Agent Distribution:
- Agent 1: 2 Critical vulnerabilities in auth/, users/
- Agent 2: 3 Injection fixes in database/, controllers/
- Agent 3: 4 Configuration items in config/, middleware/
- Agent 4: 2 Dependencies in package.json, security docs

🔒 MULTI-AGENT SECURITY IMPLEMENTATION COMPLETE

Results Summary:
- Agent 1 (Critical): Fixed SQL injection, secured JWT configuration
- Agent 2 (Injection): Added input validation, XSS protection
- Agent 3 (Config): Implemented security headers, rate limiting
- Agent 4 (Dependencies): Updated vulnerable packages, added security docs

Total Security Improvements: 11 vulnerabilities resolved
Security Posture: Improved from C+ to A-
```

## Best Practices

### When to Use
- **Before production deployments** - Catch security issues early
- **After adding user input features** - Validate new attack vectors
- **When integrating third-party libraries** - Check for dependency vulnerabilities
- **For compliance audits** - OWASP, NIST, industry standards
- **Regular security health checks** - Monthly or quarterly reviews

### Integration with Development Workflow
```bash
# Before deployment
claude gosu:security

# After feature development
git add . && claude gosu:security

# Cross-session security workflow with persistence
claude gosu:security             # Create security report
# ... session ends ...
claude gosu:work                 # Resume vulnerability fixes later
# ... continue remediation ...
claude gosu:work                 # Resume again until all critical issues fixed

# Security-focused development cycle
claude gosu:security --selective
```

### Vulnerability Remediation & File Management
The security command automatically manages security files throughout the remediation lifecycle:

**Automatic Progress Updates:**
```bash
# As vulnerabilities are fixed, security file is updated in real-time
- [x] Fix SQL injection in user search - Fixed: 2024-07-12 16:45:22
- [x] Secure JWT configuration with env variables - Fixed: 2024-07-12 16:52:18
- [ ] Implement rate limiting on auth endpoints
```

**Security Posture Tracking:**
```bash
# Security improvements tracked over time
Security Posture: C+ → A- (Improved from 65% to 87%)
Critical Vulnerabilities: 2 → 0 (All resolved)
High Priority Issues: 4 → 1 (3 resolved)
```

**Automatic Cleanup:**
```bash
# When all critical vulnerabilities are resolved
🎉 Security improvements completed successfully!
🔒 Security Posture improved from C+ to A-
🗑️ Cleaning up completed security file: .gosu/security-20240712_160315.md
✅ Security file deleted - vulnerability remediation complete
```

**Manual Security Management:**
- **Modify Report**: Update findings and save changes
- **Cancel Security Review**: Delete security file and stop work
- **Selective Remediation**: Choose specific vulnerabilities to address
- **Priority-Based Fixes**: Focus on critical/high severity issues only

## Compliance & Standards

The security command helps ensure compliance with:
- **OWASP Top 10** - Web application security risks
- **CWE** (Common Weakness Enumeration) - Software security weaknesses
- **NIST Cybersecurity Framework** - Security best practices
- **Industry Standards** - Technology-specific security guidelines

## Related Commands

- [`gosu:init`](./init.md) - Initialize workspace for persistent task management (recommended first step)
- [`gosu:work`](./work.md) - Resume work on saved security files across sessions
- [`gosu:plan`](./plan.md) - Feature planning that should include security considerations
- [`gosu:review`](./review.md) - Code quality review that includes security-related quality issues

### Complete Security Workflow
```bash
# Initialize workspace
claude gosu:init

# Security-first development lifecycle
claude gosu:plan "secure feature"   # Plan with security in mind
claude gosu:work                    # Implement with security practices
claude gosu:review                  # Review for quality and security issues
claude gosu:security                # Comprehensive security audit
claude gosu:work                    # Resume security fixes across sessions

# Security remediation workflow
claude gosu:security                # Analyze security vulnerabilities
claude gosu:work                    # Fix critical vulnerabilities first
claude gosu:review                  # Ensure fixes maintain code quality
```

## Support

The security command is part of the gosu suite. For general information, see the [main documentation](./README.md).