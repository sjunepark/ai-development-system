# AI Development System Architecture

## System Overview

This is a three-agent AI development system designed to transform rough ideas into production code efficiently:

1. **Requirements Agent**: Refines raw instructions into clear specifications
2. **Knowledge Manager**: Organizes and maintains project knowledge
3. **Development Agent**: Implements code based on requirements and knowledge

## Agent Roles and Boundaries

### Requirements Agent

- **Purpose**: Pre-process development instructions to save tokens and reduce confusion
- **Reads**: `.ai_workflow/requirements/raw_instructions.md`, knowledge base
- **Writes**: `.ai_workflow/requirements/current_requirements.md`
- **Boundaries**: Clarifies WHAT and WHY, never HOW to implement

### Knowledge Manager  

- **Purpose**: Transform raw notes into organized, accessible knowledge
- **Reads**: `.ai_workflow/raw_notes/`, `.ai_workflow/raw_resources/`
- **Writes**: `.ai_workflow/knowledge_base/`, memory bank updates
- **Boundaries**: Organizes information, never makes coding decisions

### Development Agent

- **Purpose**: Write and modify code based on clear requirements
- **Reads**: Requirements, memory bank, knowledge base (as directed)
- **Writes**: Project code, memory bank updates
- **Boundaries**: Makes all technical decisions, never organizes knowledge

## Workflow Patterns

### Pattern A: Feature Development

```markdown
You write raw instructions → Requirements Agent refines → Development Agent implements
```

### Pattern B: Knowledge Capture  

```markdown
You write raw notes → Knowledge Manager organizes → Available for all agents
```

## Directory Structure

```markdown
.ai_workflow/
├── requirements/
│   ├── raw_instructions.md      # Your rough development ideas
│   └── current_requirements.md  # Requirements Agent's refined output
├── raw_notes/                   # Your knowledge dumps
├── raw_resources/               # PDFs, docs, external resources  
├── memory_bank/                 # Development Agent's working memory
│   ├── projectbrief.md         # Core project definition
│   ├── context_routing.md      # Maps tasks to knowledge base
│   └── [other context files]
└── knowledge_base/              # Organized project knowledge
    ├── technical/              # Libraries, tools, patterns
    ├── domain/                 # Business logic, requirements
    ├── decisions/              # Architectural decisions, rationale
    └── patterns/               # Reusable solutions
```

## Inter-Agent Communication

- Agents do NOT directly communicate
- Agents communicate through files in `.ai_workflow/`
- Each agent respects others' file boundaries
- When users need a different agent, current agent should direct them appropriately

## Quick Start for Humans

### 1. Setup Agents

**Requirements Agent & Knowledge Manager**: Create separate Claude Projects (or equivalent) with respective instruction files as project instructions.

**Development Agent**: Add the three development agent rule files to your IDE's workspace rules:

- `development_agent_core.md` - Core identity and information system
- `development_agent_memory_bank.md` - Memory bank structure and files
- `development_agent_workflows.md` - Workflow processes and guidelines

> **Note:** The development agent files (`development_agent_core.md`, `development_agent_memory_bank.md`, `development_agent_workflows.md`), along with `knowledge_manager_instructions.md` and `requirements_agent_instructions.md`, should be added to your agent system as rules, agent descriptions, or project instructions, depending on the terminology of your platform. For example, Claude projects use the term "project instructions." Make sure to match the naming and import method to your specific agent system or IDE.

### 2. Create Folder Structure

```bash
mkdir -p .ai_workflow/{requirements,raw_notes,raw_resources,memory_bank}
mkdir -p .ai_workflow/knowledge_base/{technical,domain,decisions,patterns}
```

### 3. Initialize Core Files

Create `.ai_workflow/memory_bank/projectbrief.md` with your project's core purpose and goals.

### 4. Use the System

**For new features**: Write in `raw_instructions.md` → Ask Requirements Agent to refine → Tell Development Agent to implement

**For knowledge**: Drop notes in `raw_notes/` → Ask Knowledge Manager to process

**For coding**: Tell Development Agent your task (it will check for requirements first)

## Key Principles

1. **Separation of Concerns**: Each agent has a specific role
2. **Token Efficiency**: Requirements Agent prevents expensive back-and-forth
3. **Knowledge Persistence**: System maintains context across sessions
4. **Progressive Enhancement**: Start simple, system grows with your project

Remember: Let each agent do what it does best. Don't ask Requirements Agent to code or Development Agent to organize notes.
