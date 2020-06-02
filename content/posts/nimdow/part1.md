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

# Planned Features

Features implemented at time of writing this article (I will keep the list updated).

### Version 0.5

- [x] Multiple tags (single tag viewed at one time)
- [x] Fullscreen windows
- [x] Multihead support
- [x] User configuration file loaded from $XDG_CONFIG_HOME (or $HOME/.config)
- [x] Status bar integration (single monitor - integrated with Polybar)
  - [ ] Multihead status bar integration (Writing our own bar - See [#29](https://github.com/avahe-kellenberger/nimdow/issues/29))
- [x] Floating window support
  - [x] Move windows with super + left click
  - [x] Resize windows with super + right click drag
- [x] Layouts:
  - [x] Master/stack
- [x] Keybindings:
  - [x] Close window
  - [x] Toggle fullscreen
  - [x] Navigate windows
  - [x] Navigate tags
  - [x] Move windows in stack
  - [x] Move windows between tags

### Version 1.0

- TBA (partial list, still in discussion)
- [ ] Layouts
  - [ ] Monocle
- [ ] Keybindings:
  - [x] Move window between monitors
  - [ ] Add/remove window per tag
  - [ ] View multiple tags
  - [ ] Assign single window to multiple tags
  - [ ] Swap tags between monitors
  - [ ] Reload Nimdow (to apply configuration changes)
  - [ ] Switch layout to master/stack
  - [ ] Switch layout to monocle


# Tags? What about workspaces?

Workspaces and windows have a one-to-one relationship. A window is assigned to a workspace, and the only way to see that window is to view that particular workspace.

Tags have a one-to-many relationship - any number of tags can be assigned to a window. For example: If you assign tags 1, 3, and 5 to your window, your window will be visible if you are viewing any of those tags. As an added bonus, multiple tags can be viewed at once.

This system gives the user a lot more versatility in managing windows.

