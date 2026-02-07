# ⚡ Optimized Neovim Config for Odoo 14 Development

A fast, lightweight Neovim configuration specifically optimized for Odoo development. Built for speed with <30ms startup time and minimal memory footprint.

![Neovim](https://img.shields.io/badge/Neovim-0.11+-green.svg)
![Platform](https://img.shields.io/badge/platform-Windows%20%7C%20Linux%20%7C%20macOS-blue.svg)
![License](https://img.shields.io/badge/license-MIT-blue.svg)

## ✨ Features

### 🚀 Performance Optimized
- **<30ms startup time** - Lazy loading plugins
- **Minimal memory usage** - Disabled unused providers
- **No Node.js overhead** - Only Python LSP enabled
- **Transparent background** - Inherits terminal theme

### 🛠️ Development Tools
- **LSP Support** - Pyright (Python) + lemminx (XML)
- **Smart Completion** - Context-aware autocomplete with nvim-cmp
- **Syntax Highlighting** - Treesitter for Python, XML, Lua, Bash
- **File Explorer** - nvim-tree with custom keybindings
- **Fuzzy Finder** - Telescope for quick navigation
- **Git Integration** - Gitsigns for inline git status

### 🎨 UI/UX
- **Catppuccin Mocha** theme with transparent background
- **Global statusline** - Clean lualine setup
- **Indent guides** - Visual indentation markers
- **Auto-pairs** - Bracket/quote auto-closing
- **Which-key** - Interactive keymap discovery

## 📦 Requirements

- **Neovim** ≥ 0.11
- **Git**
- **Python 3** with pip
- **Pyright** language server
- Optional: **ripgrep** (for Telescope live_grep)

## 🚀 Installation

### 1. Backup existing config
```bash
# Windows
mv $env:LOCALAPPDATA\nvim $env:LOCALAPPDATA\nvim.backup

# Linux/macOS
mv ~/.config/nvim ~/.config/nvim.backup
```

### 2. Install config
```bash
# Windows
git clone https://github.com/YOUR_USERNAME/nvim-odoo-config $env:LOCALAPPDATA\nvim

# Linux/macOS
git clone https://github.com/YOUR_USERNAME/nvim-odoo-config ~/.config/nvim
```

### 3. Install dependencies
```bash
pip install pyright
```

### 4. Launch Neovim
```bash
nvim
```

Plugins will auto-install on first launch via lazy.nvim.

## ⌨️ Key Mappings

### Leader Key: `Space`

### File Navigation
| Key | Action |
|-----|--------|
| `<leader>e` | Toggle file explorer |
| `<leader>ff` | Find files |
| `<leader>fg` | Live grep |
| `<leader>fb` | Browse buffers |

### Odoo Quick Access
| Key | Action |
|-----|--------|
| `<leader>om` | Open `__manifest__.py` |
| `<leader>ov` | Browse views folder |
| `<leader>oo` | Browse models folder |

### LSP Operations
| Key | Action |
|-----|--------|
| `gd` | Go to definition |
| `gr` | Find references |
| `K` | Hover documentation |
| `<leader>rn` | Rename symbol |
| `<leader>ca` | Code actions |
| `[d` / `]d` | Previous/Next diagnostic |

### Window Management
| Key | Action |
|-----|--------|
| `<C-h/j/k/l>` | Navigate splits |
| `<C-Up/Down>` | Resize horizontal |
| `<C-Left/Right>` | Resize vertical |
| `:vsp` / `:sp` | Vertical/Horizontal split |

### File Tree (nvim-tree)
| Key | Action |
|-----|--------|
| `.` | CD into folder |
| `-` | CD to parent |
| `c` | Copy file |
| `x` | Cut file |
| `p` | Paste file |
| `d` | Delete file |
| `r` | Rename file |
| `a` | Create file/folder |

### Buffer Navigation
| Key | Action |
|-----|--------|
| `<S-h>` / `<S-l>` | Previous/Next buffer |
| `<leader>bd` | Delete buffer |
| `<leader>w` | Save file |
| `<leader>q` | Quit |

### Editing
| Key | Action |
|-----|--------|
| `gcc` | Toggle line comment |
| `gc` (visual) | Toggle block comment |
| `<` / `>` (visual) | Indent left/right |
| `J` / `K` (visual) | Move text up/down |

## 🔧 Configuration

### Indentation
Default: **2 spaces**. Odoo XML auto-detects **4 spaces**.

```lua
-- Change default indentation
opt.shiftwidth = 4
opt.tabstop = 4
opt.softtabstop = 4
```

### Disable Auto-format on Save
```lua
-- Comment out this block in init.lua
-- vim.api.nvim_create_autocmd("BufWritePre", {
--   pattern = "*.py",
--   callback = function()
--     vim.lsp.buf.format({ async = false })
--   end,
-- })
```

### Add More LSP Servers
```lua
-- In LSP config section
require("mason-lspconfig").setup({
  ensure_installed = { "pyright", "html", "cssls", "ts_ls" },
})

-- Then configure each server
vim.lsp.config.html = { ... }
vim.lsp.enable("html")
```

## 📁 Project Structure

```
~/.config/nvim/
└── init.lua          # Main configuration file
```

Single-file config for simplicity and portability.

## 🎯 Optimized for Odoo

- **Auto-detects** Odoo project structure (`*/odoo/*`, `*/addons/*`)
- **XML indentation** automatically set to 4 spaces
- **Python path** configured for module imports
- **Quick access** shortcuts for manifest, models, views
- **Type checking disabled** for Odoo's dynamic nature
- **Auto-import disabled** prevents unwanted imports

## 🐛 Troubleshooting

### Pyright not working
```bash
pip install --upgrade pyright
:LspRestart pyright
```

### Slow startup
```bash
# Check startup time
nvim --startuptime startup.log
```

### Plugins not loading
```bash
:Lazy sync
:Lazy clean
```

## 📝 License

MIT License - Feel free to use and modify.

## 🤝 Contributing

Contributions welcome! Open an issue or submit a PR.

## 💡 Tips

- Use `:checkhealth` to verify setup
- Press `<leader>` and wait to see all keybindings (which-key)
- Use `:Lazy` to manage plugins
- Use `:Mason` to manage LSP servers

---

**Author:** Zainal Abrori
**Repository:** [github.com/zainalabrori/nvim-for-odoo-dev/](https://github.com/zainalabrori/nvim-for-odoo-dev/)
