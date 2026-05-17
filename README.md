# Wordful Editorial

Open-source editorial skills for AI content creation, by Wordful.

This is a collection of [Claude Code](https://docs.anthropic.com/claude-code) skills designed to help writers, marketers, and content teams ship work that holds up — without the formulaic patterns that mark a draft as machine-generated.

## Skills

### [dissolve-ai](./dissolve-ai)

Strip AI writing patterns from a prose draft. Returns the cleaned draft — no commentary, no findings, no grade. Where a passage cannot be safely cut, leaves a `[NEEDS SPECIFIC: ...]` placeholder for the human writer to fill in. Add `--report` for an optional diagnostic block.

*More skills coming.*

## Installation

Each skill lives in its own subdirectory and includes its own install instructions. The general pattern:

```bash
# Clone this repo somewhere stable
git clone https://github.com/word-ful/editorial.git ~/wordful-editorial

# Symlink the skills you want into your Claude Code skills directory
ln -s ~/wordful-editorial/dissolve-ai ~/.claude/skills/dissolve-ai
```

Or, if you prefer copying over symlinks:

```bash
cp -r ~/wordful-editorial/dissolve-ai ~/.claude/skills/
```

See each skill's README for invocation details.

## License

MIT. See [LICENSE](./LICENSE).

## Contributing

Issues and PRs welcome. See [CONTRIBUTING.md](./CONTRIBUTING.md).

---

Created by Wordful, content ops for AI-forward marketing teams. https://wordful.com
