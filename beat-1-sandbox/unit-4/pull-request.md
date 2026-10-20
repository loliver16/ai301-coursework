# Unit 4 — Test and Submit

Path: `beat-1-sandbox/unit-4/pull-request.md`

Record of the pull request you opened against the Path Review repo, and of the evaluation
runs that produced `eval-run.txt`. This file is graded at the path above; a copy kept
anywhere else in the repository is not read.

Complete every labelled field below. Each is graded on its own; content placed under the wrong
label is not graded.

---

## Your pull request

**Pull request**

https://github.com/codepath/pathreview-ai301-fa26-howard/pull/87

**Branch**

fix/62-redis-health-probe

## Eval iterations

Answer all four sections. Quote source text directly; paraphrase does not satisfy these
fields.

**Run history**

Run 1: `--limit 3` smoke run (pkg-01, pkg-02, pkg-03)
agreement: 2/3 scored items

Run 2: `--limit 3` re-run after revising the standards-wall check
agreement: 3/3 scored items

Run 3: full run
agreement: 20/20 scored items  (bar: 18/20: PASS)

Run 4: full run with `--save-run eval-run.txt`
agreement: 20/20 scored items  (bar: 18/20: PASS)


**Package analysis**

Package: `pkg-02` (Textualize/rich#4208), category clear-accept. The gold label is accept. My first rubric rejected it, failing `standards-wall`. After I revised that check, my rubric accepts it, which agrees with the gold label.
 
The gold note says: "save_* methods reordered to clear only after a successful write, exactly the plan's shape; repro before/after shown, template's type-of-changes and changelog asks met". The line that decided my first result was the tool's evidence for `standards-wall` in `smoke.json`: "Description has no AI-assistance disclosure, which the rubric's pass condition requires (even though repo states no AI policy); type-of-changes, CHANGELOG, and issue reference are present." My first `standards wall` row made the AI-assistance disclosure and the issue reference a requirement and unconditional, so the check failed for the package even though the repo didn't have an explicit AI policy. The tool even noticed the repo has no AI policy and failed the package anyway, because the rubric told it to. I changed the pass condition so that a disclosure, an issue link, or a changelog entry is required only when the repo's template or stated policy asks for it. This fixed the next grading, so this package passes as it was supposed to. 

**Check rationale**

Rubric check for standards wall, copied exactly from `tools/pr-precheck/rubric.md`:
 
| standards-wall  | The repo's PR template and stated policy (including any AI-use policy), read against the description: each section the template asks for, any disclosure the template or policy requires, and any issue reference or changelog entry it asks for. | Pass: every section and ask that the repo's template or stated policy makes of this PR is met with real content (a ticked checklist item or a short answer that actually answers counts; a section that does not apply to this change may be marked N/A with a reason), and a reader can tell what the PR does and why. Fail: a section or ask the repo requires is missing, deleted, or empty; the repo's stated AI-use policy or template requires a disclosure and none is present; or an issue link or changelog entry that the template or policy requires is absent. Do not fail the package for an ask the repo does not make. | Required |
 
I wrote it this way because the check has to catch the two standards-wall packages and still accept the clear accepts. `pkg-01` fails because pandas' required checklist is visibly ignored, and the gold note says "no closes #xxxx, no checklist, and the stated whatsnew entry is absent from the diff". `pkg-20` fails because, in its gold note's words, "ghostty's stated policy requires disclosing all AI usage". My first version required an AI disclosure and an issue link in every repo, so after `pkg-02` was rejected I rewrote the condition to depend on what the repo's template or policy asks for, and added the closing sentence "Do not fail the package for an ask the repo does not make." I rejected keeping the unconditional rule because it would reject `pkg-02` and any other clear accept from a repo with no AI policy, meaning it would be requiring disclosures from PRs in repos where it's not necessary. 

**Trade-offs**

My rubric trades away one case: a package from a repo that states no AI-disclosure policy now passes `standards-wall` without a disclosure, even though this course treats all of the work as AI-assisted, which is a miss I accept. The gold label for `pkg-02` accepts a package with no disclosure, so the stricter rule contradicts the gold labels, and the tool can't tell from the bundle that a given package is AI-assisted. My own PR still includes a disclosure, but not because the Path Review repo requires one: its PR template has no disclosure section and CONTRIBUTING.md says nothing about AI use. I included it because this unit's instructions say "your course work is AI-assisted by design, so the disclosure always applies, in your own words." That doesn't conflict with the rubric. The conditional rule only stops the tool from failing a package for a disclosure its repo never asked for, and it doesn't stop an author from including one if they choose to. 
 
I re-ran the `--limit 3` set after the change as a canary: `pkg-02` flipped to accept, and `pkg-01`, the other standards-wall package in that set, still rejected. The full run then showed `pkg-20`, the second standards-wall package, still rejecting, and the final agreement was 20/20 scored items.

---

Related paths: `eval-run.txt` in this directory; your skill's files in
`tools/pr-precheck/`.
