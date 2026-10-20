---
name: pr-precheck
description: Grade a PR package (a candidate pull request read against the plan it claims to implement and the issue that plan belongs to) and decide whether it is ready to submit. Use when checking your own branch, draft PR title, and description before opening the pull request, or when grading an eval package bundle.
---

# pr-precheck: rubric-driven PR grading

<!--
THIS IS THE PART YOU WRITE, and it is the last one: the frame itself.
Weeks 1 through 3 handed you a working SKILL.md and you filled the
files behind it; this week the frame ships as headings, and you write
what it says. The frontmatter above and the section headings below are
fixed (CONTRACT.md's layout rule); the instructions under each heading
are yours. Write instructions to the tool, in the imperative, the way
weeks 1-3's frames spoke to you: what to read, in what order, what to
refuse, what to emit. Your executor in the rotation is the test: a
frame gap they hit (cannot tell what the tool reads, or how a verdict
gets assembled) is a missing sentence here.

One section is not yours: the JSON schema in "Verdict and output" is
reproduced from CONTRACT.md verbatim and may not be altered. Your
words decide everything around it.
-->

## The question

<!-- State, in your words, the one question this tool answers and what
a PR package is: what artifacts it contains and what they are read
against. CONTRACT.md fixes the question; your frame has to say it so
the tool cannot wander into grading something else. -->

Answer exactly one question about exactly one PR package: **“Is this pull request ready to go to review, or does it need to be improved?”** Never answer a different question. Never grade more than one package per run. Never answer from gut feel: execute the components in this directory (`rubric.md`, `procedure.md`, `references/evidence-guide.md`) and grade from what they say.
 
A PR package is a potential pull request with the following artifacts:
 
- the **title** and **description**, which are the claims made about the change;
- the **commits** and the **diff**, which are the actual code changes;
- the **test evidence**, which is what supports those claims.

The PR package is always read against the plan it claims to implement and the corresponding issue.

Check whether the diff does what the plan says, whether the plan answers the issue, whether the title and description tell the truth about the change, and whether the test evidence supports what the description claims. Stay inside that question. Do not review the idea's merit, rewrite the code, or suggest new features. If you notice something the rubric does not ask about, do not grade it.

## Inputs and modes

<!-- Define both modes. Live mode: name every input (your plan.md with
its deviation notes, your branch's diff, your draft PR title and
description, your test evidence, your issue), where each comes from,
and what a house-chain student reads instead. The branch's diff is
everything the branch changes relative to the repo's default branch:
`git diff main...HEAD` (three dots), run from the working copy, is
the command that produces it; name the source that concretely. Eval
mode: state that the bundle is the whole world, nothing is fetched,
and every check runs with the full verdict rule. -->

Work in exactly one of two modes. Decide the mode from the request: a request to grade a draft PR for a branch and issue URL is **live mode**; a request to grade an eval package bundle, identified by a bundle id, is **eval mode**. State the mode at the top of your reply.

### Live mode
 
Live mode grades the student's own submission, checked before it goes out. Read these inputs, and say in your reply where each one came from:
 
1. **The plan.** Read `plan.md` from the working copy, including every deviation note in it. A house-chain student reads the house plan instead.
2. **The diff.** Run `git diff main...HEAD` (three dots) from the working copy, on the student's branch. This produces everything the branch changes relative to the repo's default branch. If the default branch is not `main`, substitute its name. Do not use a two-dot diff, and do not read uncommitted changes in place of the committed branch diff. If `plan.md`, `pr_draft.md`, or `test_evidence.md` appear in this diff, that is debris to report under the rubric, not something to skip.
3. **The commits.** Read the commits on the branch (`git log main..HEAD`, with the same default-branch substitution).
4. **The draft PR title and description.** Read `pr_draft.md`. The first line is the title. Everything after it is the description.
5. **The test evidence.** Read `test_evidence.md`. A house-chain student reads the house repro pack instead of their own repro steps, from the links the instructor posted. The same checks grade the same things there.
6. **The issue and the repo's side of the evidence.** Gather issue-side evidence from the real repo: the issue thread (from the issue URL in the request), the PR template, and the repo's stated policy. Use `references/evidence-guide.md` to find where each piece lives.
If any input is missing or unreadable, do not guess at it. Record the gap and grade the affected checks `unclear`, which defaults to fail (see Grading discipline). Carry on with the rest.
 
### Eval mode
 
In eval mode the bundle is the whole world. The bundle holds the package (title, description, commits, diff, test evidence) together with the plan and the issue the package is read against, because nothing outside it can be fetched. Every fact comes from the bundle text. Do not fetch anything, do not run git or any other command to gather more material, and do not read anything outside the bundle. Do not read `scope.md` or `voice-guide.md`. Always grade a complete package: run every check in the rubric with the full verdict rule applied.


## The scope seam (live mode only)

<!-- Tell the tool when to read scope.md, what to do with the rules it
finds there, what to refuse, and what to do when the scope's repo line
is an unfilled placeholder. State that eval mode ignores scope.md
entirely. CONTRACT.md names the required behavior; your frame has to
instruct it. -->

`scope.md` names where the student's PR must live (its `Repo:` line) and the house rules of that environment. **In eval mode, ignore `scope.md` entirely.**
 
In live mode, read `scope.md` **before anything else**, before you read any other input:
 
1. **Check the `Repo:` line first.** If it still carries an unfilled placeholder, stop without grading. Print a short scope message telling the student to fill the `Repo:` line in `scope.md` with their section's Path Review repo (the instructor supplies the cohort's scope file), then re-run. Emit no verdict and no JSON block. This is a designed stop, not a failure.
2. **Never guess a scope.** Do not infer the repo from the branch, the remote, or the issue URL.
3. **Refuse out-of-scope work.** If the package lives outside the repo `scope.md` names, say so and refuse to grade it.
4. **Use the house rules as standards, not as new checks.** When the `Repo:` line is filled, read the house rules in `scope.md` and use them as the stated standards the rubric's checks are read against. They supply facts for grading. They do not add checks, and they do not change the verdict rule.

## The voice seam (live mode only)

<!-- Tell the tool when to read voice-guide.md, which outgoing text it
gates (the PR title and description), how to report a broken rule, and
why it never changes the verdict on its own. State that eval mode
ignores it entirely. -->

`voice-guide.md` holds the student's own rules for how they write upstream, carried forward from an earlier unit. **In eval mode, ignore `voice-guide.md` entirely.** Voice is personal and carries no gold labels. The universal communication-quality checks live in the rubric, and eval mode grades those.
 
In live mode, read `voice-guide.md` and hold the **outgoing PR text only** against its rules: the PR title and the PR description. Do not apply it to the plan, the diff, the commits, or the test evidence.
 
Report each rule the draft breaks in the summary, as a separate voice note. Each note quotes the offending text, names the rule, and gives a short suggested fix.
 
**A voice note never changes the verdict on its own.** The voice guide moves the verdict only if the rubric has a check that reads it, and then the effect comes through that check's grade under the rubric's verdict rule. A voice note is not a check.

## Component reads

<!-- Tell the tool how the pieces connect: rubric.md defines the
checks and the verdict rule, references/evidence-guide.md maps where
each evidence family lives, procedure.md is executed as written. Say
what the tool does when the procedure is silent on a step (report the
gap, never improvise around it) and what it does when rubric.md or
procedure.md has no content (the refusal rule, stated as an
instruction). -->

Three files sit behind this frame. Read all three before you grade:
 
- **`rubric.md`** defines the checks and the verdict rule. It is the only source of what you grade and how the verdict is assembled.
- **`references/evidence-guide.md`** maps where each family of evidence lives in a PR package. Use it to find the fact a check needs. It does not add checks.
- **`procedure.md`** is how you grade. Execute it as written, in its order, without skipping or reordering steps.
If `procedure.md` is silent on a step you need, report the gap in your reply and do not improvise a way around it. Grade the affected check `unclear` and say which step was missing. Never silently invent a step.
 
If `rubric.md` or `procedure.md` has no content, **refuse to grade and say so.** A file with no content is one that is empty, missing, or holds only the template's instruction comments. Name the file, say that there is nothing to grade by, and emit no verdict. Never invent checks or a method at runtime: a verdict from an empty tool looks like judgment and is noise.

## Verdict and output

<!-- State the binary verdict space (accept means submit, reject means
hold) and instruct the tool to end its reply with the fenced JSON
block below, valid and last, with nothing after it. The schema is
CONTRACT.md's, verbatim; do not edit it. -->

The verdict space is binary:
 
- **`accept`** means the package is ready to submit.
- **`reject`** means hold it.
There is no third verdict, no "accept with reservations", and no score. Reservations belong in the check evidence lines, not in the verdict. Assemble the verdict by applying the rubric's verdict rule to the check grades, never by overall impression.
 
Structure your reply in this order:
 
1. The mode, and where each input came from.
2. A readable per-check summary: one line per rubric check, giving its name, its grade, and the fact or quote that decided it. In live mode, include the voice notes here. Include any gaps you recorded.
3. The fenced JSON block below, as the **last thing in the reply**.
The JSON block is the machine-read result. It must be present, valid, and last, with nothing after it, not even a closing sentence. Use the schema exactly as given: do not alter, extend, or reorder it. Include one entry in `checks` for every check in the rubric, with the name matching the rubric's name, and keep each `evidence` value to one line. Do not use a fenced JSON block anywhere else in the reply. The `item` is the PR URL if one exists; otherwise it is the issue URL from the request in live mode, or the bundle id in eval mode.

```json
{
  "item": "<PR URL or bundle id>",
  "checks": [
    {"name": "<check name>", "grade": "pass|fail|unclear",
     "evidence": "<one line: the fact or quote that decided it>"}
  ],
  "verdict": "accept|reject"
}
```

## Grading discipline

<!-- Write the standing rules the tool grades under: evidence first,
grade the thing not the polish, the rubric decides, the procedure
decides how, and how unclear grades are treated when the rubric's
verdict rule is silent. CONTRACT.md states each as a guarantee; your
frame has to make them instructions. -->

These rules hold for every check, in both modes.
 
- **Evidence first.** Name the fact or quote that decided each check before you grade it. "Looks fine" is not evidence. The `evidence` field in the JSON is that fact or quote.
- **Grade the thing, not the polish.** Read the artifact itself against the plan, the issue, and the stated standards, never the formatting. A terse, complete PR can be ready, and a beautiful, confident one can be hiding drift. A claim in the description (such as "all tests pass") counts only if the test evidence shows it.
- **The rubric decides, not the run.** Grade only the checks `rubric.md` defines. If a check passes by its stated condition but feels wrong, it still passes: the fix belongs in the rubric, not in the run. Do not invent checks, raise or lower the rubric's bars, or apply your own taste.
- **The procedure decides how, not the run.** Follow `procedure.md` as written. Report its gaps instead of silently inventing steps.
- **Unclear defaults to fail.** Treat `unclear` as the rubric's verdict rule directs. Where the rule is silent, an unverifiable claim is a failing one: a PR you cannot verify from the package is a PR that is not ready to submit. Never resolve doubt in the package's favor.
- **Stay inside your inputs.** Read only the inputs named in this file for the current mode. Do not pull in outside knowledge to fill a hole in the evidence.
