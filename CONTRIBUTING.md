# Contributing

This project is a single markdown rulebook ([SKILL.md](SKILL.md)). There is no
build, no dependencies, and no test suite — the "code" is prose that agents
execute. That makes review standards *more* important, not less.

## Setup

```
git clone https://github.com/scottconverse/coder-tdd-qa.git
```

That's it. Edit `SKILL.md` with any editor.

## Rules for changes

1. **Portability is a hard constraint.** The body below the YAML frontmatter must
   work pasted into any agent's instructions: no Claude-specific tool names, no
   skill-loader features, no harness assumptions. If your change references a
   specific product's feature, it belongs in the README's install section, not in
   SKILL.md.
2. **Each rule stated once.** If your addition restates an existing rule in new
   words, reference the rule instead. Dedup is a feature of this document.
3. **Rules must be checkable.** "Own security" is a wish; "answer these five
   questions per change" is a rule. Prefer the form an agent can be caught
   violating.
4. **Don't grow the everyday core for release-time concerns.** Anything that only
   matters at push/publish time goes in the Release Gate, gated by tier.
5. **Update CHANGELOG.md** (Keep a Changelog format) and bump the version in both
   `SKILL.md`'s title line and the changelog, in the same commit.

## Testing a change

The test is a read-through against the failure modes this document exists to
prevent. Before opening a PR, check your changed text against each question:

- Could an agent satisfy the new/changed rule with a test that asserts nothing?
- Could it satisfy the rule by summarizing output instead of pasting it?
- Does the rule still work when the starting test suite is already red?
- Does it conflict with an autonomous (no-confirmation) operating mode?
- Does it force ceremony onto a project too small to need it?

If any answer is yes, the change isn't ready.

## Submitting

Open a PR with a description of what behavior the change prevents or enables in a
real agent session. Anecdotes from actual agent transcripts (what the agent did
wrong under the old wording) are the strongest possible evidence.
