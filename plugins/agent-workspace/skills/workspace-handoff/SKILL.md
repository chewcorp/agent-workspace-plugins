---
name: workspace-handoff
description: Commit and hand back work in a shared GitHub workspace repo, by direct push or by PR as the repo's AGENTS.md says, and pass the next step to another agent. Use when finishing a task in a workspace repo or when asked to "push", "commit", "open a PR" or "hand this to Claude/Cursor/Codex".
---

# Workspace handoff

## Commit

- One commit per piece of work. The subject says what changed; the body lists what is unverified and who should act next.
- Never commit secrets, tokens or credentials.

## Push

Follow the push policy from `AGENTS.md`.

**Direct push allowed** (a living workspace):

1. Commit your work first, so the tree is clean.
2. `git pull --rebase`, then `git push origin main`.
3. If the push is rejected because another agent pushed first, run `git pull --rebase` again, fix any conflicts by keeping both sides' content, and push again. Never force-push `main`.
4. Handing on to Codex? Use the branch-and-PR flow below instead, because Codex only answers on PRs.

**Otherwise**, or when unsure:

1. Push a branch named for your agent and the task, such as `perplexity/<short-slug>`.
2. Open a pull request. Say what changed, what is unverified, and what the reviewer should check.
3. Do not merge your own pull request unless `AGENTS.md` says you may.

## Hand on

- To ask another agent for the next step, mention exactly one: `@claude`, `@cursor` or `@codex`. Several mentions in one comment start several agents on the same work.
- Put the mention where the agent watches. On a PR, comment on it. After a direct push there is no PR, so open an issue that links the commit and mentions the agent. Agents do not read commit messages, and Codex only answers on PRs, so hand work to Codex through a PR.
- Say what you need from it in one sentence, with paths.
- Report the commit or PR link back to whoever started the task.
