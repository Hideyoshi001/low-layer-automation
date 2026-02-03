---
description: Explore codebase, create implementation plan, code, and test following EPCT workflow
argument-hint: <feature-description|ticket>
allowed-tools: Bash, Read, Edit, Write, Grep, Glob, Task, WebSearch, WebFetch
---

# EPCT Command

Explore-Plan-Code-Test workflow for implementing features systematically with thorough analysis.

**You need to always ULTRA THINK.**

## Usage

```bash
/epct <feature-description|ticket>
```

**Examples:**
```bash
/epct "Add user authentication with OAuth"
/epct "Implement dark mode toggle"
/epct "Refactor database connection pooling"
```

## Workflow Context

This command guides complete feature implementation:

```
1. /epct <feature>             # ← THIS COMMAND (full implementation)
2. /changelog <project>        # Document the changes
3. /push <project>             # Commit the work
```

## Instructions

When the user invokes `/epct <feature>`, execute the following steps:

### Step 1: Explore

Use parallel subagents to find and read all files that may be useful:
- Search for existing similar implementations as examples
- Find files that will need modification
- Identify test patterns in the codebase
- Locate documentation and configuration files
- **ULTRA THINK**: What patterns exist? What can be reused?

Subagents should return:
- Relevant file paths
- Code patterns found
- Useful context for implementation

### Step 2: Plan

Think hard and write up a detailed implementation plan:
- List all files to create or modify
- Include tests, components, and documentation
- Use your judgement for what's necessary given repo standards
- **CRITICAL**: If unsure, launch parallel subagents for web research

**Before proceeding:**
- If there are ambiguities, pause and ask the user
- Present the plan for confirmation
- **ULTRA THINK**: Is this the right approach?

### Step 3: Code

When you have a thorough implementation plan, start writing code:
- Follow the style of the existing codebase
- Prefer clearly named variables/methods over extensive comments
- Implement incrementally, testing as you go
- Run autoformatting when done
- Fix reasonable linter warnings
- **STAY IN SCOPE**: Build exactly what's planned

### Step 4: Test

Use parallel subagents to run tests:
- Run unit tests for modified code
- Run integration tests if applicable
- For UX changes, use browser to verify functionality
- Make a checklist of scenarios to test

**If testing shows problems:**
> Go back to Step 2 and **ULTRA THINK** about what went wrong.

### Step 5: Write Up

When happy with your work, write a short report for PR description:
- What you set out to do
- Choices made with brief justification
- Commands run that may be useful for future developers
- Any follow-up tasks identified

## Quality Checklist

Before completing:
- [ ] Code follows existing patterns
- [ ] All tests pass
- [ ] No linter warnings
- [ ] Documentation updated if needed
- [ ] Changes are minimal and focused

## Error Handling

| Issue | Action |
|-------|--------|
| Tests failing | Analyze errors, go back to Plan step |
| Unclear requirements | Ask user for clarification |
| Missing dependencies | Research and propose additions |
| Conflicts with existing code | Propose refactoring approach |

## Notes

- **ULTRA THINK** at each phase transition
- Use parallel agents for comprehensive exploration
- Document findings and reasoning at each step
- Test thoroughly before completion
- Priority: Correctness > Completeness > Speed

User: $ARGUMENTS
