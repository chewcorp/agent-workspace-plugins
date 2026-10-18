# agent-workspace-plugins

Plugins that let Perplexity, Claude, Cursor and Codex work in one shared GitHub workspace repo: clone it, follow its `AGENTS.md`, file findings in its wiki, and hand work on by push or PR.

## agent-workspace

| Skill | Use |
|---|---|
| `workspace-bootstrap` | Clone the workspace repo fresh, read `AGENTS.md` and the wiki before working. |
| `workspace-handoff` | Commit, then push or open a PR as the repo allows, and pass the next step to one agent. |
| `wiki-write` | File a durable finding as an OKF wiki concept with sources, index and log lines. |

### Perplexity

Plugins, Add custom, import from GitHub, and give the plugin folder URL:

```
https://github.com/chewcorp/agent-workspace-plugins/tree/main/plugins/agent-workspace
```

Then the Project instructions can be as short as:

> The workspace repo is OWNER/REPO. Run workspace-bootstrap at the start of every session and workspace-handoff before you finish.

### Claude Code

```
/plugin marketplace add chewcorp/agent-workspace-plugins
/plugin install agent-workspace@agent-workspace-plugins
```

### Codex

Codex reads `.claude-plugin/marketplace.json` as a marketplace: `codex plugin marketplace add chewcorp/agent-workspace-plugins`.

### Cursor

Put `plugins/agent-workspace` in `~/.cursor/plugins/local` (Cursor reads the root `plugin.json` as an open Agent Plugin), or copy the skill folders into a workspace repo's `.agents/skills/`, which Cursor and Codex both read.

## License

MIT
