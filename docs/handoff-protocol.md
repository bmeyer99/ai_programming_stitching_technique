# ASPT Multi-Agent Handoff Protocol

The ASPT Multi-Agent Handoff Protocol standardizes information exchange between AI agents during collaborative code development. This protocol ensures consistent context preservation, clear requirements understanding, and appropriate review criteria application.

## 1. Protocol Structure

Every handoff between agents must include the following components:

### 1.1 Context Package

```json
{
  "project": {
    "name": "String - Project identifier",
    "description": "String - Brief project description",
    "implementation_level": "String - MVP | PROTOTYPE | PRODUCTION | ENTERPRISE",
    "version": "String - Version number",
    "domain": "String - Application domain (e.g., FINTECH, HEALTHCARE)",
    "repository": "String - Repository location"
  },
  "documentation": {
    "prd_link": "String - Link/path to PRD",
    "prd_summary": "String - Key PRD points relevant to this component",
    "spec_link": "String - Link/path to technical specification",
    "additional_docs": [
      {
        "title": "String - Document title",
        "link": "String - Link/path to document",
        "relevance": "String - Why this document matters for this component"
      }
    ]
  },
  "organization_requirements": {
    "coding_standards": "String - Link to standards document",
    "custom_patterns": [
      {
        "name": "String - Pattern name",
        "description": "String - Pattern description",
        "example": "String - Example of pattern usage"
      }
    ],
    "required_wrappers": [
      {
        "name": "String - Wrapper name",
        "purpose": "String - Why this wrapper is required",
        "usage": "String - How to use this wrapper"
      }
    ]
  }
}
```

### 1.2 Component Specification

```json
{
  "component": {
    "name": "String - Component name",
    "purpose": "String - What this component does",
    "dependencies": [
      {
        "name": "String - Dependency name",
        "type": "String - INTERNAL | EXTERNAL | THIRD_PARTY",
        "version": "String - Version requirement"
      }
    ]
  },
  "interfaces": {
    "inputs": [
      {
        "name": "String - Input name",
        "type": "String - Data type",
        "constraints": "String - Validation rules",
        "example": "String - Example valid input"
      }
    ],
    "outputs": [
      {
        "name": "String - Output name",
        "type": "String - Data type",
        "example": "String - Example output"
      }
    ],
    "exceptions": [
      {
        "name": "String - Exception name",
        "trigger": "String - What causes this exception",
        "handling": "String - How it should be handled"
      }
    ]
  },
  "expected_behavior": {
    "normal_path": "String - Description of expected normal operation",
    "edge_cases": [
      {
        "scenario": "String - Edge case description",
        "handling": "String - How it should be handled"
      }
    ],
    "performance_requirements": "String - Any performance constraints"
  }
}
```

### 1.3 Development State

```json
{
  "code_state": {
    "completion_status": "String - PLANNING | IN_PROGRESS | READY_FOR_REVIEW",
    "implementation_approach": "String - Description of implementation strategy",
    "known_issues": [
      {
        "description": "String - Issue description",
        "location": "String - Where in code",
        "priority": "String - HIGH | MEDIUM | LOW"
      }
    ]
  },
  "review_history": [
    {
      "type": "String - SHALLOW | MEDIUM | DEEP",
      "agent": "String - Agent identifier",
      "timestamp": "String - ISO timestamp",
      "findings": [
        {
          "description": "String - Finding description",
          "location": "String - Where in code",
          "status": "String - OPEN | ADDRESSED | DEFERRED"
        }
      ],
      "summary": "String - Overall review summary"
    }
  ],
  "current_focus": "String - What the receiving agent should focus on"
}
```

## 2. Implementation Level Requirements

The `implementation_level` field determines appropriate review criteria:

### 2.1 MVP Level
- **Purpose**: Validate core functionality concepts quickly
- **Shallow Stitch Focus**: Basic syntax, core functionality, critical logic paths
- **Medium Stitch Focus**: Primary user flows, minimal error handling
- **Deep Stitch Focus**: Core architecture only, basic integration tests
- **What to Skip**: Comprehensive error handling, performance optimization, extensive documentation

### 2.2 Prototype Level
- **Purpose**: Demonstrate functionality with reasonable robustness
- **Shallow Stitch Focus**: Syntax, style consistency, function documentation
- **Medium Stitch Focus**: Main user flows, basic error handling, input validation
- **Deep Stitch Focus**: Component integration, basic performance considerations
- **What to Skip**: Enterprise security, comprehensive logging, full optimization

### 2.3 Production Level
- **Purpose**: Deliver reliable, maintainable software for actual use
- **Shallow Stitch Focus**: Complete style adherence, comprehensive documentation
- **Medium Stitch Focus**: Full error handling, all edge cases, comprehensive testing
- **Deep Stitch Focus**: Security, performance, scalability, deployment considerations
- **What to Skip**: Advanced optimization, enterprise-specific integrations

### 2.4 Enterprise Level
- **Purpose**: Deliver mission-critical system components
- **Shallow Stitch Focus**: Full compliance with all organizational standards
- **Medium Stitch Focus**: Comprehensive error management, observability, telemetry
- **Deep Stitch Focus**: Security compliance, disaster recovery, SLA requirements
- **What to Skip**: Nothing - all enterprise requirements must be addressed

## 3. Review Cycle Specification

Each stitch type should follow specific protocols during multi-agent handoffs:

### 3.1 Shallow Stitch Checklist

Basic checklist applicable to all implementation levels:

- **Syntax**: Is the code syntactically correct?
- **Style**: Does it follow project style guidelines?
- **Naming**: Are variables/functions named consistently and descriptively?
- **Documentation**: Are functions/classes documented appropriately for the implementation level?
- **Basic Logic**: Does the code implement the expected behavior?

Implementation-level specific additions (examples):
- **MVP**: Is core functionality working?
- **Enterprise**: Does all code follow security best practices?

### 3.2 Medium Stitch Checklist

Basic checklist applicable to all implementation levels:

- **Error Handling**: Are errors handled appropriately for the implementation level?
- **Edge Cases**: Are identified edge cases handled?
- **Input Validation**: Is input properly validated?
- **Testing**: Are appropriate tests in place for the implementation level?
- **Function Contracts**: Do functions adhere to their documented behavior?

Implementation-level specific additions (examples):
- **MVP**: Are primary user flows functional?
- **Enterprise**: Is there proper audit logging of all operations?

### 3.3 Deep Stitch Checklist

Basic checklist applicable to all implementation levels:

- **Component Integration**: Does the component integrate correctly with dependencies?
- **Architecture**: Does the implementation follow the project architecture?
- **System Requirements**: Does it meet performance/security needs for its level?
- **System Testing**: Are integration/system tests in place as appropriate?
- **Technical Debt**: Has any intentional technical debt been documented?

Implementation-level specific additions (examples):
- **MVP**: Does the overall approach validate the core concept?
- **Enterprise**: Does it meet all compliance requirements?

## 4. Custom Review Extensions

Organizations can extend review criteria with custom checks:

```json
{
  "custom_review_criteria": {
    "shallow": [
      {
        "name": "String - Check name",
        "description": "String - What to check for",
        "applicable_levels": ["MVP", "PROTOTYPE", "PRODUCTION", "ENTERPRISE"],
        "example": "String - Example of passing/failing code"
      }
    ],
    "medium": [
      {
        "name": "String - Check name",
        "description": "String - What to check for",
        "applicable_levels": ["MVP", "PROTOTYPE", "PRODUCTION", "ENTERPRISE"],
        "example": "String - Example of passing/failing code"
      }
    ],
    "deep": [
      {
        "name": "String - Check name",
        "description": "String - What to check for",
        "applicable_levels": ["MVP", "PROTOTYPE", "PRODUCTION", "ENTERPRISE"],
        "example": "String - Example of passing/failing code"
      }
    ]
  }
}
```

## 5. Handoff Process Flow

1. **Packaging**: Generating agent prepares handoff package
2. **Transmission**: Package is transferred to reviewing agent
3. **Context Loading**: Reviewing agent processes context information
4. **Review Execution**: Appropriate review type is performed
5. **Finding Documentation**: Review findings are documented
6. **Return Handoff**: Package with review findings returned to originating agent

## 6. Example Handoff Scenario

**Scenario**: Agent A has implemented a user authentication service and passes it to Agent B for a Medium Stitch review at Production implementation level.

**Handoff Package Excerpt**:
```json
{
  "project": {
    "name": "SecurityHub",
    "implementation_level": "PRODUCTION",
    "domain": "FINTECH"
  },
  "component": {
    "name": "UserAuthenticationService",
    "purpose": "Handles user authentication with multi-factor support"
  },
  "expected_behavior": {
    "normal_path": "User provides credentials, system validates and returns token",
    "edge_cases": [
      {
        "scenario": "Account locked after 5 failed attempts",
        "handling": "Return LockoutError with retry timeframe"
      }
    ]
  },
  "code_state": {
    "completion_status": "READY_FOR_REVIEW",
    "current_focus": "Please verify all security best practices are followed"
  }
}
```

**Review Response Excerpt**:
```json
{
  "review_history": [
    {
      "type": "MEDIUM",
      "agent": "Agent-B",
      "timestamp": "2025-06-29T14:30:00Z",
      "findings": [
        {
          "description": "Password hash doesn't use sufficient iterations for Production level",
          "location": "authenticate() method - Line 42",
          "status": "OPEN"
        },
        {
          "description": "Missing rate limiting for authentication attempts",
          "location": "authenticate() method",
          "status": "OPEN"
        }
      ],
      "summary": "Core functionality works correctly, but security hardening needed for Production level"
    }
  ]
}
```

By following this protocol, AI agents can effectively collaborate on code development with clear understanding of requirements, implementation level, and appropriate review criteria.

[Back to README](../README.md)
