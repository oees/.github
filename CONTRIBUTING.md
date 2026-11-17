# Contributing

These rules apply to every repository in this organisation. GitHub shows this
file in any repository that has no CONTRIBUTING file of its own. A repository's
own guide can add rules. It cannot remove these.

## How a change reaches `main`

1. Create a short-lived branch from `main`.
2. Commit your work on that branch.
3. Push the branch and open a pull request into `main`. Fill in the template.
4. Wait for the checks. Resolve every review comment thread.
5. Merge with **Rebase and merge**. GitHub deletes the branch after the merge.

GitHub enforces these rules on `main`:

- Every change goes through a pull request. Nobody pushes to `main`
  directly.
- **Rebase and merge** is the only way to merge. Merge commits and squash
  merges are turned off.
- History stays in a straight line. To update your branch, rebase it onto
  `main`. Do not merge `main` into it.
- Nobody can force-push to `main` or delete it.
- A pull request cannot merge while a review thread is still open.

You can force-push your own branch after a rebase. Use
`git push --force-with-lease`.

Every commit on your branch lands on `main` exactly as you wrote it. So make
each commit one logical change that builds and passes on its own. Clean up
your commits before you ask for review.

## Reviews

- Ask a teammate who knows the area to review your pull request.
- GitHub requires one approval before a merge, from someone other than
  whoever pushed last. You cannot approve your own pull request.
- A new push to the pull request dismisses earlier approvals, so ask for
  another review after you change it.
- A few repositories do not require an approval yet. The pull request page
  shows which rules apply. Ask for a review anyway.
- Only an approval from a person counts. A review by an AI agent or a bot is
  useful, but it is not an approval.
- Reviewers: read what the pull request says was checked. Read AI-written
  code as carefully as any other code.

## CODEOWNERS

- Every repository has a `.github/CODEOWNERS` file. Keep it in that folder,
  not in the repository root or in `docs/`.
- It names owner **teams**, not single people. Each owner team has at least
  two people, so there is always an owner other than the author who can
  approve.
- Put the catch-all line (`*`) first and more specific paths below it. For
  each file, the last line that matches wins.
- When approvals are required, the approval must come from a code owner of
  the files the pull request changes.

```text
# .github/CODEOWNERS
*   @oees/<owner-team>
```

## Branches and staging

- `main` is the default branch. Work branches start from `main` and are
  short-lived.
- Use a short name that says what the branch does.
- A `staging` branch exists only where leadership has decided that an app
  needs one. Do not create one on your own.
- Where a `staging` branch exists, follow what its owners say about how
  changes reach it. It will get the same rules as `main`, and you will be
  told before that happens. Moving changes from `staging` to `main` is
  always a pull request.
- An app without a `staging` branch deploys its staging environment, if it
  has one, from `main`.

## Agents and bots

- AI agents may write code, make commits, push to their own branches and
  open pull requests.
- Agents and bots never merge a pull request. They never approve one. They
  never push to `main` or `staging`.
- The person who asked an agent for a change is the author of that pull
  request. They read the diff, answer the review comments and merge it.
- Bots such as Dependabot open pull requests. A person reviews and merges
  them, like any other pull request.
- No app or bot can bypass the rules on `main`.
- Say in the pull request how AI was used. The template has a section for it.

## Emergencies

- If production is broken and you cannot wait for a review, still open a
  pull request, and ask an org owner to merge it.
- Org owners can bypass the rules. GitHub logs every bypass.
- After the emergency, ask for a review of the change and write down what
  happened.

## Commit messages

> **TODO (DL-10):** the commit message format is not decided yet. Until it
> is, follow the repository's own guide if it has one.

## Where the rules live

- Organisation rulesets in GitHub enforce the rules above. They apply to every
  repository, including new ones. They cover `main`, and also the default
  branch if a repository still has a different one.
- Repository settings match the rules: **Rebase and merge** on, merge commits
  off, squash merges off, branches deleted after merge.
- The org owners keep the rulesets as files in a private repository and
  apply them from there, so a change to a rule is itself a reviewed pull
  request.
- This file and the pull request template live in the organisation's `.github`
  repository. If your repository has its own CONTRIBUTING file, link to this
  one from it.
- If a rule blocks real work, ask an org owner. Do not work around it.
