# AI Stitching Programming Technique (ASPT)

<div align="center">
  
*A cyclical review methodology for AI code generation*

![Version](https://img.shields.io/badge/Version-1.0.0-blue)
![Status](https://img.shields.io/badge/Status-Draft-orange)
![License](https://img.shields.io/badge/License-MIT-green)
![ASPT](https://img.shields.io/badge/ASPT-v1.0-purple)

</div>

<!-- 
DIAGRAM: ASPT Cyclical Process
┌─────────────┐     ┌─────────────┐     ┌─────────────┐
│   GENERATE  │────>│  SHALLOW    │────>│   REFINE    │
│    CODE     │     │   STITCH    │     │             │
└─────────────┘     └─────────────┘     └──────┬──────┘
      ▲                                        │
      │                                        │
      │                                        │
┌─────┴───────┐     ┌─────────────┐     ┌─────▼──────┐
│  INTEGRATE  │<────│   DEEP      │<────│   MEDIUM   │
│             │     │   STITCH    │     │   STITCH   │
└─────────────┘     └─────────────┘     └─────────────┘
-->

## Introduction

The AI Stitching Programming Technique (ASPT) is a systematic methodology for improving AI-generated code through periodic review cycles. Inspired by the back-and-forth motion of hand stitching, ASPT requires AI coding agents to "stitch back" and review recently written code before proceeding to new functionality.

This iterative approach addresses the common problem where AI systems can effectively scaffold code structures but struggle with implementing complex logic consistently throughout a project.

<div align="center">
<i>
There's a clear gap between how expert human programmers work (iteratively with constant review) and how AI agents currently generate code (linearly with forward-only progression).
</i>
</div>

## Table of Contents

- [Overview](docs/overview.md)
  - [The Problem](docs/overview.md#the-problem)
  - [Core Principles](docs/overview.md#core-principles)
- [ASPT Specification](docs/specification.md)
  - [Checkpoint Triggers](docs/specification.md#checkpoint-triggers)
  - [Review Cycle Types](docs/specification.md#review-cycle-types)
  - [Implementation Methods](docs/specification.md#implementation-methods)
  - [Operational Flow](docs/specification.md#operational-flow)
- [Implementation Guide](docs/implementation.md)
  - [Prompt Engineering Approach](docs/implementation.md#prompt-engineering-approach)
  - [Orchestration Framework](docs/implementation.md#orchestration-framework)
  - [Model Fine-tuning Considerations](docs/implementation.md#model-fine-tuning-considerations)
  - [Integration with Development Methodologies](docs/implementation.md#integration-with-development-methodologies)
  - [Implementation Timeline](docs/implementation.md#implementation-timeline)
- [Evaluation Framework](docs/evaluation.md)
- [Advanced Features](docs/advanced-features.md)
  - [Multi-level Stitching](docs/advanced-features.md#1-multi-level-stitching)
  - [Adaptive Stitching](docs/advanced-features.md#2-adaptive-stitching)
  - [Collaborative Stitching](docs/advanced-features.md#3-collaborative-stitching)
  - [Contextual Memory](docs/advanced-features.md#4-contextual-memory)
  - [Domain-Specific Adaptations](docs/advanced-features.md#5-domain-specific-adaptations)
  - [Multi-Agent Coordination](docs/advanced-features.md#6-multi-agent-coordination)
  - [Learning and Adaptation](docs/advanced-features.md#7-learning-and-adaptation)
  - [Legacy Code Integration](docs/advanced-features.md#8-legacy-code-integration)
- [Multi-Agent Handoff Protocol](docs/handoff-protocol.md)
  - [Protocol Structure](docs/handoff-protocol.md#1-protocol-structure)
  - [Implementation Level Requirements](docs/handoff-protocol.md#2-implementation-level-requirements)
  - [Review Cycle Specification](docs/handoff-protocol.md#3-review-cycle-specification)
  - [Custom Review Extensions](docs/handoff-protocol.md#4-custom-review-extensions)
  - [Handoff Process Flow](docs/handoff-protocol.md#5-handoff-process-flow)
  - [Example Handoff Scenario](docs/handoff-protocol.md#6-example-handoff-scenario)
- [Example: ASPT in Action](docs/examples.md)
- [Benefits and Limitations](docs/benefits-limitations.md)
- [Contributing](docs/contributing.md)
- [Glossary](docs/glossary.md)
- [License](LICENSE)

## Quick Start

To quickly implement ASPT in your AI code generation workflow:

1. **For Prompt-Based Implementation**: Copy the [Prompt Engineering Template](docs/implementation.md#prompt-engineering-approach)
2. **For Multi-Agent Systems**: Review the [Handoff Protocol](docs/handoff-protocol.md)
3. **For Practical Examples**: See [ASPT in Action](docs/examples.md)

## Benefits Overview

Implementing ASPT provides numerous advantages:

1. **Improved Code Quality**: Catches issues before they propagate
2. **Enhanced Robustness**: Better coverage of edge cases and error conditions
3. **Greater Consistency**: Maintains uniform patterns throughout the codebase
4. **Better Documentation**: Ensures documentation keeps pace with implementation
5. **Reduced Technical Debt**: Identifies and addresses issues early
6. **More Complete Solutions**: Prevents the "scaffolding only" problem
7. **Closer to Human Process**: Better mimics experienced developers' workflow

See [Benefits and Limitations](docs/benefits-limitations.md) for a detailed analysis.

## License

This specification is released under the Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License (CC BY-NC-SA 4.0). This means you are free to share and adapt the material for non-commercial purposes, as long as you give appropriate credit, and distribute your contributions under the same license.

See the [LICENSE](LICENSE) file for details.

---

<div align="center">

*AI Stitching Programming Technique (ASPT) - Enabling more robust AI code generation through systematic review cycles*

</div>
