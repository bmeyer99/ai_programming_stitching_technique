# ASPT Specification

This document details the core specifications of the AI Stitching Programming Technique.

## Checkpoint Triggers

Review cycles are initiated at specific checkpoints:

| Trigger Type | Description | Example |
|--------------|-------------|---------|
| **Component Completion** | After completing a functional unit | Finishing a class or function |
| **Line Count** | After generating a specific number of lines | Every 50-100 lines of code |
| **Complexity Threshold** | After implementing complex logic | After writing nested conditionals |
| **Integration Point** | Before connecting to dependent components | Before API integration |
| **Time-Based** | After a set duration of continuous generation | Every 5 minutes |
| **User-Initiated** | When explicitly requested | User commands review |

## Review Cycle Types

ASPT defines three levels of review depth:

### 1. Shallow Stitch (SS)
- **Focus**: Syntax, style, and basic correctness
- **Frequency**: High (multiple times per component)
- **Checks**:
  - Syntax validity
  - Style consistency
  - Variable naming conventions
  - Documentation completeness
  - Basic logical flow

### 2. Medium Stitch (MS)
- **Focus**: Logical correctness and robustness
- **Frequency**: Medium (once per component)
- **Checks**:
  - Edge case handling
  - Error management
  - Input validation
  - Return value consistency
  - Function contract adherence
  - Unit test coverage

### 3. Deep Stitch (DS)
- **Focus**: Architecture and system integration
- **Frequency**: Low (at major milestones)
- **Checks**:
  - Component integration
  - Architectural pattern consistency
  - Performance considerations
  - Security implications
  - Scalability concerns
  - Global state management
  - System-level test coverage

## Implementation Methods

ASPT can be implemented through several approaches:

### 1. Prompt Engineering
Structured instructions that require AI to follow the stitching pattern, applicable to current LLM systems without modification.

### 2. Orchestration Layer
A wrapper system that manages the AI's code generation process, enforcing review cycles and maintaining context.

### 3. Model Fine-tuning
Training AI models to inherently perform cyclic reviews as part of their generation process.

### 4. Plugin/Extension Systems
Integrations with existing IDE or coding platforms that trigger and manage review cycles.

## Operational Flow

The basic ASPT operational flow follows this pattern:

```
1. PLAN: Define component requirements and acceptance criteria
2. GENERATE: Create initial component/section (50-100 lines)
3. SHALLOW STITCH: Perform syntax and style review
4. REFINE: Address issues found in review
5. GENERATE: Continue with next section
6. SHALLOW STITCH: Review new code
7. MEDIUM STITCH: Review component as a whole
8. REFINE: Address issues found in reviews
9. GENERATE: Begin next component with dependency awareness
10. SHALLOW STITCH: Review new component
11. MEDIUM STITCH: Review new component
12. DEEP STITCH: Review system integration
...and so on
```

The diagram at the top of the README illustrates this cyclical process, where each generation phase is followed by increasingly comprehensive review cycles before moving forward.

[Back to README](../README.md)
