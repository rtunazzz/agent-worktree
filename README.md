# agent-worktree

A small Bash utility for running coding agents — [Claude Code](https://github.com/anthropics/claude-code) or [Codex](https://github.com/openai/codex) — in dedicated Git worktrees, each in its own tmux pane.

## Usage

```
worktree new [--agent claude|codex] [--model MODEL] [--settings FILE] "feature description" ["initial prompt"]
worktree open [--agent claude|codex] [--model MODEL] [--settings FILE] DIRECTORY
worktree destroy DIRECTORY
```

- `new` — creates `./worktrees/<yy-mm>-<slug>` on a fresh branch, opens a tmux pane there, and launches the agent (optionally with an initial prompt).
- `open` — reopens an existing worktree and resumes its agent session.
- `destroy` — removes the worktree (and the `worktrees` tmux window if it was the last pane).

Set `WORKTREE_AGENT=codex` to change the default agent. `--model` is forwarded to the agent's `--model` flag. `--settings` is forwarded to `claude`'s `--settings` flag (handy for wiring per-worktree hooks into the session); it's claude-only and ignored with a warning for `--agent codex`.

Requires `git`, `tmux`, and whichever agent CLI you use (`claude` and/or `codex`). Symlink `worktree` onto your `PATH` and drop `_worktree` somewhere on your `fpath` for zsh completion.

## Credits

Originally based on [hschne/claude-worktree](https://github.com/hschne/claude-worktree). MIT licensed.
