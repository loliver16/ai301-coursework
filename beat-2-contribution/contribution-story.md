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
**Pull Request:** [GitHub PR link, once opened]

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

**Unit 7: [one line on the tool work]**

[2-4 sentences: the ship-gate and your gate manifest. What it produced
on your real branch, what fought you, what changed because of it.]

**Unit 8: [one line on the tool work]**

[2-4 sentences: the PR-monitor and your playbook. What it read, what it
drafted, what you did with the draft.]

---

## Why I Chose This Issue

[1-2 paragraphs in your own words: how you searched, what your scan
surfaced, what your scout's verdict said, why this issue fits your
profile, and what you hope to learn. If your scout's verdict on it
was reject and you chose it anyway, say so here and say why; choosing
against your own tool silently is what loses points. Close with an
honest read of the tool itself: where the scout fell short on a real
wild search and what you changed or would change, or what convinced
you it held up. **Record the link to your claim comment in this section too.**
Not claimed yet? Write `claim pending` and today's date where the link goes,
and add the link the moment your claim lands.]


**Toolkit**

- Tool: issue-scout (your scout: your search strategy, your rubric),
  and how you used it
- What it produced: [the scan and its verdict on this issue, described]
- Difficulties: [where it fell short, or "none met" if none did]
- What changed: [what you patched or would update, or "nothing"]

**Toolkit**

- Tool: issue-scout, run as `claude "issue-scout: grade <URL> <URL>"` on my two Issue Selection picks after patching the scope check.
- What it produced: CTSM#1547 accepted with an "ambitious" difficulty note (the maintainers haven't settled the design). ITK#796 rejected on scope-feasible because the issue asks for documentation changes across every script in Utilities, so it got no difficulty note.
- Difficulties: It rejected the issue I chose and accepted one I wouldn't pick, a Fortran climate model outside of my ability to fix due to needing a supercomputer The verdict was a judgment call on #796, since a maintainer had named three scripts as starting points. The rubric also doesn't check AI policy, issue age, or whether I can build and run the project, so I read those myself.
- What changed: I replaced my strict scope check with the scope-feasible row and added the difficulty note section. I logged the #796 judgment call in scan-notes.md," if you did. I would add rows for AI policy and issue age.

---

## Understanding the Issue

**Problem Description**

[In your own words, what is broken or missing?]

**Expected Behavior**

[What should happen?]

**Current Behavior**

[What actually happens?]

**Affected Components**

[Which parts of the codebase are involved?]

**Toolkit**

- Tool:
- What it produced:
- Difficulties:
- What changed:

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
- **Running the script safely.** I first assumed that running `UpdateRemoteModules.sh` with `--help` or no arguments was safe. Reading the script showed that without `--help` it contacts GitHub over SSH and edits `Modules/Remote/*.cmake` in place. I ran it with `--help` only, and `git status --short` was empty before and after.
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

[Your analysis of the root cause: what is causing the issue, traced
to the files and functions involved.]

**Proposed Solution**

[High-level description of your fix approach, and what you are
deliberately NOT changing.]

**Implementation Plan**

1. [Modify file X to do Y]
2. [Add or change Z]
3. [Update tests]

[Record deviations here as they happen: what changed mid-build and
why. A recorded deviation is honest work; silent drift is not.]

**Toolkit**

- Tool:
- What it produced:
- Difficulties:
- What changed:

---

## Testing Strategy

[What observable checks prove the fix: your reproduction steps re-run
against the built change (before and after), and the repo's own test
suite or checks with the outcome shown. "Tests pass" with nothing
observable named is not a strategy.]

**Toolkit**

- Tool:
- What it produced:
- Difficulties:
- What changed:

---

## Implementation Notes

[A running log, added to as you work. Date each entry. What you
built, decisions you made when you made them, wrong turns included.]

**[Date]**

[Entry]

**[Date]**

[Entry]

**Toolkit**

- Tool:
- What it produced:
- Difficulties:
- What changed:

---

## Pull Request

**PR Link:** [GitHub PR URL when opened]

**PR Description:** [what the PR says; much of the content above
adapts into it]

**Maintainer Feedback:**

- [Date]: [feedback received, or "none yet"; silence is a normal
  state and costs you nothing]
- [Date]: [how you addressed it]

**Status:** [Awaiting review / Iterating / Merged / Closed. The
status is a fact you record, never a grade: the PR is graded as
opened.]

**Toolkit**

- Tool:
- What it produced:
- Difficulties:
- What changed:

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

[What actually helped, not a reading list. List things this story
already shows you using: the doc you followed to set the environment
up, the thread that explained the bug, the person who answered you.
One real entry beats ten plausible ones.]

- [Link to documentation that helped]
- [Discussion, issue, or post that helped]
