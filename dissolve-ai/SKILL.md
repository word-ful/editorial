---
name: dissolve-ai
description: Manual-invocation skill for stripping AI writing patterns from prose drafts. Invoke ONLY when the user explicitly runs /dissolve-ai or asks by name — e.g. "run Dissolve AI on this", "strip AI patterns with Dissolve AI", "dissolve this draft". Returns a cleaned draft with formulaic AI tells removed — inflated significance, promotional framing, hollow connector phrases, emotional projection, three-item lists, structural repetition, and related patterns. Where a passage cannot be safely cut without inventing facts the skill does not have, leaves an inline [NEEDS SPECIFIC: ...] placeholder for the user to fill in. Default output is the stripped draft only — no commentary, no findings, no summary. Use the --report flag (or ask "with report") for an optional diagnostic block. Do NOT auto-trigger on general writing tasks, blog drafts, code review, or unrelated content. This skill activates only on explicit invocation.
disable-model-invocation: true
---

# Dissolve AI

Strip AI writing patterns from a prose draft. Return the cleaned draft.

## When to invoke

Only when the user explicitly asks for this skill by name. Triggers include:

- `/dissolve-ai`
- `/dissolve-ai --report`
- "run Dissolve AI on this"
- "strip this with Dissolve AI"
- "dissolve this draft"

Do NOT invoke on generic writing-help requests, editing requests, or code review. If the user is asking for general writing feedback without naming this skill, do not run it.

## How it works

### Step 1: Load the reference

Before doing anything else, read [`reference/patterns.md`](./reference/patterns.md) in full. It is in the same directory as this SKILL.md.

If it cannot be loaded, stop and output:

> **Dissolve AI: `reference/patterns.md` not found — cannot proceed.** Locate the file and retry.

### Step 2: Plan cuts

Pass through every paragraph of the draft. For each rule in the loaded ruleset, identify passages that fire.

For each firing passage, decide one of three actions:

- **Delete** — the passage is pure filler. The surrounding text reads fine without it. Hollow connectors, empty intensifiers, and stock urgency phrases are usually deletes.
- **Collapse** — the passage is load-bearing but bloated. Rewrite the sentence to keep its function while removing the AI pattern. Use only words and concepts already present in the draft. Do not introduce new claims, facts, or framing.
- **Placeholder** — the passage cannot be cut without breaking the sentence, and the skill does not have the specific fact needed to replace it cleanly. Insert an inline `[NEEDS SPECIFIC: <what's missing>]` marker.

### Step 3: Apply cuts

Produce the stripped draft. The stripped draft is:

- Plain prose, no inline annotations, no strike-through, no markers — except `[NEEDS SPECIFIC: ...]` placeholders where the skill could not safely cut.
- Paste-able as-is into any destination (CMS, doc, email).
- Faithful to the original's argument and intent. Do not reorder paragraphs. Do not introduce new ideas. Do not insert voice the original did not have. Note: argument is not the same as structure — the skill is free to restructure sentences, integrate fragments into flowing prose, and dissolve formulaic patterns like staccato rhythm, two-sentence quips, and bullet-list scaffolds. The constraint is on inventing content, not on preserving form.

### Step 4: Output

**Default output:** the stripped draft. Nothing else.

```
[stripped draft, copy-pasteable, with [NEEDS SPECIFIC: ...] placeholders inline where applicable]
```

No preamble. No "here is your stripped draft." No summary. Just the draft.

**With `--report` flag (or if user explicitly asks for a report):** stripped draft, then a horizontal rule, then a compact diagnostic block.

```
[stripped draft]

---

## Dissolve AI report

**Cuts:** N
**Words removed:** M of total (X%)
**Top patterns:** [pattern name] (count), [pattern name] (count), [pattern name] (count)
**Placeholders inserted:** P

### Cuts

| # | Paragraph | Original | Action | Rule |
|---|-----------|----------|--------|------|
| 1 | 1 | "It's worth noting that..." | Deleted | Hollow connector |
| 2 | 1 | "...stands as a transformative force..." | Collapsed | Inflated significance |
| 3 | 3 | "enhanced efficiency, personalized experiences, and data-driven insights" | Placeholder | Formulaic three-item list |

[...one row per cut...]
```

Keep the report compact. It is a reference for power users — not a graded report card.

## The three action types in detail

### Delete

Use when removing the passage causes no structural damage. The next sentence still reads cleanly.

Examples of typical deletes:
- "It's worth noting that"
- "In today's rapidly evolving digital landscape"
- "In conclusion,"
- "You'll be amazed by what's possible."
- "The transformation is already underway."

### Collapse

Use when the sentence is structurally necessary but bloated. Rewrite to keep its function with fewer words and no AI patterns. Constraints:

- Use only words and concepts already in the draft.
- Do not introduce new facts, numbers, names, or framings.
- If a clean collapse requires information not in the draft, use a Placeholder instead.

Example:
- Original: "AI has emerged as a pivotal tool — one that marketers can no longer afford to ignore."
- Collapsed: "Marketers are using AI." (If the surrounding text doesn't already say this, even the collapse may not be safe — consider Delete or Placeholder.)

### Placeholder

Use when the passage is load-bearing AND the skill cannot replace it without inventing a fact. The placeholder format is:

```
[NEEDS SPECIFIC: <one short phrase describing what's missing>]
```

Examples:
- "Vanguard cut its marketing ops team by [NEEDS SPECIFIC: percentage] after [NEEDS SPECIFIC: which AI deployment]."
- "The benefits are [NEEDS SPECIFIC: name one concrete outcome with a number]."

Placeholders are honest about what the skill cannot do without guidance. They are greppable and obvious. The user cannot ship the draft without resolving them, which is the point.

## What this skill does NOT do

- It does not generate voice the original did not have.
- It does not introduce facts, numbers, names, or claims the original did not include.
- It does not rewrite your text to sound "correct."
- It does not score writing quality. A stripped draft is not necessarily a good draft — it is a draft without the AI tells.
- It does not check facts, citations, audience fit, or brand voice.
- It does not reorder paragraphs or restructure arguments.

## Limits to acknowledge

The skill removes patterns. It cannot supply substance. If the original draft is entirely filler, the stripped draft will be sparse — often a series of `[NEEDS SPECIFIC: ...]` placeholders. That is the correct output. It exposes how much of the original was carrying no information. Present it without apology.

Human editorial judgment still owns the final call. The skill produces input to a decision; it does not make the decision.
