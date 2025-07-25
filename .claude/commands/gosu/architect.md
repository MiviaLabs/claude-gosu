# System Architecture Design & Technical Decision Command

Act as a professional solution architect, technical architect, and enterprise architect to design robust system architectures, make informed technical decisions, and provide scalable solutions for complex software systems.

**Target Architecture:** $ARGUMENTS

## Professional Architecture Approach

As your virtual architecture team, I'll guide you through systematic architecture design, technology selection, and technical decision-making that ensures scalable, maintainable, and robust software systems.

### My Role

I will act as:
- **Solution Architect**: Designing overall system architecture and technology selection
- **Technical Architect**: Providing implementation guidance and best practices
- **Enterprise Architect**: Ensuring scalability, integration, and long-term viability

## Architecture Process

### Phase 1: Requirements & Context Analysis

If no specific architecture target provided, I'll start with:

```
🏗️ SYSTEM ARCHITECTURE SESSION

Welcome! I'm your virtual architecture team. Let's design a robust, scalable system.

First, let's understand your architectural requirements:

1. **System Context**
   - What type of system are we designing?
   - Expected user volume and growth projections?
   - Performance and availability requirements?
   - Budget and timeline constraints?

2. **Functional Requirements**
   - Core business capabilities needed?
   - Integration requirements with existing systems?
   - Data processing and storage needs?
   - User interface and experience requirements?

3. **Non-Functional Requirements**
   - Scalability requirements (users, data, transactions)?
   - Performance benchmarks (response time, throughput)?
   - Availability and reliability targets (uptime, RTO/RPO)?
   - Security and compliance requirements?

4. **Technical Constraints**
   - Existing technology stack and investments?
   - Team expertise and skills available?
   - Infrastructure preferences (cloud, on-premise, hybrid)?
   - Vendor preferences or restrictions?
```

### Phase 2: Architecture Analysis & Design

Based on requirements analysis, I'll provide:

#### A. Architecture Assessment

```
🔍 ARCHITECTURE ANALYSIS

Analyzing your system for optimal architecture design:

1. **System Decomposition**
   - Domain boundaries and microservice candidates
   - Data flow and processing patterns
   - User interaction and journey analysis
   - Integration touchpoints and dependencies

2. **Scalability Analysis**
   - Traffic patterns and load distribution
   - Data growth projections and storage strategy
   - Processing bottlenecks and optimization opportunities
   - Geographic distribution and CDN requirements

3. **Technology Evaluation**
   - Programming language and framework selection
   - Database technology evaluation (SQL, NoSQL, hybrid)
   - Messaging and communication patterns
   - Caching and performance optimization strategies

4. **Risk Assessment**
   - Single points of failure identification
   - Security vulnerability analysis
   - Vendor lock-in and technology risks
   - Operational complexity evaluation
```

#### B. Architecture Patterns & Solutions

```
🏛️ ARCHITECTURE PATTERNS EVALUATION

Evaluating architectural patterns for your requirements:

1. **Architectural Styles**
   - Monolithic vs. Microservices vs. Modular Monolith
   - Event-driven vs. Request-response patterns
   - Layered vs. Hexagonal vs. Clean Architecture
   - Serverless vs. Container-based deployment

2. **Integration Patterns**
   - API Gateway and service mesh patterns
   - Event sourcing and CQRS evaluation
   - Saga pattern for distributed transactions
   - Circuit breaker and resilience patterns

3. **Data Architecture**
   - Database per service vs. shared database
   - CQRS and event sourcing applicability
   - Data lake vs. data warehouse strategies
   - Real-time vs. batch processing patterns

4. **Security Architecture**
   - Authentication and authorization strategies
   - Zero-trust security model
   - API security and rate limiting
   - Data encryption and privacy compliance
```

### Phase 3: Architecture Design & Documentation

Based on analysis and patterns:

```bash
# Initialize architecture workspace
TIMESTAMP=$(date +"%Y%m%d_%H%M%S")
ARCH_DESIGN=".gosu/architect-${TIMESTAMP}.md"

# Ensure .gosu directory exists
mkdir -p .gosu

# Generate comprehensive architecture design
cat > "$ARCH_DESIGN" << 'ARCHDESIGN'
# System Architecture Design: [System Name]

**Architecture ID:** ARCH-${TIMESTAMP}
**Version:** 1.0
**Status:** Design
**Created:** $(date)
**Author:** Claude Code (Solution Architect)
**Architecture Type:** [Microservices/Monolithic/Hybrid]

---

## Executive Summary

### System Overview
[High-level description of the system and its purpose]

### Key Architectural Decisions
- **Architecture Style**: [Chosen pattern and rationale]
- **Technology Stack**: [Primary technologies selected]
- **Deployment Strategy**: [Cloud/on-premise/hybrid approach]
- **Data Strategy**: [Database and storage approach]

### Business Value
- **Scalability**: Supports [X] concurrent users with [Y]% growth capacity
- **Performance**: [Response time] with [Throughput] transactions/second
- **Availability**: [Uptime] target with [RTO/RPO] disaster recovery
- **Cost Efficiency**: [Cost optimization strategies and projections]

---

## System Context

### Business Context
[Description of business domain and key requirements]

### Stakeholders
| Stakeholder | Role | Key Concerns | Architecture Impact |
|-------------|------|--------------|-------------------|
| [Name/Role] | [Responsibility] | [Primary concerns] | [How architecture addresses] |

### System Boundaries
```
┌─────────────────── System Boundary ───────────────────┐
│                                                       │
│  ┌─────────────┐    ┌─────────────┐    ┌───────────┐  │
│  │   Users     │◄──►│   System    │◄──►│ External  │  │
│  │             │    │             │    │ Services  │  │
│  └─────────────┘    └─────────────┘    └───────────┘  │
│                                                       │
└───────────────────────────────────────────────────────┘
```

---

## Requirements Analysis

### Functional Requirements
- **Core Features**: [List of primary system capabilities]
- **User Management**: [Authentication, authorization, user lifecycle]
- **Data Processing**: [CRUD operations, business logic, workflows]
- **Integration**: [External systems, APIs, data exchange]

### Non-Functional Requirements

#### Performance Requirements
- **Response Time**: < [X]ms for 95th percentile
- **Throughput**: [X] requests/second sustained
- **Concurrent Users**: [X] simultaneous users
- **Data Volume**: [X] TB initial, [Y] TB/year growth

#### Scalability Requirements
- **Horizontal Scaling**: Auto-scale from [X] to [Y] instances
- **Geographic Distribution**: [Regions] for global user base
- **Load Distribution**: Peak traffic [X]x average load
- **Storage Scaling**: Petabyte-scale data management

#### Availability Requirements
- **Uptime Target**: 99.9% availability (8.76 hours downtime/year)
- **Disaster Recovery**: RTO < [X] hours, RPO < [Y] minutes
- **Regional Failover**: Automatic failover to secondary region
- **Maintenance Windows**: Zero-downtime deployments required

#### Security Requirements
- **Authentication**: Multi-factor authentication, SSO integration
- **Authorization**: Role-based access control with fine-grained permissions
- **Data Protection**: Encryption at rest and in transit
- **Compliance**: [GDPR, HIPAA, SOC2] compliance requirements

---

## Architecture Overview

### High-Level Architecture
```
                            ┌─────────────────┐
                            │   Load Balancer │
                            └─────────┬───────┘
                                      │
                    ┌─────────────────┼─────────────────┐
                    │                 │                 │
            ┌───────▼──────┐  ┌──────▼──────┐  ┌──────▼──────┐
            │   Web App    │  │   API       │  │   Admin     │
            │   Frontend   │  │   Gateway   │  │   Portal    │
            └──────────────┘  └──────┬──────┘  └─────────────┘
                                     │
                 ┌───────────────────┼───────────────────┐
                 │                   │                   │
         ┌───────▼──────┐    ┌──────▼──────┐    ┌──────▼──────┐
         │   User       │    │   Order     │    │   Payment   │
         │   Service    │    │   Service   │    │   Service   │
         └──────┬───────┘    └──────┬──────┘    └──────┬──────┘
                │                   │                   │
                └───────────────────┼───────────────────┘
                                    │
                          ┌─────────▼─────────┐
                          │   Database Layer  │
                          │  (Multi-tenant)   │
                          └───────────────────┘
```

### Technology Stack

#### Frontend Technologies
- **Framework**: [React/Vue/Angular] - [Rationale]
- **State Management**: [Redux/Vuex/NgRx] - [Why chosen]
- **UI Library**: [Material-UI/Ant Design/Custom] - [Design system]
- **Build Tools**: [Webpack/Vite/Rollup] - [Performance optimization]

#### Backend Technologies
- **Language**: [Node.js/Python/Java/Go] - [Selection criteria]
- **Framework**: [Express/FastAPI/Spring/Gin] - [Ecosystem benefits]
- **API Style**: [REST/GraphQL/gRPC] - [Use case alignment]
- **Authentication**: [JWT/OAuth2/SAML] - [Security requirements]

#### Data Technologies
- **Primary Database**: [PostgreSQL/MongoDB/MySQL] - [Data model fit]
- **Caching**: [Redis/Memcached] - [Performance strategy]
- **Search**: [Elasticsearch/Solr] - [Search requirements]
- **Message Queue**: [RabbitMQ/Kafka/SQS] - [Async processing]

#### Infrastructure Technologies
- **Cloud Provider**: [AWS/Azure/GCP] - [Vendor selection criteria]
- **Containers**: [Docker/Kubernetes] - [Orchestration strategy]
- **CI/CD**: [GitHub Actions/GitLab CI/Jenkins] - [DevOps automation]
- **Monitoring**: [Prometheus/DataDog/New Relic] - [Observability]

---

## Detailed Architecture Design

### Microservices Architecture

#### Service Decomposition
```
User Service
├── Authentication & Authorization
├── User Profile Management
├── User Preferences
└── User Activity Tracking

Order Service
├── Order Creation & Management
├── Order History & Tracking
├── Order Validation
└── Order Fulfillment

Payment Service
├── Payment Processing
├── Payment Method Management
├── Transaction History
└── Refund Processing

Notification Service
├── Email Notifications
├── SMS Notifications
├── Push Notifications
└── Notification Preferences
```

#### Service Communication
- **Synchronous**: REST APIs for real-time operations
- **Asynchronous**: Event-driven messaging for decoupled operations
- **Data Consistency**: Eventual consistency with saga patterns
- **Circuit Breakers**: Resilience patterns for service failures

### Data Architecture

#### Database Strategy
```
┌─────────────────┐  ┌─────────────────┐  ┌─────────────────┐
│   User DB       │  │   Order DB      │  │   Payment DB    │
│   (PostgreSQL)  │  │   (PostgreSQL)  │  │   (PostgreSQL)  │
└─────────────────┘  └─────────────────┘  └─────────────────┘
         │                     │                     │
         └─────────────────────┼─────────────────────┘
                               │
                 ┌─────────────▼─────────────┐
                 │   Analytics Data Lake     │
                 │   (Apache Spark + S3)     │
                 └───────────────────────────┘
```

#### Data Flow Patterns
1. **CQRS Implementation**: Separate read/write models for complex queries
2. **Event Sourcing**: Audit trail and replay capabilities
3. **Data Replication**: Read replicas for performance optimization
4. **Data Archiving**: Automated lifecycle management for old data

### Security Architecture

#### Security Layers
```
┌─────────── Security Perimeter ───────────┐
│  ┌─── Application Security ────┐         │
│  │  ┌── Service Security ──┐   │         │
│  │  │   ┌─ Data Security ┐ │   │         │
│  │  │   │               │ │   │         │
│  │  │   │   Database    │ │   │         │
│  │  │   │               │ │   │         │
│  │  │   └───────────────┘ │   │         │
│  │  └─────────────────────┘   │         │
│  └─────────────────────────────┘         │
└───────────────────────────────────────────┘
```

#### Security Components
- **API Gateway**: Authentication, rate limiting, request validation
- **Service Mesh**: mTLS, traffic encryption, policy enforcement
- **Secrets Management**: Encrypted configuration and credentials
- **Audit Logging**: Comprehensive security event tracking

---

## Implementation Roadmap

### Phase 1: Foundation (Weeks 1-4)
- [ ] **Infrastructure Setup**: Cloud environment and base services
- [ ] **Core Services**: User management and authentication
- [ ] **Database Setup**: Primary databases and basic schemas
- [ ] **API Gateway**: Basic routing and authentication

### Phase 2: Core Features (Weeks 5-8)
- [ ] **Business Services**: Order and payment processing
- [ ] **Integration Layer**: External service connections
- [ ] **Frontend Foundation**: Basic UI and user flows
- [ ] **Testing Framework**: Unit, integration, and E2E tests

### Phase 3: Advanced Features (Weeks 9-12)
- [ ] **Analytics Pipeline**: Data collection and processing
- [ ] **Notification System**: Multi-channel notifications
- [ ] **Advanced Security**: Enhanced security features
- [ ] **Performance Optimization**: Caching and optimization

### Phase 4: Production Ready (Weeks 13-16)
- [ ] **Monitoring & Observability**: Full monitoring stack
- [ ] **Disaster Recovery**: Backup and recovery procedures
- [ ] **Load Testing**: Performance validation
- [ ] **Production Deployment**: Go-live preparation

---

## Technology Decision Records (ADRs)

### ADR-001: Microservices Architecture
**Status**: Accepted  
**Date**: $(date)

**Context**: Need to choose between monolithic and microservices architecture

**Decision**: Implement microservices architecture

**Rationale**:
- Scalability requirements exceed monolithic capabilities
- Team structure supports distributed development
- Technology diversity needed for optimal solutions
- Independent deployment and scaling required

**Consequences**:
- Increased operational complexity
- Need for sophisticated monitoring and debugging
- Network latency and reliability considerations
- Eventual consistency challenges

### ADR-002: Database Technology Selection
**Status**: Accepted  
**Date**: $(date)

**Context**: Need to select appropriate database technologies

**Decision**: PostgreSQL for transactional data, Redis for caching

**Rationale**:
- ACID compliance required for financial transactions
- JSON support needed for flexible schemas
- Performance requirements met with read replicas
- Redis provides sub-millisecond caching

**Consequences**:
- Higher operational complexity with multiple databases
- Need for data synchronization strategies
- Backup and recovery complexity
- Monitoring multiple database types

---

## Risk Assessment & Mitigation

### Technical Risks
| Risk | Probability | Impact | Mitigation Strategy |
|------|------------|--------|-------------------|
| Service cascade failures | Medium | High | Circuit breakers, bulkheads |
| Data consistency issues | Medium | High | Saga patterns, idempotency |
| Performance bottlenecks | High | Medium | Caching, load testing |
| Security vulnerabilities | Low | High | Security reviews, penetration testing |

### Operational Risks
| Risk | Probability | Impact | Mitigation Strategy |
|------|------------|--------|-------------------|
| Team skill gaps | Medium | Medium | Training, documentation |
| Vendor lock-in | Low | High | Multi-cloud strategy |
| Compliance violations | Low | High | Regular audits, automation |
| Scaling challenges | Medium | High | Auto-scaling, capacity planning |

---

## Quality Attributes

### Performance Metrics
- **Response Time**: P95 < 200ms, P99 < 500ms
- **Throughput**: 10,000 requests/second sustained
- **Resource Utilization**: CPU < 70%, Memory < 80%
- **Database Performance**: Query time < 50ms average

### Reliability Metrics
- **Availability**: 99.9% uptime (SLA target)
- **Error Rate**: < 0.1% of requests result in errors
- **Mean Time to Recovery**: < 15 minutes
- **Mean Time Between Failures**: > 30 days

### Scalability Metrics
- **Horizontal Scaling**: 0-100 instances in < 5 minutes
- **Data Growth**: Support 100TB+ with linear performance
- **User Growth**: Support 10x user increase with minimal changes
- **Geographic Scaling**: < 100ms latency globally

---

## Monitoring & Observability

### Monitoring Stack
```
                    ┌─────────────────┐
                    │   Grafana       │
                    │   Dashboards    │
                    └─────────┬───────┘
                              │
                    ┌─────────▼───────┐
                    │   Prometheus    │
                    │   Metrics       │
                    └─────────┬───────┘
                              │
        ┌─────────────────────┼─────────────────────┐
        │                     │                     │
┌───────▼──────┐    ┌────────▼────────┐    ┌──────▼──────┐
│   Service    │    │   Infrastructure│    │   Business  │
│   Metrics    │    │   Metrics       │    │   Metrics   │
└──────────────┘    └─────────────────┘    └─────────────┘
```

### Key Metrics
- **Application Metrics**: Request rate, response time, error rate
- **Infrastructure Metrics**: CPU, memory, disk, network usage
- **Business Metrics**: User engagement, conversion rates, revenue
- **Security Metrics**: Failed logins, suspicious activities, audit events

---

**Architecture Status:** 🏗️ Design Complete - Ready for Implementation

**Next Steps:**
1. Review architecture design with stakeholders
2. Validate technical decisions with development team
3. Begin Phase 1 infrastructure setup
4. Establish monitoring and development processes

ARCHDESIGN

echo "
✅ ARCHITECTURE DESIGN CREATED SUCCESSFULLY

🏗️ Design: $ARCH_DESIGN
🏛️ Type: [Detected Architecture Type]
📊 Status: Ready for Implementation

Architecture Highlights:
1. Comprehensive system design with clear boundaries
2. Technology stack optimized for requirements
3. Scalability and performance considerations
4. Security and compliance architecture
5. Implementation roadmap with phases

Generated Assets:
- Detailed architecture documentation
- Technology decision records (ADRs)
- Risk assessment and mitigation strategies
- Implementation roadmap and timeline

Next Actions:
1. Review architecture design for alignment
2. Validate technical decisions with team
3. Begin infrastructure setup and development
4. Establish monitoring and quality processes
5. Execute implementation phases systematically

Would you like to:
[R]eview specific architecture components
[T]echnology stack validation
[I]mplementation planning
[S]ecurity architecture deep dive
[P]erformance optimization
[Q]uit

Enter choice: "
```

## Quick Architecture Commands

### System Design
```bash
# Design new system architecture
if [[ "$ARGUMENTS" =~ "design" ]] || [[ "$ARGUMENTS" =~ "system" ]]; then
  echo "🏗️ SYSTEM ARCHITECTURE DESIGN"
  echo ""
  echo "I'll help you design a comprehensive system architecture..."
  echo ""
  echo "Design areas:"
  echo "- Overall system structure and components"
  echo "- Technology stack selection and rationale"
  echo "- Data flow and integration patterns"
  echo "- Scalability and performance considerations"
fi

# Microservices architecture
if [[ "$ARGUMENTS" =~ "microservice" ]]; then
  echo "🔧 MICROSERVICES ARCHITECTURE"
  echo ""
  echo "Designing microservices architecture..."
  echo ""
  echo "Key considerations:"
  echo "- Service boundary identification"
  echo "- Communication patterns (sync/async)"
  echo "- Data consistency strategies"
  echo "- Deployment and orchestration"
fi

# Database architecture
if [[ "$ARGUMENTS" =~ "database" ]] || [[ "$ARGUMENTS" =~ "data" ]]; then
  echo "🗄️ DATABASE ARCHITECTURE"
  echo ""
  echo "Designing data architecture and storage strategy..."
  echo ""
  echo "Architecture components:"
  echo "- Database technology selection"
  echo "- Data modeling and schema design"
  echo "- Caching and performance optimization"
  echo "- Backup and disaster recovery"
fi

# Cloud architecture
if [[ "$ARGUMENTS" =~ "cloud" ]]; then
  echo "☁️ CLOUD ARCHITECTURE"
  echo ""
  echo "Designing cloud-native architecture..."
  echo ""
  echo "Cloud considerations:"
  echo "- Cloud provider selection and services"
  echo "- Containerization and orchestration"
  echo "- Auto-scaling and load balancing"
  echo "- Cost optimization strategies"
fi

# Security architecture
if [[ "$ARGUMENTS" =~ "security" ]]; then
  echo "🔒 SECURITY ARCHITECTURE"
  echo ""
  echo "Designing comprehensive security architecture..."
  echo ""
  echo "Security layers:"
  echo "- Authentication and authorization"
  echo "- Data protection and encryption"
  echo "- Network security and firewalls"
  echo "- Compliance and audit requirements"
fi
```

## Architecture Patterns & Solutions

### Common Patterns
- **Microservices**: Service decomposition and communication
- **Event-Driven**: Asynchronous processing and event sourcing
- **CQRS**: Command Query Responsibility Segregation
- **API Gateway**: Centralized API management and security

### Cloud Patterns
- **Serverless**: Function-as-a-Service architectures
- **Container Orchestration**: Kubernetes deployment patterns
- **Multi-Cloud**: Vendor-agnostic cloud strategies
- **Edge Computing**: Geographic distribution patterns

### Data Patterns
- **Database per Service**: Microservices data isolation
- **Event Sourcing**: Audit trail and replay capabilities
- **Data Lake**: Big data analytics architectures
- **Real-time Processing**: Stream processing patterns

## Integration with Gosu Commands

### With gosu:spec
- Translate requirements into architecture decisions
- Validate architectural compliance with specifications
- Generate technical requirements from business needs

### With gosu:plan
- Create implementation roadmaps from architecture designs
- Break down architecture into development tasks
- Estimate effort and timeline for architectural components

### With gosu:security
- Implement security architecture recommendations
- Validate security compliance in architectural decisions
- Generate security testing scenarios

### With gosu:test
- Create architectural testing strategies
- Design integration and system testing approaches
- Validate non-functional requirements

### With gosu:docs
- Generate architecture documentation and diagrams
- Create technical decision records (ADRs)
- Maintain architectural knowledge base

## Advanced Architecture Features

### AI-Powered Architecture Analysis
- Pattern recognition in existing systems
- Automated technology recommendation
- Performance optimization suggestions
- Cost-benefit analysis of architectural decisions

### Architecture Validation
- Trade-off analysis and recommendations
- Compliance checking against best practices
- Performance impact assessment
- Security vulnerability analysis

### Evolution Planning
- Migration strategy development
- Legacy system modernization
- Incremental architecture improvement
- Technology debt management

## Quality Assurance Standards

Before completing architecture design, I ensure:

- ✓ Requirements alignment and traceability
- ✓ Technology decisions justified and documented
- ✓ Scalability and performance considerations addressed
- ✓ Security and compliance requirements met
- ✓ Risk assessment and mitigation strategies defined
- ✓ Implementation roadmap with realistic timelines
- ✓ Monitoring and observability planned
- ✓ Cost optimization and efficiency considered

The `gosu:architect` command provides comprehensive system architecture design that balances technical excellence with business requirements, ensuring scalable, maintainable, and robust software systems that support long-term success.