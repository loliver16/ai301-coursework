# Evidence guide: where proof lives in a reproduction package

<!--
THIS IS THE PART YOU WRITE (new this week: Unit 1 handed you this file
finished; the scaffolding fades). The skill uses this guide as its map:
for every kind of proof a rubric check names, this file says WHERE to
find it in a package and WHAT GOOD LOOKS LIKE when you do.

Under each family heading below, write:

- Where it lives: the exact places to look. In an eval bundle (which
  section of the package: the issue context, the repo-facts block, the
  claim comment, the repro report and its parts). In live mode (where
  on GitHub or in the draft: the issue thread, the repo's docs, the
  student's draft comment).
- What good looks like: one or two sentences someone else could apply.
  Prefer observable conditions ("the versions named match what the
  issue targets, or the difference is called out") over adjectives
  ("environment is thorough").

A rubric check whose evidence this guide cannot locate is a check
nobody else can execute; the rubric swap showed you what that feels
like. Write the map you wish your grader had.
-->

## Environment

<!-- Where the environment record lives, and what a sufficient one
looks like against the issue's stated target. -->
**Where it lives**
- Eval bundle: Found in the environment section of the repro report. Compare it to the issue context (the versions and platform the issue targets) and the repo-facts block (supported versions, setup requirements).
- Live mode: the environment section of the draft repro report. Compare it to (a) the issue thread, where the reporter's OS, version, and any filled-in issue-template fields state the target; and (b) the repo's docs and config, such as the README, setup docs, and version or CI files (for example `pyproject.toml`, `package.json`, `.tool-versions`, workflow files), which state supported versions.
**What good looks like**
- The record names the operating system ,the language runtime or tool, the package manager, the version of the software under test (a release version, a commit hash, or an unreleased branch).
- The versions are not required but preffered. Provided versions should match what the issue targets, or the difference is called out explicitly (for example, "issue reports 2.3.1; I tested on `main` at abc1234").

## Steps

<!-- Where the reproduction steps live, and what makes them followable
by a stranger, starting state to trigger. -->

**Where it lives**
- Eval bundle: the steps section of the repro report. Compare it to the issue context (the reporter's own steps) and the repo-facts block (the documented setup procedure).
- Live mode: the steps section of the draft repro report. Compare it to the reporter's steps in the issue thread and the setup instructions in the repo's docs.
**What good looks like**
- The starting state is clear: either an installed version recorded in the Environment section, or, for source or unreleased code, a clone and checkout of the recorded commit followed by the repo's documented setup commands.
- Commands are exact, copy-pasteable, and in order, ending with the action meant to trigger the bug, even if the attempt does not reproduce it. An honest cannot-reproduce can still have followable steps.
- Any input the bug needs is pasted, is the issue's own public file or script, or is described precisely enough that a stranger could recreate it (for example, a minimal config with the one unrecognized section named). Inputs that live in a private repo or an unshared config cannot be recreated, so they fail.
- A stranger could run the steps without guessing. Steps are concise, but nothing needed to run them is left out.


## Behavior shown

<!-- Where the artifacts live (output excerpts, logs, screenshots),
and what it means for an artifact to show the issue's behavior rather
than an adjacent one. -->

**Where it lives**
- Eval bundle: the output excerpts, logs, or screenshots attached to the repro report. Compare them to the symptom described in the issue context.
- Live mode: the pasted terminal output (code blocks), logs, or screenshots in the draft repro report. Compare them to the symptom described in the issue thread (the error message, wrong value, or visible misbehavior).
**What good looks like**
- The artifact shows the specific symptom the issue names (the same error text, the same wrong output, the same visible defect), along with the command or action that produced it.
- Text logs should be trimmed to the relevant lines but not altered. A screenshot should show enough context (window, version, or command) to tell where it came from.
- An artifact that shows an adjacent behavior does not count: a different error, a setup or install failure, or the expected behavior working correctly.


## Honesty

<!-- Where claims and their backing meet: how to tell a report that
says exactly what happened (including an honest cannot-reproduce) from
one that claims more than its evidence shows. -->

The claim comment is where the claims are made, and the repro report is the evidence that backs them up. In an eval bundle, read the claim comment first, list what it says happened or will happen, then look for each item in the repro report section (its environment, steps, and pasted output or screenshots). In live mode, do the same with the claim comment on the issue thread (or in the draft file) and the draft repro report. On a claim-only draft there is no report yet, so the claim comment must promise work and must not state results as already true.
 
A package that says exactly what happened passes this test for every claim in the claim comment:
- Each claim about what was done or found (for example, that the bug was reproduced, on which version, or under which conditions) is backed by the report: the recorded environment and steps match what the claim says, and the output shows the issue's behavior.
- The claim comment does not go further than the report. If the report shows only part of the behavior, or a different result than the issue describes, the claim comment says so.
- An honest cannot-reproduce counts as this kind of package. The claim comment says the bug could not be reproduced, and the report records the environment and steps in full and shows what happened instead.

A package that claims more than its evidence shows fails the test on at least one claim:
- The claim comment says the bug was reproduced, but the report's output shows something else (a different error, a setup failure) or contains no output at all.
- The claim comment names versions, conditions, or a root cause that the report does not record or demonstrate.
- The claim comment says something was tested that the report's steps never show.
- The claim comment reads like the issue's own description restated, with no matching report to show that anything was run.


## Comms

<!-- Where the words meet the repo: the claim comment against the
issue, the comments against the repo's stated templates and
contribution policy (including AI-use disclosure requirements), and
what specific-and-honest looks like next to boilerplate. -->

To check the claim comment against the issue, look in an eval bundle for the issue context, or in live mode look at the issue thread itself (is it still open and unclaimed, did a maintainer give issue details and instructions). Next, every comment is checked against the repo's stated templates and contribution policy. In an eval bundle, use the repo-facts block to check, and in live mode, use the repo's CONTRIBUTING file, its issue and PR templates, and any AI-use disclosure policy. If the policy requires a disclosure or a template format, a comment without it fails this check.
 
Specific and honest looks much different from boilerplate by showing the contributor put thought and effort into this issue. A specific comment names the issue, refers to its actual symptom or area, says what the author will do next, and promises the report. Boilerplate, such as "I'd like to work on this!", could be pasted onto any issue unchanged. An honest comment promises next-steps rather than asserting results that do not exist yet or promising deadlines that potentially might not be met. Also, any AI-use disclosure it makes should be accurate. Finally, the comment's tone should stay respectful and professional by being courteous of the maintainer and their time, and doens't inlcude demands to be assigned, pressure for a reply, or blame toward the reporter or the code. 