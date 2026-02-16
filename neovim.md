# Neovim Cheatsheet

## Navigation & File Management

| Shortcut | Action | Description |
| :--- | :--- | :--- |
| `<Leader><Leader>` | **Find Files** | Fuzzy search for any file in the project |
| `<Leader>,` | **Buffers** | Search through currently open files |
| `<Leader>/` | **Ripgrep** | Search for text inside all files |
| `-` | **Oil.nvim** | Open file explorer (edit folders like text) |

### Oil.nvim Shortcuts
- `Enter`: Open the file or directory under the cursor.
- `-`: Go up one directory level.
- `:w`: Save changes to the filesystem (rename, delete, move).

## IDE Features (LSP)

| Shortcut | Action | Description |
| :--- | :--- | :--- |
| `gd` | **Definition** | Jump to where a variable/function is defined |
| `K` | **Hover** | Show documentation for item under cursor |
| `gr` | **References** | List all usages of a variable/function |
| `rn` | **Rename** | Rename variable across the whole project |
| `[d` | **Prev Diagnostic** | Jump to previous error or warning |
| `]d` | **Next Diagnostic** | Jump to next error or warning |

## Commenting (`Comment.nvim`)

- `gcc`: Toggle comment on the current line.
- `gc`: (Visual Mode) Toggle comment on the highlighted block.

## System Commands

| Command | Action |
| :--- | :--- |
| `:Lazy` | Manage and update plugins |
| `:Mason` | Install/Manage Language Servers |
| `:checkhealth` | Run Neovim health check |
