# Neovim

## version stable

NVIM v0.11.6
Build type: Release
LuaJIT 2.1.1741730670

## liste de plugins

* [junegunn/fzf.vim](https://github.com/junegunn/fzf.vim)
* [stsewd/fzf-checkout.vim](https://github.com/stsewd/fzf-checkout.vim)
* [tpope/vim-fugitive](https://github.com/tpope/vim-fugitive)
* [markdown](https://github.com/markdown)
* [google/vim-searchindex](https://github.com/google/vim-searchindex)
* [neovim/nvim-lspconfig](https://github.com/neovim/nvim-lspconfig)
* [mfussenegger/nvim-jdtls](https://github.com/mfussenegger/nvim-jdtls)
* [tpope/vim-classpath](https://github.com/tpope/vim-classpath)
* [ellisonleao/gruvbox.nvim](https://github.com/ellisonleao/gruvbox.nvim)
* [thedenisnikulin/vim-cyberpunk](https://github.com/thedenisnikulin/vim-cyberpunk)
* [sainnhe/everforest](https://github.com/sainnhe/everforest)
* [preservim/nerdtree](https://github.com/preservim/nerdtree)
* [ryanoasis/vim-devicons](https://github.com/ryanoasis/vim-devicons)
* [udalov/kotlin-vim](https://github.com/udalov/kotlin-vim)
* [nvim-treesitter/nvim-treesitter](https://github.com/nvim-treesitter/nvim-treesitter)
* [hrsh7th/nvim-cmp](https://github.com/hrsh7th/nvim-cmp)
* [hrsh7th/cmp-nvim-lsp](https://github.com/hrsh7th/cmp-nvim-lsp)
* [hrsh7th/cmp-vsnip](https://github.com/hrsh7th/cmp-vsnip)
* [hrsh7th/vim-vsnip](https://github.com/hrsh7th/vim-vsnip)
* [tpope/vim-commentary](https://github.com/tpope/vim-commentary)
* [windwp/nvim-autopairs](https://github.com/windwp/nvim-autopairs)
* [serenevoid/kiwi.nvim](https://github.com/serenevoid/kiwi.nvim)
* telescope

## global conf

```lua
--- global setup -----
----------------------

local g   = vim.g
local o   = vim.o
local opt = vim.opt
local A   = vim.api

-- Number of screen lines to keep above and below the cursor
o.scrolloff = 8

-- Better editor UI
o.number = true
o.numberwidth = 2
o.relativenumber = true
o.signcolumn = 'yes'
o.cursorline = true

-- Better editing experience
o.expandtab = true
o.smarttab = true
o.cindent = true
o.autoindent = true
o.wrap = false
o.textwidth = 300
o.tabstop = 4
o.shiftwidth = 4
o.softtabstop = -1 -- If negative, shiftwidth value is used
o.list = true
o.listchars = 'trail:·,nbsp:◇,tab:→ ,extends:▸,precedes:◂'
-- o.listchars = 'eol:¬,space:·,lead: ,trail:·,nbsp:◇,tab:→-,extends:▸,precedes:◂,multispace:···⬝,leadmultispace:│   ,'
-- o.formatoptions = 'qrn1'

-- Makes neovim and host OS clipboard play nicely with each other
o.clipboard = 'unnamedplus'

-- Case insensitive searching UNLESS /C or capital in search
o.ignorecase = true
o.smartcase = true

-- Undo and backup options
o.backup = false
o.writebackup = false
o.undofile = true
o.swapfile = false

-- Remember 50 items in commandline history
o.history = 50

-- Better buffer splitting
o.splitright = true
o.splitbelow = true

opt.mouse = "a"

-- Map <leader> to space
g.mapleader = ' '
g.maplocalleader = ' '
``` 

## key maps

```lua
-------------------------------------------------
-- KEYBINDINGS
-------------------------------------------------

local function map(m, k, v)
   vim.keymap.set(m, k, v, { silent = true })
end


map('n','<leader>n', ':NERDTreeFocus<CR>')
map('n','<C-n>',':NERDTree<CR>')
map('n','<C-t>',':NERDTreeToggle<CR>')
map('n','<C-f>',':NERDTreeFind<CR>')

map('n','<leader>t',':belowright 8 split | terminal<CR>')
-- exit mode insert in terminal
map('t','<Esc>','<C-\\><C-n>')
-- FZF on open buffers
map('n','<leader>b',':Buffers<CR>')
-- telescope remap
local builtin = require('telescope.builtin')
vim.keymap.set('n', '<leader>ff', builtin.find_files, {})
vim.keymap.set('n', '<leader>fg', builtin.live_grep, {})
vim.keymap.set('n', '<leader>fw', builtin.grep_string, {})
vim.keymap.set('n', '<leader>fb', builtin.buffers, {})
vim.keymap.set('n', '<leader>fh', builtin.help_tags, {})
vim.keymap.set('n', 'gb', builtin.git_branches , {})

-- copy / paste
map('n','<leader>c','"+y')
map('n','<leader>v','"+p')
-- format json file
map('n','<leader>j',':%! jq [.]<CR>')
map('n', '<C-p>', ':MarkdownPreview<CR>')
```
