# Three-Agent Workflow Setup Guide

This guide helps you set up the three-agent AI development workflow in your project.

## Quick Setup Steps

### 1. Copy Core Files to Your Project

Copy these files from `llm-ide-dev/workflow/` to your project's `.ai_workflow/` directory:

```bash
# From llm-ide-dev root, assuming your project is at ../your-project/

# Copy system architecture
cp workflow/system_architecture.md ../your-project/.ai_workflow/

# Create agent instructions directory
mkdir -p ../your-project/.ai_workflow/agent_instructions/

# Copy all agent instructions
cp workflow/development_agent_*.md ../your-project/.ai_workflow/agent_instructions/
cp workflow/knowledge_manager_instructions.md ../your-project/.ai_workflow/agent_instructions/
cp workflow/requirements_agent_instructions.md ../your-project/.ai_workflow/agent_instructions/
```

### 2. Create Directory Structure

In your project root:

```bash
# Create all required directories
mkdir -p .ai_workflow/{requirements,raw_notes,raw_resources,memory_bank}
mkdir -p .ai_workflow/knowledge_base/{technical,domain,decisions,patterns}
```

### 3. Set Up Agent Instructions

**For IDEs (Windsurf, Cursor, etc.) - Development Agent:**

- Copy `templates/agent_instructions/development_agent_instructions.md` to your workspace rules
- This simple file tells the Development Agent to read its full instructions from the `.ai_workflow/agent_instructions/` directory

**For Separate AI Assistants (Claude Projects, etc.) - Requirements & Knowledge Agents:**

- Copy `templates/agent_instructions/requirements_agent_instructions.md` as project instructions
- Copy `templates/agent_instructions/knowledge_manager_instructions.md` as project instructions
- These simple files tell each agent to read their full instructions from the `.ai_workflow/agent_instructions/` directory

### 4. Initialize Core Files

Create `.ai_workflow/memory_bank/projectbrief.md`:

```markdown
# Project Brief

## Project Name
[Your project name]

## Purpose
[What this project does and why it exists]

## Core Requirements
- [Key requirement 1]
- [Key requirement 2]
- [Key requirement 3]

## Constraints
- [Technical constraints]
- [Business constraints]
- [Time constraints]
```

Create `.ai_workflow/requirements/raw_instructions.md` (empty file for user input)

Create `.ai_workflow/knowledge_base/index.md`:

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

## How to Use the Workflow

### For New Features

1. Write rough ideas in `.ai_workflow/requirements/raw_instructions.md`
2. Ask Requirements Agent to process them
3. Development Agent will find refined requirements in `current_requirements.md`

### For Knowledge Management

1. Drop notes in `.ai_workflow/raw_notes/`
2. Drop PDFs/docs in `.ai_workflow/raw_resources/`
3. Ask Knowledge Manager to process them

### For Development

1. Tell Development Agent what you want to build
2. Agent checks for requirements first, then implements
3. Agent updates memory bank as needed

## File Organization Summary

```text
your-project/
├── .ai_workflow/
│   ├── system_architecture.md              # How the system works
│   ├── agent_instructions/                 # Full instructions for each agent
│   │   ├── development_agent_*.md         # 3 files for dev agent
│   │   ├── knowledge_manager_instructions.md
│   │   └── requirements_agent_instructions.md
│   ├── requirements/                       # Requirements workflow
│   ├── raw_notes/                         # Your knowledge input
│   ├── raw_resources/                     # Your document input
│   ├── memory_bank/                       # Dev agent's working memory
│   └── knowledge_base/                    # Organized knowledge
└── [your source code and project files]
```

## Key Principles

1. **Each agent reads from `.ai_workflow/agent_instructions/`** - The template files in your IDE/assistant just point to these full instructions
2. **Separation of concerns** - Each agent has specific responsibilities
3. **Knowledge flows through files** - Agents don't talk directly to each other
4. **Start simple** - You don't need all features from day one
