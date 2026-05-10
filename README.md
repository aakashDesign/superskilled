# Design Skills for AI

A curated, open-source collection of skills that teach AI assistants to think and act like a senior product designer. Each skill is a self-contained directory with a `SKILL.md` describing when to invoke it and the playbook to follow.

The skills are written in the Anthropic [Claude Skills](https://docs.claude.com/en/docs/claude-code/skills) format, but the playbooks themselves are model-agnostic and can be adapted to any system prompt or agent framework.

## Skills

| Skill | Use it for |
| --- | --- |
| [ux-copywriting](skills/ux-copywriting/SKILL.md) | Writing and reviewing interface copy — buttons, errors, empty states, onboarding |
| [frontend-design](skills/frontend-design/SKILL.md) | Translating design intent into well-structured, accessible, themeable frontend code |
| [ux-audit](skills/ux-audit/SKILL.md) | Auditing an existing flow, screen, or component against UX heuristics and accessibility |

## Repository layout

```
skills-project/
├── README.md
└── skills/
    ├── ux-copywriting/SKILL.md
    ├── frontend-design/SKILL.md
    └── ux-audit/SKILL.md
```

Each skill stands alone. Drop the directory into a `.claude/skills/` folder (Claude Code), reference it from a system prompt, or read it as a checklist.

## Using a skill with Claude Code

```bash
mkdir -p .claude/skills
cp -r skills/ux-copywriting .claude/skills/
```

Claude will discover the skill automatically and invoke it when its `description` matches the user's request.

## Contributing

Issues and PRs are welcome — especially real before/after examples that sharpen the heuristics. Each skill aims to stay short, opinionated, and runnable.

## License

MIT
