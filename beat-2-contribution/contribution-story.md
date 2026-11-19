# Contribution: Standardize documentation in `Utilities` scripts #796

Path: `beat-2-contribution/contribution-story.md`

This file is Assignment 5, and it is graded at the path above; a copy kept anywhere else in
the repository is not read. **Keep every section header below under its exact name** — the
format criteria grade exactly that. Your course repo link is the whole submission: no tool
files and no evidence uploads are part of Assignment 5.

**Contribution Number:** [1]
**Student:** Lauren Oliver
**GitHub Username:** loliver16
**Issue:** https://github.com/InsightSoftwareConsortium/ITK/issues/796
**Pull Request:** https://github.com/InsightSoftwareConsortium/ITK/pull/7207

One repository, built across units 5 to 8, telling the whole story of your real
contribution. Fill it as you work, not at the end — the sections below ask for evidence that
is far easier to write down as it happens than to reconstruct in the last weekend.

Contribution Number stays `[1]` unless you make more than one contribution this term; it
just numbers them.

---

## Toolkit

Every story section below, from Why I Chose This Issue through Pull
Request, ends with a Toolkit block: which tool did that phase's work
and how you used it, what it produced, what difficulties or
shortcomings it presented, and what you changed or would change
because of them. Together the blocks are the thread the rubric's
Toolkit points read, and they are the raw material for your unit-9
portfolio, so keep them current as you work rather than
reconstructing them later.

A Toolkit block looks like this (copy it into each story section and
fill it there):

```text
**Toolkit**

- Tool: [which tool did this phase's work, and how you used it]
- What it produced: [described in a sentence or a short excerpt]
- Difficulties: [what fought you or fell short, or "none met"]
- What changed: [the patch, revision, or workaround, what you would
  update, or "nothing"]
```

This section also keeps one short dated entry per week of tool work,
starting below: what you built or changed that week, what broke, and
what you changed because of it. The blocks tell the story where it
happened; these entries are the toolkit's own timeline.

All four entries are graded. Keep every heading below, and fill each
one in the week it belongs to.

**Unit 9: Turned issue-select into issue-scout, which searches GitHub with my own queries and grades the top five results.**

I built issue-scout with the strategy of prioritizing my backend experience and interest by creating seven gh queries for Python and Java backend issues that use ranking filters to drop assigned, stale, and heavily discussed issues. My first scan showed that my maintainer check passed any repo whose owner had filed issues that day, even if the maintainer hadn't been actively responding to contributors and approving PR's, which is why I tightened it to require the repo have a commit, merged PR, or recent reply to someone else's issue. I tried adding an umbrella-issue rule to the scope check category to prevent issues with many subtasks from being accepted, since a newcomer can't realistically complete them in one PR. However, the resulting tests showed this change flipped good issues to reject so I removed this rule and left scopecheck as is, noting this limitation.

**Unit 10: Added upstream rules to my voice guard and wrote a CLAUDE.local.md for ITK.**

I added rules for claims, questions, and pings to my voice guide and installed the hook that checks my comments before they post. Nothing broke: the guard log shows the wiring test was blocked as expected and my claim passed on its first check, though I haven't yet seen it stop a bad draft. My ITK memory file started from a Unit 9 assumption that running UpdateRemoteModules.sh with no arguments was safe. Reading the script showed it edits Modules/Remote files in place, so I changed the rule to `--help` only.

**Unit 11: Used plan-check and pr-precheck to plan, implement, and ship my changes**

I skipped the ship-gate tool and used my plan-check and pr-precheck skills as the checks before my PR instead. plan-check passed my plan for ITK#796, and pr-precheck returned accept on my package for PR #7207. It fought me at first: it refused to grade because scope.md pointed at the course's practice repo and house rules, and it failed my test evidence until I ensured it was thoroughly documented. What changed because of it is that I set the `Repo:` line to ITK, commented out the Path Review house rules that don't apply to ITK, and put labeled before and after outputs in test_evidence.md.

**Unit 8: [one line on the tool work]**

[2-4 sentences: the PR-monitor and your playbook. What it read, what it
drafted, what you did with the draft.]

---

## Why I Chose This Issue

I found my issue through the CodePath Issue Selection site, using the tags "good first issue," “Java,” and “Python.” It was hard to find a good one, because many I initially chose were already claimed, had open PRs, or had so much history that a newcomer couldn't add anything new. I narrowed it to two: ITK#796 (standardizing documentation in the Utilities scripts) and CTSM#1547 (adding an option that logs variable names before a history write). My scout accepted CTSM#1547 with an "ambitious" difficulty note, because the maintainers hadn't settled on a design, and rejected ITK#796 on scope-feasible, so it got no difficulty note. I favored the CTSM issue at first, but after reading its setup and other issues in the repo, I realized getting the climate model running on my computer would be a huge undertaking, and it didn't feel like a good first issue.

I chose ITK#796 anyway, even though my scout rejected it. The verdict was about the issue as written, which asks to document every script in Utilities, but a maintainer's comment named three scripts as places to start. I narrowed my claim to one, UpdateRemoteModules.sh, and treated that as my override of the rubric. ITK isn't a perfect match for my interests, since it's C++ image analysis and this is documentation for bash scripts, but I decided to choose it anyways since the Insight Toolkit (ITK) is used for image analysis and data classification, which fits my data interest. Additionally, I felt this contribution could still be a good learning experience for me to familiarize myself with scripting and the structure of this application, while also learning proper documentation formats. The scout got the basics right, but it accepted an issue I couldn't realistically work on and rejected the one I chose, and it doesn't check issue age or whether I can build and run a project, so I had to read those myself (one of the suggested scripts named in 2019 has since been removed). My claim comment can be found here: https://github.com/InsightSoftwareConsortium/ITK/issues/796#issuecomment-6734822638

**Toolkit**

- Tool: issue-scout, run as `claude "issue-scout: grade <URL> <URL>"` on my two Issue Selection picks after patching the scope check.
- What it produced: CTSM#1547 accepted with an "ambitious" difficulty note (the maintainers haven't settled the design). ITK#796 rejected on scope-feasible because the issue asks for documentation changes across every script in Utilities, so it got no difficulty note.
- Difficulties: It rejected the issue I chose and accepted one I wouldn't pick, a Fortran climate model outside of my ability because it requires a tedious setup process and more maintainer guidance before starting. The verdict was a judgment call on #796, since a maintainer had named three scripts as starting points. The rubric also doesn't check AI policy, issue age, or whether I can build and run the project, so I read those myself.
- What changed: I replaced my strict scope check with the scope-feasible row and added the difficulty note section. I logged the #796 judgment call in scan-notes.md. I would add rows for AI policy and issue age.

---

## Understanding the Issue

**Problem Description**

Many scripts in `Utilities` and `Utilities/Maintenance` don't have proper documentation, so mostly maintainers and a few others know what they do and how to use them. The issue asks for the following standard documentation format for these scripts: a header comment and a `--help` message with NAME, SYNOPSIS, DESCRIPTION, OPTIONS, IMPLEMENTATION, EXAMPLES and SEE ALSO. I will start with `UpdateRemoteModules.sh`, one of the scripts suggested in the issue.

**Expected Behavior**
The script's header comment and its `--help` output should both contain the seven sections, describe the `-ongreen` option, and say accurately what the script does, including that it edits `Modules/Remote/*.cmake` files in place. A new contributor could then understand the script without reading its code. My fix doesn't change how the script runs.

**Current Behavior**
Right now, the header comment (lines 22-26) is two sentences, and `usage()` (lines 30-41) prints those same sentences with a `Usage:` line, so `--help` shows one paragraph and none of the seven sections. `-ongreen` isn't documented anywhere, and the help text says the script updates modules "whose CI build status is successful," although that check only runs with `-ongreen`. Nothing warns that running the script without `--help` contacts GitHub over SSH and edits files in place.

**Affected Components**

I will only make changes to the header comment and the text `usage()` that prints in `Utilities/Maintenance/UpdateRemoteModules.sh`. I'll read Release.md and `UpdateRequiredITKVersionInRemoteModules.sh` for context and style, but not change them.This PR changes no script behavior, touches no other script, and leaves out the Software Guide section and any rendering or automation, which the issue mentions as possibilities for the future. 

**Toolkit**

- Tool: No tool was used for this section, but Claude chat was used to evaluate my descriptions
- What it produced: A list of corrections, including a fix to the description clarifying the exact changes, " and Current Behavior to add for specificity (-ongreen undocumented, the help text's wrong default, no in-place edit warning).
- Difficulties: No difficulties were encountered. All changes were made to provide more accuracy and detail. 
- What changed: I made the Current and Expected Behavior sections specific, narrowed the "no code changes" claim to "no changes to how the script runs," and added the Software Guide and rendering work to my out-of-scope list.

---

## Reproduction Process

**Environment Setup**

I reproduced the issue on the following environment:
- macOS 15.3.2 (24D81), run on 2026-11-16
- Fork `loliver16/ITK`, cloned locally, on `main` at `772f60f83b29283ff5e02e9f86e6e78d2a1bfa04` (2026-11-14, merge of PR #7158)
- Ran `./Utilities/SetupForDevelopment.sh`
- No build needed; every step below only reads files
- Shell: /bin/bash GNU bash, version 3.2.57(1)-release (arm64-apple-darwin24); git version 2.55.0
- Package manager: none used (read-only steps, no build)

Challenges:
- **Running the script safely.** I first assumed that running `UpdateRemoteModules.sh` with no arguments was safe. Reading the script showed that without `--help` it contacts GitHub over SSH and edits `Modules/Remote/*.cmake` in place. I ran it with `--help` only, and `git status --short` was empty before and after.
- **Missing versions in my first draft.** My first report listed the OS and commit but not the shell or git versions, and `repro-check` failed it on `env-recorded`. I added them.
- No installation problems. The setup script ran without errors.


**Steps to Reproduce**

Run from the repo root. `--help` is the only safe way to run this script. Without it, the script contacts GitHub over SSH and edits `Modules/Remote/*.cmake` in place.

1. `git checkout 772f60f83b29283ff5e02e9f86e6e78d2a1bfa04`
2. `nl -ba Utilities/Maintenance/UpdateRemoteModules.sh | sed -n '20,45p'` (header comment and `usage()`)
3. `./Utilities/Maintenance/UpdateRemoteModules.sh --help`
4. `grep -n -E 'NAME|SYNOPSIS|DESCRIPTION|OPTIONS|IMPLEMENTATION|EXAMPLES|SEE ALSO' Utilities/Maintenance/UpdateRemoteModules.sh`
5. `nl -ba Utilities/Maintenance/UpdateRemoteModules.sh | sed -n '71,76p;109,115p'` (the `-ongreen` handling)
6. `git status --short` (before and after; both empty, nothing was modified)
7. Observed result: `--help` prints a `Usage:` line and one paragraph that repeats the header comment (lines 22-26). The grep finds none of the issue's seven sections, and `-ongreen` (handled at line 71) appears in neither the header nor the help text.

**Reproduction Evidence**

- **Commit showing reproduction:** Commit: none (read-only; nothing committed)
- **Screenshots/logs:** excerpts from my terminal log (run 2026-11-16 at 772f60f; `git status --short` was empty before and after, so nothing was modified)

  `--help` output:
  ```
  Usage: ./Utilities/Maintenance/UpdateRemoteModules.sh

  Use this script to update the git commit hashes of all successful remote
  modules.

  The script updates the git commit hashes in ITK's Modules/Remote
  '*.remote.cmake' files for the remote modules whose CI build status is
  successful.
  ```

  Section-name search (no output):
  ```
  $ grep -n -E 'NAME|SYNOPSIS|DESCRIPTION|OPTIONS|IMPLEMENTATION|EXAMPLES|SEE ALSO' Utilities/Maintenance/UpdateRemoteModules.sh
  ```

  `-ongreen` and the CI-status check:
  ```
  71:if [ $# -ge 1 ] && [ $1 = "-ongreen" ]; then
  109:  if [ $ongreen -eq 1 ]; then
  ```
  
- **My findings:**

    ***1. The documentation lacks the sections the issue asks for.***
      - The header comment (lines 22-26) is a two-sentence summary. `usage()` (lines 30-41) prints the same text with a `Usage:` line added.
      - The `--help` output (step 3) is one `Usage:` line and one paragraph:
      
        ```
        Usage: ./Utilities/Maintenance/UpdateRemoteModules.sh
      
        Use this script to update the git commit hashes of all successful remote
        modules.
      
        The script updates the git commit hashes in ITK's Modules/Remote
        '*.remote.cmake' files for the remote modules whose CI build status is
        successful.
        ```
      - The grep in step 4 finds none of NAME, SYNOPSIS, DESCRIPTION, OPTIONS, IMPLEMENTATION, EXAMPLES, or SEE ALSO anywhere in the script (no output).

    ***2. The `-ongreen` option is undocumented.***
      - The script reads it at line 71 (`if [ $# -ge 1 ] && [ $1 = "-ongreen" ]; then`) and sets `ongreen=1`.
      - Neither the header nor the `--help` text mentions it.
      - The CI-status check (`curl` to the GitHub status API) is inside `if [ $ongreen -eq 1 ]` at line 109. The help text says the script updates modules "whose CI build status is successful," which describes what the flag does, not what the script does by default.



**Toolkit**

- Tool: repro-check, run as `claude "repro-check: grade my claim comment in claim-draft.md and my repro report in repro-draft.md for issue https://github.com/InsightSoftwareConsortium/ITK/issues/796"`.
- What it produced: The first run failed `env-recorded` because I hadn't recorded the shell and git versions. After I added them, the second run passed all four required checks, and it verified my quoted lines and the `-ongreen` claim against the script at 772f60f.
- Difficulties: I closed the terminal and lost the output, so I had to resume the session to recover it. Otherwise, no other difficulties were encountered and this process went relatively smoothly. While I didn't post the plan on the issue (because of unit 10 directions not too), I plan on building off of this reproduction report to create my plan. 
- What changed: I added the shell and git versions to the environment section, kept the plan out of the repro, and will save the output with `tee` next time.

---

## Solution Approach

**Analysis**

ITK#796 asks for standard documentation in the `Utilities` scripts: a header comment and a `--help` message with NAME, SYNOPSIS, DESCRIPTION, OPTIONS, IMPLEMENTATION, EXAMPLES and SEE ALSO. I narrowed this to `Utilities/Maintenance/UpdateRemoteModules.sh`, one of the three scripts a maintainer suggested as starting points.

In that script the documentation exists in two places, and both are thin:

- **Header comment (lines 22-26):** two sentences after the license block, saying the script updates the git commit hashes of remote modules.
- **`usage()` (lines 30-41):** prints a `Usage:` line plus the same text as one paragraph. This is all `--help` shows.

None of the seven sections appear anywhere in the file. A `grep` for them finds nothing.

The documentation is also incomplete and slightly misleading about the script's one option:

- **`-ongreen` is never mentioned.** It's read at line 71, and the GitHub CI-status check (the `curl` call) only runs inside `if [ $ongreen -eq 1 ]` at line 109.
- **The help text describes the wrong behavior.** It says the script updates modules "whose CI build status is successful," which is what `-ongreen` does, not what the script does by default.

Nothing in the cause is a code bug. The text in the header and in `usage()` is what's missing and wrong. A reader would also have no warning that running the script without `--help` contacts GitHub over SSH and edits `Modules/Remote/*.cmake` in place.


**Proposed Solution**

Rewrite the header comment and the text printed by `usage()` in `UpdateRemoteModules.sh`, using the issue's seven sections in the issue's order. The content will cover:

- what the script does and what it changes (files edited in place, GitHub contacted over SSH)
- the `-ongreen` option and what it changes
- how the script works, including where it sits in the Release.md remote-module update procedure
- examples
- references to related files, such as `UpdateRequiredITKVersionInRemoteModules.sh` and Release.md

Each section name goes in uppercase on its own line with its text indented beneath it, in the man-page style the issue links.

***What I won't change:***

- Any behavior of the script, only comments and the text `usage()` prints. That leaves `--help` exiting with status 1, the option loop breaking on the first argument, the unused `die()`, and the uninitialized `help` variable, all as they are.
- The other scripts in `Utilities`.
- Release.md.
- The ITK Software Guide section the issue mentions.
- Any automation that renders script docs to a web page.
- The `*.remote.cmake` versus `*.cmake` wording, which I checked and found isn't a real gap.

The issue covers every script, so my PR will reference it, not close it.


**Implementation Plan**

1. Fetch upstream and branch off `upstream/main`.
2. Read the header of `UpdateRequiredITKVersionInRemoteModules.sh` for local style, and read the whole of `UpdateRemoteModules.sh` so the IMPLEMENTATION and EXAMPLES sections describe what it actually does.
3. Rewrite the header comment (lines 22-26) with the seven sections.
4. Rewrite the text `usage()` prints (lines 30-41) to match, including `-ongreen`.
5. Run `bash -n` on the script.
6. Run `./Utilities/Maintenance/UpdateRemoteModules.sh --help`, the only safe invocation, as the first argument. Confirm `git status --short` shows no changes besides my edit.
7. Grep the --help output, not just the file, for all seven section names. Also check that -ongreen appears in that output and that the ‘CI build status is successful’ sentence is gone or only describes what -ongreen does.
8. Check `git diff` touches only comments and `usage()` text in this one file.
9. Commit with a `DOC:` prefix and save the before and after output in `test_evidence.md`. This file won't be tracked and its contents will go into the PR description. Addiotnally, the `DOC:` commit will not have a co-authored by trailer. 

[Record deviations here as they happen: what changed mid-build and
why. A recorded deviation is honest work; silent drift is not.]
Deviations:
- 11/18: An additional step I had to take before committing and pushing my changes was running the repo's checks: `pre-commit run --files Utilities/Maintenance/UpdateRemoteModules.sh` and `git prepush`. This required me to install pre-commit, then I ran each and all applicable hooks passed, signaling the changes were ready to be committed and pushed. 


**Toolkit**

- Tool: plan-check, run as `claude "plan-check: grade my plan in plan.md and draft comment in plan-comment.md for issue https://github.com/InsightSoftwareConsortium/ITK/issues/796"`.
- What it produced: A verdict of accept, with all five required checks passing (diagnosis-grounded, bounded-scope, executable-by-a-stranger, test-decisive, comment-faithful). It checked my line numbers and the `-ongreen` claim against the script, and confirmed the `*.remote.cmake` call. It also listed four things to fix before building and some typos in my comment.
- Difficulties: The skill's procedure.md reads the comment from comment.md, but my file is plan-comment.md, so it used mine. It also noted that nothing says what counts as repro evidence for a docs issue, since I never posted a repro comment.
- What changed: I changed my test step to grep the `--help` output and check `-ongreen` and the CI-status sentence in it, because grepping the file would pass if only the header changed. I added a line saying the sections are formatted man-page style, kept test_evidence.md out of the commit, and left the Co-Authored-By trailer off my DOC: commit, as ITK's attribution.md requires. I also fixed the typos in my plan comment and reworded its last sentence to explain why the PR covers one script.

---

## Testing Strategy

The change only touches the header comment and the usage() text, so the
checks prove two things: the help output and header now carry the
requested sections, and the script's behavior is unchanged. All outputs
are in the PR's collapsed "Test results" block.

**Before the fix** (from my reproduction):
- `UpdateRemoteModules.sh --help` printed the old short usage text, with
  no NAME, SYNOPSIS, DESCRIPTION, OPTIONS, IMPLEMENTATION, EXAMPLES, or
  SEE ALSO sections.
- Grepping the script for those section names found nothing.
- A grep for -ongreen found it only in the code (lines 71, 72, 75, 109,
  138), with no description of what it does.

**After the fix:**
- `UpdateRemoteModules.sh --help` prints the full standardized text,
  including the -ongreen description.
- The same section grep now matches every section header in the script
  header, and the -ongreen grep finds the option documented.
- `bash -n` reports no syntax errors.
- `git diff --stat` shows 117 insertions and 13 deletions, all in this one
  file. `git diff --check` reports no whitespace problems.

**Repo checks:**
- `pre-commit run --files Utilities/Maintenance/UpdateRemoteModules.sh`
  passed every hook that applies to the file.
- `git prepush` accepted the single `DOC:` commit.
- CI on PR #7207 passed.

I did not run the full update, since it contacts GitHub over SSH and rewrites the remote module files. Because the changes only include comments and help text, `bash -n` and a matching `--help` run are the checks that the show the documentation effectively while leaving the functionality and remote modules untouched. 

**Toolkit**

- Tool: pr-precheck
- What it produced:A verdict on whether my test evidence is observable and thorough, not just a claim that tests pass. It first returned "unclear" when it couldn't find the commit and push pre checks ITK requires, then passed once the evidence was in place.
- Difficulties: Originally, I had posted my test evidence in a file outside of ITK repo, so the tool failed due to insufficient testing. Also, when trying to run the commit pre check from ITK documentation, it was failing and required me to install pre-commit to get it to run properly. 
- What changed: I installed pre-commit, ran it on the changed file, and put the before and after outputs, labeled, in this repo's test_evidence.md. The not-tested check passed on the next run.

---

## Implementation Notes

**11/09**

Narrowed the scope from issue #796 ("Standardize documentation in
Utilities scripts") to one file, Utilities/Maintenance/UpdateRemoteModules.sh.
The change covers only the header comment and the usage() help text, with
no behavior change. I wrote down what I would not change in plan.md so
the PR stays reviewable. The maintainer's idea of rendering the docs on
a web page is out of scope.

**11/16**

Read the script before editing it, since I hadn't worked with shell scripts. The points that shaped the text: -ongreen is only read as the first argument and adds a GitHub commit-status check, so modules that aren't "success" are left unchanged and listed as failing. Without it, every module with a newer commit is updated. usage() is an unquoted heredoc, so `$` and backticks expand, and a line with only EOF would end it early. I kept that in mind while editing.

**11/17**

Wrote the new header (NAME, SYNOPSIS, DESCRIPTION, OPTIONS, IMPLEMENTATION, EXAMPLES, SEE ALSO) and made usage() match it. Left several oddities alone on purpose, because fixing them would change behavior: --help exits with status 1, the option loop breaks on the first argument, die() is unused, and the help variable is uninitialized. Replaced the old five-line header and eight-line usage text.

**11/18**

Committed as "DOC: Standardize UpdateRemoteModules.sh header and help text". Ran into several things along the way. The first commit message was rejected, so I recovered it with git commit -e. pre-commit wasn't installed, so I installed it and re-ran the hooks.

**11/18**

pr-precheck wouldn't accept the package at first. Its Repo: line pointed at the course's practice repo, my test results were in another repo's test_evidence.md, and its house rules asked for a branch name format that ITK doesn't require. I fixed the Repo: line, moved the evidence, and commented out the Path Review section of scope.md since it doesn't apply to ITK. The final run returned accept.

**11/18**

Pushed the branch to my fork and opened PR #7207 against ITK. CI passed and I marked it ready for review. The automated PR bot scored it 5/5 and called it low impact.


**Toolkit**

- Tool: Claude (chat), plus the pr-precheck output from the PR step
- What it produced: Plain-language explanations of the shell script and first drafts of the commit body and wording, which I then edited.
- Difficulties: I had no scripting experience before this and I didn't have a script to reference the documentation structure I was implementing. I used resources the maintainer recommended and claude to create and implement the new format. 
- What changed: I rewrote the text in my own words. I checked each claim in the header and usage() against the script's real output before committing. 

---

## Pull Request

**PR Link:** https://github.com/InsightSoftwareConsortium/ITK/pull/7207

**PR Description:** 
Document UpdateRemoteModules.sh with the header and --help sections requested in #796 (NAME through SEE ALSO), including the -ongreen option. Only comments and help text change; script behavior is unchanged.
This covers only this script, so it references the issue and doesn't close it.
Refs #796.


**Maintainer Feedback:**

- 11/18: No maintainer feedback yet. The automated PR bot gave my PR a 5/5 score, noting my changes are low impact and it looks safe to merge. 
- [Date]: [how you addressed it]

**Status:** Awaiting Review

**Toolkit**

- Tool: pr-precheck (I skipped the optional ship-gate and used pr-precheck
  as my pre-PR check.)
- What it produced:A pass/fail verdict on my PR package (plan, diff,
  description, and test evidence) against four checks: silent-drift,
  not-tested, unreviewable, and standards-wall. The final run returned
  accept, and I opened the PR after that.
- Difficulties: The first difficulty I encountered was that my pr-precheck tool was   still scoped to only focus on the Path Review repo (from the previous contribution), so it would not run for this new contribution. After changing the tool's scope to my issues repo (ITK), it then ran but rejected my pr because the nottested check was unclear: "no pre-commit or git prepush output appears in test_evidence.md or pr_draft.md." While I had run these check pre commit and push, I did not document them so I went back to do this. Once this check passed, the standards-wall check then failed because the house rules in the tool's scope went against my issue's branch naming conventions, creating a conflict. I decided to comment out the house rules in SCOPE.md because they were centered around the previous contribution for Path Review and weren't applicable for this issue. Finally, I ran the tool once more and everything passed.
- What changed: I set the `Repo:` line in scope.md to InsightSoftwareConsortium/ITK and commented out the Path Review section, since those rules don't apply to ITK. I graded against ITK's own PR template, commit rules, and pr audit check instead. I installed pre-commit, ran it on the changed file, and put the real output in test_evidence.md. Then, I re-ran pr-precheck and it accepted my pr.

---

## Learnings and Reflections

**Technical Skills Gained**

[What you learned technically, named concretely.]

**Challenges Overcome**

[What was hard and how you solved it; point at the real events, the
Toolkit blocks above are full of them.]

**What I'd Do Differently Next Time**

[Reflection on your process.]

---

## Resources Used

Helpful Documentation:
- https://linux.die.net/man/7/groff_man
- https://stackoverflow.com/questions/14008125/shell-script-common-template
- https://public.dhe.ibm.com/software/dw/aix/au-kornshellscripting/au-kornshellscripting-pdf.pdf

Other helpful resources:
- The Maintainers original comments, which gave specifically detailed the 7 sections they wanted included in the documentation: https://github.com/InsightSoftwareConsortium/ITK/issues/796#issue-439051963
