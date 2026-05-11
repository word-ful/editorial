---
name: dissolve-ai
description: Manual-invocation skill for reviewing prose drafts against a catalogued ruleset of AI writing patterns. Invoke ONLY when the user explicitly runs /dissolve-ai or asks by name — e.g. "run Dissolve AI on this", "check this with Dissolve AI", "review this for AI patterns using Dissolve AI". Scans the draft against rules covering inflated significance, promotional framing, emotional projection, hollow connector phrases, em-dash overuse, formulaic three-item lists, structural repetition, and related tells. Returns a structured findings report with quoted passages, rule references, severity, and clustering signals. Operates in Review mode only — flags issues, does not rewrite. Do NOT auto-trigger on general writing tasks, blog drafts, code review, or unrelated content. This skill activates only on explicit invocation.
---

# Dissolve AI

A review-mode skill that scans prose drafts for the writing patterns that mark content as machine-generated.

## When to invoke

Only when the user explicitly asks for this skill by name. Triggers include:

- `/dissolve-ai`
- "run Dissolve AI on this"
- "check this with Dissolve AI"
- "review this draft for AI patterns" (when the user has named this skill in context)

Do NOT invoke on generic writing-help requests, editing requests, or code review. If the user is asking for general writing feedback without naming this skill, do not run it.

## How it works

### Step 1: Load the reference

Before doing anything else, read [`reference/patterns.md`](./reference/patterns.md) in full. It is in the same directory as this SKILL.md.

If it cannot be loaded, stop and output:

> **Dissolve AI: `reference/patterns.md` not found — cannot proceed.** Locate the file and retry.

### Step 2: Scan the draft

Pass through every paragraph of the draft. For each rule in the loaded ruleset, check whether the draft contains the pattern.

For each hit, record:

- The quoted passage (exact text from the draft)
- The rule name
- A one-line explanation of why this pattern fires here
- Severity (Low / Medium / High — see below)

**Severity guide:**

- **Low** — a single instance of a low-risk pattern in an otherwise clean draft
- **Medium** — a clear instance of a pattern, or a low-risk pattern repeated
- **High** — a strong instance of a high-risk pattern (inflated significance, hollow connector, emotional projection in opening or closing position), or a pattern that clusters with others

### Step 3: Apply flagging rules

- Flag **clustering**: multiple flagged patterns in the same paragraph signal a structural problem, not a word-choice problem.
- Flag **frequency**: the same pattern repeating across multiple sections signals formulaic construction.
- Flag **structural repetition**: identical sentence architecture repeated across sections, regardless of vocabulary.
- Do not flag isolated instances of low-risk patterns unless they compound with others. An occasional em-dash is fine; em-dashes as the dominant rhythm device is not.

### Step 4: Produce the report

Output a Markdown report using the format below. Do not paraphrase the draft. Quote the actual passages.

## Output format

```
# Dissolve AI Review

**Verdict:** [Clean / Minor flags / Major flags / Heavy AI patterning]
**Flags found:** N
**Overall severity:** [Low / Medium / High]

## Summary

[1–2 sentences describing the overall pattern of issues, or noting that the draft reads cleanly. If patterns cluster in specific sections, name those sections.]

## Findings

### 1. [Rule name]

> [Quoted passage from the draft, exact wording]

**Why this fires:** [One-line explanation, specific to this passage.]
**Severity:** [Low / Medium / High]

### 2. [Rule name]

> [Quoted passage]

**Why this fires:** [...]
**Severity:** [...]

[...continue for each finding...]

## Pattern clustering

[If clustering detected: identify which paragraphs and which patterns. Otherwise: "None detected."]

## Structural repetition

[If detected: describe the repeated structure with examples. Otherwise: "None detected."]

## Recommended priorities

[Top 3 issues to address first, in order. Skip this section if Verdict is "Clean".]
```

## What this skill does NOT do

- It does not rewrite the draft. Review mode only in v1.
- It does not score overall writing quality. A draft can pass every check and still be poorly argued.
- It does not check facts, citations, or claims.
- It does not check tone, brand voice, or audience fit.

## Limits to acknowledge

This is a pattern-detection tool. Patterns are diagnostic signals, not verdicts. A draft can fire several flags and still be the right piece — context matters, and a human editor still owns the final call. Present the report as input to a decision, not as the decision itself.
