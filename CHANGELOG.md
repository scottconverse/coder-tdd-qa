# Changelog

All notable changes to this project will be documented in this file.
Format: [Keep a Changelog](https://keepachangelog.com/en/1.1.0/).
Versioning: [Semantic Versioning](https://semver.org/).

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
