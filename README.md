# IdeaVim Configuration Guide

This document explains how the current `.ideavimrc` works, what plugins are enabled, and the most important shortcuts/combos.

## Overview

- **Leader key**: `Space`
- **Main goals**:
  - Faster navigation between files, tabs, methods, and splits
  - Quick access to IntelliJ/Android Studio actions from Vim mode
  - Better editing workflow with EasyMotion, multi-cursor, and refactor shortcuts

## Plugins Enabled

- `easymotion/vim-easymotion`
- `preservim/nerdtree`
- `machakann/vim-highlightedyank`

Also enabled through `set` options:

- `surround`
- `multiple-cursors`
- `argtextobj`
- `commentary`
- `which-key`

## Core Editor Behavior

- Relative + absolute line numbers: `set number relativenumber`
- Search behavior:
  - `ignorecase` + `smartcase`
  - incremental search (`incsearch`)
  - highlight results (`hlsearch`)
- Clipboard integration: `set clipboard+=unnamed`
- IDE-aware line join: `set ideajoin`
- No key timeout: `set notimeout`

## Mode / Quality-of-Life Mappings

- **Exit insert mode quickly**: `jk` → `<Esc>`
- **Clear search highlight**: `<leader>/`
- **Reformat code**: `\r`
- **Firebender accept completion**: `<Tab>`

## Word Motion Improvements

These remap word motions to better handle camelCase/snake_case navigation:

- `w` → `[w`
- `e` → `]w`
- `b` → `[b`
- `ge` → `[b`

## EasyMotion

- `<leader>f` → EasyMotion `s`
- `<leader>e` → EasyMotion `f`

## Go To / Code Navigation

- `gd` → Go to declaration
- `gy` → Go to type declaration
- `gI` → Go to implementation
- `gn` → Next method
- `gp` → Previous method

## Tab + Split Navigation

### Tabs

- `<leader>j` → Previous tab
- `<leader>k` → Next tab

### Split focus movement

- `Ctrl + Left/Right/Down/Up` → move focus between splits
- `Alt + j/k/l/;` (normal mode):
  - `Alt+j` → left split
  - `Alt+k` → bottom split
  - `Alt+l` → top split
  - `Alt+;` → right split
- Same `Alt` mappings also work from insert mode (auto-exit insert first)

### Split management

- `<leader>sv` → Vertical split
- `<leader>sh` → Horizontal split
- `<leader>sw` → Close current split/editor tab
- `<leader>sa` → Close all other splits/editors

## Which-Key Groups (Leader Menus)

### Actions

- `<leader>a` → Quick Fix / Intentions

### Search (`<leader>s`)

- `<leader>se` → Search Everywhere
- `<leader>sr` → Recent Files
- `<leader>su` → Find Usages
- `<leader>sp` → Recent Projects

### Navigation (`<leader>n`)

- `<leader>ne` → Next Error
- `<leader>no` → Next Occurrence
- `<leader>ns` → Switcher
- `<leader>nn` → Go to Line
- `<leader>n,` → Back
- `<leader>n.` → Forward

### Git (`<leader>g`)

- `<leader>gg` → Commit/Checkin
- `<leader>gc` → Branches
- `<leader>gp` → Commit & Push
- `<leader>gP` → Push
- `<leader>gm` → Git menu
- `<leader>gf` → Fetch
- `<leader>ga` → Annotate / blame
- `<leader>gl` → Version Control tool window
- `<leader>gt` → Commit tool window

### Gradle / Build (`<leader>G`)

- `<leader>Gg` → Android sync project
- `<leader>Gs` → Sync all external projects
- `<leader>Gc` → Execute Gradle task
- `<leader>Gb` → Compile dirty
- `<leader>GB` → Make project
- `<leader>Gr` → Refresh dependencies
- `<leader>GC` → Compile project
- `<leader>GR` → Rebuild project
- `<leader>Gt` → Gradle tool window
- `<leader>Gv` → Build variants
- `<leader>Gl` → Show Gradle daemons

### Run (`<leader>r`)

- `<leader>rn` → Run
- `<leader>rc` → Choose run configuration
- `<leader>rs` → Stop
- `<leader>rr` → Rerun
- `<leader>rd` → Debug class
- `<leader>rh` → Test history/import tests
- `<leader>rm` → Run menu
- `<leader>rf` → Rerun failed tests

### Debug (`<leader>d`)

- `<leader>dt` → Toggle breakpoint
- `<leader>ds` → Start listening
- `<leader>do` → Step over
- `<leader>di` → Step into
- `<leader>dr` → Evaluate expression
- `<leader>dC` → Run to cursor
- `<leader>dc` → Resume

### Multi-cursor (`<leader>m`)

- `<leader>mj` → Add cursor below
- `<leader>mk` → Add cursor above
- `<leader>mn` → Select next occurrence
- `<leader>mN` → Unselect previous occurrence
- `<leader>ma` → Select all occurrences
- `<leader>ml` (visual) → Cursor per selected line
- `<leader>ms` → Skip occurrence
- `<leader>mr` → Remove all extra cursors

### Visual multi-cursor (`<leader>v`)

- `<leader>vj` (visual) → Add cursor down
- `<leader>vk` (visual) → Add cursor up
- `<leader>vn` → Select next match
- `<leader>va` → Select all matches

### Language / Refactor (`<leader>l`)

- `<leader>lm` → Refactor menu
- `<leader>lr` → Rename
- `<leader>lc` → Change signature
- `<leader>lv` → Introduce variable
- `<leader>lR` (visual) → Extract method/function
- `<leader>lf` → Reformat code
- `<leader>oi` → Optimize imports
- `<leader>ls` → File structure popup

### Tool windows (`<leader>t`)

- `<leader>tr` → Run window
- `<leader>td` → Debug window
- `<leader>tg` → Version control window
- `<leader>tt` → Terminal window
- `<leader>tl` → Logcat window

## NERDTree

- `Ctrl+n` → Open NERDTree
- Inside NERDTree:
  - `j` → Activate/open node
  - `k` → Jump parent

Useful commands (manual):

- `:NERDTreeFocus`
- `:NERDTreeToggle`
- `:NERDTreeClose`
- `:NERDTreeFind`
- `:NERDTreeRefreshRoot`

## Notes

- If a mapping does not work, check if the target IDE action exists in your IDE version.
- To discover action IDs, use `:actionlist` or `Ctrl+Shift+A` and inspect action names.
- This setup is optimized for JetBrains IDEs + IdeaVim plugin.
