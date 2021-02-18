# Tree Sitter

## Table of content

- [What is Tree Sitter](##what-is-tree-sitter)
- [A bit more about Tree Sitter](##a-bit-more-about-tree-sitter)
- [nvim-treesitter](##nvim-treesitter)
- [Requirements](##requirements)
- [Installing](##installing)
- [Syntax Highlighting](##syntax-highlighting)
- [Incremental Selection](##incremental-selection)
- [Indentation](##indentation)
- [Folding](##folding)
- [Final Configuration](##final-configuration)

## What is Tree Sitter

Tree-sitter is a parser generator tool and an incremental parsing library.
It can build a concrete syntax tree for a source file and efficiently update
the syntax tree as the source file is edited

- General enough to parse any programming language
- Fast enough to parse on every keystroke in a text editor
- Robust enough to provide useful results even in the presence of syntax errors
- Dependency-free so that the runtime library (which is written in pure C)
can be embedded in any application

## A bit more about Tree Sitter

You can play with tree sitter [https://tree-sitter.github.io/tree-sitter/playground](https://tree-sitter.github.io/tree-sitter/playground)

- Syntax tree
- Branches
- Incremental parsing
- Error recovery

## nvim-treesitter

Simple and easy way to use the interface for tree-sitter in Neovim and to provide
some basic functionality such as,

- Syntax highlighting
- Incremental selection
- Indentation
- Folding

## Requirements

- Neovim 0.5 or higher

## Installing

- Install nvim-treesitter

```vim
" vim-plug
Plug 'nvim-treesitter/nvim-treesitter', {'do': ':TSUpdate'}
```

- Install Language parser

```vim
:TSInstall {language}
" :TSInstall java
" :TSInstall python
```

## Configuration

```lua
require('nvim-treesitter.configs').setup({
    ensure_installed = "all",

    highlight = {
        enable = true,
        custom_captures = {
            -- ["keyword"] = "TSString",
        },
    },

    incremental_selection = {
        enable = true,
        keymaps = {
            init_selection = "gnn",
            node_incremental = "grn",
            scope_incremental = "grc",
            node_decremental = "grm",
        },
    },

    indent = {
        enable = true
    },
})

vim.api.nvim_exec([[
    set foldmethod=expr
    set foldexpr=nvim_treesitter#foldexpr()
]], true)
```

## Tree Sitter supported Colorscheme

You might need nvim-treesitter supported colorscheme. List of few colorscheme
available below.

- [https://github.com/rockerBOO/awesome-neovim#treesitter-support](https://github.com/rockerBOO/awesome-neovim#treesitter-support)
- [https://github.com/nvim-treesitter/nvim-treesitter/wiki/Colorschemes](https://github.com/nvim-treesitter/nvim-treesitter/wiki/Colorschemes)
