# AI Development Workflow: Dual-LLM System

## Overview

This workflow establishes a powerful dual-LLM development system where:
- **Claude** acts as your Knowledge Base Manager (librarian/curator)
- **Windsurf** acts as your Code Expert (developer/implementer)

The system solves the problem of context management in AI-assisted development by separating concerns: Claude organizes all project knowledge while Windsurf focuses on coding with access to only the most relevant information.

## Quick Start

### 1. Setup Windsurf
1. Open Windsurf's Customizations (top right slider menu)
2. Navigate to Rules panel
3. Click "+ Global" to create global rules
4. Copy the entire content of `windsurf_global_rules.md` into the global rules

### 2. Setup Claude
1. Create a new Claude Project on claude.ai
2. Add the content of `claude_project_instructions.md` as the project instructions
3. Enable MCP filesystem access for the project directory

### 3. Create Project Structure
```bash
# In your project root, create:
mkdir -p .project_knowledge/raw_notes
mkdir -p .project_knowledge/raw_resources
mkdir -p .project_knowledge/memory_bank
mkdir -p .project_knowledge/knowledge_base/technical
mkdir -p .project_knowledge/knowledge_base/domain
mkdir -p .project_knowledge/knowledge_base/decisions
mkdir -p .project_knowledge/knowledge_base/patterns
```

### 4. Initialize Memory Bank
Create these essential files in `.project_knowledge/memory_bank/`:
- `projectbrief.md` - Core project goals and requirements
- `context_routing.md` - Guides Windsurf to relevant knowledge base files

## System Architecture

```
Your Project/
├── .project_knowledge/          # All knowledge management
│   ├── raw_notes/              # YOUR INBOX - dump thoughts here
│   ├── raw_resources/          # YOUR INBOX - dump PDFs, docs here
│   ├── memory_bank/            # Windsurf's focused working memory
│   └── knowledge_base/         # Claude's comprehensive knowledge
│       ├── technical/          # Library preferences, patterns
│       ├── domain/             # Business logic, requirements
│       ├── decisions/          # Why certain choices were made
│       └── patterns/           # Reusable solutions
│
├── src/                        # Your actual code
└── [other project files]
```

## Core Workflow

### 1. Capture Ideas (You)
Drop any thoughts, notes, or resources into:
- `.project_knowledge/raw_notes/` for text files
- `.project_knowledge/raw_resources/` for PDFs, docs, etc.

No need to organize - just dump and go!

### 2. Process Knowledge (Claude)
Claude regularly:
- Monitors raw folders for new content
- Extracts and categorizes information
- Updates the knowledge base with organized content
- Updates routing to guide Windsurf
- Archives processed raw files

### 3. Code with Context (Windsurf)
Windsurf:
- Reads memory bank for current context
- Follows routing to access relevant knowledge
- Makes all coding decisions
- Updates memory bank after significant changes

## Example Workflow

### Scenario: Adding a New Technology Decision

1. **You write** in `.project_knowledge/raw_notes/async_decision.md`:
   ```markdown
   Decided to use AsyncIO for all LLM calls
   - Better performance with multiple models
   - Prevents blocking on slow API responses
   - Use aiohttp for HTTP calls
   ```

2. **Claude processes** this into:
   - Updates `.project_knowledge/knowledge_base/decisions/async_architecture.md`
   - Updates `.project_knowledge/knowledge_base/technical/async_patterns.md`
   - Adds to `.project_knowledge/memory_bank/context_routing.md`:
     ```markdown
     ### When implementing async LLM calls:
     - READ: `.project_knowledge/knowledge_base/technical/async_patterns.md`
     - READ: `.project_knowledge/knowledge_base/decisions/async_architecture.md`
     ```

3. **Windsurf implements** by:
   - Reading the routing guide
   - Accessing the specified knowledge base files
   - Implementing async patterns as documented

## Key Principles

### 1. Separation of Concerns
- **You**: Provide raw information and make decisions
- **Claude**: Organize knowledge, never make coding decisions
- **Windsurf**: Make all coding decisions, never organize knowledge

### 2. Information Hierarchy
```
knowledge_base (authoritative) 
    ↓ 
memory_bank (working subset) 
    ↓ 
current coding session
```

### 3. Git-Diff Friendly
Both LLMs use incremental edits to ensure all changes are trackable through version control.

## Common Commands

### For Claude:
- "Process the raw notes folder"
- "Update the routing for [specific feature]"
- "What's in our knowledge base about [topic]?"

### For Windsurf:
- "Implement [feature] following our patterns"
- "Update memory bank" (triggers full review)
- "What's our approach for [technical area]?"

## Best Practices

1. **Dump First, Organize Later**: Don't worry about organizing your thoughts. Put everything in raw folders.

2. **Technical Preferences vs Decisions**:
   - Preference: "Use Pydantic for data validation" ✓
   - Decision: "Create User model with these fields" ✗ (Windsurf decides)

3. **Keep Context Focused**: Memory bank should only contain what's relevant to current work.

4. **Regular Processing**: Have Claude process raw inputs at least daily to keep knowledge current.

5. **Clear Routing**: Ensure context_routing.md clearly maps tasks to knowledge base files.

## Troubleshooting

### "Windsurf isn't finding the right context"
- Check `.project_knowledge/memory_bank/context_routing.md`
- Ensure Claude has processed recent raw notes
- Verify knowledge base files exist at specified paths

### "Too much context in memory bank"
- Have Claude review and trim to only current work
- Move historical context to knowledge base

### "Conflicting information"
- Knowledge base is authoritative
- Have Claude update memory bank to match
- Document the resolution in decisions folder

## File Templates

### For raw_notes/ (your scratchpad):
```markdown
# [Topic/Date]

## Thoughts
- [Unorganized thoughts]
- [Decisions made]
- [Problems encountered]

## References
- [Links, quotes, etc.]
```

### For Claude's knowledge base files:
```markdown
# [Topic]

## Current Approach
[What we're doing now]

## Previous Approaches
[What we tried before and why we changed]

## Key Principles
[Important guidelines]

## Examples
[Concrete examples]
```

## Adopting This Workflow

To use this workflow in your project:

1. Copy this directory's files to your project
2. Create the `.project_knowledge/` structure
3. Set up both LLMs with their respective rules/instructions
4. Start dropping notes into raw folders
5. Have Claude process and organize
6. Code with Windsurf using the organized knowledge

Remember: The power comes from the separation - let each LLM do what it does best!
