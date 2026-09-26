# Rules for AI agents working in this repository

These rules apply to every AI agent: Claude Code (cloud or local), Claude in Chrome or desktop, and any other assistant. The org owner (Alex) directs the work. **Agents never overwrite each other's work, and nothing reaches `main` without a pull request.**

## Before you change anything
1. `git fetch origin` then `git status`. If your local copy is behind `origin/main`, update it first (`git pull --ff-only origin main`). Never start from a stale copy.
2. Read `git log --oneline -15 origin/main` and any open pull requests. Other agents may have just added work. **Don't remove or rewrite files you didn't create in this task**, and especially not these:
   - `.github/` (CI workflows, CODEOWNERS, Dependabot)
   - `SECURITY.md`
   - `AGENTS.md` / `CLAUDE.md`

   If you think one of them is wrong, say so to Alex. Don't change it.

## How to make changes
3. Work on a **new branch**: `claude/<short-topic>` (or `feature/…`, `fix/…`). Never commit directly to `main`.
4. Push the branch and open a **pull request**. Alex merges. A ruleset blocks direct pushes to `main`. If you see `GH013 … Changes must be made through a pull request`, that is the protection working. Open a PR; don't look for a way around it.
5. **Never** `git push --force` or `--force-with-lease` to a branch you didn't create, never rewrite history (`rebase`, `amend`, `reset --hard` on pushed commits), and never delete branches you didn't create.
6. If your push is rejected with "non-fast-forward" or "fetch first": someone else pushed. Run `git pull --rebase` **on your own branch only**, re-check that their changes are still there, then push. Never force.
7. Generated output (for example a build script that rewrites templates): after running it, run `git diff --stat` and make sure it didn't delete or revert anything outside what you intended. If it did, restore those files (`git checkout origin/main -- <path>`) before committing.

## Identity and honesty
8. Set a real git identity before committing. Commits by "Your Name / you@example.com" can't be traced. Use `git config user.name` and `user.email` for the owner's account, or the tool's own identity.
9. Label AI work: branch prefix `claude/`, a PR description that says it's AI-authored, and the `ai-authored` label if it exists.
10. Don't claim anything is done, fixed or secure without evidence (a command's output, a CI run link). Report failures as failures.

## Never
- Commit secrets. That includes `.env`, keys, tokens, webhook URLs and passwords, and also pasting them into PRs, issues or chat.
- Disable, skip or weaken CI checks or tests to get a green build.
- Change repository or organization settings, rulesets, visibility, or app permissions. Those go through the owner's settings process.
- Merge your own pull request unless Alex has explicitly told you to merge that specific PR.

