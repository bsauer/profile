"Based on http://www.jonlee.ca/hacking-vim-the-ultimate-vimrc/
set nocompatible
set bs=2 "set backspace to be able to delete previous characters
"Enable line numbering, taking up 6 spaces
" set number

" Toggle paste mode with F5
" set pastetoggle=        "pt:    useful so auto-indenting doesn't mess up code when pasting
nnoremap <F2> :set invpaste paste?<CR>
set pastetoggle=<F2>
set showmode


" Uncomment the following to have Vim jump to the last position when
" reopening a file
if has("autocmd")
      au BufReadPost * if line("'\"") > 0 && line("'\"") <= line("$")
          \| exe "normal g'\"" | endif
  endif
 
"Turn off word wrapping
set wrap!
 
"Turn on smart indent
"set smartindent
set tabstop=4 "set tab character to 4 characters
set expandtab "turn tabs into whitespace
set shiftwidth=4 "indent width for autoindent
filetype indent on "indent depends on filetype
 
"Shortcut to auto indent entire file
nmap <F11> 1G=G
imap <F11> <ESC>1G=Ga
 
"Turn on incremental search with ignore case (except explicit caps)
set hlsearch
set incsearch
set ignorecase
set smartcase
 
"Informative status line
set statusline=%F%m%r%h%w\ [TYPE=%Y\ %{&ff}]\ [%l/%L\ (%p%%)]
if &term == "xterm" || &term == "vt220"
  " Let the title stuff work even if we don't open the DISPLAY
  set title
  set t_ts=]2;
  set t_fs=
endif
   
 
"Set color scheme
set t_Co=256
"colorscheme desert256
syntax enable
 
"Enable indent folding
"set foldenable
"set fdm=indent
 
"Set space to toggle a fold
"nnoremap <space> zA
 
"Hide buffer when not in window (to prevent relogin with FTP edit)
set bufhidden=hide
 
"Have 3 lines of offset (or buffer) when scrolling
set scrolloff=3

"""""""""""""""
" gVim Settings
"""""""""""""""
"Set the font and size
set guifont=Lucida\ Console "Hide toolbar
set guioptions-=T
 
"Enable balloon tooltips on spelling suggestions and folds
function! FoldSpellBalloon()
let foldStart = foldclosed(v:beval_lnum )
let foldEnd = foldclosedend(v:beval_lnum)
let lines = []
" Detect if we are in a fold
if foldStart < 0
" Detect if we are on a misspelled word
let lines = spellsuggest( spellbadword(v:beval_text)[ 0 ], 5, 0 )
else
" we are in a fold
let numLines = foldEnd . foldStart + 1
" if we have too many lines in fold, show only the first 14
" and the last 14 lines
if ( numLines > 31 )
let lines = getline( foldStart, foldStart + 14 )
let lines += [ '-- Snipped ' . ( numLines - 30 ) . ' lines --' ]
let lines += getline( foldEnd . 14, foldEnd )
else
"less than 30 lines, lets show all of them
let lines = getline( foldStart, foldEnd )
endif
endif
" return result
return join( lines, has( .balloon_multiline. ) ? .\n. : . . )
endfunction
"set balloonexpr=FoldSpellBalloon()
"set ballooneval

"""""""""""""""
" Extra Options
"""""""""""""""
"Set line numbering to take up 5 spaces
 set numberwidth=5 "Highlight current line
" set cursorline
 
"Turn on spell checking with English dictionary
 set spell
 set spelllang=en
 set spellsuggest=9 "show only 9 suggestions for misspelled words

"Turn on statusbar and make insert aware
 function! InsertStatuslineColor(mode)
   if a:mode == 'i'
     hi statusline guibg=Cyan ctermfg=6 guifg=Black ctermbg=0
   elseif a:mode == 'r'
     hi statusline guibg=Purple ctermfg=5 guifg=Black ctermbg=0
   else
     hi statusline guibg=DarkRed ctermfg=1 guifg=Black ctermbg=0
   endif
 endfunction

 au InsertEnter * call InsertStatuslineColor(v:insertmode)
 au InsertLeave * hi statusline guibg=DarkGrey ctermfg=8 guifg=White ctermbg=15

" default the statusline to green when entering Vim
 hi statusline guibg=DarkGrey ctermfg=8 guifg=White ctermbg=15

" Formats the statusline
 set statusline=%f                           " file name
 set statusline+=[%{strlen(&fenc)?&fenc:'none'}, "file encoding
 set statusline+=%{&ff}] "file format
 set statusline+=%y      "filetype
 set statusline+=%h      "help file flag
 set statusline+=%m      "modified flag
 set statusline+=%r      "read only flag

 set statusline+=\ %=                        " align left
 set statusline+=Line:%l/%L[%p%%]            " line X of Y [percent of file]
 set statusline+=\ Col:%c                    " current column
 set statusline+=\ Buf:%n                    " Buffer number
 set statusline+=\ [%b][0x%B]\               " ASCII and byte code under cursor
 set laststatus=2
