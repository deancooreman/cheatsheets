# Neovim Cheatsheet

## Navigation & File Management

| Shortcut | Description |
| :--- | :--- |
| `-` | Open file explorer (Oil) |
| `Space + Space` | Find files |
| `Space + ,` | Search buffers |
| `Space + /` | Search in project (ripgrep) |

### Oil.nvim Shortcuts
- `Enter`: Open the file or directory under the cursor.
- `-`: Go up one directory level.
- `:w`: Save changes to the filesystem (rename, delete, move).

## IDE Features (LSP)

| Shortcut | Description |
| :--- | :--- |
| `gd` | Jump to where a variable/function is defined |
| `K` | Show documentation for item under cursor |
| `gr` | List all usages of a variable/function |
| `Space + rn` | Rename variable across the whole project |
| `Space + ca` | Code actions (fix imports, etc.) |
| `[d` | Jump to previous diagnostic (error/warning) |
| `]d` | Jump to next diagnostic (error/warning) |

## Autocompletion (blink.cmp)

| Shortcut | Description |
| :--- | :--- |
| `Tab` | Accept suggestion / go to next item |
| `Shift + Tab` | Go to previous item |

## Commenting (`Comment.nvim`)

- `gcc`: Toggle comment on the current line.
- `gc`: (Visual Mode) Toggle comment on the highlighted block.

## Markdown Preview

| Shortcut | Description |
| :--- | :--- |
| `Space + mp` | Toggle live preview in browser |

## System Commands

| Command | Action |
| :--- | :--- |
| `:Lazy` | Manage and update plugins |
| `:Lazy sync` | Install + update + clean all plugins |
| `:Lazy clean` | Remove unused plugins |
| `:Mason` | Install/Manage Language Servers |
| `:checkhealth` | Run Neovim health check |

## Installed Language Servers

| Server | Language |
| :--- | :--- |
| `pyright` | Python |
| `bashls` | Bash |
| `marksman` | Markdown |

## Moving Around

| Command | Action |
| :--- | :--- |
| `h` | Move cursor left |
| `j` | Move cursor down |
| `k` | Move cursor up |
| `l` | Move cursor right |
| `0` | Move cursor to beginning of line |
| `^` | Move cursor to first non-whitespace character |
| `$` | Move cursor to end of line |
| `gg` | Move cursor to beginning of file |
| `G` | Move cursor to end of file |
| `5G` | Move cursor to line 5 |
| `Ctrl + u` | Scroll up half a page |
| `Ctrl + d` | Scroll down half a page |

## File Management

| Command | Action |
| :--- | :--- |
| `:e filename` | Open file for editing |
| `:w` | Save current buffer |
| `:w filename` | Save buffer as filename |
| `:q` | Close current window |
| `:wq` | Save and close |
| `:q!` | Close without saving |
| `:wa` | Save all open buffers |

## Visual Mode

| Command | Action |
| :--- | :--- |
| `v` | Select character by character |
| `V` | Select line by line |
| `y` | Yank (copy) selection |
| `d` | Delete selection |
| `c` | Change selection and enter Insert mode |

## Editing

| Command | Action |
| :--- | :--- |
| `i` | Insert before cursor |
| `a` | Insert after cursor |
| `I` | Insert at beginning of line |
| `A` | Insert at end of line |
| `o` | New line below and insert |
| `O` | New line above and insert |
| `dd` | Delete current line |
| `D` | Delete to end of line |
| `C` | Change to end of line |
| `cw` | Change to end of word |
| `ciw` | Change entire word under cursor |
| `u` | Undo |
| `Ctrl + r` | Redo |

