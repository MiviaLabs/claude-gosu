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

## Command Options

After the security analysis, you'll be prompted with:

```
🔒 SECURITY REVIEW COMPLETE

Found 12 security issues:
- 2 Critical vulnerabilities
- 4 High priority issues  
- 5 Medium priority issues
- 1 Low priority issue

Would you like me to proceed with implementing fixes?

Options:
1. Yes - Create todo list and begin implementing critical fixes
2. No - Stop here, review only
3. Selective - Let me choose which issues to fix
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

# Security-focused development cycle
claude gosu:security --selective
```

## Compliance & Standards

The security command helps ensure compliance with:
- **OWASP Top 10** - Web application security risks
- **CWE** (Common Weakness Enumeration) - Software security weaknesses
- **NIST Cybersecurity Framework** - Security best practices
- **Industry Standards** - Technology-specific security guidelines

## Related Commands

- [`gosu:review`](./review.md) - Code quality review that includes security-related quality issues
- Use both commands together for comprehensive code health assessment

## Support

The security command is part of the gosu suite. For general information, see the [main documentation](./README.md).