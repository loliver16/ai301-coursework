# Rubric: is this pull request ready to submit?

<!--
THIS IS THE PART YOU WRITE (fourth week running; this is the rubric's
final form in the sandbox). Your frame in SKILL.md executes whatever
checks you define here, via your procedure.md. It ships empty on
purpose: the judgment is your work.

A filled rubric must contain:

1. At least one row in the checks table. Each row needs all four
   columns:
   - Check: a short name (used in the output JSON).
   - Evidence: exactly what to look at, and where in the package. Name
     the part (the diff read against the plan's scope, the test
     evidence read against the plan's test plan, the description read
     against the diff, the repo-facts block's template asks) or a
     location from your references/evidence-guide.md. "The PR" is not
     a source; "the diff's changed files read against the plan's
     stated boundary" is.
   - Pass condition: a decision rule about the OUTCOME that someone
     else could apply and get your answer. Judge the thing itself
     (does the diff fall inside the plan plus its deviation notes? is
     the claimed evidence observable?), never the write-up's shape
     (how long the description is, how many commits there are).
     Structure-shaped checks are what make graders disagree with
     themselves.
   - Weight: `required` (a fail here holds the package) or `preferred`
     (never changes the verdict).

2. A verdict rule below the table: how the check grades combine into
   accept (submit) or reject (hold), including how `unclear` is
   treated. The verdict space is binary. State the `unclear`
   treatment explicitly: the frame here is YOUR SKILL.md, so a rubric
   that stays silent is only covered if your frame's grading
   discipline says what happens (the contract's own default is that
   an unverifiable claim fails).

Cover what actually gets bad PRs submitted. The failure families the
lecture named ARE the harness's scoring categories, same names as the
eval README: silent drift (the diff silently does more or less than
the posted plan, or the description claims fidelity the diff
contradicts), not tested (the evidence proves nothing observable, or
the repo's own checks were never run), unreviewable (debris or
unrelated hunks bury the change), and standards wall (the repo's
stated template and disclosure asks are ignored). Your evidence
guide's four headings map onto these one to one (plan fidelity =
silent drift, test evidence = not tested, diff quality =
unreviewable, standards and comms = standards wall), and the category
floor is scored on exactly these names plus clear accept. A rubric
that ignores a category will fail the eval packages built around
that category. And remember the honest-outcome
rule, fourth week running: a PR that honestly discloses a shortfall
can be ready; a rubric that equates "less than everything" with
"hold" fails the set.
-->

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| silent-drift | The diff's changed files and behavior, read against the plan's stated scope plus its deviation notes. The description's claims about scope or fidelity, read against the diff. | Pass: every behavior change in the diff falls inside the plan plus its recorded deviation notes; nothing the plan promises is missing unless a deviation note or the description says so; and no claim in the description about what the PR does or doesn't touch is contradicted by the diff. Fail: the diff does more or less than the plan with no disclosure, or the description claims fidelity the diff contradicts. A disclosed deviation or shortfall passes. | Required |
| not-tested | 	The test evidence, read against the plan's test plan and repro steps (before and after). The output of the repo's own test suite, run on this branch. The description's testing claims, read against that output. | Pass: the repo's own checks were run on this branch with observable output (a passing result, or a failing result with its reason stated), and the repro shows an observable before and after for the claimed behavior, and the description claims no more than the output shows. Fail: the evidence is only assertion ("tested, works"), the repo's own checks were never run, the repro has no observable before and after, or the output contradicts a description claim (for example, "all tests pass" beside a failing result). | Required |
| unreviewable  | The list of files and hunks in the diff, each traced back to the plan or a deviation note. | Pass: every file and hunk is attributable to the plan or a deviation note, and none is debris. Debris means working notes (plan.md, pr_draft.md, test_evidence.md), scratch or debug files, committed build or generated artifacts, and unrelated formatting churn. A large diff passes if every hunk traces to the plan. Fail: any debris is present, or hunks unrelated to the plan are mixed in so that a reviewer cannot isolate the change. | Required |
| standards-wall  | The repo's PR template and stated policy (including any AI-use policy), read against the description: each section the template asks for, any disclosure the template or policy requires, and any issue reference or changelog entry it asks for. | Pass: every section and ask that the repo's template or stated policy makes of this PR is met with real content (a ticked checklist item or a short answer that actually answers counts; a section that does not apply to this change may be marked N/A with a reason), and a reader can tell what the PR does and why. Fail: a section or ask the repo requires is missing, deleted, or empty; the repo's stated AI-use policy or template requires a disclosure and none is present; or an issue link or changelog entry that the template or policy requires is absent. Do not fail the package for an ask the repo does not make. | Required |

## Verdict rule

<!-- State how the grades above combine into accept or reject, and how
unclear is treated. Example shape (write your own): "accept if every
required check passes; preferred checks never change the verdict;
unclear counts as fail." -->

Grade each check pass, fail, or unclear. Accept if and only if all four checks pass. Reject if any check fails. unclear counts as fail: a claim you cannot verify from the package is a failing one. All four checks are required, so none is advisory and there is no partial credit. Put reservations in the evidence lines, not in the verdict.

When one problem touches two checks, grade each check on its own condition. A stray unrelated behavior change can fail both silent drift (it changes behavior the plan did not authorize) and unreviewable (it buries the change). Voice notes never change the verdict.
