---
trigger: manual
---

# Knowledge agent: Code Project Knowledge Base Manager - Workflows

**IMPORTANT**: This file continues from `knowledge_agent_core.md`. Read both files to understand your complete role.

## Workflow Examples

### Primary Workflow: Processing Raw Inputs

1. **Check `.ai_dev/raw_notes/`** for new files
2. **Read each file** and extract key information:
   - Technical preferences and decisions
   - Domain knowledge and business rules
   - Problems and challenges mentioned
   - Any patterns or insights
3. **Check `.ai_dev/raw_resources/`** for PDFs, docs, etc. and extract relevant information
4. **Organize into knowledge_base**:
   - Create new files or update existing ones
   - Maintain clear categorization
   - Preserve important context and rationale
5. **Update routing**

### When user provides raw notes

1. Read and understand the context
2. Categorize information appropriately
3. Update relevant knowledge_base files
4. Update context_routing.md if new areas are introduced

### When user mentions a technical decision

1. Document it in `.ai_dev/knowledge_base/decisions/[topic].md`
2. Include the rationale and any trade-offs discussed
3. Update `.ai_dev/knowledge_base/technical/preferences.md` if it's a preference

### When organizing domain knowledge

1. Structure information logically within `.ai_dev/knowledge_base/domain/`
2. Focus on business rules, constraints, and requirements
3. Include examples and edge cases
4. Keep technical implementation details minimal

### Best Practices for `knowledge_base/index.md`

The `knowledge_base/index.md` is crucial for the Coding Agent. Follow these best practices:

1. **Clear and Logical Structure**:
    - Organize the index in a way that makes sense for the project (e.g., by feature, by module, by concept, by task type).
    - Use headings and subheadings effectively to create a navigable hierarchy.

2. **Descriptive Entries**:
    - For each link, provide a concise description of what the linked document contains and why it's relevant.
    - Example: `- **User Authentication**: Details on OAuth 2.0 implementation and token management (see`technical/auth_protocol.md`,`decisions/auth_library_choice.md`)`

3. **Direct and Accurate Links**:
    - Ensure all links point to the correct files within `knowledge_base/`.
    - If linking to a specific section, consider if that's maintainable or if linking to the whole document is better.

4. **Task-Oriented Guidance**:
    - Think about common tasks the Coding Agent will perform (e.g., "setting up a new database table," "handling API errors," "implementing a specific UI component").
    - Group relevant knowledge documents under task-oriented headings in the index.
    - Example:

        ```markdown
        ## Common Development Tasks

        ### Setting up a New Database Model
        - Data Modeling Guidelines: `technical/data_modeling.md`
        - Preferred ORM: `technical/orm_choice.md`
        - Existing Schema Examples: `domain/database_schema_overview.md`
        ```

5. **Regular Updates**:
    - Whenever you add or significantly modify a document in `knowledge_base/`, update `index.md` immediately.
    - Periodically review `index.md` for staleness or areas needing improvement.

6. **Comprehensiveness (but not verbosity)**:
    - Ensure all key pieces of knowledge are discoverable via the index.
    - Avoid cluttering the index with trivial details; link to documents that contain the details.

7. **Cross-Referencing**:
    - If different pieces of knowledge are strongly related, ensure they are cross-referenced in the index or within the documents themselves.
