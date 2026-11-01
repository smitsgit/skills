# smitsgit/skills

Agent skills for Claude Code, Codex, Cursor, and other tools that support the
[Agent Skills](https://agentskills.io) `SKILL.md` format.

## Install

```bash
# Interactive: pick skills and agents
npx skills add https://github.com/smitsgit/skills

# A single skill (shorthand works too: npx skills add smitsgit/skills ...)
npx skills add https://github.com/smitsgit/skills --skill hello-world

# Pick the agents
npx skills add smitsgit/skills --skill hello-world -a claude-code -a codex -a cursor

# Install for your user instead of the current project
npx skills add smitsgit/skills --skill hello-world -g

# List what's available without installing
npx skills add smitsgit/skills --list
```

### Where each agent looks (project scope)

| Agent       | Install location                 | Notes |
|-------------|----------------------------------|-------|
| Claude Code | `.claude/skills/<name>/`         | Symlinked to `.agents/skills` when you install to several agents. Restart the session if the skill doesn't show up. |
| Codex       | `.agents/skills/<name>/`         | Shared "universal" location. |
| Cursor      | `.agents/skills/<name>/`         | Shared "universal" location. |

When you pick more than one agent, the CLI keeps one copy in `.agents/skills`
and symlinks it into the other folders. Use `--copy` if your setup can't handle
symlinks, for example on Windows without developer mode or in some Docker mounts.

### Manual install (no npx)

Copy `skills/<name>/` (the whole folder, not just `SKILL.md`) into the agent's
skills directory listed above.

## Skills

| Skill | Description |
|-------|-------------|
| [hello-world](skills/hello-world/SKILL.md) | Test skill. Says hello and checks that the skill and its bundled files installed correctly. |

Test it after installing by asking your agent: **"run the hello world skill"**.
It should end with `Skill check: PASS`.

## Authoring a new skill

```
skills/
  <skill-name>/
    SKILL.md        # required
    reference.md    # optional supporting files, scripts/, assets/ ...
```

Rules that keep a skill working in every agent:

- `name` in the frontmatter must match the folder name: lowercase letters,
  digits, and hyphens, up to 64 characters.
- `description` is required, up to 1024 characters. Say what the skill does
  **and when to use it**, because agents decide whether to load a skill from
  this text alone.
- Keep the frontmatter portable (`name`, `description`, optionally `license`,
  `metadata`). Tool-specific fields like Claude's `allowed-tools` are ignored
  by other agents, so don't depend on them.
- Link supporting files with relative paths from `SKILL.md`, and keep
  `SKILL.md` under about 500 lines. Put long detail in separate files.
- Don't assume a particular agent's tool names (e.g. "use the Bash tool").
  Describe the action instead ("run this command").
- Test locally before pushing:
  `npx skills add ./ --skill <name> -a claude-code -a codex -a cursor`
  from a scratch project directory, pointing at this repo's path.

## License

MIT
