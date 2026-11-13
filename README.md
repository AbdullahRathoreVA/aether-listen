# Aether Listen

Find people already asking for what you sell on Hacker News, Reddit and
StackExchange, ranked by buying intent. A free skill for AI agents (Claude Code,
Codex CLI, Cursor and any agent that reads `SKILL.md`).

- **Listens** to public, read-only endpoints. No API keys, no login.
- **Ranks by buying intent** from phrases you choose, and drops vendors, launch
  posts and job ads.
- **Learns your taste**: after 20 approve or reject decisions a small local
  model starts ranking by what you approve, and reports its own
  cross-validated accuracy.
- **Never posts.** It drafts; you decide and post yourself.

Two standard-library Python scripts. The one that uses the network reads no
files; the one that reads your files has no network code.

## Install

With the skills CLI:

```bash
npx skills add AbdullahRathoreVA/aether-listen
```

Or copy this folder into your agent's skills directory (for Claude Code:
`~/.claude/skills/aether-listen`). Then ask your agent: "Who is asking for what
I sell this week?"

## Run it by hand

```bash
python scripts/listen.py --hn "invoice software" --reddit smallbusiness --se softwarerecs > posts.json
```

```bash
python scripts/signals.py ingest posts.json
```

```bash
python scripts/signals.py top 10
```

Settings live in `aether.json` in your project; see
[references/profile.md](references/profile.md).

## More free skills

| Skill | What it does |
|---|---|
| [Aether Engine](https://github.com/AbdullahRathoreVA/aether-engine-skill) | Finds people asking for what you sell, plans and publishes audited SEO pages, checks drafts for filler |
| **Aether Listen** | This one |
| [Agent Team](https://github.com/AbdullahRathoreVA/agent-team) | Plans a task for a team of AI agents and coordinates their handoffs through Git |
| [Secret Scan](https://github.com/AbdullahRathoreVA/secret-scan) | Finds leaked keys in a repository's Git history before you make it public |

## Licence

MIT. See [LICENSE](LICENSE).
