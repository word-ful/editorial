# Changelog

All notable changes to Wordful Editorial skills are documented here.

The format follows [Keep a Changelog](https://keepachangelog.com/en/1.1.0/), and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

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
