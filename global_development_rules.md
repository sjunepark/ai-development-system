# Global Development Rules

## MCP Tools

- **context7**: Use when searching for documentation not available by default
- **sequential-thinking**: Always use when available
  - But don't use it when the user says not to use it(in short, "Don't SQ").
- **filesystem**: Use it when you need to access files located outside of the current project
  - Do not use this for accessing files in the current project. The current project can be handled by the IDE(Windsurf, etc.)

## Development Approach

### Incremental Development

- Make edits incrementally for git-diff friendliness and trackability
- Prefer small, testable chunks over large operations
- Mimic human development: write → test → iterate
- Use temporary scripts/notebooks in `scripts/` to test code

### Code Quality & Safety

- **Type Safety**: Use `Ruff` and `Pyright` for Python projects
- Maintain strict type hints and validation
- Follow established linting rules

### Communication & Clarity

- **Clarify ambiguity** before action - never pre-assume or speculate
- Ask specific questions when requirements are vague
- Confirm understanding of complex tasks before implementation

### Learning from Mistakes

- When errors occur, create/update workspace rule files
- Document mistakes to prevent repetition
- Keep rule files under 6,000 characters
- Group similar topics into separate rule files
- Avoid creating too many rule files

### Best Practices

- Write code in functional, testable chunks
- Document significant architectural decisions
- Maintain clear separation of concerns
- Prioritize readability and maintainability
