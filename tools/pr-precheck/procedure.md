# Procedure: how this tool grades a PR package

<!--
THIS IS THE PART YOU WRITE (second week running for the procedure).
Week 3 you wrote these steps for a plan package; this week the graded
object is a PR package, and the read that matters most is a
side-by-side: the diff against the plan, the evidence against the test
plan, the description against both. Your week-3 procedure is the
pattern; do not paste it unchanged, because its read order was built
for a different object.

Your rotation is the design brief again, and this week friction routes
three ways: a stall on WHAT to decide is a rubric gap, a stall on
WHERE to look is a procedure gap (this file), and a stall on what the
tool even reads or outputs is a frame gap (your SKILL.md). A complete
procedure lets someone who has never seen a PR package before grade
one exactly the way you would.

Under each stage heading below, write the concrete steps for that
stage. The one-line note under each heading says what a complete
procedure must decide there. Write steps, not intentions: "read the
plan's scope pair before opening the diff, and list the files the plan
names" is a step; "understand the change" is a wish.
-->

## Read order

<!-- What gets read, in what order, before any check is graded, and
what to note down from each part while reading. A complete procedure
decides where the plan sits in the order (before the diff? before the
description?) and says why the order matters for the side-by-side
checks that come later. -->

Read the pieces in this order and write down what each step says to note. The order matters because the checks compare pieces side by side. The plan is read before the diff so that the diff is measured against what was promised, not explained after the fact. The description is read last so that its claims are checked, not trusted.
 
1. **Live mode only: `scope.md`.** Read it before anything else. If the `Repo:` line is an unfilled placeholder, stop and print the scope message as your frame directs. Skip this step in eval mode.
2. **The issue.** Note what the issue asks for and any maintainer direction in the thread.
3. **The plan.** Note three lists: the files and areas in its stated scope, its boundary (what it says it will not touch), and each deviation note with what it re-ties. Note the plan's test plan as a list of the behaviors it says will be shown.
4. **The repo's template and stated policy.** Note every template section by name, the disclosure ask, and each stated rule.
5. **The diff.** Note every changed file and, inside each file, every separate hunk, with a one-line description of what each does.
6. **The commits.** Note anything in the commit list that the diff does not explain.
7. **The test evidence.** Note the command for the repo's own checks and its outcome, the repro's before and after, and any failing result with its stated reason.
8. **The title and description.** Note each claim about scope, fidelity, testing, or the issue, and each template section's content.


## Evidence gathering

<!-- For each evidence family your rubric's checks name, the concrete
gathering move: which part of the package (or, live, which file, diff,
or page per your evidence guide) to pull the fact from, and what to
record. The load-bearing gathers this week are pairings: diff files
against plan scope, claimed evidence against the plan's test plan and
the repo's checks, description claims against diff contents. A
complete procedure leaves no check whose evidence an executor would
have to hunt for. -->

Gather the evidence for each check from your notes. Where a note is missing, go to the place the evidence guide names for it once. Record what you find. Do not grade yet.
 
**For silent drift**
1. Pair every changed file and hunk from step 5 against the plan's scope and boundary and its deviation notes. Sort each into one of three lists: *in the plan*, *covered by a deviation note*, or *uncovered*.
2. Go through the plan's scope and list every promised item the diff does not contain. For each, record whether a deviation note or the description says it was left out.
3. Pair each fidelity claim in the description (words such as "only", "just", "fully", "also") against the diff. Record each claim the diff contradicts.

**For not tested**
1. Record the repo's own check command and its visible outcome. If the outcome is a failure, record the reason given.
2. Check that the output belongs to this change: it should name this branch's files or tests, not generic output.
3. Pair each behavior in the plan's test plan against the evidence. Record, for each, the observable before, the expected after, and the actual after.
4. Pair each testing claim in the description against the output. Record each claim the output does not support.

**For unreviewable**
1. Walk the file list from step 5. Mark any file that is a working note (`plan.md`, `pr_draft.md`, `test_evidence.md`), a scratch or debug file, or a committed build or generated artifact.
2. Walk each hunk. Mark debug leftovers, dead code, commented-out blocks, formatting churn, and drive-by edits.
3. In live mode, run `git status` for context, but count only what is in the branch diff. Untracked notes outside the diff are not debris in the PR.

**For standards wall**
1. Pair each template section from step 4 against the description. Record each section as filled with real content, blank, placeholder, or unexplained "N/A".
2. Record whether the template or the repo's stated policy asks for an AI-use disclosure. If it does, record whether the disclosure is present. If neither asks, record "not asked".
3. Record whether the template or policy asks for an issue reference or a changelog entry. If it does, record whether it is present. If neither asks, record "not asked".
4. Record whether the title and description let a reader tell what the PR does and why.
5. Pair each stated rule and each piece of maintainer direction against the package. Record each one the package does not follow.


## Check execution

<!-- How one check runs against gathered evidence: in what order the
checks execute, what an executor does when evidence for a check is
genuinely absent, and when a check may be graded without re-reading
the whole package. A complete procedure makes two executors grade the
same package the same way. -->

1. Grade the checks in rubric order: silent drift, not tested, unreviewable, standards wall.
2. For each check, apply its pass condition literally to the notes you gathered for it. Grade `pass` only if every part of the pass condition holds. Grade `fail` if any fail condition is observed. Grade `unclear` if evidence for a part is genuinely absent, or if it cannot be verified from the package.
3. Grade each check on its own condition. A problem that touches two checks is graded in each. Do not let one check's grade change another's.
4. Write the check's evidence line before settling its grade: one line with the fact or quote that decided it. For a `pass`, name the strongest fact that shows the condition holds. For an `unclear`, name what is missing. Put any reservation in this line.
5. Grade from the gathered notes. Re-read the package only if your notes contain a conflict or a gap. Do not re-read to look for a reason to change a grade.
6. If a check passes by its stated condition but feels wrong, it still passes. Record the concern in the evidence line and leave the grade alone.


## Verdict assembly

<!-- How the per-check grades become the final accept or reject:
apply your rubric's verdict rule, state how unclear grades enter it,
and say what gets quoted in the output for the deciding check: the
check whose failure the verdict turned on. When more than one check
failed, your procedure picks which one gets quoted (first failing
required check in rubric order is a fine rule); nothing picks it for
you, so write the rule down. A complete procedure produces the same
verdict from the same grades, every time. -->

1. Apply the rubric's verdict rule: **accept** if all four checks pass; **reject** if any check fails. `unclear` counts as fail. Set the verdict from the grades only, never from overall impression.
2. Pick the deciding check: the **first check in rubric order whose grade is not `pass`**. Fail and unclear are treated alike for this choice. If more than one check is not `pass`, only the first is the deciding check. If all four pass, there is no deciding check.
3. Write the summary. Begin with the verdict and the deciding check, quoting that check's evidence line. For `accept`, state that all four checks passed. Then list all four checks in rubric order, one line each, with name, grade, and evidence.
4. List any gaps you recorded, such as inputs that were missing or steps this procedure did not cover.
5. Live mode only: after the verdict is set, read `voice-guide.md` and add the voice notes to the summary as your frame directs. Voice notes do not change the verdict. Skip this step in eval mode.
6. End the reply with the JSON block your frame defines, with all four checks in rubric order and the verdict from step 1. Put nothing after it.
