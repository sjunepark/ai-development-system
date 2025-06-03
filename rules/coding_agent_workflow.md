---
trigger: manual
---

# Coding agent Workflows

## Core Workflows

### Chat Mode Workflow

```mermaid
flowchart TD
    Start[Start] --> CheckReqs[Check refined_requirements.md]
    CheckReqs --> ReadFiles[Read memory bank]
    ReadFiles --> CheckRouting[Check context_routing.md]
    CheckRouting --> ReadKB[Read relevant Knowledge Base files]
    ReadKB --> CheckFiles{Files Complete?}

    CheckFiles -->|No| Plan[Create Plan]
    Plan --> Document[Document in Chat]

    CheckFiles -->|Yes| Verify[Verify Context]
    Verify --> Strategy[Develop Strategy]
    Strategy --> Present[Present Approach]
```

### Write Mode Workflow

```mermaid
flowchart TD
    Start[Start] --> CheckReqs[Check refined_requirements.md]
    CheckReqs --> Context[Check memory bank]
    Context --> Routing[Check context_routing.md]
    Routing --> KB[Read relevant Knowledge Base]
    KB --> Update[Update Documentation]
    Update --> Execute[Execute Task]
    Execute --> Document[Document Changes]
    Document --> ClearReqs[Clear implemented requirements]
```

## Update Process

When updating memory bank documentation:

```mermaid
flowchart TD
    Start[Update Process]
    
    subgraph Process
        P1[Review ALL Files]
        P2[Document Current State]
        P3[Clarify Next Steps]
        P4[Document Insights & Patterns]
        
        P1 --> P2 --> P3 --> P4
    end
    
    Start --> Process
```

## Workflow Guidelines

### Starting a New Task

1. **Always check `refined_requirements.md` FIRST**
   - This contains refined requirements from the Requirements Agent
   - If it has content, this is your primary task
   - Clear it after implementation

2. **Read ALL memory bank files**
   - Start with `project_brief.md` for foundation
   - Review `active_context.md` for current state
   - Check `progress.md` for what's completed

3. **Consult `context_routing.md`**
   - This guides you to relevant Knowledge Base files
   - Read indicated files before starting work

### During Development

1. **Make incremental changes**
   - Use `edit_file` for trackable modifications
   - Commit logical chunks of work

2. **Update documentation as you work**
   - Document significant decisions in `active_context.md`
   - Update `progress.md` when features are complete

3. **When encountering new patterns**
   - Document in memory bank
   - Suggest Knowledge Base updates to user

### Completing Tasks

1. **Update `progress.md`**
   - Mark completed features
   - Note any new issues discovered

2. **Clear `refined_requirements.md`**
   - Remove implemented requirements
   - Note any partial implementations

3. **Update `active_context.md`**
   - Document what was done
   - Note next logical steps

### Special: "Update memory bank" Command

When user explicitly says **"update memory bank"**:

1. **Review EVERY memory bank file**
   - Even if some don't need updates
   - Focus on `active_context.md` and `progress.md`

2. **Document current project state**
   - Recent changes
   - Current challenges
   - Next steps

3. **Capture insights and patterns**
   - Technical learnings
   - Design decisions
   - Process improvements
