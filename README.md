# Koan Dev Workflow Plugin

A Claude Code plugin providing development workflow commands for planning, documentation, commits, and codebase exploration.

## Installation

```bash
/plugin install github:DylanNWatt/claude-planning-plugin
```

Or add to your project's `.claude/settings.json`:

```json
{
  "plugins": ["github:DylanNWatt/claude-planning-plugin"]
}
```

## Commands

### `/plan <feature description>`

Creates a structured feature plan in `./docs/plans`. The plan includes:
- Overview and context
- Desired outcomes
- Open questions (checkmarkable)
- Task breakdown (checkmarkable)
- Security considerations

**Example:**
```
/plan Add user authentication with OAuth
```

### `/execute_plan <path to plan>`

Executes a plan file task-by-task. Reviews open questions, ensures tests pass before marking tasks complete, and updates the plan as work progresses.

**Example:**
```
/execute_plan ./docs/plans/auth-feature.md
```

### `/update_plan`

Updates the current plan with recently learned information and marks completed tasks.

### `/commit`

Bundles outstanding changes into logical commits with good messages. Also:
- Checks for sensitive data before committing
- Runs all server tests
- Ensures TypeScript has no warnings or errors

### `/examine <component>`

Thoroughly examines a component of the project, documenting:
- Testing commands and best practices
- Architecture layers and interfaces
- Utilities (linting, compilers, etc.)

Outputs documentation to `./docs/docs/agent_docs/<layer>`.

**Example:**
```
/examine server
```

### `/docs`

Creates a plan for building Sphinx documentation covering client, server, and infrastructure.

### `/update_docs`

Updates existing documentation based on recent session changes, removing outdated content.

### `/devcontainer`

Creates a devcontainer configuration for VS Code and GitHub Codespaces with:
- Automatic dependency setup
- PostgreSQL configuration on first launch
- Auto-starting frontend and backend
- Hot reload for code changes

## License

MIT
