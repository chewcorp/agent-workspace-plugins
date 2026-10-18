---
name: workspace-bootstrap
description: Start work in a shared GitHub workspace repo. Use at the start of every session or task that names a workspace repo, or when told to "use the repo as the workspace", "read the repo instructions" or "check the wiki first".
---

# Workspace bootstrap

A workspace repo is shared by several agents (Perplexity, Claude, Cursor, Codex) and people. It is the only memory all of them share, so read it fresh and write back to it.

## Steps

1. **Clone fresh.** Clone the repo named in your instructions with `git clone https://github.com/OWNER/REPO`. Do not reuse a copy from project files, an earlier session or memory: those go stale.
2. **Read the rules.** Read `AGENTS.md` at the repo root. If it is missing, read `CLAUDE.md`, then `README.md`. The repo's rules override this skill wherever they differ.
3. **Read what it points to.** Open every file `AGENTS.md` says to read before working, such as a wiki maintenance guide or an intent doc.
4. **Check the wiki first.** If there is a `wiki/`, read `wiki/index.md`, then the folder index, then the concept pages that match the task. Answer from them before researching, and respect any `stale_after` or check date.
5. **Note the push policy.** Record whether `AGENTS.md` allows direct pushes to `main` or wants a branch and PR. The `workspace-handoff` skill uses it.

## While working

- Durable findings go in the wiki: see the `wiki-write` skill. Long write-ups go where `AGENTS.md` says, usually `docs/`.
- New unknowns go in the repo's open-questions file if it has one.
- Cite every external claim with a link and the date you checked it.
- Before finishing, hand the work back with the `workspace-handoff` skill. Work that is not committed is lost to every other agent.
