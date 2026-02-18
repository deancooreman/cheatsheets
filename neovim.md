# Neovim Cheatsheet

## Navigation & File Management

| Shortcut | Description |
| :--- | :--- |
| `-` | Open file explorer (edit folders like text) |
| `space + space` | Find files |
| `space + ,` | Search buffers |
| `Space + /` | Search in project |

### Oil.nvim Shortcuts
- `Enter`: Open the file or directory under the cursor.
- `-`: Go up one directory level.
- `:w`: Save changes to the filesystem (rename, delete, move).
- `ctrl + 6`: close file explorer

## IDE Features (LSP)

| Shortcut | Description |
| :--- | :--- |
| `gd` | Jump to where a variable/function is defined |
| `K` | Show documentation for item under cursor |
| `gr` | List all usages of a variable/function |
| `rn` | Rename variable across the whole project |
| `[d` | Jump to previous error or warning |
| `]d` | Jump to next error or warning |

## Commenting (`Comment.nvim`)

- `gcc`: Toggle comment on the current line.
- `gc`: (Visual Mode) Toggle comment on the highlighted block.

## Markdown Preview

| Shortcut | Description |
| :--- | :--- |
| `space + md` | Toggle live preview |

## System Commands

| Command | Action |
| :--- | :--- |
| `:Lazy` | Manage and update plugins |
| `:Mason` | Install/Manage Language Servers |
| `:checkhealth` | Run Neovim health check |

## Moving around

| Command | Action |
| :--- | :--- |
| `h` | Move cursor left |
| `j` | Move cursor down |
| `k` | Move cursor up |
| `l` | Move cursor right |
| `0` | Move cursor to beginning of line |
| `^` | Move cursor to first non-whitespace character of line |
| `$` | Move cursor to end of line |
| `gg` | Move cursor to beginning of the file |
| `G` | Move cursor to end of the file |
| `5G` | Move cursor to line number 5 |

## File Management

| Command | Action |
| :--- | :--- |
| `:e filename` | Open file for editing |
| `:w` | Save current buffer to disk |
| `:w filename` | Save current buffer to filename |
| `:q` | Close the current window |
| `:wq` | Save and close the current window |
| `:q!` | Close the current window without saving |
| `:wa` | Save all open buffers to disk |

## Visual mode

| Command | Action |
| :--- | :--- |
| `v` | Enter Visual mode and select text character by character |
| `V` | Enter Visual mode and select text line by line |
| `y` | Yank (copy) the selected line |
| `d` | Delete the selected text |
| `c` | Change the selected text and enter Insert mode |

## Editing

| Command | Action |
| :--- | :--- |
| `i` | Enter Insert mode before the cursor |
| `a` | Enter Insert mode after the cursor |
| `I` | Enter Insert mode at beginning of the line |
| `A` | Enter Insert mode at the end of the line |
| `o` | Insert a new line below the current line and enter Insert mode |
| `O` | Insert a new line above the current line and enter Insert mode |
| `dd` | Delete the current line |
| `D` | Delete from the cursor to the end of the line |
| `C` | Change from the cursor to the end of the line and enter Insert mode |
| `u` | Undo the last change |
| `cw` | Change from cursor to end of word and enter Insert mode |
| `cb` | Change from cursor to beginning of word and enter Insert mode |
