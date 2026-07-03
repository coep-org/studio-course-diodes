# This repo is your digital lab notebook

Your grade is not based only on the final working solution. It's based on
the **process** visible in this repo: your commits, your journal entries,
and how you responded to review feedback.

## How this works

1. **Your assignment is a GitHub Issue**, labeled `sow`, opened by faculty.
   Read the acceptance criteria — that Issue stays open until you close it
   by merging a PR that satisfies them.
2. **Work in a branch**, not directly on `main`.
   `git checkout -b fix/rectifier-ripple`
3. **Commit often, with real messages.** "fixed bug" is not a message.
   "Reduced ripple by swapping C1 from 100µF to 470µF per spec" is.
   Fourteen small commits documenting fourteen attempts is exactly what
   this system is designed to capture — don't squash your failures away.
4. **Write a journal entry every week** in `/journal/`, copied from
   `journal/TEMPLATE.md`. This is where you explain *why* something failed,
   not just that it did.
5. **Open a PR** against `main` when you're ready for review. Fill out the
   PR template, link the journal entry and the Issue. Your faculty/TA is
   auto-requested as reviewer via CODEOWNERS.
6. **Respond to review comments** on the PR — this back-and-forth is part
   of the record, not overhead to get through quickly.

## What not to do

- Don't do all your work locally and push one giant commit at the deadline.
  There's nothing to assess in a single commit.
- Don't delete or rewrite history to hide a failed approach. The failed
  approach is the point.
