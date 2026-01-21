# dev-picker

A simple interactive folder picker for your dev directory. Type `dev` in your terminal and use arrow keys to select a project.

![demo](https://github.com/user-attachments/assets/placeholder-add-your-gif-here)

## Features

- Lists your `~/dev` folders in reverse chronological order (most recently modified first)
- Arrow keys to navigate, Enter to select, Esc to cancel
- Fuzzy search - just start typing to filter
- Clean, colorful interface

## Quick Setup (with Claude Code)

Paste this into Claude Code:

```
Install fzf and add a dev folder picker function to my .zshrc. The function should list ~/dev directories in reverse chronological order using fzf with these options: height 25 lines, reverse layout, rounded border, prompt "📂 dev > ", pointer "▶", marker "✓", and Tokyo Night colors (bg+:#3b4261, fg+:#c0caf5, pointer:#ff9e64, prompt:#7aa2f7, border:#565f89). Then reload my shell config.
```

## Manual Setup

### 1. Install fzf

```bash
brew install fzf
```

### 2. Add to your ~/.zshrc

```bash
# Interactive dev folder picker with fzf
dev() {
  local dir
  dir=$(ls -dt ~/dev/*/ 2>/dev/null | fzf \
    --height 25 \
    --reverse \
    --border rounded \
    --prompt "📂 dev > " \
    --pointer "▶" \
    --marker "✓" \
    --color "bg+:#3b4261,fg+:#c0caf5,pointer:#ff9e64,prompt:#7aa2f7,border:#565f89") && cd "$dir"
}
```

### 3. Reload your shell

```bash
source ~/.zshrc
```

## Usage

```bash
dev
```

Then:
- Use **↑/↓** arrow keys to navigate
- **Type** to fuzzy search
- **Enter** to cd into the selected folder
- **Esc** or **Ctrl+C** to cancel

## Customization

Change the dev directory by replacing `~/dev` with your preferred path.

Adjust how many folders are shown by changing `--height 25`.

## License

MIT
