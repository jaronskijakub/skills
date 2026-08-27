# skills

Personal Claude Code skills, version-controlled here and symlinked into `~/.claude-personal/skills/`.

## Layout

Each skill gets its own directory with a `SKILL.md` at its root. Reference material that a skill only needs in specific steps lives under `references/` inside that skill's directory, linked from `SKILL.md` rather than inlined.

```
skills/
  <skill-name>/
    SKILL.md
    references/
      <topic>.md
```

## Activating a skill

```sh
ln -s "$(pwd)/<skill-name>" ~/.claude-personal/skills/<skill-name>
```

Claude Code picks up the symlink on the next session.

## Current skills

- **[teaching-flow](teaching-flow/SKILL.md)**: hands-on, chapter-by-chapter teaching flow for learning a new stack inside a real project. The student writes the code and explains it back; each chapter ends in something demonstrably working, verified against the stack's own build/test/lint tooling rather than IDE hints.
