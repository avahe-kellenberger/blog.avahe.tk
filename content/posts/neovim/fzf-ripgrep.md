---
title: "(Neo)vim - Fzf and Ripgrep"
date: 2020-05-02T22:02:33-04:00
draft: false
---

# Prefer Video?

**[Video form of this blog post](https://www.youtube.com/watch?v=loNdGAnKEf8&feature=youtu.be)**

### tl;dr / I am an experienced (neo)vim user

0. You may want to use a plugin manager; we are using [vim-plug](https://github.com/junegunn/vim-plug) for the tutorial.
1. Install [fzf.vim](https://github.com/junegunn/fzf.vim) and [ripgrep](https://github.com/BurntSushi/ripgrep).
2. Configure key mappings for `:Files`, `:GFiles`,  and `:Rg`

## Functionality

We will gain the following functionality from integrating Fzf and Ripgrep into (neo)vim:

### Fuzzy searching files (:Files)

![:Files](/neovim-fzf/files.png)

### Fuzzy searching open buffers (:Buffers)

![:Buffers](/neovim-fzf/buffers.png)

### Fuzzy searching files tracked by git (:GFiles)

![Filtering](/neovim-fzf/filtering.png)

### Blazing fast textual search with Ripgrep

![:Rg](/neovim-fzf/ripgrep.png)

## Installation

- [Installation docs for fzf.vim](https://github.com/junegunn/fzf#installation) 
- [Installation docs for ripgrep](https://github.com/BurntSushi/ripgrep#installation)

Once you have the tools installed, let's set up some basic key mappings in `init.vim` or `.vimrc`:

```VimL

nnoremap <C-p> :Files<CR>
nnoremap <C-o> :Buffers<CR>
nnoremap <C-g> :GFiles<CR>
nnoremap <C-f> :Rg 

```

One thing to note, is that there is an empty space after `:Rg`. This is so we don't have to bother adding it manually after pressing `<C-f>`.

## Conclusion

That's all there is to it! Go ahead and give your new key mappings a whirl.

Don't forget to check out [the numerous available commands for fzf.vim](https://github.com/junegunn/fzf.vim#commands) to really personalize your setup and make your vim editing fly.

