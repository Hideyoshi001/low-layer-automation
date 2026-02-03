---
description: Create and optimize command prompts with command-specific patterns
argument-hint: <action> <name> - e.g., "create deploy", "refactor @commands/commit.md"
allowed-tools: Read, Write, Edit, Glob, WebFetch
---

# Ask Command

Create actionable command prompts that match existing patterns in the repository.

**You need to always ULTRA THINK.**

## Usage

```bash
/ask-command <action> <name>
```

**Examples:**
```bash
/ask-command create deploy
/ask-command refactor @commands/commit.md
/ask-command update @commands/release.md
```

## Workflow Context

This command is used to create or improve slash commands:

```
1. /ask-command create <name>      # Create new command from template
2. /ask-command refactor @path     # Enhance existing command
3. /ask-command update @path       # Modify specific sections
```

## Instructions

When the user invokes `/ask-command <action> <name>`, execute the following steps:

### Step 0: Research Slash Commands

- Fetch official documentation from https://docs.claude.com/en/docs/claude-code/slash-commands
- Review existing commands in `.CLAUDE/commands/` directory for patterns
- **CRITICAL**: Always consult documentation for latest best practices

### Step 1: Parse Arguments

Determine action type:
- `create <name>`: New command from template
- `refactor @path`: Enhance existing command
- `update @path`: Modify specific sections

### Step 2: Choose Pattern

Select appropriate format based on docs and examples:
- **Step-by-step workflow** for process commands (release, push, changelog)
- **Numbered workflow** for analysis commands (debug, epct)
- **Reference sections** for specialist commands (web-design)

### Step 3: Write/Update File

Save to `.CLAUDE/commands/` directory:
- New commands: `.CLAUDE/commands/<name>.md`
- Updates: Preserve all existing content and structure
- **ALWAYS**: Follow the standard command pattern

## Command Pattern Standard

All commands MUST follow this structure:

```markdown
---
description: Short description of the command
---

# Command Title

Brief description paragraph.

**You need to always ULTRA THINK.**

## Usage

\`\`\`bash
/command <args>
\`\`\`

**Examples:**
\`\`\`bash
/command example1
/command example2
\`\`\`

## Workflow Context (optional)

## Instructions

When the user invokes `/command <args>`, execute the following steps:

### Step 0: ...
### Step 1: ...

## Error Handling

## Notes

User: $ARGUMENTS
```

## Error Handling

| Error | Cause | Solution |
|-------|-------|----------|
| "Command already exists" | File exists | Use `refactor` or `update` action |
| "Invalid action" | Unknown action | Use create, refactor, or update |
| "Path not found" | Invalid @path | Check file exists |

## Notes

- Always use the `.md` extension
- Keep the tone professional, technical, and concise
- End with `User: $ARGUMENTS`
- Follow existing patterns strictly

User: $ARGUMENTS
