# Evidence guide: where evidence lives in a plan package

<!--
THIS IS THE PART YOU WRITE (second week running: the judgment files
stay in your hands). The skill uses this guide as its map: for every
kind of evidence a rubric check names, this file says WHERE to find it
in a plan package and WHAT GOOD LOOKS LIKE when you do.

Under each family heading below, write:

- Where it lives: the exact places to look. In an eval bundle (which
  section of the package: the issue context, the repro-evidence block,
  the candidate plan's scope statement or test plan, the plan comment,
  the repo-facts block). In live mode (where on GitHub or in the
  draft: the issue thread, the student's posted repro comment, the
  repo's docs, the draft plan and comment).
- What good looks like: one or two sentences someone else could apply.
  Prefer observable conditions ("the stated cause cites behavior the
  repro evidence actually shows") over adjectives ("diagnosis is
  solid").

A rubric check whose evidence this guide cannot locate is a check
nobody else can execute, and this week that cuts twice: your
procedure.md tells the skill WHEN to gather each family, and this
guide tells it WHERE. Write the map you wish your executor had.
-->

## Diagnosis and grounding

<!-- Where the plan states its cause, and where the repro evidence
pins down the behavior that cause must explain. What it means for a
diagnosis to follow from the evidence rather than contradict or
ignore it. -->

**Where it lives:**
- Eval bundle: the cause is stated in the candidate plan (its diagnosis section) and restated in the plan comment. The behavior it must explain is in the repro-evidence block, in every step, especially control runs, isolation steps, debug output, and timing results. The issue context shows what maintainers have already isolated.
- Live mode: the cause is in the diagnosis section of `plan.md` and restated in `comment.md`. The evidence is the student's posted repro comment on the issue (or, on the house issue, the quoted house repro pack in `plan.md`), plus the maintainer comments in the issue thread.

**What good looks like:** The stated cause explains the behavior in the repro evidence, and no repro step contradicts it. The comment states the same cause as the plan. Judge the cause against the steps, not against how confident the plan or the thread sounds.

## Scope

<!-- Where the plan bounds itself: the in-scope statement, the
not-in-scope line, the files or areas named. What one bounded change
looks like next to a drive-by rewrite. -->

**Where it lives:**
- Eval bundle: the plan bounds itself through the candidate plan's scope statement, its approach, and the files or areas it names. This can also include anything the comment lists as not in scopre. Also, check the plan comment for anything it promises beyond the plan.
- Live mode: the same sections in `plan.md`, plus the draft in `comment.md`.
**What good looks like:** Everything listed is needed to fix the reproduced symptom, so the plan is one reviewable change. Extra work the issue never asked for (refactors, migrations, new features) means it is not bounded, even if the core fix is right. A plan narrower than the issue is fine if it says what it defers and why.

## Executability

<!-- Where the plan says what will actually be done: files or areas,
approach, order of work. What it means for a stranger to be able to
start executing without asking the author anything. -->

**Where it lives:**
- Eval bundle: the candidate plan's files/areas and approach sections.
- Live mode: the same sections in `plan.md`; check the named files or areas against the repo itself when possible.
**What good looks like:** The plan names where the change goes and commits to one approach. Someone new to the repo could start working without asking the author anything. Key decisions left for build time ("whichever is easier", "somewhere") or vauge directions mean it is not executable.

## Test plan

<!-- Where the plan says how success will be observed, and how that
maps onto the repro evidence's steps and artifacts. What a decisive
test plan names that a vague one does not. -->

**Where it lives:**
- Eval bundle: the candidate plan's test plan, read against the steps and artifacts in the repro-evidence block.
- Live mode: the test plan in `plan.md`, read against the posted repro steps.
**What good looks like:** The test plan names an observable outcome tied to the repro steps (a specific output, exit code, or behavior) and states the expected result after the fix. Anyone could run it and tell pass from fail. Running the general test suite alone is not a test of the fix.

## Honesty

<!-- Where claims meet uncertainty: risks, unknowns, and deviations.
How to tell stated unknowns from false confidence, and where an
honest mid-build deviation gets recorded. -->

**Where it lives:**
- Eval bundle: the candidate plan's risks and unknowns, and how the diagnosis words its claims (stated as fact versus as a hypothesis).
- Live mode: the risks and unknowns in `plan.md`, and any note in `plan.md` recording a deviation from the plan during the build.
**What good looks like:** What the evidence does not confirm is labeled as unknown, not stated as fact. A deviation made during the build is recorded in `plan.md` with what changed and why.

## Comms

<!-- Where the words meet the thread and the repo: the plan comment
read against the issue's maintainer signals (thread highlights, or
the live thread) and against the repo-facts block's stated templates,
contributing asks, and contribution policy (including AI-use
disclosure requirements). What thread-aware looks like next to
boilerplate. -->

**Where it lives:**
- Eval bundle: the plan comment, read against the thread highlights in the issue context and the repo-facts block (stated templates, contributing asks, and contribution policy, including any AI-use disclosure requirement).
- Live mode: the draft in `comment.md`, read against the live issue thread and the repo's docs (such as CONTRIBUTING and any AI policy).
**What good looks like:** The plan comment states the problem found, what will be done, and how it will be proven, and promises nothing beyond the plan. It engages any explicit maintainer direction in the thread and follows the repo's stated conventions, including disclosure if required. A thread-aware comment responds to what was actually said; boilerplate does not.