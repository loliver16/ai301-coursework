# Rubric: is this a good first issue?

<!--
THIS IS THE PART YOU WRITE. The skill in SKILL.md executes whatever checks
you define here. It ships empty on purpose: the judgment is your work.

A filled rubric must contain:

1. At least one row in the checks table. Each row needs all four columns:
   - Check: a short name (used in the output JSON).
   - Evidence: exactly what to look at, and where. Name the source
     (repo-facts block, issue body, comment thread, or the locations in
     references/evidence-guide.md). "The repo" is not a source; "the last
     5 default-branch commit dates" is.
   - Pass condition: a condition someone else could apply and get your
     answer. Prefer thresholds with numbers ("a maintainer commented
     within 30 days") over adjectives ("maintainer is responsive").
   - Weight: `required` (a fail here rejects the issue) or `preferred`
     (never changes the verdict; a nice-to-have that helps rank the
     issues you accept).

2. A verdict rule below the table: how the check grades combine into
   accept or reject, including how `unclear` is treated. The verdict
   space is binary. If you write no rule for `unclear`, the skill treats
   it as fail.

Cover what actually kills first contributions. The lecture named four
families: the maintainer is alive, the repo is in use, the scope fits a
newcomer, and nobody else is already on it. A rubric that ignores a family
will fail eval issues designed around that family.
-->

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| The maintainer is alive | Check the repo facts issues tab for most recent issues or issues that have been changed most recently | A maintainer has created or commented on an issue within the last year | Required |
| The repo is in use | Check the number of stars on the repo | Accept if the number of stars is over 50 | Preferred |
| The scope fits a newcomer | Look at the issue’s description, labels, and contribution poloicy | Issue info should have steps or directions on how to reproduce the issue, or it should provide suggestions on how to fix it. The issue should fail if the contribution policy does not allow AI use. The following labels support, but do not soley determine, and issue being a good fit: good first issue, priority low or medium, p3. | Required |
| Nobody else is already on it | Look in the issue under status, assignees, and comments | There are no assignees or merged pull requests linked to the issue. Any linked pull requests should be closed. The issue status is set to open. The issue should fail if there are more than 20 comments under this issue. | Required |
## Verdict rule

<!-- State how the grades above combine into accept or reject, and how
unclear is treated. Example shape (write your own): "accept if every
required check passes; preferred checks never change the verdict, they
rank accepted issues; unclear counts as fail." -->

All three required conditions must be true. If any category is marked as unclear, that is considered a failure. Preffered status is used to rank issues but can't change the verdict. For the preferred condition, place issues into three categories: high, medium, and low. A high issue has 50> forks and star, medium has 10>=, and low has < 10. Rank issues based on their status from high to low. 