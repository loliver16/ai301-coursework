# Unit 1 — Issue Selection

Path: `beat-1-sandbox/unit-1/selection.md`

Record of the issue carried into Unit 2, and of the evaluation runs that produced
`eval-run.txt`. This file is graded at the path above; a copy kept anywhere else in
the repository is not read.

Complete every labelled field below. Each is graded on its own; content placed under the
wrong label is not graded.

---

## Selected issue

**Issue link**

https://github.com/codepath/pathreview-ai301-fa26-howard/issues/62

**Verdict output**

**The verdict must record `accept` for this issue.** Choose an issue your own skill
accepts. If your skill rejects every candidate you try, that is a signal about your
rubric rather than about the issues: revise it and re-run — retries are unlimited and a
partial re-run costs about $0.20 — or run the skill on different candidates. Output
recording `reject` for the issue you chose earns no credit for this field.

```
❯ /issue-select grade these candidate first issues: https://github.com/codepath/pathreview-ai301-fa26-howard/issues/72, https://github.com/codepath/pathreview-ai301-fa26-howard/issues/62, https://github.com/codepath/pathreview-ai301-fa26-howard/issues/58

I'll start by reading the skill's scope and rubric.

  Ran 2 shell commands

All three candidates are in the scoped repo. Gathering evidence now.

  Listed 1 directory, ran 9 shell commands

All evidence gathered. Grading each candidate independently against rubric.md, with the Path Review house rule applied to the claim-signal check.

Repo facts (shared by all three): codepath/pathreview-ai301-fa26-howard — in scope. 0 stars, 6 forks, not archived, last push 2026-09-16, no releases. docs/CONTRIBUTING.md exists and states no AI-use restriction (silence passes). Maintainer life: Aburke225 (COLLABORATOR) opened and labeled all three issues on 2026-09-14 and commented on issues 2026-09-16; margaretfero-codepath (CONTRIBUTOR) reviewed PR #76 on 2026-09-25 — well inside the one-year threshold.

Accepted, in fit order

1. #62 — Health check references settings.redis_host, which does not exist on Settings
- Maintainer is alive: pass — opened 2026-09-14 by Aburke225 (COLLABORATOR).
- Scope fits a newcomer: pass — body names the cause and the fix (Settings "carries a single redis_url, which the probe should use instead") plus steps to reproduce; labeled good first issue.
- Nobody else on it: pass — no assignees, 0 comments, no linked PRs, state open.
- Repo in use (preferred): fail — 0 stars, tier low.
- Fit: best match on the profile — an API route wired to a config object and a Redis client, i.e. backend/infrastructure plumbing, and the cleanest thread of the three.

2. #72 — verify_password raises UnknownHashError on malformed stored hashes
- Maintainer is alive: pass — opened 2026-09-14 by Aburke225 (COLLABORATOR).
- Scope fits a newcomer: pass — names the two relevant files, the intended behavior ("fail closed (return False)"), the xfail marker to remove, and a 1–2 hour estimate; labeled good first issue.
- Nobody else on it: pass — no assignees, 2 comments (≤20), no merged PR, state open. The two comments are classmate SHEKHAR-Y (association NONE) claiming it and announcing open PR #76.
- Repo in use (preferred): fail — 0 stars, tier low.
- Fit: backend core/security.py, api-labeled — solid, but hashing rather than the data/systems work the profile targets.

Tension worth flagging: #72 turns entirely on how the house rule is read. The rubric's condition says "any linked pull requests should be closed," and PR #76 is open. The scope's house rule says other students' claim signals do not block an issue here, and the evidence guide explicitly calls an open linked PR "an active claim" — so I read #76 (a classmate's, association NONE, unmerged) as a neutralized claim rather than a blocker. On a strictly literal reading of that clause alone, #72 would be rejected. The rubric would be clearer if it said whose PRs count.

3. #58 — Bias detector patterns are too narrow to match common phrasings
- Maintainer is alive: pass — opened 2026-09-14 by Aburke225 (COLLABORATOR).
- Scope fits a newcomer: pass — runnable repro snippet with observed vs. expected output and the nine named failing tests. No good first issue label, but the rubric treats labels as supporting, not determining.
- Nobody else on it: pass — no assignees, 0 comments, no linked PRs, state open.
- Repo in use (preferred): fail — 0 stars, tier low.
- Fit: text-processing in safety/, further from APIs, databases, and pipelines than the other two.

No candidate was rejected. The preferred check fails identically for all three (same repo, 0 stars, low tier), so it does no ranking work — the order above comes from the fit profile.

[
  {
    "item": "https://github.com/codepath/pathreview-ai301-fa26-howard/issues/62",
    "checks": [
      {"name": "The maintainer is alive", "grade": "pass", "evidence": "Issue opened 2026-09-14 by Aburke225 (author_association COLLABORATOR), who also commented on issues #52/#43 on 2026-09-16 — within the last year."},
      {"name": "The repo is in use", "grade": "fail", "evidence": "stargazers_count = 0, which is under the 50-star threshold (forks_count = 6; tier low)."},
      {"name": "The scope fits a newcomer", "grade": "pass", "evidence": "Body gives the fix ('carries a single redis_url, which the probe should use instead') and 'Steps to reproduce: call GET /health'; labeled 'good first issue'; docs/CONTRIBUTING.md states no AI-use restriction."},
      {"name": "Nobody else is already on it", "grade": "pass", "evidence": "state=open, assignees=[], comments=0, timeline shows only label events — no linked or merged PRs."}
    ],
    "verdict": "accept"
  },
  {
    "item": "https://github.com/codepath/pathreview-ai301-fa26-howard/issues/72",
    "checks": [
      {"name": "The maintainer is alive", "grade": "pass", "evidence": "Issue opened and labeled 2026-09-14 by Aburke225 (author_association COLLABORATOR); margaretfero-codepath (CONTRIBUTOR) commented on PR #76 on 2026-09-25."},
      {"name": "The repo is in use", "grade": "fail", "evidence": "stargazers_count = 0, which is under the 50-star threshold (forks_count = 6; tier low)."},
      {"name": "The scope fits a newcomer", "grade": "pass", "evidence": "Body names relevant files core/security.py and tests/unit/test_security.py, the intended behavior 'fail closed (return False)', and 'Estimated effort: 1-2 hours'; labeled 'good first issue'."},
      {"name": "Nobody else is already on it", "grade": "pass", "evidence": "state=open, assignees=[], 2 comments (<=20), and no merged PR; the sole claim and open PR #76 are from classmate SHEKHAR-Y (association NONE), which the Path Review house rule says does not block."}
    ],
    "verdict": "accept"
  },
  {
    "item": "https://github.com/codepath/pathreview-ai301-fa26-howard/issues/58",
    "checks": [
      {"name": "The maintainer is alive", "grade": "pass", "evidence": "Issue opened 2026-09-14 by Aburke225 (author_association COLLABORATOR), who also commented on issues #52/#43 on 2026-09-16 — within the last year."},
      {"name": "The repo is in use", "grade": "fail", "evidence": "stargazers_count = 0, which is under the 50-star threshold (forks_count = 6; tier low)."},
      {"name": "The scope fits a newcomer", "grade": "pass", "evidence": "Body carries a runnable 'Steps to reproduce' snippet with observed vs. expected output and names 9 failing tests in tests/unit/test_bias_detector.py; labels bug/safety/tier-1 (no good-first-issue label, which the rubric treats as non-determining)."},
      {"name": "Nobody else is already on it", "grade": "pass", "evidence": "state=open, assignees=[], comments=0, timeline shows only label events — no linked or merged PRs."}
    ],
    "verdict": "accept"
  }
]

✻ Churned for 2m 18s · done 11:31 PM

※ recap: Goal was grading three Path Review issues as first-contribution candidates. All three passed the rubric; ranked #62 first, then #72, then #58. Next step is picking one and claiming it. (disable recaps in /config)
```

---

## Eval iterations

Quote source text directly in each field below. Paraphrase does not satisfy them.

**Run history**

[The agreement score of each run you did, in order. A single run is a complete answer if
only one run occurred. **The last score in your list must match the agreement line in the
`eval-run.txt` you committed** — that file is the record of your final run.]

Run 1: categories: claimed 4/4  clear-accept 2/8  dead-repo 3/3  policy 1/1  scope 4/4
agreement: 14/20 scored items  (bar: 18/20: below the bar)

Run 2: categories: claimed 4/4  clear-accept 3/8  dead-repo 3/3  policy 0/1  scope 3/4
agreement: 13/20 scored items  (bar: 18/20: below the bar; category floor unmet: no match in policy)

Run 3: categories: claimed 4/4  clear-accept 7/8  dead-repo 3/3  policy 0/1  scope 3/4
agreement: 17/20 scored items  (bar: 18/20: below the bar; category floor unmet: no match in policy)

Run 4: categories: claimed 4/4  clear-accept 8/8  dead-repo 3/3  policy 1/1  scope 4/4
agreement: 20/20 scored items  (bar: 18/20: PASS)

Run 5: categories: claimed 4/4  clear-accept 6/8  dead-repo 3/3  policy 1/1  scope 4/4
agreement: 18/20 scored items  (bar: 18/20: PASS)
run written to eval-run.txt

**Issue analysis**

issue-12 (category: policy) — my rubric's verdict: reject; gold label: reject. The repo (bookwyrm-social/bookwyrm) looks healthy on every other axis: recent commits and merged PRs within days of each other, a fast maintainer response time on recent issues, and the issue itself is unclaimed with no assignees or linked PRs, plus a "good first issue" label. But the repo's CONTRIBUTING.md explicitly states it does not accept AI-generated code or documentation. My rubric catches this with a standalone required check that fails the issue regardless of labels or other signals, so despite passing every liveness and claim check, the issue is correctly rejected on contribution-policy grounds alone.

**Check rationale**

Check from rubric.md:  
| Nobody else is already on it | Look in the issue under status, assignees, and comments | There are no assignees or merged pull requests linked to the issue. Any linked pull requests should be closed. The issue status is set to open. The issue should fail if there are more than 20 comments under this issue. | Required |

My reasoning:
I chose to focus on the issue status and assignees because I noticed these were good giveaways that someone had already claimed an issue or completed it and closed it. Additionally, I check that their are no merged pull requests linked to the issue because sometimes, issues are completed but the status might not be changed yet. I specify "merged" pull requests because sometimes previous contributors open a PR that is closed and not merged, meaning the issue still needs to be solved. I also noted the comment limit because one specific issue had around 50 comments, and often that is a bad sign when there is that much discourse, especially for someone who doesn't have much contribution experience. 

**Trade-offs**

This check trades precision for simplicity. The 20-comment cutoff and the "any linked PR must be closed" rule are blunt proxies for contention, so they can't distinguish a genuinely contested issue from one that just generated long technical discussion, or a stale PR from active ones. As a result, my rubric will sometimes reject issues that are actually fine to claim. I accept this because a check that also weighed recency of activity would be more accurate but harder to specify reliably, and for a newcomer, it's safer to skip a borderline issue than risk duplicating someone else's work or taking on more than they can handle for their first issue. 

---

## Selection rationale

Graded on whether all three are answered, in your own words. Not on how good the
reasoning is, and not on length — a short honest answer to each earns the full marks.
This is also the basis for the claim comment you write in Unit 2.

**Selection rationale**

[Answer all three:

1. The issue's fit to your interests and to the time available.
2. What the verdict identified correctly, and what you weighed that the rubric could
   not.
3. The anticipated difficulty in claiming it.]

Issue selected: https://github.com/codepath/pathreview-ai301-fa26-howard/issues/62

1. This one caught my eye because it's exactly the kind of backend work I want more reps on: a FastAPI health check that's silently broken because the code refers to settings that don't actually exist. It's also small enough that I can realistically finish it in the time I have before Unit 6, which mattered given everything else on my plate.
2. My rubric got the objective stuff right: nobody's claimed it, it's tagged "good first issue," and the description is unusually clear. It names the exact file, the exact broken attributes, and even gives you the steps to see the bug happen. What the rubric couldn't tell me was whether I'd actually feel confident touching this code. I don't know this repo at all yet, so I read through the issue myself and decided the fix (swapping two nonexistent settings for the one that actually exists) was simple enough to trace even as a newcomer.
3. Honestly, I think this will be on the easier side. It sounds like a one or two line fix once I find where redis_host and redis_port are being referenced. The bigger learning curve will probably just be getting oriented in a codebase I've never opened before. Since this is a shared classroom repo, someone else might already be looking at it too, but per the house rules that's not a problem. I can claim it and work on it regardless.

---

Related paths: `eval-run.txt` in this directory; your skill's files in
`tools/issue-select/`.
