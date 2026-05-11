# Dissolve AI

A [Claude Code](https://docs.anthropic.com/claude-code) skill that reviews prose drafts for the writing patterns that mark content as machine-generated.

Most "AI detector" tools score a draft as a probability of being AI-written. Dissolve AI does something more useful for writers: it tells you *which specific patterns* in your draft read as machine-generated, with quoted passages and rule references, so you know what to fix.

## What it catches

The reference ruleset catalogs patterns across categories including:

- **Inflated significance** — "pivotal moment," "part of a broader movement," "stands as a testament to"
- **Promotional framing** — routine details described as if for a press release
- **Emotional projection** — telling the reader how to feel ("you'll be amazed by," "captivating experience")
- **Hollow connector phrases** — "it's worth noting that," "in conclusion," "moreover, it is important to recognize"
- **Em-dash overuse and rhythmic monotony** — every paragraph built on the same beat
- **Formulaic three-item lists** — comma-separated triplets where one specific would be stronger
- **Structural symmetry** — section after section built to the same architecture
- **Empty intensifiers and qualifiers** — "incredibly," "remarkably," "truly," "deeply"

See [`reference/patterns.md`](./reference/patterns.md) for the full ruleset.

## Example

A typical AI-flavored marketing paragraph:

> In today's rapidly evolving digital landscape, artificial intelligence stands as a transformative force reshaping how brands connect with audiences. It's worth noting that this isn't just a passing trend — AI represents a fundamental shift, underscoring the importance of staying ahead of the curve. The benefits are clear: enhanced efficiency, personalized experiences, and data-driven insights.

A Dissolve AI report on that passage would flag:

- *"rapidly evolving digital landscape"* — empty scene-setting phrase
- *"stands as a transformative force"* — inflated significance, promotional framing
- *"It's worth noting that"* — hollow connector
- *"underscoring the importance of"* — inflated significance
- *"enhanced efficiency, personalized experiences, and data-driven insights"* — formulaic three-item list
- Pattern clustering: 5 flags in 3 sentences = heavy AI patterning

See [`examples/`](./examples) for full before/after.

## Install

```bash
# Clone the parent repo
git clone https://github.com/word-ful/editorial.git ~/wordful-editorial

# Symlink this skill into your Claude Code skills directory
ln -s ~/wordful-editorial/dissolve-ai ~/.claude/skills/dissolve-ai
```

Or copy the folder directly:

```bash
cp -r ~/wordful-editorial/dissolve-ai ~/.claude/skills/
```

## Usage

In Claude Code, share or paste your draft, then invoke:

```
/dissolve-ai
```

Or ask in plain language, naming the skill:

> "Run Dissolve AI on this draft."
>
> "Check this with Dissolve AI."

You'll get back a structured report: flagged passages, rule names, severity, clustering signals, and an overall verdict.

## What this skill does NOT do

- It does not rewrite your draft. v1 is Review-only — rewrite mode is on the roadmap.
- It does not score quality. A clean review means the draft is not formulaic. It does not mean the draft is good.
- It does not replace a human editor.

## Roadmap

- **v0.2** — Rewrite mode (produces a cleaned draft alongside the review)
- **v0.3** — Optional output formats (diff, redline, summary-only)
- **Later** — Plugin marketplace install path

## License

MIT. See [LICENSE](../LICENSE).

---

Created by Wordful, content ops for AI-forward marketing teams. https://wordful.com
