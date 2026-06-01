# Skill: newproject

Creates a standard UIB research project folder structure with CLAUDE.md, README, and first progress log.

## Trigger

Use this skill when the user says:
- "new project"
- "start a project"
- "create project <name>"
- `/newproject <name>`

## Behavior

Follow the instructions in `.claude/commands/newproject.md` exactly.

If no project name is provided, ask: "What should the project be called?"

After creating the structure, show the user the folder tree and prompt them to fill in the research question in README.md.
