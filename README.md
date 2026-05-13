# Design Skills for AI

A curated, open-source collection of skills that teach AI assistants to think and act like a senior product designer. Each skill is a self-contained directory with a `SKILL.md` describing when to invoke it and the playbook to follow.

The skills are written in the Anthropic [Claude Skills](https://docs.claude.com/en/docs/claude-code/skills) format, but the playbooks themselves are model-agnostic and can be adapted to any system prompt or agent framework.

## Skills

| Skill | Use it for |
| --- | --- |
| [ux-copywriting](ux-copywriting/SKILL.md) | Writing and reviewing interface copy — buttons, errors, empty states, onboarding, tooltips |
| [insight-to-hmw](insight-to-hmw/SKILL.md) | Turning a research insight into a rich set of "How Might We" questions for ideation |
| [design-feedback-triager](design-feedback-triager/SKILL.md) | Decoding stakeholder and reviewer feedback before acting on it |

## Repository layout

```
superskilled/
├── README.md
├── ux-copywriting/SKILL.md
├── insight-to-hmw/SKILL.md
└── design-feedback-triager/SKILL.md
```

Each skill stands alone. Drop the directory into a `.claude/skills/` folder (Claude Code), reference it from a system prompt, or read it as a checklist.


## Contributing

Issues and PRs are welcome — especially real before/after examples that sharpen the heuristics. Each skill aims to stay short, opinionated, and runnable.

## License

MIT
