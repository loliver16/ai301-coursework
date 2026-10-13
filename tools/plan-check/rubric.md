# Rubric: is this plan ready to post and build from?

<!--
THIS IS THE PART YOU WRITE. The skill in SKILL.md executes whatever
checks you define here (via your procedure.md). It ships empty on
purpose: the judgment is your work.

A filled rubric must contain:

1. At least one row in the checks table. Each row needs all four
   columns:
   - Check: a short name (used in the output JSON).
   - Evidence: exactly what to look at, and where in the package. Name
     the part (the plan's scope statement, the test plan read against
     the repro evidence's steps, the plan comment read against the
     thread highlights, the repo-facts block) or a location from your
     references/evidence-guide.md. "The plan" is not a source; "the
     plan's stated cause read against what the repro evidence shows"
     is.
   - Pass condition: a decision rule about the OUTCOME that someone
     else could apply and get your answer. Judge the thing itself (is
     this one bounded change? could a stranger start executing it?),
     never the write-up's shape (how many sections it has, how long it
     is, whether it uses headings). Structure-shaped checks are what
     make graders disagree with themselves.
   - Weight: `required` (a fail here holds the package) or `preferred`
     (never changes the verdict).

2. A verdict rule below the table: how the check grades combine into
   accept (ready) or reject (hold), including how `unclear` is
   treated. The verdict space is binary. If you write no rule for
   `unclear`, the skill treats it as fail.

Cover what actually gets bad plans posted. The lecture named the
failure families: the diagnosis ignores or contradicts the reproduced
evidence, the change is unbounded (scope creep), the plan targets the
symptom while the evidence points at the cause, a stranger could not
start executing it, the test plan proves nothing observable, the
unknowns are dressed up as certainty, and the comment ignores what the
thread or the repo's stated conventions ask. A rubric that ignores a
family will fail eval packages designed around that family.
-->

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| bounded-scope | Check the plan's scope statement, approach, and files/areas, and read against the symptom the issue and repro evidence report. Count everything the plan commits to doing in this change, including anything the draft comment promises. | Pass if everything the plan commits to is needed to fix the reproduced symptom, so the result is one reviewable change. Fail if the plan commits to work the issue did not ask for and the fix does not need, even when the core fix is correct and buried inside the extra work. Pass if the plan is narrower than the issue but says what it defers and why. An honest, reasoned deferral is not scope creep. | Required |
| diagnosis-grounded | Check the plan's stated cause and compare against every step of the repro evidence and against what the maintainers have already isolated. Do not take the plan's or the thread's confidence as evidence. | Pass if the stated cause is consistent with all of the repro evidence, and no step rules it out. Fail if the cause is contradicted or ignored by the evidence, or if an unconfirmed cause, meaning it has no evidence backing it, is stated as fact. | Required |
| executable-by-a-stranger | Check the plan's approach and files/areas. Someone new to the repo should be able to follow them. | Pass if the plan specifies where to make changes and commits to one approach, so that a newcomer could easily execute this plan. Fail if the location or approach is vague or the key decisions are left for build time. | Required |
| test-decisive | Check the plan's test plan for steps and an expected output | Pass if the test plan names an observable outcome for this bug, with the expected result after the fix stated, so pass or fail is not ambiguous. Fail if result is vague or relies only on running the general test suite | Required |
| comment-faithful | Check the draft plan comment, thread highlights, and the repo-facts block. | Pass if the comment is consistent with the plan, says what was found, what will be done, and how it will be proven, engages any explicit maintainer direction or prior work in the thread, and follows the repo's stated conventions (such as AI disclosure or human-written comments). Fail if it commits to changes beyond the plan or ignores any of these. Statements about how the work relates to existing PRs or discussion are not extra scope. | Required |

## Verdict rule

<!-- State how the grades above combine into accept or reject, and how
unclear is treated. Example shape (write your own): "accept if every
required check passes; preferred checks never change the verdict;
unclear counts as fail." -->

Accept if every check passes. Reject if any check fails. unclear counts as fail.