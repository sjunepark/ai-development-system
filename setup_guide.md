# Setup Guide

This guide helps you integrate the three-agent AI workflow into your project.

## Prerequisites

- Windsurf IDE
- (Optional) Claude Desktop(with filesystem MCP) for Requirements Agent and Knowledge agent

## Setup Steps

### 1. Create Directory Structure

```bash
# In your project root
mkdir -p .ai_dev/requirements .ai_dev/memory_bank .ai_dev/raw_knowledge/{raw_notes,raw_resources}
mkdir -p .ai_dev/knowledge_base/{technical,domain,decisions,patterns}
```

### 2. Copy Workflow Files

```bash
# From ai-coding-workflow repository root
cp system_architecture.md YOUR_PROJECT/.ai_dev/
```

### 3. Initialize Core Files

Create empty files:

- `.ai_dev/memory_bank/project_brief.md`
- `.ai_dev/memory_bank/product_context.md`
- `.ai_dev/memory_bank/active_context.md`
- `.ai_dev/memory_bank/system_patterns.md`
- `.ai_dev/memory_bank/tech_context.md`
- `.ai_dev/memory_bank/progress.md`
- `.ai_dev/requirements/raw_requirements.md`
- `.ai_dev/requirements/refined_requirements.md`
- `.ai_dev/knowledge_base/index.md`

### 4. Configure Agents

```bash
# From ai-coding-workflow repository root
cp -r rules/* YOUR_PROJECT/.windsurf/rules/
```

#### When using Claude Desktop(with filesystem MCP)

Create Requirements Agent project with instructions:

```text
You are the Requirements Agent. Read your complete instructions from:
`.windsurf/rules/requirements_agent_instructions.md`
```

Create Knowledge agent project with instructions:

```text
You are the Knowledge agent. Read your complete instructions from:
`.windsurf/rules/knowledge_agent_instructions.md`
```
