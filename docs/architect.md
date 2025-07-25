# gosu:architect - System Architecture Design & Technical Decision Guidance

Act as a professional solution architect, technical architect, and enterprise architect to design robust system architectures, make informed technical decisions, and provide scalable solutions for complex software systems.

## Overview

The `gosu:architect` command provides comprehensive system architecture design and technical decision-making guidance that ensures scalable, maintainable, and robust software systems. This command acts as your virtual architecture team to guide complex system design.

## Usage

```bash
# Interactive mode - comprehensive architecture session
claude gosu:architect

# Design system architecture
claude gosu:architect "design microservices architecture"

# Technology stack selection
claude gosu:architect "evaluate technology stack"

# Architecture review and validation
claude gosu:architect "review current architecture"

# Scalability planning
claude gosu:architect "design for scale"

# Integration architecture
claude gosu:architect "design API integration"
```

## Key Features

### 1. Professional Architecture Team Approach

Claude Code acts as your virtual architecture team:

- **Solution Architect**: Designing overall system architecture and technology selection
- **Technical Architect**: Providing implementation guidance and best practices
- **Enterprise Architect**: Ensuring scalability, integration, and long-term viability

### 2. Comprehensive Architecture Design

#### System Architecture Patterns
- **Microservices**: Service decomposition and communication patterns
- **Monolithic**: Modular monolith design and organization
- **Event-Driven**: Asynchronous processing and event sourcing
- **Serverless**: Function-as-a-Service architecture design

#### Technology Stack Evaluation
- **Programming Languages**: Analysis and selection based on requirements
- **Frameworks**: Evaluation of web, mobile, and backend frameworks
- **Databases**: SQL, NoSQL, and hybrid database strategies
- **Infrastructure**: Cloud, containerization, and deployment strategies

#### Integration Architecture
- **API Design**: RESTful, GraphQL, and gRPC API strategies
- **Message Queues**: Asynchronous communication patterns
- **Service Mesh**: Microservices communication and security
- **External Integrations**: Third-party service integration patterns

### 3. Architecture Decision Making

#### Technology Decision Records (ADRs)
- **Decision Documentation**: Systematic recording of architectural decisions
- **Trade-off Analysis**: Detailed analysis of alternatives and rationale
- **Impact Assessment**: Understanding consequences of architectural choices
- **Evolution Planning**: Planning for future architectural changes

#### Risk Assessment
- **Technical Risks**: Identification and mitigation of technical risks
- **Scalability Risks**: Planning for growth and performance challenges
- **Security Risks**: Architecture-level security considerations
- **Operational Risks**: Deployment, monitoring, and maintenance challenges

### 4. Scalability and Performance Design

#### Scalability Patterns
- **Horizontal Scaling**: Auto-scaling and load distribution strategies
- **Vertical Scaling**: Resource optimization and performance tuning
- **Geographic Distribution**: Global deployment and CDN strategies
- **Data Partitioning**: Sharding and data distribution patterns

#### Performance Optimization
- **Caching Strategies**: Multi-level caching and cache invalidation
- **Database Optimization**: Query optimization and index strategies
- **Resource Management**: Memory, CPU, and I/O optimization
- **Network Optimization**: Latency reduction and bandwidth optimization

## Architecture Process

### Phase 1: Requirements Analysis
1. **Business Requirements**: Understanding business goals and constraints
2. **Functional Requirements**: System capabilities and feature requirements
3. **Non-Functional Requirements**: Performance, scalability, security requirements
4. **Constraints Analysis**: Technical, budget, and timeline constraints

### Phase 2: Architecture Design
1. **System Decomposition**: Breaking down the system into manageable components
2. **Technology Selection**: Choosing appropriate technologies and frameworks
3. **Integration Design**: Designing component interactions and data flow
4. **Security Architecture**: Implementing comprehensive security measures

### Phase 3: Documentation and Validation
1. **Architecture Documentation**: Comprehensive documentation of design decisions
2. **Prototype Development**: Proof-of-concept implementations
3. **Review and Validation**: Stakeholder review and technical validation
4. **Implementation Planning**: Roadmap for architecture implementation

### Phase 4: Evolution and Maintenance
1. **Architecture Monitoring**: Tracking architecture health and performance
2. **Evolution Planning**: Planning for architectural changes and improvements
3. **Technology Updates**: Managing technology upgrades and migrations
4. **Knowledge Transfer**: Ensuring team understanding and capabilities

## Architecture Patterns and Solutions

### Cloud Architecture Patterns
- **Multi-Cloud**: Vendor-agnostic cloud strategies
- **Hybrid Cloud**: On-premise and cloud integration
- **Cloud-Native**: Containerization and orchestration
- **Edge Computing**: Geographic distribution and edge processing

### Data Architecture Patterns
- **Database per Service**: Microservices data isolation
- **Event Sourcing**: Audit trail and event replay capabilities
- **CQRS**: Command Query Responsibility Segregation
- **Data Lake**: Big data analytics and processing

### Security Architecture Patterns
- **Zero Trust**: Security model and implementation
- **Defense in Depth**: Layered security approach
- **API Security**: Authentication, authorization, and rate limiting
- **Data Protection**: Encryption and privacy compliance

### Integration Patterns
- **API Gateway**: Centralized API management
- **Service Mesh**: Microservices communication
- **Event Bus**: Event-driven architecture
- **Circuit Breaker**: Resilience and fault tolerance

## Output Format

The command creates comprehensive architecture designs in `.gosu/architect-YYYYMMDD_HHMMSS.md` format with:

- **Architecture Overview**: System context, stakeholders, and high-level design
- **Detailed Design**: Component architecture, technology stack, and integration patterns
- **Technology Decision Records**: Documented architectural decisions with rationale
- **Implementation Roadmap**: Phased approach with milestones and dependencies
- **Risk Assessment**: Technical risks and mitigation strategies
- **Quality Attributes**: Performance, scalability, security, and reliability considerations

## Integration with Other Commands

### With gosu:spec
- **Requirements Alignment**: Ensure architecture meets specified requirements
- **Traceability**: Maintain links between requirements and architectural decisions
- **Stakeholder Communication**: Translate technical architecture to business value

### With gosu:plan
- **Implementation Planning**: Break down architecture into development tasks
- **Timeline Estimation**: Estimate implementation effort and dependencies
- **Resource Planning**: Identify required skills and team structure

### With gosu:security
- **Security Architecture**: Implement comprehensive security measures
- **Threat Modeling**: Identify and mitigate security risks
- **Compliance**: Ensure architecture meets security and compliance requirements

### With gosu:test
- **Testing Strategy**: Design testing approaches for complex architectures
- **Performance Testing**: Validate non-functional requirements
- **Integration Testing**: Test component interactions and interfaces

### With gosu:docs
- **Architecture Documentation**: Generate comprehensive system documentation
- **Decision Records**: Document and maintain architectural decisions
- **Knowledge Management**: Ensure architectural knowledge is preserved

## Advanced Features

### AI-Powered Architecture Analysis
- **Pattern Recognition**: Identify optimal patterns for specific requirements
- **Technology Recommendation**: AI-driven technology selection based on context
- **Performance Prediction**: Model performance characteristics of architectural choices
- **Cost Optimization**: Analyze cost implications of architectural decisions

### Architecture Validation
- **Trade-off Analysis**: Systematic analysis of architectural alternatives
- **Compliance Checking**: Validate against architectural standards and best practices
- **Performance Modeling**: Predict system performance under various loads
- **Security Assessment**: Evaluate security posture of architectural designs

### Evolution and Migration
- **Legacy Modernization**: Strategies for modernizing existing systems
- **Migration Planning**: Phased migration approaches with minimal disruption
- **Technology Debt**: Identify and plan resolution of architectural technical debt
- **Continuous Architecture**: Evolutionary architecture principles and practices

## Best Practices

### When to Use gosu:architect

- **New system design**: Comprehensive architecture for new projects
- **Technology migration**: Planning migration to new technologies or platforms
- **Scalability planning**: Designing for significant growth and scale
- **Integration projects**: Complex system integration and API design
- **Architecture review**: Validation and improvement of existing architectures

### Architecture Workflow Integration

```bash
# Complete architecture workflow
claude gosu:architect "analyze requirements"     # Requirements analysis
claude gosu:architect "design system"           # Architecture design
claude gosu:architect "validate design"         # Review and validation
claude gosu:plan "implementation roadmap"       # Implementation planning
```

### Quality Assurance Standards

Before completing architecture design:

- ✓ Requirements alignment verified and documented
- ✓ Technology decisions justified with clear rationale
- ✓ Scalability and performance requirements addressed
- ✓ Security and compliance considerations implemented
- ✓ Risk assessment completed with mitigation strategies
- ✓ Implementation roadmap realistic and achievable
- ✓ Monitoring and observability planned and designed
- ✓ Cost optimization and efficiency considered

## Benefits for Agentic Development

The `gosu:architect` command is crucial for agentic development because it:

1. **Provides Direction**: Clear architectural guidance for AI agent development efforts
2. **Ensures Scalability**: Designs that can handle growth and complexity
3. **Manages Complexity**: Breaks down complex systems into manageable components
4. **Enables Innovation**: Provides framework for exploring new technologies safely
5. **Reduces Risk**: Systematic risk assessment and mitigation planning
6. **Supports Evolution**: Architectural patterns that support continuous improvement

## Architecture Documentation and Communication

### Visual Documentation
- **System Diagrams**: High-level system architecture visualization
- **Component Diagrams**: Detailed component relationships and interfaces
- **Deployment Diagrams**: Infrastructure and deployment architecture
- **Data Flow Diagrams**: Information flow and processing visualization

### Technical Communication
- **Architecture Decision Records**: Systematic decision documentation
- **Trade-off Analysis**: Detailed comparison of architectural alternatives
- **Implementation Guides**: Technical guidance for development teams
- **Integration Specifications**: Detailed interface and integration documentation

The command transforms architecture design from an ad-hoc process into a systematic, well-documented, and validated approach that provides solid foundations for complex software systems and enables confident development by both human developers and AI agents.