
### Settings
set norelativenumber number
set nocompatible
set hidden
set nocp
set rtp+='/Users/krislitman/tabnine-vim'
set history=100
set wildmenu
filetype plugin on
set hlsearch
set incsearch
### Set NERDTree to open on start with cursor in window
autocmd VimEnter * NERDTree | wincmd p

### Settings for rainbow brackets
let g:rainbow_active = 1 set to 0 if you want to enable it later via :RainbowToggle

### Grep Settings
set grepprg=rg\ --vimgrep\ --smart-case\ --follow

### Set Key Mappings
nnoremap <esc><esc> :noh<return><esc>
nnoremap <silent> <C-f> :Files<CR>
nmap <C-e> :NERDTreeToggle<CR>
vmap ++ <plug>NERDCommenterToggle
nmap ++ <plug>NERDCommenterToggle
inoremap jk <Esc>

### For Plug Management System
let data_dir = has('nvim') ? stdpath('data') . '/site' : '~/.vim'
if empty(glob(data_dir . '/autoload/plug.vim'))
  silent execute '!curl -fLo '.data_dir.'/autoload/plug.vim --create-dirs  https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim'
  autocmd VimEnter * PlugInstall --sync | source $MYVIMRC
endif

### Beggining of Plugins
call plug#begin('~/.vim/plugged')

Plug 'ryanoasis/vim-devicons'
Plug 'neoclide/coc.nvim', {'branch': 'release'}
Plug 'tiagofumo/vim-nerdtree-syntax-highlight'
Plug 'PhilRunninger/nerdtree-buffer-ops'
Plug 'scrooloose/nerdtree'
Plug 'Xuyuanp/nerdtree-git-plugin'
Plug 'airblade/vim-gitgutter'
Plug 'scrooloose/nerdcommenter'
Plug 'christoomey/vim-tmux-navigator'
Plug 'arcticicestudio/nord-vim'
Plug 'junegunn/fzf.vim'
Plug 'junegunn/fzf', { 'do': { -> fzf#install() } }
Plug 'itchyny/lightline.vim'
Plug 'luochen1990/rainbow'
Plug 'iamcco/markdown-preview.nvim', { 'do': 'cd app && yarn install'  }
Plug 'ap/vim-css-color',
Plug 'psliwka/vim-smoothie',
Plug 'bronson/vim-trailing-whitespace',
Plug 'mg979/vim-visual-multi', {'branch': 'master'},
Plug 'tpope/vim-surround'

call plug#end()

### Colorscheme
colorscheme nord

" Use tab for trigger completion with characters ahead and navigate.
" Use command ':verbose imap <tab>' to make sure tab is not mapped by
" other plugin before putting this into your config.
inoremap <silent><expr> <TAB>
      \ pumvisible() ? "\<C-n>" :
      \ <SID>check_back_space() ? "\<TAB>" :
      \ coc#refresh()
inoremap <expr><S-TAB> pumvisible() ? "\<C-p>" : "\<C-h>"

function! s:check_back_space() abort
  let col = col('.') - 1
  return !col || getline('.')[col - 1]  =~# '\s'
endfunction

### Settings for COC
let g:coc_global_extensions = [
			\ 'coc-snippets',
			\ 'coc-pairs',
			\ 'coc-tsserver',
			\ 'coc-eslint',
			\ 'coc-prettier',
			\ 'coc-json',
			\ ]
set hidden


### Lightline Settings
"
set laststatus=2
if !has('gui_running')
  set t_Co=256
endif

let g:lightline = {
      \ 'colorscheme': 'nord',
      \	'active': {
      \   'left': [ [ 'mode', 'paste' ],
      \             [ 'gitbranch', 'readonly', 'filename', 'modified' ] ]
      \ },
      \ 'component_function': {
      \   'gitbranch': 'FugitiveHead'
      \ },
      \ }

