# wt - Git Worktree Manager

A friendly CLI wrapper around `git worktree` - because life's too short to remember all those flags.

## Quick Start

```bash
# Install
curl -o ~/.local/bin/wt https://raw.githubusercontent.com/mizrahidaniel/git-worktree-manager/main/wt
chmod +x ~/.local/bin/wt

# Usage
wt list                    # Show all worktrees
wt add feature/new-api     # Create worktree for branch
wt remove feature/old      # Delete worktree
wt prune                   # Clean up stale references
```

## Why?

Git worktrees are powerful but underused because the commands are verbose:

```bash
# Before
git worktree add ../feature-x -b feature-x
git worktree remove ../feature-x
git worktree list

# After
wt add feature-x
wt remove feature-x
wt list
```

## Features

- 🎯 **Simple commands** - `add`, `remove`, `list`, `prune`
- 🌿 **Smart branch handling** - Works with local, remote, or new branches
- 📂 **Sensible defaults** - Worktrees go in `../` by default
- ✨ **Pretty output** - Emojis and clear formatting
- 🔧 **Configurable** - Set `WORKTREE_BASE` to customize location

## Installation

**macOS/Linux:**
```bash
curl -o ~/.local/bin/wt https://raw.githubusercontent.com/mizrahidaniel/git-worktree-manager/main/wt
chmod +x ~/.local/bin/wt
```

**Manual:**
```bash
git clone https://github.com/mizrahidaniel/git-worktree-manager.git
cd git-worktree-manager
ln -s $(pwd)/wt ~/.local/bin/wt
```

## Commands

### `wt list`
Show all worktrees for the current repository.

### `wt add <branch>`
Create a new worktree for the specified branch.

- If branch exists locally → checks it out
- If branch exists on remote → creates local tracking branch
- If branch is new → creates new branch

### `wt remove <branch>`
Delete a worktree.

### `wt prune`
Clean up stale worktree references (e.g., after manual deletion).

## Configuration

Set `WORKTREE_BASE` to control where worktrees are created:

```bash
export WORKTREE_BASE="$HOME/worktrees"
wt add feature/new-ui  # Creates ~/worktrees/feature/new-ui
```

Default: `../` (sibling directory to your main repo)

## License

MIT
