# Changelog

All notable changes to this project will be documented in this file.
Format: [Keep a Changelog](https://keepachangelog.com/en/1.1.0/).
Versioning: [Semantic Versioning](https://semver.org/).

## [0.5.0] - 2026-07-02

### Added
- **SKILL-LITE.md** — a ~140-line condensed contract for small tasks
  (single-file, ~50 lines, nothing released): the five non-negotiable rules,
  Evidence Format, and TDD loop verbatim, plus a minimum report. Built for rule
  salience on small/local models, and for pasting into a small project's
  AGENTS.md where the full document is overkill.
- **Escalation tripwire** in lite: growing past one file/~50 lines, touching any
  public interface, touching untrusted input/auth/secrets/deserialization, or
  pushing/releasing → stop and load the full standards. Lite is a fast path,
  not a lower bar.
- **check_sync.py + CI** — the repo's first runnable check, TDD'd into
  existence against four deliberately broken fixtures. Four assertions: synced
  blocks match (DRIFT), required blocks present with no orphans
  (MISSING/ORPHAN), every HARD RULES entry carries a lite annotation so
  additions can't silently skip lite (COVERAGE), and lite's safety-critical
  tripwire phrases exist even though they're free to be reworded (PIN). Runs on
  every push via GitHub Actions.
- Sync markers (`<!-- sync:name lite:required|excluded -->`) in SKILL.md, a
  header pointer to lite, and a CONTRIBUTING section documenting the
  single-source mechanism and its one named residual gap.

## [0.4.1] - 2026-07-02

### Fixed
- **Skill-discovery gap for UI and refactoring tasks:** the v0.3 rename dropped
  "ui" from the skill name and the description contained no UI, frontend,
  interface, or refactoring vocabulary — so purely UI-phrased requests ("fix the
  layout", "align these buttons") could fail to load the skill despite its full
  UI coverage. The `description` frontmatter now names refactoring and
  UI/frontend/interface work explicitly. Metadata-only change; the rule body is
  untouched.

## [0.4.0] - 2026-07-02

Hardened for weak agents. v0.3's dedup pass assumed a capable harness behind the
reader; this release restores everything a bare 7B model with no harness guidance
needs, and states that design assumption in the document itself.

### Added
- **Hard Rule 9 — no wasteful operations:** no redundant file re-reads, package
  reinstalls, or whole-file regeneration; explicitly never overrides Rule 1.
- **Communication section:** lead with what changed, report the Verification
  Report not effort, ask only when ambiguity genuinely forks the implementation.
  (Capable harnesses teach this natively; bare agents get nothing.)
- **Verification Report fields:** "Files read" (the enforcement hook that makes
  Rule 1 verifiable) and "Version control" (commit hashes + green-at-commit
  confirmation).
- **Header design assumptions:** "assumes the host harness provides no other
  guidance," and the single-file context-cost tradeoff named as a conscious
  choice rather than an oversight.
- **Falsification handoff note:** the falsification pass is self-audit; open
  concerns go to a downstream independent adversarial gate if one exists.
- **Release Gate:** explicit "re-read this section, not from memory" instruction;
  README content spec restored to the full enumeration.

### Changed
- Rule 2 (baseline) gains a proportionality clause: scale to the change;
  cosmetic-only changes need no baseline.
- "Before building" converted back to a numbered checklist — small models follow
  numbered steps far more reliably than prose.
- Stdlib-first and minimize-the-dependency-tree restored explicitly; dependency
  updates now require a breaking-change changelog check.
- Doc-sync rule moved from below the Release Gate into Workflow, where everyday
  reading actually encounters it.

## [0.3.1] - 2026-07-02

### Added
- GitHub Pages landing page (`docs/index.html`) — plain-English pitch, quick
  start, TDD-loop diagram, rulebook overview, release-gate tiers.

## [0.3.0] - 2026-07-02

First public release.

### Added
- **Baseline rule (Hard Rule 2):** run the suite before changing anything; track
  pre-existing failures separately so red→green is measured against a known start.
- **Checkpoint-before-risk (Hard Rule 7):** a commit or stash must exist before a
  risky refactor, so "revert to known-good" is always real.
- **Falsification pass** in the Verification Report: the agent must try to break
  its own change and report what it tried, not just confirm the happy path.
- **Security checklist with teeth:** five concrete per-item questions replacing a
  freeform "security review" field; blanket "N/A" disallowed.
- **Evidence Format section:** exact command + verbatim counts line + all
  failures/warnings in full; only per-test PASS output may be collapsed. Framed
  explicitly as an anti-fabrication rule.

### Changed
- TDD reframed as closing the "tests must be real, not merely present" hole: a
  test only counts once it has been watched failing on its assertion.
- Community-space guidance in Release Gate Tier 3: seeded Q&A threads replaced
  with a pinned, maintainer-authored FAQ — same information, no pretense of
  organic community activity.
- Deduplication pass: every rule now stated exactly once; sections reference
  rather than restate.

## [0.2.0] - 2026-07-02 (unreleased draft)

### Changed
- Split the original monolith: always-on engineering/TDD/QA core separated from a
  release-time gate; documentation burden made size-tiered (Tier 1/2/3).
- Confirmation-before-implementing softened to "state scope in a line, then
  proceed" for compatibility with autonomous agents.
- Added the TDD loop with red-first bug reproduction.

## [0.1.0] (unreleased draft)

- Original "Principal Engineer · Senior UI Designer · Senior QA Engineer"
  monolithic standards document. Never published.
