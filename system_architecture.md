# AI Development System Architecture

## System Overview

This is a system designed to use LLM powered IDEs to write code. The main focus of this system is to provide relevant context and information to agents(powered by LLM), so it can write high quality code.

In addition, the processes below will also be powered by agents:

- The organization and update of knowledge(relevant context, information and references)
- Requirements/instructions refinement, so that the coding agent effectively understand the user's requirements

1. **Requirements Agent**: Refines raw instructions into clear specifications
2. **Knowledge agent**: Organizes and maintains project knowledge
3. **Coding agent**: Implements code based on requirements and knowledge

## Agent Roles and Boundaries

### Requirements Agent

- **Purpose**: Pre-process development instructions to save tokens and reduce confusion
- **Reads**:
  - `.ai_dev/requirements/raw_requirements.md`
  - `.ai_dev/knowledge_base/`
- **Writes**:
  - `.ai_dev/requirements/refined_requirements.md`
- **Boundaries**: Clarifies WHAT and WHY, never HOW to implement

### Knowledge agent  

- **Purpose**: Transform raw notes into organized, accessible knowledge
- **Reads**:
  - `.ai_dev/raw_knowledge/`
- **Writes**:
  - `.ai_dev/knowledge_base/`
- **Boundaries**: Organizes information, never makes coding decisions

### Coding agent

- **Purpose**: Write and modify code based on clear requirements
- **Reads**:
  - `.ai_dev/requirements/refined_requirements.md`
  - `.ai_dev/memory_bank/`
  - `.ai_dev/knowledge_base/`
- **Writes**:
  - Project code
  - `.ai_dev/memory_bank/`
  - `.ai_dev/knowledge_base/`
- **Boundaries**: Makes all technical decisions

## Workflow Patterns

### Pattern A: Feature Development

```text
You write raw instructions → Requirements Agent refines → Coding agent implements
```

### Pattern B: Knowledge Capture  

```text
You write raw notes → Knowledge agent organizes → Available for all agents
```

## Directory Structure

```text
.ai_dev/
├── memory_bank/          # Coding agent's working memory
│   ├── project_brief.md         # Core project definition
│   ├── product_context.md
│   ├── active_context.md
│   ├── system_patterns.md
│   ├── tech_context.md
│   └── progress.md
├── requirements/
│   ├── raw_requirements.md      # Your rough development instructions/requirements
│   └── refined_requirements.md  # Requirements Agent's refined output
├── raw_knowledge/ 
│   ├── raw_notes/               # Your knowledge scratchpad, which are to be refined
│   └── raw_resources/           # PDFs, docs, external resources
├── knowledge_base/              # Organized project knowledge
│   ├── index.md                 # Knowledge base index, which is going to be used by the Coding agent to find relevant knowledge
│   ├── technical/               # Libraries, tools, patterns
│   ├── domain/                  # Business logic, requirements
│   ├── decisions/               # Architectural decisions, rationale
│   └── patterns/                # Reusable solutions
└── system_architecture.md
```

## Inter-Agent Communication

- Agents do NOT directly communicate
- Agents communicate through files in `.ai_dev/`
- Each agent respects others' file boundaries
- When users need a different agent, current agent should direct them appropriately

## Key Principles

1. **Separation of Concerns**: Each agent has a specific role
2. **Knowledge Persistence**: System maintains context across sessions
3. **Progressive Enhancement**: Start simple, system grows with your project

Remember: Let each agent do what it does best. Don't ask Requirements Agent to code or Coding agent to organize notes.
