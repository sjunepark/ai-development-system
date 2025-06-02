# AI Development Workflow: Three-Agent System

## Overview

This workflow establishes a powerful three-agent development system where:

- **Requirements Agent** acts as your Instruction Refiner (preprocessor/clarifier)
- **Knowledge Manager** acts as your Knowledge Base Manager (librarian/curator)
- **Development Agent** acts as your Code Expert (developer/implementer)

The system solves two key problems in AI-assisted development:

1. **Instruction Clarity**: Requirements Agent refines your rough ideas into clear specifications, saving tokens and reducing back-and-forth with the Development Agent
2. **Context Management**: Knowledge Manager organizes all project knowledge while Development Agent focuses on coding with access to only the most relevant information

## Quick Start

### 1. Setup Requirements Agent

1. Create a new project in your chosen LLM platform (e.g., Claude Project on claude.ai)
2. Add the content of `requirements_agent_instructions.md` as the project instructions
3. Enable filesystem access for the project directory

### 2. Setup Development Agent

1. Open your development environment's customizations (e.g., Windsurf's top right slider menu, Cursor's settings)
2. Navigate to Rules panel
3. Click "+ Global" to create global rules
4. Copy the entire content of `development_agent_rules.md` into the global rules

### 3. Setup Knowledge Manager

1. Create a new project in your chosen LLM platform (e.g., Claude Project on claude.ai)
2. Add the content of `knowledge_manager_instructions.md` as the project instructions
3. Enable filesystem access for the project directory (e.g., MCP filesystem access)

### 4. Create Project Structure

```bash
# In your project root, create:
mkdir -p .project_knowledge/requirements
mkdir -p .project_knowledge/raw_notes
mkdir -p .project_knowledge/raw_resources
mkdir -p .project_knowledge/memory_bank
mkdir -p .project_knowledge/knowledge_base/technical
mkdir -p .project_knowledge/knowledge_base/domain
mkdir -p .project_knowledge/knowledge_base/decisions
mkdir -p .project_knowledge/knowledge_base/patterns
```

### 5. Initialize Core Files

Create these essential files:

**In `.project_knowledge/memory_bank/`:**

- `projectbrief.md` - Core project goals and requirements
- `context_routing.md` - Guides Development Agent to relevant knowledge base files

**In `.project_knowledge/requirements/`:**

- `raw_instructions.md` - Your unorganized development instructions
- `current_requirements.md` - Requirements Agent's refined output

## System Architecture

```markdown
Your Project/
├── .project_knowledge/          # All knowledge management
│   ├── requirements/           # Requirements processing
│   │   ├── raw_instructions.md # YOUR rough development instructions
│   │   └── current_requirements.md # Refined requirements for Development Agent
│   ├── raw_notes/              # YOUR INBOX - dump thoughts here
│   ├── raw_resources/          # YOUR INBOX - dump PDFs, docs here
│   ├── memory_bank/            # Development Agent's focused working memory
│   └── knowledge_base/         # Knowledge Manager's comprehensive knowledge
│       ├── technical/          # Library preferences, patterns
│       ├── domain/             # Business logic, requirements
│       ├── decisions/          # Why certain choices were made
│       └── patterns/           # Reusable solutions
│
├── src/                        # Your actual code
└── [other project files]
```

## Core Workflows

### Workflow A: Development Instructions (You → Requirements → Development)

1. **Write Raw Instructions (You)**
   - Write rough ideas in `.project_knowledge/requirements/raw_instructions.md`
   - Don't worry about structure or completeness

2. **Refine Requirements (Requirements Agent)**
   - Reads your raw instructions
   - Asks clarifying questions about purpose and goals
   - Outputs clean requirements to `current_requirements.md`
   - References knowledge base instead of duplicating info

3. **Implement Code (Development Agent)**
   - Reads refined requirements from `current_requirements.md`
   - Accesses relevant knowledge base as needed
   - Makes all technical decisions
   - Implements the solution

### Workflow B: Knowledge Management (You → Knowledge Manager)

1. **Capture Ideas (You)**
   - Drop thoughts/notes into `.project_knowledge/raw_notes/`
   - Drop PDFs/docs into `.project_knowledge/raw_resources/`

2. **Process Knowledge (Knowledge Manager)**
   - Monitors raw folders for new content
   - Extracts and categorizes information
   - Updates the knowledge base with organized content
   - Updates routing to guide Development Agent
   - Archives processed raw files

## Example Workflows

### Example A: Implementing a New Feature

1. **You write** in `.project_knowledge/requirements/raw_instructions.md`:

   ```markdown
   Need to add user authentication. Should support email/password and maybe Google. 
   Need to track login attempts for security. Fast login is important.
   ```

2. **Requirements Agent clarifies**:
   - "What happens after failed login attempts? (lock account, delay, captcha?)"
   - "Should users be able to stay logged in? For how long?"
   - "What user data should be stored? (profile, preferences?)"

3. **Requirements Agent outputs** to `current_requirements.md`:

   ```markdown
   # Current Requirements
   
   ## Overview
   Implement user authentication system with email/password and Google OAuth
   
   ## Requirements
   
   ### Requirement 1: Authentication Methods
   **Purpose**: Allow users to securely access their accounts
   **Acceptance Criteria**:
   - [ ] Email/password authentication
   - [ ] Google OAuth integration
   - [ ] Session management with 30-day remember me option
   
   ### Requirement 2: Security Features
   **Purpose**: Protect against unauthorized access
   **Acceptance Criteria**:
   - [ ] Track failed login attempts
   - [ ] Lock account after 5 failed attempts
   - [ ] Email notification on lock
   - [ ] Login completes in under 2 seconds
   ```

4. **Development Agent implements** based on clear requirements

### Example B: Adding a New Technology Decision

1. **You write** in `.project_knowledge/raw_notes/async_decision.md`:

   ```markdown
   Decided to use AsyncIO for all LLM calls
   - Better performance with multiple models
   - Prevents blocking on slow API responses
   - Use aiohttp for HTTP calls
   ```

2. **Knowledge Manager processes** this into:
   - Updates `.project_knowledge/knowledge_base/decisions/async_architecture.md`
   - Updates `.project_knowledge/knowledge_base/technical/async_patterns.md`
   - Adds to `.project_knowledge/memory_bank/context_routing.md`:

     ```markdown
     ### When implementing async LLM calls:
     - READ: `.project_knowledge/knowledge_base/technical/async_patterns.md`
     - READ: `.project_knowledge/knowledge_base/decisions/async_architecture.md`
     ```

3. **Development Agent implements** by:
   - Reading the routing guide
   - Accessing the specified knowledge base files
   - Implementing async patterns as documented

## Key Principles

### 1. Separation of Concerns

- **You**: Provide raw information and make decisions
- **Requirements Agent**: Clarify WHAT needs to be done and WHY
- **Knowledge Manager**: Organize knowledge, never make coding decisions
- **Development Agent**: Decide HOW to implement and execute

### 2. Information Hierarchy

```text
knowledge_base (authoritative) 
    ↓ 
memory_bank (working subset) 
    ↓ 
current coding session
```

### 3. Git-Diff Friendly

Both agents use incremental edits to ensure all changes are trackable through version control.

## Common Commands

### For Requirements Agent

- "Help me refine my development instructions"
- "I want to add [rough feature idea]"
- "Review and clarify the raw instructions"

### For Knowledge Manager

- "Process the raw notes folder"
- "Update the routing for [specific feature]"
- "What's in our knowledge base about [topic]?"

### For Development Agent

- "Implement the requirements in current_requirements.md"
- "Update memory bank" (triggers full review)
- "What's our approach for [technical area]?"

## Best Practices

1. **Dump First, Organize Later**: Don't worry about organizing your thoughts. Put everything in raw folders.

2. **Use Requirements Agent for Development Tasks**: When you need something built, start with Requirements Agent to save Development Agent tokens.

3. **Technical Preferences vs Decisions**:
   - Preference: "Use Pydantic for data validation" ✓ (Knowledge base)
   - Requirement: "Users need to log in" ✓ (Requirements Agent)
   - Decision: "Create User model with these fields" ✗ (Development Agent decides)

4. **Keep Context Focused**: Memory bank should only contain what's relevant to current work.

5. **Regular Processing**: Have Knowledge Manager process raw inputs at least daily to keep knowledge current.

6. **Clear Routing**: Ensure context_routing.md clearly maps tasks to knowledge base files.

## Troubleshooting

### "My instructions are too vague for Development Agent"

- Use Requirements Agent to refine them first
- Write rough ideas in `raw_instructions.md`
- Let Requirements Agent ask clarifying questions

### "Development Agent isn't finding the right context"

- Check `.project_knowledge/memory_bank/context_routing.md`
- Ensure Knowledge Manager has processed recent raw notes
- Verify knowledge base files exist at specified paths

### "Too much context in memory bank"

- Have Knowledge Manager review and trim to only current work
- Move historical context to knowledge base

### "Conflicting information"

- Knowledge base is authoritative
- Have Knowledge Manager update memory bank to match
- Document the resolution in decisions folder

## File Templates

### For requirements/raw_instructions.md (development tasks)

```markdown
# Raw Development Instructions

## What I Want
[Rough description of features/changes needed]

## Why
[Any context about why this is needed]

## Other Thoughts
[Any constraints, preferences, or random ideas]
```

### For raw_notes/ (your knowledge scratchpad)

```markdown
# [Topic/Date]

## Thoughts
- [Unorganized thoughts]
- [Decisions made]
- [Problems encountered]

## References
- [Links, quotes, etc.]
```

### For Knowledge Manager's knowledge base files

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
2. Create the `.project_knowledge/` structure including the `requirements/` folder
3. Set up all three agents with their respective rules/instructions
4. For development tasks: Start with Requirements Agent to refine your instructions
5. For knowledge: Drop notes into raw folders and have Knowledge Manager process them
6. Code with Development Agent using refined requirements and organized knowledge

Remember: The power comes from the separation - let each agent do what it does best!
