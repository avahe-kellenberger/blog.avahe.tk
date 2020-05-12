---
title: "Nimdow - A tiling window manager written in Nim"
date: 2020-05-12T16:22:13-04:00
draft: false
---

**[Nimdow GitHub Link](https://github.com/avahe-kellenberger/nimdow/tree/master)**

# What is Nim?

[Nim](https://nim-lang.org/) is an awesome programming language that I've recently picked up.

An excerpt from the official site:


_**"Efficient, expressive, elegant**_

_**Nim is a statically typed compiled systems programming language.
It combines successful concepts from mature languages like Python, Ada and Modula."**_

It has quickly become my favorite programming language. Nim is very powerful and easy to use.

# The Project

[Nimdow](https://github.com/avahe-kellenberger/nimdow/tree/master) is a [tiling window manager (twm)](https://en.wikipedia.org/wiki/Tiling_window_manager) written in Nim. The goal of Nimdow is to be a full-featured minimal twm, similar to that of [dwm](https://dwm.suckless.org/) with more sensible defaults.

Currently, the project has not reached Beta release, but is being developed at a fast and steady pace.

**Beta release is planned for June 1st, 2020.**

# Planned Features

Features implemented at time of writing this article (I will keep the list updated).

### Beta Release (version 0.5)


- [x] Multiple tags (single tag viewed at one time)
- [x] Fullscreen windows
- [ ] Multihead support
- [x] User configuration file loaded from `$XDG_CONFIG_HOME` (or `$HOME/.config`)
- [ ] Status bar integration (probably 3rd party status bar)
- [ ] Layouts:
  - [x] Master/stack
  - [ ] Monocle
- [ ] Keybindings:
  - [x] Close window
  - [x] Toggle fullscreen
  - [ ] Switch layout to master/stack
  - [ ] Switch layout to monocle
  - [x] Navigate windows
  - [x] Navigate tags
  - [x] Move windows in stack
  - [x] Move windows between tags
  - [ ] Add/remove window per tag

### Official Release (version 1.0)

This is a partial list, and will be expanded as I decide on which features to add.

- [ ] Floating window support
- [ ] Keybindings:
  - [ ] View multiple tags
  - [ ] Assign single window to multiple tags
  - [ ] Move window between screens
  - [ ] Swap tags between screens
  - [ ] Reload Nimdow (to apply configuration changes)


# Tags? What about workspaces?

Workspaces and windows have a one-to-one relationship. A window is assigned to a workspace, and the only way to see that window is to view that particular workspace.

Tags have a one-to-many relationship - any number of tags can be assigned to a window. For example: If you assign tags 1, 3, and 5 to your window, your window will be visible if you are viewing any of those tags. As an added bonus, multiple tags can be viewed at once.

This system gives the user a lot more versatility in managing windows.

