# coder-tdd-qa

A portable rulebook for AI coding agents: test-driven development, honest
verification, and a size-gated release checklist — in one markdown file that works
in Claude Code, Codex, or any agent that reads instructions.

## What this is (plain English)

AI coding assistants have a bad habit: they write code, say "done, it works," and
move on — without ever proving it. Sometimes the tests they wrote don't actually
test anything. Sometimes they summarize a test run in a way that hides failures.

This project is a set of written rules you hand to your AI assistant that closes
those loopholes. The core idea is simple: **a test only counts if the assistant
watched it fail first.** A test that has never failed might be testing nothing at
all. So the rules force the assistant to write the test, watch it fail, then write
the code that makes it pass — and to show you the raw, uneditable proof at each
step. Before calling anything done, the assistant must also try to *break* its own
work and tell you what happened.

You don't need to understand the rules to benefit from them. Install the file,
and your assistant follows them.

## Install (technical)

**Claude Code** — copy [SKILL.md](SKILL.md) into a skills directory:

```
# personal (all projects)
~/.claude/skills/coder-tdd-qa/SKILL.md

# or per-project
<repo>/.claude/skills/coder-tdd-qa/SKILL.md
```

**Codex / other agents** — paste everything below the YAML frontmatter of
[SKILL.md](SKILL.md) into the repo's `AGENTS.md` (or the agent's system prompt).
The body is harness-agnostic by construction: no tool names, no skill-loader
features, no file-layout assumptions.

## What's inside

| Section | What it does |
|---|---|
| Hard Rules | 8 rules; 1–5 non-negotiable (read-before-write, baseline-before-change, run-before-done, TDD, no secrets), 6–8 overridable with acknowledgment |
| Evidence Format | Anti-fabrication: exact command + verbatim counts line + all failures in full; only per-test PASS spam may be collapsed |
| The TDD Loop | Red → watch it fail on the assertion → minimal green → refactor → widen against the baseline. Bug fixes start with a failing reproduction test |
| Roles | Engineer / UI designer / QA lenses, applied only where the task involves them |
| Workflow | Before/during/when-things-go-wrong, checkpoint-before-risk, task-type-switch rule |
| Verification Report | Scaled report: baseline vs. end state, TDD evidence, a falsification pass (try to break your own change), a security checklist with per-item answers |
| Release Gate | Push = release event. Three tiers so a weekend utility doesn't get flagship ceremony |

## Design principles

- **Tests must be real, not merely present.** "Write a test" is a rule an agent can
  satisfy with a test that asserts nothing. Watching it fail on its assertion is
  the only cheap guarantee it's wired to the behavior. That's why TDD is the core,
  not an add-on.
- **Evidence, not assertions.** Verbatim counts and complete failures are an
  anti-fraud forcing function — summarized output is where fake greens hide.
- **Falsify before sign-off.** A self-report only surfaces the gaps the
  self-reporter looks for. The rules require an adversarial pass against the
  agent's own change.
- **Baseline first.** Red→green is meaningless if the suite was already red when
  the agent arrived. Pre-existing failures are recorded and tracked separately.
- **Ceremony scales with stakes.** Every public repo gets a secrets scan and
  hygiene files; only published packages get packaging checks; only flagship
  projects get manuals and landing pages, and only when asked.
- **Each rule stated once.** No duplication between sections — later sections
  reference, never restate.

## Requirements

None. It's a markdown file. Any agent that reads instructions can use it.

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md).

## License

[MIT](LICENSE)
