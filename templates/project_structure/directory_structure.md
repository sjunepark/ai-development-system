# AI Workflow Directory Structure Template

This is the directory structure you need to create in your project:

```text
.ai_workflow/
├── system_architecture.md       # Copy from llm-ide-dev/workflow/
├── agent_instructions/          # Full agent instructions
│   ├── development_agent_core.md
│   ├── development_agent_memory_bank.md
│   ├── development_agent_workflows.md
│   ├── knowledge_manager_instructions.md
│   └── requirements_agent_instructions.md
├── requirements/
│   ├── raw_instructions.md     # User writes rough ideas here
│   └── current_requirements.md # Requirements Agent outputs here
├── raw_notes/                  # User drops unorganized notes here
├── raw_resources/              # User drops PDFs/docs here
├── memory_bank/                # Development Agent's working memory
│   ├── projectbrief.md        # Initialize with project description
│   ├── productContext.md
│   ├── activeContext.md
│   ├── systemPatterns.md
│   ├── techContext.md
│   ├── progress.md
│   └── context_routing.md
└── knowledge_base/             # Knowledge Manager organizes here
    ├── technical/
    ├── domain/
    ├── decisions/
    ├── patterns/
    └── index.md
```

## Initial Files to Create

### 1. projectbrief.md

Create this file in `.ai_workflow/memory_bank/` with:

- Project name and purpose
- Core goals and requirements
- Key constraints or considerations

### 2. raw_instructions.md  

Create empty file in `.ai_workflow/requirements/` for user input

### 3. index.md

Create in `.ai_workflow/knowledge_base/` with:

```markdown
# Knowledge Base Index

## Technical
- (Files will be added by Knowledge Manager)

## Domain
- (Files will be added by Knowledge Manager)

## Decisions
- (Files will be added by Knowledge Manager)

## Patterns
- (Files will be added by Knowledge Manager)
```
