## Vim command

### normal mode

- `i`

goto insert
    
    - `shift + i`
        
    在当前行的最前面插入

- `a`
	
	在当前选中字符后插入
	
	-   `shift + a`
	
	    在当前行的最后面插入
	
- `o`

    在本行的下一行开启新行 && goto edit mode

    - `shift + o`

        在本行的上一行开启新行 &&  goto edit mode

- `h l j k`

    h => left	l => right	j => down	k => up

- `Esc`

    quit edit mode && goto normal mode
    
- `x`

    删除当前光标下的字符

- `d` + <motion>

    - `d + ->`

        往右删除一个字符 

    - `d + 3->`

        往右删除三个字符

    - `d+d`

        剪切当前行，连续两个当前字符表示对当前行的操作

- `p`

    paste

- `y`

    copy

- `c`change

    delete && goto edit

- `w`

    goto the next word

    - `cw` 

    	delete the next word

    - `cb`

        delete the prv word

    - `ciw` change in word

        delete the word when in the word
        
    - `ci"`

        delete the contant in `""`

- `f`

    find

    - `fb`

        find `b` in this line

    - `df:`

        delete the contant before : in this line

- `b`

    goto the previous word

- `u`

    unmake
    
- `ctrl + r`

    redo

###  command mode

- `:`
	goto command mode
	
- `w`
	write file
	
- `q`
	quit vim
	
- `split`

  create screen

  - `C-w +[hjkl]`

      to select screen

  - `[e|edit] path`

      open the file of path

- `tabe`

    open new vim tab

    - `-tabnext`
### edit mode

### visual mode

-   `v`

    goto visual mode, do something like mouse

-   `shift + v`

    line select visual mode

-   `:` 

    run the nromal command for every line

    ep: 

    ```shell
    nromal Iindex
    =============
      1 index1
      2 index2
      3 index3
      4 index4
      5 index5
      6 index6
      7 index7
    ```

-   `ctrl + v`

    goto visual block mode, select a block

## some about .vimrc

create file in ~/.vim/vimrc

| Param   | Value                 | Description                     |
| :------ | --------------------- | ------------------------------- |
| noremap | (beforeKey, afterKey) | 使beforeKey的按键效果到afterKey	|
| map     | (bCmd, aCmd)          | 使bCmd的效果由aCmd替换          	|
| syntac  | on/off                | 代码高亮                       	|
| set | number/nonumber | 设置 |
| exec | command | 新建窗口时执行 |
|	|	|	|



## Plug

```sh
let mapleader=" "
"j改为向下跳跃五行
"noremap j 5j 

"nop means no operation
map s <nop>
"CR means Enter
map S :w<CR>
map Q :q<CR> 
"重新加载vimrc
map R :source $MYVIMRC<CR>

"向右分屏
map sl :set splitright<CR>:vsplit<CR>
"向左分屏
map sh :set nosplitright<CR>:vsplit<CR> 
"向下分屏
map sj :set splitbelow<CR>:split<CR>
"向上分屏
map sk :set nosplitbelow<CR>:split<CR>

"兼容vi
set nocompatible
"read fileTYpe
filetype on
filetype indent on
filetype plugin on
filetype plugin indent on
"使用鼠标
set mouse=a
set encoding=utf-8
"修正终端配色
let &t_ut=''
"调整缩进长度
set expandtab
set tabstop=2
set shiftwidth=2
set softtabstop=2
"显示行尾空格
set list
"修改缩进
set listchars=tab:▸\ ,trail:▫
set scrolloff=5
set tw=0
set indentexpr=
"type back to the end of line
set backspace=indent,eol,start
"收起代码
set foldmethod=indent
"光标设置
set foldlevel=99
let &t_SI = "\<Esc>]50;CursorShape=1\x7"
let &t_SR = "\<Esc>]50;CursorShape=2\x7"
let &t_EI = "\<Esc>]50;CursorShape=0\x7"
"设置底部状态栏
set laststatus=2
"可以在vim中对当前目录执行命令
set autochdir
"每次打开时光标会回到上一次的位置
au BufReadPost * if line("'\"") > 1 && line("'\"") <= line("$") | exe "normal! g'\"" | endif

map ; :

"修改分屏大小
map <UP> :res +5<CR>
map <down> :res -5<CR>
map <left> :vertical resize-5<CR>
map <right> :vertical resize+5<CR>

map tu :tabe<CR>
map tn :tabnext<CR>
map tp :-tabnext<CR>

map se <C-w>t<C-w>H
map sq <C-w>t<C-w>K
" N key: go to the start of the line
noremap <C-n> 0
" I key: go to the end of the line
noremap <C-i> $

"切换分屏
map <LEADER>h <C-w>h
map <LEADER>j <C-w>j
map <LEADER>k <C-w>k
map <LEADER>l <C-w>l

"设置行号
set number
"活动行号
set norelativenumber
"当前行的下划线
set cursorline
"字符不超过窗口
set wrap
"显示输入的字符
set showcmd
"命令模式下的命令补 全
set wildmenu
"设置查找结果高亮
set hlsearch
"设置查找时的字符高亮
set incsearch
"忽略大小写
set ignorecase
"出现大写时必须匹配大写
set smartcase

noremap = nzz
noremap - Nzz
noremap <LEADER><CR> :nohlsearch<CR>

"新建的文件不做搜索高亮
exec "nohlsearch"

syntax on

"使用插件
call plug#begin('~/.vim/plugged')

Plug 'vim-airline/vim-airline'
Plug 'connorholyday/vim-snazzy' 

"" File navigation
Plug 'scrooloose/nerdtree', { 'on': 'NERDTreeToggle' }
Plug 'Xuyuanp/nerdtree-git-plugin'

"" Taglist
Plug 'majutsushi/tagbar', { 'on': 'TagbarOpenAutoClose' }

"" Error checking
Plug 'w0rp/ale'

"" Auto Complete
Plug 'Valloric/YouCompleteMe'

"" Undo Tree
Plug 'mbbill/undotree/'

"" Other visual enhancement
Plug 'nathanaelkane/vim-indent-guides'
Plug 'itchyny/vim-cursorword'
"
"" Git
Plug 'rhysd/conflict-marker.vim'
Plug 'tpope/vim-fugitive'
Plug 'mhinz/vim-signify'
Plug 'gisphm/vim-gitignore', { 'for': ['gitignore', 'vim-plug'] }

"" HTML, CSS, JavaScript, PHP, JSON, etc.
Plug 'elzr/vim-json'
Plug 'hail2u/vim-css3-syntax'
Plug 'spf13/PIV', { 'for' :['php', 'vim-plug'] }
Plug 'gko/vim-coloresque', { 'for': ['vim-plug', 'php', 'html', 'javascript', 'css', 'less'] }
Plug 'pangloss/vim-javascript', { 'for' :['javascript', 'vim-plug'] }
Plug 'mattn/emmet-vim'

"" Python
Plug 'vim-scripts/indentpython.vim'

"" Markdown
Plug 'iamcco/markdown-preview.nvim', { 'do': { -> mkdp#util#install_sync() }, 'for' :['markdown', 'vim-plug'] }
Plug 'dhruvasagar/vim-table-mode', { 'on': 'TableModeToggle' }
Plug 'vimwiki/vimwiki'

"" Bookmarks
Plug 'kshenoy/vim-signature'

"" Other useful utilities
Plug 'terryma/vim-multiple-cursors'
Plug 'junegunn/goyo.vim' " distraction free writing mode
Plug 'tpope/vim-surround' " type ysks' to wrap the word with '' or type cs'` to change 'word' to `word`
Plug 'godlygeek/tabular' " type ;Tabularize /= to align the =
Plug 'gcmt/wildfire.vim' " in Visual mode, type i' to select all text in '', or type i) i] i} ip
Plug 'scrooloose/nerdcommenter' " in <space>cc to comment a line

"" Dependencies
Plug 'MarcWeber/vim-addon-mw-utils'
Plug 'kana/vim-textobj-user'
Plug 'fadein/vim-FIGlet'

call plug#end()
"设置透明
let g:SnazzyTransparent = 1
"使用snazzy 配色
colorscheme snazzy


" ===
" === NERDTree
" ===
map tt :NERDTreeToggle<CR>
let NERDTreeMapOpenExpl = ""
let NERDTreeMapUpdir = ""
let NERDTreeMapUpdirKeepOpen = "l"
let NERDTreeMapOpenSplit = ""
let NERDTreeOpenVSplit = ""
let NERDTreeMapActivateNode = "i"
let NERDTreeMapOpenInTab = "o"
let NERDTreeMapPreview = ""
let NERDTreeMapCloseDir = "n"
let NERDTreeMapChangeRoot = "y"


" ==
" == NERDTree-git
" ==
let g:NERDTreeIndicatorMapCustom = {
    \ "Modified"  : "✹",
    \ "Staged"    : "✚",
    \ "Untracked" : "✭",
    \ "Renamed"   : "➜",
    \ "Unmerged"  : "═",
    \ "Deleted"   : "✖",
    \ "Dirty"     : "✗",
    \ "Clean"     : "✔︎",
    \ "Unknown"   : "?"
    \ }


" ===
" === You Complete ME
" ===
nnoremap gd :YcmCompleter GoToDefinitionElseDeclaration<CR>
nnoremap g/ :YcmCompleter GetDoc<CR>
nnoremap gt :YcmCompleter GetType<CR>
nnoremap gr :YcmCompleter GoToReferences<CR>
let g:ycm_autoclose_preview_window_after_completion=0
let g:ycm_autoclose_preview_window_after_insertion=1
let g:ycm_use_clangd = 0
let g:ycm_python_interpreter_path = "/bin/python3"
let g:ycm_python_binary_path = "/bin/python3"


" ===
" === ale
" ===
let b:ale_linters = ['pylint']
let b:ale_fixers = ['autopep8', 'yapf']


" ===
" === Taglist
" ===
map <silent> T :TagbarOpenAutoClose<CR>


" ===
" === MarkdownPreview
" ===
let g:mkdp_auto_start = 0
let g:mkdp_auto_close = 1
let g:mkdp_refresh_slow = 0
let g:mkdp_command_for_global = 0
let g:mkdp_open_to_the_world = 0
let g:mkdp_open_ip = ''
let g:mkdp_browser = 'chromium'
let g:mkdp_echo_preview_url = 0
let g:mkdp_browserfunc = ''
let g:mkdp_preview_options = {
    \ 'mkit': {},
    \ 'katex': {},
    \ 'uml': {},
    \ 'maid': {},
    \ 'disable_sync_scroll': 0,
    \ 'sync_scroll_type': 'middle',
    \ 'hide_yaml_meta': 1
    \ }
let g:mkdp_markdown_css = ''
let g:mkdp_highlight_css = ''
let g:mkdp_port = ''
let g:mkdp_page_title = '「${name}」'


" ===
" === vim-table-mode
" ===
map <LEADER>tm :TableModeToggle<CR>

" ===
" === Python-syntax
" ===
let g:python_highlight_all = 1
" let g:python_slow_sync = 0


" ===
" === vim-indent-guide
" ===
let g:indent_guides_guide_size = 1
let g:indent_guides_start_level = 2
let g:indent_guides_enable_on_vim_startup = 1
let g:indent_guides_color_change_percent = 1
silent! unmap <LEADER>ig
autocmd WinEnter * silent! unmap <LEADER>ig


" ===
" === Goyo
" ===
map <LEADER>gy :Goyo<CR>


" ===
" === vim-signiture
" ===
let g:SignatureMap = {
        \ 'Leader'             :  "m",
        \ 'PlaceNextMark'      :  "m,",
        \ 'ToggleMarkAtLine'   :  "m.",
        \ 'PurgeMarksAtLine'   :  "dm-",
        \ 'DeleteMark'         :  "dm",
        \ 'PurgeMarks'         :  "dm/",
        \ 'PurgeMarkers'       :  "dm?",
        \ 'GotoNextLineAlpha'  :  "m<LEADER>",
        \ 'GotoPrevLineAlpha'  :  "",
        \ 'GotoNextSpotAlpha'  :  "m<LEADER>",
        \ 'GotoPrevSpotAlpha'  :  "",
        \ 'GotoNextLineByPos'  :  "",
        \ 'GotoPrevLineByPos'  :  "",
        \ 'GotoNextSpotByPos'  :  "mn",
        \ 'GotoPrevSpotByPos'  :  "mp",
        \ 'GotoNextMarker'     :  "",
        \ 'GotoPrevMarker'     :  "",
        \ 'GotoNextMarkerAny'  :  "",
        \ 'GotoPrevMarkerAny'  :  "",
        \ 'ListLocalMarks'     :  "m/",
        \ 'ListLocalMarkers'   :  "m?"
        \ }


" ===
" === Undotree
" ===
let g:undotree_DiffAutoOpen = 0
map L :UndotreeToggle<CR>

```

