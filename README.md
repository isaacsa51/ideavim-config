# IdeaVim Configuration

This repo is a simple/basic yet powerful configuration of the IdeaVim keymaps that works well with any Jetbrains IDE with the support of the IdeaVim plug.
Take note that the keymaps used is strongly based on the youtube tutorial of IdeaVim Cast on YT.

## Sections

The config of this *vimrc* is based in 5 parts:

  - [Basic/Default configuration from IdeaVim installation](#Basic/Default-configuration)
  - [Customization of the editor & plugins for Vim](#Customization-of-the-editor-&-plugins-for-Vim)
  - [Exit modes](#Exit-modes)
  - [Navigation](#Navigation)
  - [NERDTree](#NERDTree)
  
### Basic/Default configuration

As the title says, just a normal, predefined lines from the clean instalation from IdeaVim that works best for IntelliJ

```
"source ~/.vimrc

"" -- Suggested options --
" Show a few lines of context around the cursor. Note that this makes the
" text scroll if you mouse-click near the start or end of the window.
set scrolloff=5

" Do incremental searching.
set incsearch

" Don't use Ex mode, use Q for formatting.
map Q gq
```

### Customization of the editor & plugins for Vim

In this section is just a simple configuration of the editor view from the IDE itself, taking for example setting relative numbers instead of showing the number of the code in the editor, this change is used to move faster and get how many lines to jump; also taking with the installation of [easymotion](https://github.com/easymotion/vim-easymotion) & [NERDTree](https://github.com/preservim/nerdtree).

Take note that the leader key in this config is the *Space* key

```
Plug 'easymotion/vim-easymotion'
Plug 'preservim/nerdtree'

set number relativenumber
set ideajoin
set easymotion
set surround

"" Leader key
let mapleader = " "
```

### Exit Modes

Instead of using the `ESC` key everytime you need to exit the INSERT mode from Vim, just create a remap of that command to a `jk` or `kj` press:

```
"" Easy exit mode
inoremap jk <esc>
inoremap kj <esc>

```

### Navigation

Here we have an interesting setup for the IDE itself, we use as usual `h j k l` as the navigation cluster to move between tabs and splitted windows.

```
"" Navigation
nmap <Leader>j :action PreviousTab<CR>
nmap <Leader>k :action NextTab<CR>

nmap <c-\> :action SplitVertically<CR>
nmap <c--> :action SplitHorizontally<CR>
nmap <c-=> :action Unsplit<CR>
nmap <c-m> :action MoveEditorToOppositeTabGroup<CR>

sethandler <c-j> a:vim
sethandler <c-k> a:vim

nmap <c-h> <c-w>h
nmap <c-l> <c-w>l
nmap <c-j> <c-w>j
nmap <c-k> <c-w>k
```

It's configured to use `CTRL+<key>` to split or move the focused tab & `CTRL+<h,j,k,l>` to move the focus when having multiple windows in the same IDE.

Don't forget to see that to move between tabs in the same group we use `<Leader>+j` or `<Leader>+k` instead of `h` & `l`, this is configured in that way becuase of the ease of access and following the extension keymap of Vimium.

### NERDTree

I added support of NERDTree to move easily between the files of the file tree of the project itself but still I use a lot the `Shift + Shift` keymap to open a certain file easily as an habit from my side.

```
"" NERDTreeNavigation
"" Commands:
""  Ctrl-n  Opens NERDTree window
""  q       Close the NERDTree window
""  o       Open files, directories and bookmarks
""  go      Open selected file, but leave cursor in NERDTree
""  <C-J>
""  <C-K>
""  R       Refresh directories
""  m       Show nerdtree menu
set NERDTree

map <c-n> :NERDTree<CR>

let g:NERDTreeMapActivateNode='j'
let g:NERDTreeMApJumpParent='k'
":NERDTreeFocus
":NERDTreeToggle
":NERDTreeClose
":NERDTreeFind
":NERDTreeRefreshRoot
```

Full documentation of NERDTree and how to use it is [here.](https://github.com/preservim/nerdtree)
