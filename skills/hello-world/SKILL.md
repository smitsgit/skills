---
name: hello-world
description: A test skill that greets the user and confirms that skills from smitsgit/skills are installed and loading correctly. Use when the user says "hello world skill", asks to test or verify that skills are working, or asks which agent and skill setup they are running.
license: MIT
---

# Hello World

A minimal skill that proves installation works across agents (Claude Code, Codex, Cursor, and others).

## When this skill runs

1. Greet the user with: **"👋 Hello from the hello-world skill (smitsgit/skills)!"**
2. Tell them which agent/tool you are (e.g. Claude Code, Codex, Cursor) if you know it.
3. Report the path you loaded this `SKILL.md` from, if you can see it.
4. Read [reference.md](reference.md) in this skill's folder and print the "secret phrase" from it. This confirms that bundled supporting files were installed alongside `SKILL.md`, not only the skill file itself.
5. End with one line: `Skill check: PASS` if steps 1–4 succeeded, otherwise `Skill check: PARTIAL` plus what failed.

Keep the whole response under 10 lines.
