# Wordful Editorial

Open-source editorial skills for AI content creation, by Wordful.

This is a collection of [Claude Code](https://docs.anthropic.com/claude-code) skills designed to help writers, marketers, and content teams ship work that holds up — without the formulaic patterns that mark a draft as machine-generated.

## Skills

### [dissolve-ai](./dissolve-ai)

Review a prose draft for AI writing patterns. Returns a structured report: flagged passages, rule references, severity, and clustering signals. Review-only in v1 — flags issues, does not rewrite.

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
