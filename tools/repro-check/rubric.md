# Rubric: is this reproduction package ready to post?

<!--
THIS IS THE PART YOU WRITE. The skill in SKILL.md executes whatever
checks you define here. It ships empty on purpose: the judgment is your
work.

A filled rubric must contain:

1. At least one row in the checks table. Each row needs all four
   columns:
   - Check: a short name (used in the output JSON).
   - Evidence: exactly what to look at, and where in the package. Name
     the part (the claim comment, the repro report's environment
     record, the artifacts read against the issue's description, the
     repo-facts block) or a location from your
     references/evidence-guide.md. "The report" is not a source; "the
     output excerpt read against the error the issue describes" is.
   - Pass condition: a decision rule about the OUTCOME that someone
     else could apply and get your answer. Judge the thing itself (does
     the artifact show the issue's behavior?), never the write-up's
     shape (how many steps it has, how long it is, whether it uses a
     template's headings). Structure-shaped checks are what make
     graders disagree with themselves.
   - Weight: `required` (a fail here holds the package) or `preferred`
     (never changes the verdict).

2. A verdict rule below the table: how the check grades combine into
   accept (ready) or reject (hold), including how `unclear` is
   treated. The verdict space is binary. If you write no rule for
   `unclear`, the skill treats it as fail.

Cover what actually gets bad packages posted. The lecture named the
proof families: the environment is recorded, the steps are complete
and followable, the behavior shown matches the issue (not an adjacent
one), the outcome is stated honestly (an evidenced cannot-reproduce is
a pass, a confident wrong-target is not), and the words respect the
repo's conventions. A rubric that ignores a family will fail eval
packages designed around that family.
-->

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| env-recorded | Find the environment section of the repro report and compare to any environment claims in the issue and repo facts. | Lists the OS, the language/tool, the package manager, and the version of the software under test (a release version, a commit hash, or an unreleased branch). The versions are not required but are preferred and must match the issue's target unless the difference is called out.| Required |
| steps-followable | Find the steps section of the repro report and compare with the issue's steps and the repo's setup docs. | A stranger could run the steps without guessing. The starting state is clear (an installed version recorded, or a clone and checkout of the recorded commit with setup commands). Commands are exact and in order, and the steps end with the action meant to trigger the bug, even if the attempt does not reproduce it. Any needed input is pasted, is the issue's own public file or script, or is described precisely enough for a stranger to recreate it. Private or unshared inputs, vague commands, or missing steps fail.e | Required |
| behavior-matches | Look for expected and actual behavior listed in repro report. Use artifacts (output, logs, or screenshots in the repro report) to compareactual behavior with the symptom stated in the issue. | Repro report states the expected and actual behavior, and an artifact shows the specific symptom the issue names (same error or wrong output). An artifact showing a different error, a setup failure, or no artifact fails. A report that doesn't specifiy the expected and actual behavior fails. An honest cannot-reproduce passes if it shows what happened instead. | Required |
| claim-specific | Find claim comment and compare to the issue thread. | Comment should name the issue, refers to its actual symptom or area, state the next step, and promise the report. It is courteous and factual, with no demands, pressure for a reply, or blame. If the repo's stated AI policy requires disclosure of AI assistance, the comments disclose it. If the policy restricts AI-written comments, they comply. If the repo has no such rule, none is needed. Boilerplate claims are too generic and fail. | Required |


## Verdict rule

<!-- State how the grades above combine into accept or reject, and how
unclear is treated. Example shape (write your own): "accept if every
required check passes; preferred checks never change the verdict;
unclear counts as fail." -->

## Verdict rule

Accept if every Required check that applies passes; otherwise reject. Preferred checks never change the verdict. A check that is unclear, or that lacks the evidence needed to grade it, counts as a fail. On a claim-only draft with no repro report yet, env-recorded, steps-followable, and behavior-matches are not yet applicable and are left out of the verdict, so it depends on claim-specific alone. Once a repro report exists, all four checks apply. An honest cannot-reproduce is not a reason to reject: it is graded by the same checks and can be accepted.
