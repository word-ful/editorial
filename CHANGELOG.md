# Changelog

All notable changes to Wordful Editorial skills are documented here.

The format follows [Keep a Changelog](https://keepachangelog.com/en/1.1.0/), and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

## [0.2.2] — 2026-05-11

### Changed
- Dropped "Claude Code" from top-line positioning in both READMEs. The skill is described as "a skill" rather than "a Claude Code skill" to keep brand framing platform-agnostic. Technical install/usage instructions still reference Claude Code where accurate.
- Added a bullet to the "What this skill does NOT do" section in both SKILL.md and dissolve-ai/README.md: *It does not rewrite your text to sound "correct."* Clarifies that Dissolve AI removes patterns; it does not impose a house style or "fix" prose toward any standard of correctness.

## [0.2.1] — 2026-05-11

### Changed
- **dissolve-ai SKILL.md** — clarified that "faithful to the original" means faithful to the *argument*, not the *structure*. The skill is free to restructure sentences, integrate fragments, and dissolve formulaic patterns. The previous wording created a loophole that allowed protecting platform-native cadences (e.g. LinkedIn-style staccato fragments and two-sentence quips) as "structure."
- **dissolve-ai examples** — replaced the synthesized marketing-paragraph example with a real LinkedIn post strip. The new example demonstrates pattern dissolution on competently written but heavily patterned prose, where the issue is cadence rather than empty filler.

## [0.2.0] — 2026-05-11

### Changed
- **dissolve-ai** is now Strip mode by default. The skill returns a cleaned draft with AI patterns removed — no commentary, no findings, no summary. Previous Review-mode behavior moved behind an opt-in `--report` flag.
- Strip mode applies one of three actions per flagged passage: Delete (cut entirely), Collapse (rewrite using only words already in the draft), or Placeholder (insert an inline `[NEEDS SPECIFIC: ...]` marker where the skill cannot replace without inventing facts).
- Skill description and trigger phrasing updated to lead with strip behavior.

### Rationale
A report is a lecture the user did not ask for. The stripped draft is the deliverable. Most users will read it, decide if it works, and ship it or revert. The diagnostic block remains available for power users via `--report`.

## [0.1.0] — 2026-05-11

### Added
- `dissolve-ai` skill — Review-mode scanner for catalogued AI writing patterns. Returns a structured findings report with flagged passages, rule references, severity, and clustering signals.
