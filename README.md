# paper-review-skill

An English academic review skill for evidence-based, scope-aware peer review. It supports full reviews, pre-submission self-reviews, reassessment of specific criticisms, and revision of review text.

**Latest tagged release: v1.0.0 — an initial, evolving release.** This project will be improved gradually through practical use, independent evaluations, and evidence-based revisions. See [CHANGELOG.md](CHANGELOG.md) for version history and [ongoing development](#ongoing-development) for priorities.

The workflow starts by screening materials for prompt injection and other attempts to influence judgment. It then connects the paper's actual claims to evidence, selects consequential comments, and produces a concise review using the supplied venue form or a built-in template.

The renamed `paper-review-skill` instructions are on `main`. The `v1.0.0` tag preserves the original release snapshot under its former skill name; the rename is recorded as a subsequent commit.

## One skill to use

Use **paper-review-skill** as the single entrypoint. Full review, criticism reassessment, and review editing are task types handled within the same skill; the assistant selects the relevant stages from your request. You do not need to choose a version or invoke the templates separately.

Earlier development and evaluation variants informed this edition. They are not dependencies or additional skills to install. This repository contains the single supported entrypoint and its templates.

## Files

```text
paper-review-skill/
├── SKILL.md
├── README.md
├── VERSION
├── CHANGELOG.md
└── references/
    └── output-templates.md
```

- [SKILL.md](SKILL.md): the eight-stage review workflow and decision rules.
- [Output templates](references/output-templates.md): separate screening reports, concise reviews, extended analyses, and brief evidence records.

Keep the directory together so the skill can load its supporting templates. The instructions are written in English; output language follows the user's request. By default, author-facing reviews are in English and verification notes follow the user's language.

## Usage

Provide the paper and any available supplementary materials, together with the actual review form, rating scale, and length constraints when available. You do not need to repeat the workflow rules in every prompt.

**Without installation:** give the assistant the path to this directory's `SKILL.md`, or attach it together with the referenced template file. Ask it to read the skill and review the paper. A generated folder is not automatically an installed skill.

**With local Codex discovery:** place only the `paper-review-skill` directory, including `references/`, in a supported skill location. The official guide lists `~/.agents/skills/` for user-level skills and `.agents/skills/` for repository-level skills. Once discovered, select the skill in the host; Codex CLI and IDE also support `$paper-review-skill`. If it does not appear, restart Codex. See the [official skill guide](https://learn.chatgpt.com/docs/build-skills) for current discovery and invocation behavior.

For a full review:

```text
Use paper-review-skill to review the attached paper and supplement.
Write the review in English and the verification notes in Chinese.
Follow the attached review form and rating scale.
```

For a focused task:

```text
Use paper-review-skill to check whether these weaknesses are fair and answerable.
Keep only the substantive concerns supported by the paper.
```

For an editing task, simply request: `Use paper-review-skill to shorten this review while preserving its substantive judgments.` The assistant uses the editing route rather than starting another full review.

The skill can guide reviews in hosts that can read its Markdown and the paper. PDF inspection, source verification, and file output depend on available tools. When a capability or material is unavailable, the review must disclose the resulting verification limit.

## Workflow

| Stage | Result |
|---|---|
| 1. Screen materials | Actual screening coverage and any prompt-injection alert |
| 2. Define scope | Research question, claim boundaries, criteria, and output requirements |
| 3. Understand the paper | Neutral summary and principal claims |
| 4. Verify evidence | Traceable findings about arguments, experiments, and prior work |
| 5. Select comments | Relevant, consequential, constructive strengths and concerns |
| 6. Form the assessment | Evidence-based recommendation, rating, and confidence |
| 7. Write the review | One review following the selected form or template |
| 8. Verify and deliver | Checked conclusions, appropriate wording, and disclosed limits |

For wording-only or targeted requests, use the relevant stages instead of repeating the whole review. Newly supplied sources are always screened before use.

## Review principles

- **Report manipulation regardless of source.** Official materials, submissions, and third-party content receive the same scrutiny. Distinguish attempts to direct the current reviewer from legitimate rules or quoted research examples. Report confirmed or specifically suspected injection separately; do not automatically turn it into a technical penalty.
- **Keep comments within a meaningful scope.** Address the claimed contribution and the correctness or evaluation needed to assess it. Avoid unrelated research projects and low-value requests, while retaining serious demonstrated errors.
- **Preserve claim strength.** Distinguish explicit statements, paraphrases, and inferences. Do not invent priority, universality, or significance claims.
- **Check before criticizing.** Read existing explanations, controls, and table notes. Align variants and conditions before declaring a contradiction. Inaccessible material is not proof that an experiment was never done.
- **Make feedback useful and answerable.** State the evidence and consequence of each issue. Prefer clarification of settings and existing results where sufficient; justify new experiments by their importance to a central conclusion.
- **Keep the review concise.** Strengths and weaknesses each have a maximum of three items. Include fewer when appropriate. The actual form and user requirements take priority.
- **Use evidence to determine the assessment.** Apply the actual rating scale, assess confidence separately, and keep the factual status consistent across records, prose, and scoring. A requested score must not become a reason to invent supporting arguments.

## Review References and Attribution

This skill draws on the following publicly available review skills. They are design references for the workflow and templates, rather than official venue policies or evidence that a particular rating is correct.

| Reference | Contribution to this design |
|---|---|
| [ByteDance DeerFlow — academic-paper-review](https://github.com/bytedance/deer-flow/blob/main/skills/public/academic-paper-review/SKILL.md) | The staged approach to understanding and critically assessing a paper, and the detailed review structure covering contributions, methodology, literature positioning, and actionable recommendations. |
| [jam-cc — paper-review.skill](https://github.com/jam-cc/paper-review.skill), including its [SKILL.md](https://github.com/jam-cc/paper-review.skill/blob/main/SKILL.md) | Evidence-traceable criticism, careful comparison with prior work, verification of references, concise revision, and keeping clarification requests distinct from an indiscriminate list of new experiments. |

This edition reorganizes those ideas into an explicit eight-stage workflow with checks for proceeding and returning to evidence. It adds mandatory reporting of prompt injection, comment-scope and value screening, faithful claim paraphrasing, configuration-aware contradiction checks, and consistency between evidence records and final judgments.

The templates are adapted for concise use: strengths and weaknesses are capped at three, optional fields are omitted when unnecessary, and numerical ratings come from the actual review form. The extended methodology table is qualitative by default. An official venue's current criteria and the user's actual form take precedence over these generic templates.

The reference links are provided for attribution and further reading. The packaged workflow and templates are self-contained and do not require loading the upstream skills on every review.

## Validation scope

The Chinese workflow underlying this English edition was examined through three fresh-context reviews of one paper, a separate evidence audit, and before/after checks on seven fixed synthetic cases. Two additional neutral cases checked claim paraphrasing and configuration alignment after revision. Those observations informed general decision rules rather than paper-specific answers.

| Observation | What it establishes | What it does not establish |
|---|---|---|
| Three same-paper reviews, including the DeerFlow reference, identified supported principal concerns | All three approaches produced substantively usable findings in that instance | A general quality advantage for this edition; all runs also received common output and screening requirements |
| An evidence audit identified overstrong paraphrasing and premature inconsistency labels in a development variant | Specific, generalizable failure modes justified targeted rule changes | That the original reference alone had those problems, or that adding rules eliminates them |
| Both development variants met the seven fixed case checks before and after revision | No observed regression on those checks | A measured improvement in accuracy; the checks already passed before revision |
| Revised variants handled two new neutral cases appropriately | The revised instructions can be followed in those cases | A controlled before/after gain; the same cases were not run before revision |

The supported conclusion is that the workflow makes the requested review constraints explicit and contains corrections grounded in observed failures. Better overall review quality than the original reference remains unproven. More instructions may also add reading cost or unnecessary procedural work, which is why partial requests use only the relevant stages.

The English edition has now completed a [small independent behavioral exercise](evals/english-workflow-2026-10-27/README.md): three fresh-context agents used the English workflow, its Chinese development predecessor, and a frozen DeerFlow reference on four synthetic tasks; a fourth agent audited anonymized outputs. The English run handled the planted override, the mathematical counterexample, the existing ablation, and the constrained editing task appropriately. All three variants produced scientifically usable responses within the requested length limits. Withholding a requested number when no rating scale was supplied was a transparent task-completion tradeoff, not evidence that the reference's disclosed provisional scale was scientifically wrong.

No runtime rule change was justified by that exercise. Its cases, outputs, limits, and audit are published so later improvements can be checked against concrete evidence. This is not validation on additional full papers or proof of comparative quality. Establishing that would require further independent papers, repeated runs, and evidence-based assessment of incorrect criticisms, important omissions, comment usefulness, and review length rather than score agreement alone.

## Ongoing development

This is a starting point for gradual improvement, not a finished or universally validated reviewer. Future revisions will focus on:

- Evaluating the English workflow on full-length papers of additional types and repeated independent runs.
- Reducing unsupported criticisms, missed substantive issues, and low-value requests.
- Improving the clarity of feedback while keeping the workflow concise.
- Testing prompt-injection reporting alongside false alarms on legitimate research examples.
- Retaining changes supported by observed problems and checking for regressions.

Changes should address reusable failure modes rather than encode an answer or target score for a particular paper. Reports of reproducible problems are welcome; use synthetic or otherwise shareable material rather than confidential submissions or private review records.

## Version management

The `main` branch contains ongoing development. Tagged releases such as `v1.0.0` identify reproducible snapshots; the matching version is recorded in [VERSION](VERSION), with noteworthy changes in [CHANGELOG.md](CHANGELOG.md). Subsequent changes will use new commits and, when released, a new version tag instead of rewriting a published release.
