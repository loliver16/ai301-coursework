# Evidence guide: where evidence lives in a PR package

<!--
THIS IS THE PART YOU WRITE (third week running: the map stays in your
hands). Your tool uses this guide as its map: for every kind of
evidence a rubric check names, this file says WHERE to find it in a PR
package and WHAT GOOD LOOKS LIKE when you do.

The four families below are the harness's failure categories under
the names the eval README uses: plan fidelity = silent-drift, test
evidence = not-tested, diff quality = unreviewable, standards and
comms = standards-wall. A package that fails none of them is a
clear-accept. Under each family heading below, write:

- Where it lives: the exact places to look. In an eval bundle (which
  section of the package: the plan-context block's scope pair and test
  plan, the candidate PR's diff, commits, description, or
  test-evidence section, the repo-facts block's template asks and
  stated policy). In live mode (where in your working copy and on
  GitHub: your plan.md and its deviation notes, your branch's diff,
  your draft title and description, your captured test output, the
  repo's PR template and CONTRIBUTING.md).
- What good looks like: one or two sentences someone else could apply.
  Prefer observable conditions ("every changed file falls inside the
  plan's stated boundary or a deviation note") over adjectives ("the
  diff is clean").

A rubric check whose evidence this guide cannot locate is a check
nobody else can execute, and this week that cuts three ways: your
procedure says WHEN to gather each family, this guide says WHERE, and
your SKILL.md says the tool reads both. Write the map you wish your
executor had.
-->

## Plan fidelity (harness category: silent-drift)

<!-- Where the plan states its scope, boundary, and deviation notes,
and where the diff shows what actually changed. What it means for a
diff to match the plan, for an honest deviation to re-tie a mismatch,
and what silent drift looks like in each direction (more than the
plan, or less with no note). The description's fidelity claims read
against the diff live here too: a description claiming more or less
than the diff delivers is silent drift, not a comms problem. -->

**Where it lives**
- *Eval bundle:* the plan-context block holds the plan's stated scope, its boundary, and any deviation notes. The candidate PR's diff and commits show what actually changed. The candidate PR's description holds the fidelity claims.
- *Live mode:* `plan.md` in the working copy (scope, boundary, and every deviation note), `git diff main...HEAD` for the change (substitute the default branch if it is not `main`), `git log main..HEAD` for the commits, and the title and description in `pr_draft.md`. A house-chain student reads the house plan instead of `plan.md`.
**What good looks like**
- Every changed file and behavior falls inside the plan's stated boundary or inside a recorded deviation note.
- Everything the plan promises is present in the diff, or a deviation note or the description says what was left out.
- An honest deviation re-ties a mismatch: a note that names what changed and why makes the diff match the plan again.
**What drift looks like**
- *More than the plan:* the diff changes behavior, files, or areas the plan never named, with no note.
- *Less than the plan:* a promised piece is missing from the diff, with no note.
- *Claims the diff contradicts:* the description says "only touches X" or "fully fixes Y" and the diff shows otherwise. A description that claims more or less than the diff delivers is silent drift, not a comms problem.

## Test evidence (harness category: not-tested)

<!-- Where the PR shows its proof: the test-evidence section's
before/after against the plan's test plan and the reproduction's own
steps, and the outcome of the repo's own checks or suite. What
decisive looks like (an observable behavior named, the expected-after
stated, the checks' outcome visible) next to "tests pass". -->

**Where it lives**
- *Eval bundle:* the candidate PR's test-evidence section, read against the plan-context block's test plan and the reproduction's own steps.
- *Live mode:* `test_evidence.md` (the captured output of the repo's own test suite and the before-and-after repro), read against the test plan in `plan.md`. The command that runs the repo's own checks is in the repo's README or CI config. A house-chain student reads the house repro pack's steps.
**What good looks like**
- The repo's own checks were run on this branch, and their outcome is visible: the command, and a passing result, or a failing result with its reason stated.
- The repro shows an observable before and after: a named behavior, the expected result after the change, and the actual result after the change.
- The description's testing claims match what the output shows.
**What does not count**
- Assertion alone: "tests pass", "works for me", "tested locally".
- A suite that was never run, or output that does not belong to this branch.
- A repro whose "after" restates the fix instead of showing the behavior.
- Output that contradicts the description, such as "all tests pass" beside a failure.

## Diff quality (harness category: unreviewable)

<!-- Where the change itself lives: the unified diff and the commit
list. What a reviewable change looks like (the fix visible, nothing
unrelated riding along) and the debris tells: debug leftovers, dead
code, commented-out blocks, formatting churn, drive-by edits. -->

**Where it lives**
- *Eval bundle:* the candidate PR's unified diff and its commit list.
- *Live mode:* `git diff main...HEAD` (the full branch diff) and `git log main..HEAD`. Run `git status` as well, to see whether working notes are sitting in the working copy.
**What good looks like**
- The fix is visible: a reviewer can read the diff and see what changed and why.
- Every file and hunk traces back to the plan or a deviation note, and nothing unrelated rides along. Judge by what is in the diff, not by how big it is or how many commits it has.
**The debris tells**
- Working notes committed into the change: `plan.md`, `pr_draft.md`, `test_evidence.md`.
- Debug leftovers: stray `print` or logging calls, temporary flags, scratch files.
- Dead code and commented-out blocks.
- Committed build or generated artifacts.
- Formatting churn: whitespace, re-indentation, or reordering in lines the change did not need to touch.
- Drive-by edits: unrelated fixes or cleanups in files the plan did not name.

## Standards and comms (harness category: standards-wall)

<!-- Where the repo states its asks (the repo-facts block's PR
template sections, contributing instructions, and stated policy,
including AI-use disclosure) and where the PR honors them: the
stated sections filled with real content, the disclosure present,
explicit maintainer direction in the thread engaged. What compliant
looks like next to boilerplate or a visibly ignored ask. (Whether
the description's claims match the diff is plan fidelity, above.) -->

**Where it lives**
- *Eval bundle:* the repo-facts block holds the PR template's sections and asks, the contributing instructions, and the stated policy, including the AI-use disclosure rule. The candidate PR's description is what gets checked against them.
- *Live mode:* the repo's PR template at `.github/PULL_REQUEST_TEMPLATE.md`, the repo's `CONTRIBUTING.md`, any policy the repo states (and the house rules in `scope.md`), and the issue thread for explicit maintainer direction. Check them against the title and description in `pr_draft.md`.
**What good looks like**
- Every section of the template is filled with real content. A short answer that actually answers counts.
- If the template or the repo's stated policy asks for an AI-use disclosure, it is present, in the author's own words. If neither asks for one, its absence is not a failure. (In live mode, Path Review's template has a disclosure section, so it applies.)
- The issue is named (for example, `Fixes #<number>`).
- The title and description let a reader tell what the PR does and why.
- Explicit maintainer direction in the thread is engaged with, not ignored.
**What does not count**
- Boilerplate: a section left blank, filled with placeholder text, or marked "N/A" with no reason.
- Deleted template headings.
- A visibly ignored ask: a stated policy or maintainer instruction the PR does not follow.

Whether the description's claims match the diff is plan fidelity, above, not a standards-and-comms question.
