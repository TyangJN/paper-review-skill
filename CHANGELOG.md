# Changelog

Noteworthy changes are recorded here. Releases use version tags so the workflow can be inspected and compared over time.

## Unreleased

### Changed

- Renamed the repository and current skill entrypoint from `review-skill` to `paper-review-skill` to make the academic paper review purpose explicit.
- Updated the README, package directory, invocation examples, and release display name.
- Preserved the published `v1.0.0` tag and its source snapshot; the naming update is tracked in a new commit on `main`.

## 1.0.0 — 2026-10-27

### Added

- A single English `review-skill` entrypoint for full review, targeted reassessment, and review editing.
- An eight-stage workflow covering material screening, scope, comprehension, evidence verification, comment selection, assessment, writing, and final checks.
- Separate prompt-injection alerts and author-facing review templates.
- Concise and extended review templates, plus brief evidence records.
- Explicit limits of three strengths and three weaknesses, with no requirement to fill them.
- Guidance on faithful claim paraphrasing, configuration-aware contradiction checks, and consistent factual status across records and final judgments.
- Review references and attribution to the DeerFlow and jam-cc review skills.
- A description of limited prior evaluation, current uncertainty, and gradual improvement priorities.

### Validation

- Skill structure and packaged local references checked.
- Prior evaluations concerned the underlying Chinese workflows. This release does not claim a demonstrated overall advantage over the referenced skills or a completed independent evaluation of the English edition.
