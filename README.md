# Wordful Editorial

Open-source editorial skills for AI content creation, by Wordful.

This is a collection of skills designed to help writers, marketers, and content teams ship work that holds up — without the formulaic patterns that mark a draft as machine-generated.

## Skills

### [dissolve-ai](./dissolve-ai)

Strip AI writing patterns from a prose draft. Returns the cleaned draft — no commentary, no findings, no grade. Where a passage cannot be safely cut, leaves a `[NEEDS SPECIFIC: ...]` placeholder for the human writer to fill in. Add `--report` for an optional diagnostic block.

*More skills coming.*

## Installation

### Recommended: plugin install (one command, no terminal)

Inside Claude Code, run:

```
/plugin marketplace add word-ful/editorial
/plugin install dissolve-ai@editorial
```

That's it. Updates apply automatically when new versions ship.

### Alternative: manual install

If you'd rather clone and symlink:

```bash
git clone https://github.com/word-ful/editorial.git ~/wordful-editorial
ln -s ~/wordful-editorial/dissolve-ai ~/.claude/skills/dissolve-ai
```

Then restart Claude Code.

See each skill's README for invocation details.

## License

MIT. See [LICENSE](./LICENSE).

## Contributing

Issues and PRs welcome. See [CONTRIBUTING.md](./CONTRIBUTING.md).

---

Created by Wordful, content ops for AI-forward marketing teams. https://wordful.com
