# Dissolve AI

A [Claude Code](https://docs.anthropic.com/claude-code) skill that strips AI writing patterns from a prose draft and gives the cleaned draft back to you.

No grading. No commentary. No report card. You paste a draft. You get back a draft with the AI tells removed.

Where a passage can't be cleanly cut without inventing facts, the skill leaves a `[NEEDS SPECIFIC: ...]` placeholder — an honest signal that the original was carrying no substance there, and that the human writer has to supply it.

## What it strips

The reference ruleset catalogs patterns across categories including:

- **Inflated significance** — "pivotal moment," "part of a broader movement," "stands as a testament to"
- **Promotional framing** — routine details described as if for a press release
- **Emotional projection** — telling the reader how to feel ("you'll be amazed by")
- **Hollow connector phrases** — "it's worth noting that," "in conclusion," "moreover"
- **Em-dash overuse and rhythmic monotony**
- **Formulaic three-item lists** — comma-separated abstract noun triplets
- **"Not just X — it's Y" constructions** — assertion by contrast without earned weight
- **Superfluous jargon** — "operationalize," "surface area," "granularity" used as default rather than as deliberate choice
- **Structural symmetry** — every paragraph built to the same shape

See [`reference/patterns.md`](./reference/patterns.md) for the full ruleset.

## Example

A typical AI-flavored marketing paragraph:

> In today's rapidly evolving digital landscape, artificial intelligence stands as a transformative force reshaping how brands connect with audiences. It's worth noting that this isn't just a passing trend — AI represents a fundamental shift, underscoring the importance of staying ahead of the curve. The benefits are clear: enhanced efficiency, personalized experiences, and data-driven insights.

After Dissolve AI:

> Marketing teams are using AI for [NEEDS SPECIFIC: one or two concrete applications]. [NEEDS SPECIFIC: name a company, what they deployed, and a measurable outcome].

That's the whole output. No findings, no grade, no advice. The sparse result is the point — when the original is largely filler, the stripped draft exposes it. The placeholders tell the writer exactly where the substance is missing.

See [`examples/`](./examples) for the full before/after.

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

You'll get back the stripped draft. Nothing else.

If you want a diagnostic block showing what was cut and why — useful for power users, internal QA, or training your eye on the patterns — add the `--report` flag:

```
/dissolve-ai --report
```

Or ask in plain language, naming the skill:

> "Run Dissolve AI on this."
>
> "Dissolve this draft with a report."

## What this skill does NOT do

- It does not generate voice the original did not have.
- It does not introduce facts, numbers, or claims the original did not include.
- It does not score writing quality. A stripped draft is not necessarily a good draft.
- It does not check facts, citations, or audience fit.
- It does not replace a human editor.

## Roadmap

- **v0.3** — Bring-your-own-sample mode (`--sample <paragraph>`) for voice-aware collapses
- **v0.4** — Plugin marketplace install path
- **Later** — Per-rule severity tuning, custom ruleset extensions

## License

MIT. See [LICENSE](../LICENSE).

---

Created by Wordful, content ops for AI-forward marketing teams. https://wordful.com
