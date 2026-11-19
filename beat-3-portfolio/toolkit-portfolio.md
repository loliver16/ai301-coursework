# Toolkit Portfolio

Path: `beat-3-portfolio/toolkit-portfolio.md`

This file is Assignment 6, and it is graded at the path above; a copy kept anywhere else in
the repository is not read. It has been waiting here since you created the repo in unit 1;
unit 9 is when you write it.

**Only this page is read.** Your `tools/` folders and your installed skill folders are never
opened, so every piece of evidence you want seen has to live inline here: an output excerpt,
a before/after pair, a dated commit reference.

**Write every sentence yourself.** AI may gather diffs, dates and excerpts for you; it does
not draft entries.

**Keep every section header below under its exact name** — Featured Tools, Inventory, The
Arc, and Limitations and What's Next. Feature three or four tools, each in the entry shape
shown below; give every other tool one inventory line.

**Some lines below are labelled, and the label is how they are read.** Three places on this
page use a `Label: your words` shape — the arc's beats, the tool-limits list, and nothing
else. Keep those labels exactly as written, one per line, and never delete a labelled line:
where you have nothing to put after a label, write `none` and move on. A deleted label reads
as a deleted answer.

**Before you finish**, replace every `[bracketed prompt]` with your own words, then delete
the unused `[Tool name]` entry stub, its copy-me sentence, and the prompt sentences under
each header. A leftover bracketed prompt reads as unfilled.

**Student:** Lauren Oliver

## Featured Tools

Three or four tools, presented in depth. Open with a few sentences
on why you chose these.

Full credit asks the featured set to show real change: **at least two** of your featured
entries should show a tool that visibly moved through use. An honest entry for a tool that
barely changed — saying so, dating what did happen, and giving the reason — earns the solid
middle tier and never fails you.

Each tool's honest limit is not written here. It goes in the tool-limits list at the
bottom of this page, one line per featured tool, so that the limits sit together and can be
read as a set.

I chose to discuss issue scout, voice guard, and pr precheck because these tools were the most effective in helping me work through this contribution process, from claim to pr. All three of these tools played a significant role in ensuring I stayed on track and was properly prepared before submitting anything. 

Copy the entry shape below once per featured tool and fill it there.

**Issue Scout**

**What it is, and the judgment hole I wrote:** 

Issue scout is able to find and grade issues to determine if they are best fit for contribution based on my profile. This makes finding an issue super efficient and ensures that any chosen issue is fit for someone new to contributing like myself. This tool builds off of the original issue-select tool by adding a search-strategy, which has personal queries used for the search process. In these queries, I prioritized issues with python or java, backend work, api work, performance improvements, and pipeline changes. This fits my personal and professional interests in backend engineering and database work. Additionally, the verdict rule in the rubric uses the repo's stars to create tiers (high, medium, and low) based on how likely that issue's repo is a good fit: high is 50 or more, medium is 10 to 49, and low is under 10. I did this to emphasize the importance of working in a well established repo and where my contributions could make an impact, versus a new repo that has minimal users and traction. 

**How it evolved, dated:**

The original limitation of issue-select was that it had no ability to search for issues, only grade one's provided. Therefore, in unit 9 (11/7), I added the search-stratgy.md and updated rubric.md and scope.md. After running my initial search, I noticed that the skill return the max number of issues (100), but they varied in how new they were. To fix this and prioritize newer issues, I added the label --sort updated. Also, I emphasized this in the ranking filters section by including a rule to "drop any result not updated in the last 60 days." In my rubric.md, I updated the "maintainer is alive" check to require a repo to have a recent commit, merged PR, or recent reply to prove a maintainer is alive AND active. This also prevents very new issues (i.e a day old) from being included, which gives them time to be claimed, worked on, or clarifies by others. One final change I made on 11/8 was replacing the scope fits a newcomer check to scope feasible, which grades issues with a difficulty score when they pass and helps limit umbrella issue, where an issue has a large, multi-pr scope. 

**Evidence:**

Before I changed the scope fits a newcomer role, issue #796 passed the scan:   {
    "item": "https://github.com/InsightSoftwareConsortium/ITK/issues/796",
    "checks": [
      {"name": "The maintainer is alive", "grade": "pass", "evidence": "2026-11-08 hjmjohnson: 'Merge pull request #7136' on default branch"},
      {"name": "The repo is in use", "grade": "pass", "evidence": "1673 stars (>50); not archived"},
      {"name": "The scope fits a newcomer", "grade": "pass", "evidence": "Body lists required doc sections (NAME, SYNOPSIS, ...); member comment names 3 starter scripts; label 'Good first issue'; AGENTS.md sets AI conditions, not a ban"},
      {"name": "Nobody else is already on it", "grade": "pass", "evidence": "State OPEN, assignees [], cross-refs #4241/#4242 are open issues not PRs, 1 comment"}
    ],
    "verdict": "accept"
  }

However, once changing this row to scope feasible, this issue was rejected because it's scope was too large to be feasible:
  {
    "item": "https://github.com/InsightSoftwareConsortium/ITK/issues/796",
    "checks": [
      {"name": "The maintainer is alive", "grade": "pass", "evidence": "hjmjohnson merged PRs #7136, #7139, #7137 on main on 2026-11-07/08"},
      {"name": "The repo is in use", "grade": "pass", "evidence": "1673 stars (>50); not archived; last push 2026-11-09"},
      {"name": "scope-feasible", "grade": "fail", "evidence": "Asks to standardize documentation across the scripts in Utilities and Utilities/Maintenance plus a Software Guide section: an 'improve X everywhere' sweep, not one piece of work"},
      {"name": "Nobody else is already on it", "grade": "pass", "evidence": "State OPEN, assignees: none, cross-refs are open issues #4241/#4242 (no PRs), 1 comment"}
    ],
    "verdict": "reject"
  }

This was a good change because the grader is right, this issue has a very large scope as it references all scripts within two different folder (atleast 20 scripts), which is not a feasible task to claim unless the scope was narrowed, which is what I ended up doing with the maintainers advice. 


**Voice Guard**

**What it is, and the judgment hole I wrote:** 
Voice guard is a hook run in claude that evalauates whether the claim/draft submitted has a human voice and meets specific standards. The main goal of the standards is to prevent any tones/behaviors that might not be productive or taken well by maintainers. Some examples of things I listed should never be posted are Implying I would do a better job than previous contributors, and copy/pasting from the issue description and claiming it's my own. These standards are located in `voice-guide.md.`

**How it evolved, dated:** 

I created this hook in Unit 10 (11/09) by installing it, then creating an upstream voice guide, which is where I detailed my background, expectations, and limitations for claims and responses. The human voice rule is probably one of the most important because, even though I often use AI to help draft responses, I don't wan't maintainers to discredit my reply or ignore it because it sounds robotic. Additionally, I'm usually an expressive typer so robotic replies or short, statements don't match my voice and it it's something I have to constantly edit out of my claims before this hook was added. 

**Evidence:** 

When I went to upload my claim, voice guard was run as a hook and passed, thus allowing my claim to go through with posting:

- 2026-11-09 01:16 [hook] stop: no body the guard can read (interactive and --help forms are stopped on purpose) | target: gh issue comment --help
- 2026-11-09 02:39 [hook] pass | target: gh issue comment https://github.com/InsightSoftwareConsortium/ITK/issues/796 --body-file

Here, you can see the hook passed for my issue that I ended up claiming, while it stopped for --help because there was no comment body, so nothing to read forced it to pause (intended behavior). Here was the final claim comment: 

```
Hi! I'd like to take a first pass at this if it's still available. I'm new to contributing here, so I'll start small by creating documentation for UpdateRemoteModules.sh since UploadBinaryData.sh, which was recommended in the thread, has since been removed. Happy to switch to a different script if you'd prefer.

My first step is to read through UpdateRemoteModules.sh and check what it currently documents against what the issue asks for, and I'll report back here with my findings and plan.
```

While I didn't run into a submission where voice-guard rejected an issue, this hook is a cool and useful safety gate to ensure I'm maintaining a good status, being polite, and providing enough information. 


**pr-precheck**

**What it is, and the judgment hole I wrote:** [what the tool does,
and the part of it that is your judgment: the rubric, strategy,
guide, manifest, or playbook you wrote.]

pr precheck grades a pr package using a rubric with these categories: silent drift, standards-wall, not-tested, and un-reviewable. The purpose of this grading is to ensure the pr draft complies with repo and maintainer expectation, then ensures it can be easily reviewed. Defining these rubric categories required me to step into the maintainer's shoes and understand a baseline of what is important and helpful in a pr draft. Even though maintainers may have differing opinions on the details, they often want to easily see what steps were taken, the evidence to support that, and any other information about the change in a concise, readable format. The standards wall check was especially helpful for me as I worked on my contribution because due to working in a large repo, it was easy to miss some of the requirements/standards defined, so pr precheck catching these gaps prevented my PR from being delayed unnecisarily, 

**How it evolved, dated:** [the changes that made it yours, each
with its date and the friction that drove it; your weekly Toolkit
entries are the source.]

The friction related to this tool began on 11/18 when I first ran it in my pr draft and it rejected because it couldn't find my complete testing documentation. In this case, I had run the tests as a part of the commit process but hadn't saved the result or run the pre push test, so I'm grateful this was caught for me. After fixing this, another problem popped up with the standards wall that prevent my pr from passing. This created significantly more friction because despite my pr having all of it's necessary components (in relation to standards + expectations), it was still failing because of the scope still referencing the path review repo and rules. This revealed that while my pr-precheck is documented as grading all pr packages, I had not changed the scope to reflect this and allow a wider diversity of issues + prs to be reviewed. I widened the scope by changing the `Repo:` line to ITK and commenting out the path review house rule. After this, the pr precheck ran successfully and I was able to push my changes for review! While my PR hasn't been reviewed by a maintainer yet, the automatic pr bot did review it and scored it 5/5, proving that my work was thorough. 

**Evidence:** [show, don't claim: an output excerpt, a before/after
pair, or a dated commit reference, inline here. Draw it from your real
term work where you can - a catch this tool actually made, a
before/after from your own repo or PR - which is graded separately from
whether an artifact is present at all. A short, telling excerpt beats a
pasted transcript.]

Run 3 shows the failure that resulted from the limited scope of pr-precheck to path review: 

```
To reach accept: either rename the branch to fix/796-update-remote-modules-help (it isn't pushed yet, so git branch -m fix/796-update-remote-modules-help is all it takes), or get your instructor to confirm the Path Review house rules don't apply to an ITK PR. Since you're asking them about scope anyway, settle both in one question.
{
  "item": "https://github.com/InsightSoftwareConsortium/ITK/issues/796",
  "checks": [
    {"name": "silent-drift", "grade": "pass",
     "evidence": "Diff rewrites only the header comment and usage() text with all seven sections; the code is untouched, matching 'script behavior is unchanged'; Release.md placement is only in SEE ALSO (reservation)"},
    {"name": "not-tested", "grade": "pass",
     "evidence": "Before/after --help shown; section grep 0 -> 7 matches; bash -n and git diff --check clean; pre-commit run --files passed incl. kw-pre-commit; description discloses the update path was not run"},
    {"name": "unreviewable", "grade": "pass",
     "evidence": "1 file, 2 hunks (header, usage()), both trace to plan steps 3-4; working notes are in .git/info/exclude and absent from the diff"},
    {"name": "standards-wall", "grade": "fail",
     "evidence": "scope.md house rule requires the fix/<issue-number>-<slug> branch; the branch is doc-796-update-remote-modules-help (ITK template, Refs #796, and the <details> AI disclosure are all met)"}
  ],
  "verdict": "reject"
}
```

It specifically points to the house rules in scope.md as the blocker, which in this case actually opposed my repo's branch naming conventions by enforcing this:
```
"Open the pull request from the
  `fix/<issue-number>-<slug>` branch on your fork, against the
  semester repo's default branch. 
```

I reviewed the house rules and determined they weren't fit for work outside of the Path Review repo, so I commented them out for the sake of this pr. I also set the repo to ITK, then I ran pr precheck again and it accepted my draft: 

```
{
  "item": "https://github.com/InsightSoftwareConsortium/ITK/issues/796",
  "checks": [
    {"name": "silent-drift", "grade": "pass",
     "evidence": "Diff touches only the header comment and usage() heredoc in UpdateRemoteModules.sh, adding all 7 sections and -ongreen; behavior unchanged as claimed (reservation: Release.md step position only named in SEE ALSO)"},
    {"name": "not-tested", "grade": "pass",
     "evidence": "pre-commit run --files on the script all Passed; --help before/after shown, with grep of output finding all 7 sections and no 'CI build status'; description claims match and disclose the update path was not run"},
    {"name": "unreviewable", "grade": "pass",
     "evidence": "upstream/main...HEAD changes 1 file (Utilities/Maintenance/UpdateRemoteModules.sh) in 2 hunks, both in the plan; working notes excluded via .git/info/exclude"},
    {"name": "standards-wall", "grade": "pass",
     "evidence": "Template checklist fully answered with N/A reasons, 'Refs #796' present, AI disclosure in <details> per attribution.md, commit has a DOC: prefix, a 61-char subject and no AI trailer"}
  ],
  "verdict": "accept"
}
```

## Inventory

One line each for the rest of the toolkit: what it is and where it
stands (one bullet per tool; a compact sentence or two is fine).

- [Tool name: one line.]

## The Arc

The story of the toolkit in order: friction, change, result, dated.
Your weekly Toolkit entries are the source; read your own record and
tell it oldest first.

Write one block per beat, in the shape below, oldest first. Keep all four labels on every
beat, each on its own line. The `Result:` line is what the beat was for: it says what
happened *after* the change, which is not the same sentence as the change itself. If a beat
never reached a result, write `Result: none` — an honest beat that did not land still counts
fully as a beat.

Full credit asks for **at least two** beats whose `Result:` line names something that
actually happened afterwards. A beat about something that did not work counts fully as a
beat, and when the work happened never moves this score.

**Beat 1**
Date: [a date, or a month and year]
Friction: [what was going wrong, and how you noticed]
Change: [what you changed because of it]
Result: [what happened afterwards, or the word none]

**Beat 2**
Date: [a date, or a month and year]
Friction: [what was going wrong, and how you noticed]
Change: [what you changed because of it]
Result: [what happened afterwards, or the word none]

Copy the beat shape above for as many beats as your term had.

## Limitations and What's Next

What the toolkit as a whole still does not do, and what you would
build or change next. Write this section last; it will be better
after the rest.

[The honest limits, and what comes next, in your own sentences.]

**Tool limits.** One line per featured tool, in the same order as the entries above, naming
where that tool still stops or what it still gets wrong. A small honest limit is full credit;
"none really" is not a limit. If a tool genuinely has none you can name, write `none` after
its label rather than deleting the line.

issue-scout: [where this tool still stops, in plain words, or the word none]
[tool name]: [where this tool still stops, in plain words, or the word none]
