---
trigger: always_on
---

# Development Agent Workflows

## Core Workflows

### Chat Mode Workflow

```mermaid
flowchart TD
    Start[Start] --> CheckReqs[Check current_requirements.md]
    CheckReqs --> ReadFiles[Read Memory Bank]
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
    Start[Start] --> CheckReqs[Check current_requirements.md]
    CheckReqs --> Context[Check Memory Bank]
    Context --> Routing[Check context_routing.md]
    Routing --> KB[Read relevant Knowledge Base]
    KB --> Update[Update Documentation]
    Update --> Execute[Execute Task]
    Execute --> Document[Document Changes]
    Document --> ClearReqs[Clear implemented requirements]
```

## Update Process

When updating Memory Bank documentation:

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

1. **Always check `current_requirements.md` FIRST**
   - This contains refined requirements from the Requirements Agent
   - If it has content, this is your primary task
   - Clear it after implementation

2. **Read ALL Memory Bank files**
   - Start with `projectbrief.md` for foundation
   - Review `activeContext.md` for current state
   - Check `progress.md` for what's completed

3. **Consult `context_routing.md`**
   - This guides you to relevant Knowledge Base files
   - Read indicated files before starting work

### During Development

1. **Make incremental changes**
   - Use `edit_file` for trackable modifications
   - Commit logical chunks of work

2. **Update documentation as you work**
   - Document significant decisions in `activeContext.md`
   - Update `progress.md` when features are complete

3. **When encountering new patterns**
   - Document in Memory Bank
   - Suggest Knowledge Base updates to user

### Completing Tasks

1. **Update `progress.md`**
   - Mark completed features
   - Note any new issues discovered

2. **Clear `current_requirements.md`**
   - Remove implemented requirements
   - Note any partial implementations

3. **Update `activeContext.md`**
   - Document what was done
   - Note next logical steps

### Special: "Update Memory Bank" Command

When user explicitly says **"update memory bank"**:

1. **Review EVERY Memory Bank file**
   - Even if some don't need updates
   - Focus on `activeContext.md` and `progress.md`

2. **Document current project state**
   - Recent changes
   - Current challenges
   - Next steps

3. **Capture insights and patterns**
   - Technical learnings
   - Design decisions
   - Process improvements
