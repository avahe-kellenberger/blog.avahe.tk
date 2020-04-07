---
title: "Setting up Neovim for Typescript - Part 1"
date: 2020-04-06T15:48:45-04:00
tags: ["neovim", "typescript", "vim", "linux"]
draft: false
---

# Overall Goal of this Guide

We will be creating an IDE-like experience with Neovim, specifically for Typescript development.


### tl;dr / I am an experienced (neo)vim user

0. You may want to use a plugin manager; we are using [vim-plug](https://github.com/junegunn/vim-plug) for the tutorial.
1. Install [coc-nvim](https://github.com/neoclide/coc.nvim) and [coc-tsserver](https://github.com/neoclide/coc-tsserver).
2. Copy the defaults in `coc-nvim`'s README.md


# Getting Started

## vim-plug

#### Installation

If you do not already have a plugin manager set up for neovim, give [vim-plug](https://github.com/junegunn/vim-plug) a try.

There are installation instructions in the repo's `README.md` which is displayed on the page by default. We will be using vim-plug to install all of our plugins for this tutorial series. 

#### Configuration

Put the following code at the top of your neovim configuration file (`~/.config/nvim/init.vim` for Linux):

```VimL

call plug#begin(stdpath('data') . '/plugged')
" Plugins will be placed here
call plug#end()

```

## CoC - Conquer of Completion

**Conquer of Completion** is an intellisense engine for Vim/Neovim.

We will use CoC to interact with advanced [lsp](https://microsoft.github.io/language-server-protocol/) client plugins, to obtain fancy IDE-like features such as auto-complete, viewing documentation, jump-to-definition, and linting.

#### Installation

Place the line `Plug 'neoclide/coc-nvim'` in your `init.vim` file between the lines containing `plug#begin` and `plug#end`.

Your configuration file (`init.vim`) should now look like the following:

```VimL

call plug#begin(stdpath('data') . '/plugged')
Plug 'neoclide/coc.nvim', {'branch': 'release'}
call plug#end()

```

Now, execute `:PlugInstall` from inside Neovim. This will install `coc-nvim`.

#### Configuration

Copy the example configuration block from [coc-nvim's README](https://github.com/neoclide/coc.nvim#example-vim-configuration) into your `init.vim` file.

There will be a lot of lines, but we'll go over much of the functionality later in this guide.

## coc-tsserver

**coc-tsserver** is an lsp extension for **coc-nvim** - [Read their README file](https://github.com/neoclide/coc-tsserver#coc-tsserver) to personalize your settings.

#### Installation

Place the following lines in your `init.vim`, after `call plug#end()`:

```VimL

" Declare CoC extensions
let g:coc_global_extensions = [
  \ 'coc-tsserver'
  \ ]

```

CoC will automatically install any CoC extensions declared in the array.

#### Configuration

The above should be enough to get us going with `coc-tsserver` for now, but you should take the time to read the documentation on GitHub.

## Extra init.vim settings that you may enjoy

```VimL

" Show line numbers
set number

" Tabs have width of 2, use spaces instead of tab characters
set expandtab
set smarttab
set shiftwidth=2
set softtabstop=2
set tabstop=2

```

## Set up a Typescript Project

This should be enough to get us going for some basic Typescript programming! Let's set up a small example.

1. Create a new directory for your project
2. `yarn add -D typescript` or `npm install -D typescript`
3. `npx tsc --init`
4. `nvim index.ts`

Next, let's add some source code to play around with.

```typescript

const foobar: string = '5';
const bar: string = 'apples';

log(foobar);
log(bar);
log(foobar);

/**
 * Logs a string.
 * @param {string} str The string to log.
 */
function log(str: string): void {
  console.log(str);
}

log(foobar);

```

Attempt assigning numbers to strings, provide incorrect parameters to functions, and other improper actions. You will receive errors from `coc-tsserver` informing you of the mistakes.

## Default Keybindings

- `[g` and `]g` navigate between errors
- `K`  shows definitions and documentation
- `gd` goes to definitions
- `gy` goes to type definitions
- `gi` goes to implementations
- `gr` goes to references

The `\` character is your `<leader>` by default.

- Attempt to rename variables and functions by pressing `<leader>rn` then typing a new name.
- `<leader>f` formats selected code
- `<leader>ac` shows a list of actions to take when hovering over an error or warning
- `<leader>qf` "quickly fixes" an error or warning your cursor is on
- `<space>a` Show all diagnostics
- `<space>e` Manage extensions
- `<space>c` Show/execute available CoC commands
- `<space>o` Find symbol in current buffer
- `<space>s` Find symbol in current workspace
- `<space>j` Do default code action for the next item
- `<space>k` Do default code action for the previous item
- `<space>p` Resume most recent CoC list

