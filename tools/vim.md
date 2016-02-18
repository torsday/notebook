# Vim

<!-- TOC depthFrom:2 depthTo:6 withLinks:1 updateOnSave:1 orderedList:0 -->

- [[`.vimrc`](https://github.com/torsday/dotfiles/blob/master/.vimrc)](#vimrchttpsgithubcomtorsdaydotfilesblobmastervimrc)
	- [Font](#font)
	- [Custom Functions](#custom-functions)
	- [References](#references)
- [Custom commands](#custom-commands)
- [Easy file diffing](#easy-file-diffing)
- [or](#or)
- [Vim Profiling](#vim-profiling)
- [Search & Replace in multiple files](#search-replace-in-multiple-files)
- [Yanking text to register](#yanking-text-to-register)
- [Macros](#macros)
	- [To record a macro:](#to-record-a-macro)
	- [To run the macro:](#to-run-the-macro)

<!-- /TOC -->

## [`.vimrc`](https://github.com/torsday/dotfiles/blob/master/.vimrc)

markdown fenced code block highlighting

*Note: Not all languages are supported. To see a list of lanugages you have installed on Mac (with Vim installed by Homebrew) run* `ls -l /usr/local/Cellar/vim/7.4.1190/share/vim/vim74/syntax`

```sh
let g:markdown_fenced_languages = [
    'bash=sh',
    'css',
    'html',
    'javascript',
    'php',
    'python',
    'ruby',
    'vim'
]
```

```sh
" to setup neobundle (which this vimrc uses)
" https://github.com/Shougo/neobundle.vim
" $ mkdir -p ~/.vim/bundle
" $ git clone https://github.com/Shougo/neobundle.vim ~/.vim/bundle/neobundle.vim
" Launch vim, run :NeoBundleInstall
```

Use Vim settings, rather than Vi settings. This must be first, because it changes other options as a side effect.

```sh
set nocompatible
```

Make backspace behave in a sane manner.

```sh
set backspace=indent,eol,start
```

```sh
syntax on
```

Enable file type detection and do language-dependent indenting.

```sh
filetype plugin indent on
```

show line numbers

```sh
set number
```

```sh
set softtabstop=2 shiftwidth=2 expandtab
```

Enable filetypes

```sh
filetype on
filetype plugin on
filetype indent on
```

```sh
set wildmenu
set showmatch
```

```sh
inoremap kj <esc>
```

autocomplete brackets

```sh
inoremap { {<CR><BS>}<Esc>ko
```

### Font

```sh
"set anti enc=utf-8
set guifont=Source\ Code\ Pro:h14
```

```sh
" NEOBUNDLE

" Note: Skip initialization for vim-tiny or vim-small.
if !1 | finish | endif

if has('vim_starting')
  if &compatible
    set nocompatible               " Be iMproved
  endif

   " Required:
   set runtimepath+=~/.vim/bundle/neobundle.vim/
 endif

" Required:
call neobundle#begin(expand('~/.vim/bundle/'))

" Let NeoBundle manage NeoBundle
" Required:
NeoBundleFetch 'Shougo/neobundle.vim'

" My Bundles here:
" Refer to |:NeoBundle-examples|.
" Note: You don't set neobundle setting in .gvimrc!
"
"  NeoBundle 'Shougo/vimproc.vim', {
" \ 'build' : {
" \     'windows' : 'tools\\update-dll-mingw',
" \     'cygwin' : 'make -f make_cygwin.mak',
" \     'mac' : 'make -f make_mac.mak',
" \     'linux' : 'make',
" \     'unix' : 'gmake',
" \    },
" \ }

" NeoBundle 'scrooloose/nerdtree'
" NeoBundle 'Shougo/unite.vim'
" NeoBundle 'junegunn/vim-easy-align'
" NeoBundle 'Lokaltog/vim-easymotion'
" NeoBundle 'rstacruz/sparkup'
" NeoBundle 'tpope/vim-surround'
" NeoBundle 'mileszs/ack.vim'
" NeoBundle 'ddollar/nerdcommenter'
" NeoBundle 'tpope/vim-unimpaired'
" NeoBundle 'ervandew/supertab'
" NeoBundle 'scrooloose/syntastic'
" NeoBundle 'majutsushi/tagbar'
" NeoBundle 'MarcWeber/vim-addon-mw-utils'
" NeoBundle 'tomtom/tlib_vim'
" NeoBundle 'garbas/vim-snipmate'
" NeoBundle 'honza/vim-snippets'
" NeoBundle 'garbas/vim-snipmate'
" NeoBundle 'Lokaltog/vim-easymotion'
" NeoBundle 'chrisbra/NrrwRgn'
" NeoBundle 'tpope/vim-fugitive'
" NeoBundle 'vim-scripts/ZoomWin'
" NeoBundle 'jeetsukumaran/vim-buffergator'
" NeoBundle 'skalnik/vim-vroom'
" NeoBundle 'terryma/vim-multiple-cursors'
" NeoBundle 'bronson/vim-trailing-whitespace'
NeoBundle 'trusktr/seti.vim'
NeoBundle 'bling/vim-airline'
NeoBundle 'sjl/gundo.vim'
NeoBundle 'rking/ag.vim'
NeoBundle 'kien/ctrlp.vim'

call neobundle#end()
```

```sh
colorscheme seti
let g:airline_theme='luna'
set laststatus=2
```

```sh
" toggle gundo
nnoremap <leader>u :GundoToggle<CR>
```

```sh
" open ag.vim
nnoremap <leader>a :Ag
```

```sh
" CtrlP settings
let g:ctrlp_match_window = 'bottom,order:ttb'
let g:ctrlp_switch_buffer = 0
let g:ctrlp_working_path_mode = 0
let g:ctrlp_user_command = 'ag %s -l --nocolor --hidden -g ""'
"let g:ctrlp_user_command = 'ag %s -l --nocolor -g ""'
```

```sh
" allows cursor change in tmux mode
if exists('$TMUX')
    let &t_SI = "\<Esc>Ptmux;\<Esc>\<Esc>]50;CursorShape=1\x7\<Esc>\\"
    let &t_EI = "\<Esc>Ptmux;\<Esc>\<Esc>]50;CursorShape=0\x7\<Esc>\\"
else
    let &t_SI = "\<Esc>]50;CursorShape=1\x7"
    let &t_EI = "\<Esc>]50;CursorShape=0\x7"
endif
```

```sh
augroup configgroup
    autocmd!
    autocmd VimEnter * highlight clear SignColumn
    autocmd BufWritePre *.php,*.py,*.js,*.txt,*.hs,*.java,*.md
                \:call <SID>StripTrailingWhitespaces()
    autocmd FileType java setlocal noexpandtab
    autocmd FileType java setlocal list
    autocmd FileType java setlocal listchars=tab:+\ ,eol:-
    autocmd FileType java setlocal formatprg=par\ -w80\ -T4
    autocmd FileType php setlocal expandtab
    autocmd FileType php setlocal list
    autocmd FileType php setlocal listchars=tab:+\ ,eol:-
    autocmd FileType php setlocal formatprg=par\ -w80\ -T4
    autocmd FileType ruby setlocal tabstop=2
    autocmd FileType ruby setlocal shiftwidth=2
    autocmd FileType ruby setlocal softtabstop=2
    autocmd FileType ruby setlocal commentstring=#\ %s
    autocmd FileType python setlocal commentstring=#\ %s
    autocmd BufEnter *.cls setlocal filetype=java
    autocmd BufEnter *.zsh-theme setlocal filetype=zsh
    autocmd BufEnter Makefile setlocal noexpandtab
    autocmd BufEnter *.sh setlocal tabstop=2
    autocmd BufEnter *.sh setlocal shiftwidth=2
    autocmd BufEnter *.sh setlocal softtabstop=2
augroup END

" Required:
filetype plugin indent on

" If there are uninstalled bundles found on startup,
" this will conveniently prompt you to install them.
NeoBundleCheck
```

### Custom Functions

```sh
" toggle between number and relativenumber
function! ToggleNumber()
    if(&relativenumber == 1)
        set norelativenumber
        set number
    else
        set relativenumber
    endif
endfunc
```

```sh
" strips trailing whitespace at the end of files. this
" is called on buffer write in the autogroup above.
function! <SID>StripTrailingWhitespaces()
    " save last search & cursor position
    let _s=@/
    let l = line(".")
    let c = col(".")
    %s/\s\+$//e
    let @/=_s
    call cursor(l, c)
endfunction
```

```sh
let g:netrw_liststyle=3
```

### References

* [A Good Vimrc](http://dougblack.io/words/a-good-vimrc.html)


---
## Custom commands

Custom commands in Vim are defined via the `command` command. As I learn new
things throughout the week, I like to write them down in a `TIL.md` file. I
found myself constantly running `:tabe ~/Documents/TIL.md` to open my file in a
new tab. To streamline the process, I added the following to my `.vimrc`:

```vimscript
command TIL tabe~/Document/TIL.md
```

Now, whenever I want to write down something I've learned I can just run `:TIL`.

User-defined commands _must_ start with a uppercase letter.

More details in `:help command`, or check out the [online vim docs].

[online vim docs]: http://vimdoc.sourceforge.net/htmldoc/map.html#:command


---
## Easy file diffing

Vim comes with its own diff viewer. It can be launched from the command-line
with:

```bash
vim -d file1 file2
## or
vimdiff file1 file2
```

You can also get a diff from within Vim by opening two files in
splits and running `:diffthis`.

More details in `:help vimdiff`, or check out the [online docs].

[online docs]: http://vimdoc.sourceforge.net/htmldoc/diff.html#vimdiff


---
## Vim Profiling

I recently encountered a situation where Vim was taking an *excruciatingly* long
time to launch. From some manual testing, I was able to isolate the problem to a
particular directory, but I wasn't sure what was causing it. I then discovered
Vim ships with profiling tools that would tell me how much time was spent in
each of the functions that ran during startup. See the [official docs] for more
info.

I'll start with the shell command I ended up running:

```sh
vim -c 'profile start vim.log' -c 'profile func *' -c 'e config/routes.rb' -c 'q'
```

The `-c` option tells Vim to execute the given command after loading the first
file (in this case the empty buffer), and will execute multiple `-c` options
sequentially.

To break it down:

* `-c 'profile start vim.log'` starts the profiler, logging results to the
  vim.log file.
* `-c 'profile func *'` enables profiling of functions matching the given
  pattern. All functions, in this case.
* `-c 'e config/routes.rb'` opens the routes file. This was arbitrary for my
  purposes, as opening any file in the Rails application was slow.
* `-c 'q'` quits.

The `vim.log` file has a lot of detail about the functions that were executed.
Here's a short one that was near the top for me.

```text
FUNCTION  fugitive#is_git_dir()
Called 18 times
Total time:   0.000396
 Self time:   0.000233

count  total (s)   self (s)
   18   0.000271   0.000108   let path = s:sub(a:path, '[\/]$', '') . '/'
   18              0.000107   return isdirectory(path.'objects') && isdirectory(path.'refs') && getfsize(path.'HEAD') > 10

```

That's interesting, for sure, but the good stuff is at the bottom of the file,
where functions are sorted by execution time. Here's my top offender.

```text
count  total (s)   self (s)  function
    1   2.203751   0.000457  rails#buffer_syntax()
```

[official docs]: http://vimdoc.sourceforge.net/htmldoc/repeat.html#profiling


---
## Search & Replace in multiple files

I recently had to replace static files path in multiple files from a project
I were working on, after boggling my mind trying to do it with
[sed](http://en.wikipedia.org/wiki/Sed), I gave up and looked up how to do it
using VIM, I was sure there was a way.

When VIM is started, you can specify multiple files to open as buffers from the
terminal:

```bash
vim *.html
```

This will open all html files on the current directory as buffers.
* You can list the buffers using `:ls`
* You can add a buffer using `:badd <filename>`
* You can close a buffer using `:bdelete <buffer_number>`

Now you can run commands on all open buffers:

```vimscript
:bufdo <command>
```

Searching all instances of **foo** and replacing with **bar**:

```vimscript
:bufdo %s/foo/bar/ge
```

**Notice**: the **e** on the replace command tells vim to ignore errors,
otherwise vim would print an error on each file that doesn't have a match for
**foo**

You can now open the buffers (`:buffer <buffer_number>`) and verify that the
text was replaced.

But this command only replaced the text, we need to save the files to persist
changes:

You can either run another **bufdo** with the **update** command to save the
files:

```vimscript
:bufdo update
```

Or you can pipe it on the first command:

```vimscript
:bufdo %s/foo/bar/g | update
```

And that's it!


---

## Yanking text to register

Yanking and deleting text will save the text to the same unnamed register. Every
time you delete a word, your yanked word will be overwritten. This caused me
endless amounts of frustration when I accidentally deleted a word and had to
remember what I yanked earlier.

I learned that you can specify a register to save your yanked word to by
prepending your yank command with `"a`. Where `a` is a register. There are a
number of different registers which do different things. If you want to learn
more read VIM's [register
documentation](http://vimdoc.sourceforge.net/htmldoc/change.html#registers).

An example usage is:

`"ayw`

This will save the yanked word to the register `a`. After deleting various
things in your file you can always paste your yanked word by:

`"ap`

You can view the contents of all registers via the `:registers` command.

Even after deleting various words in your file, your yanked word will always be
in register `a`.  The VIM wiki has more details on [Replacing a word with yanked
text](http://vim.wikia.com/wiki/Replace_a_word_with_yanked_text).


## Macros

If you want to repeat a bunch of vim commands for running multiple times, record them in a macro.


### To record a macro:

1. type `q` followed by any char: **[a-z]**
1. type your vim commands
1. type `q` again to finish recording

### To run the macro:

`@` followed by the **same char** you chose to store the macro.
