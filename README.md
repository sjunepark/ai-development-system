# LLM IDE Dev

This repository contains AI development resources, workflows, and global rules for use with AI-powered code editors and IDEs (such as Windsurf, Cursor, etc).

## Repository Structure

```console
llm-ide-dev/
├── workflow/                    # Three-agent workflow methodology
│   ├── system_architecture.md   # Complete system design
│   ├── development_agent_rules.md
│   ├── development_agent_workspace_rules.md  # For project .windsurf/rules/
│   ├── knowledge_manager_instructions.md
│   └── requirements_agent_instructions.md
└── global_development_rules.md  # Universal coding rules (separate from workflow)
```

## Contents

### 1. Three-Agent Workflow System (`/workflow`)

A complete methodology for organizing AI-assisted development using three specialized agents:

- **Requirements Agent**: Refines raw instructions into clear specifications
- **Knowledge Manager**: Organizes and maintains project knowledge
- **Development Agent**: Implements code based on requirements and knowledge

See [workflow/system_architecture.md](./workflow/system_architecture.md) for detailed information.

### 2. Global Development Rules

Universal coding principles and tool configurations that apply to all projects, regardless of whether they use the three-agent workflow. Includes:

- MCP tools configuration
- Incremental development practices
- Type safety standards
- Error handling and learning patterns

## Usage

### For Projects Using the Three-Agent Workflow

1. Copy `workflow/development_agent_workspace_rules.md` to your project's `.windsurf/rules/` directory
2. Set up the `.ai_workflow/` structure as described in the system architecture
3. Configure the other agents as per their instruction files

### For All Projects

Add `global_development_rules.md` to your IDE's global rules:

- **Windsurf**: Settings → Rules → +Global
- **Cursor**: Follow similar global configuration steps
