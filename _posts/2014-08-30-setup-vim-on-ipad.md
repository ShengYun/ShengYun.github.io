---
layout: post
title: Setup vim on iPad
---

It has been 10 days since I arrived in Boston, seems everything is good. Courses will begin at September 2, and some homework was already posted online. `Introduction to Computer Graphics` has a lot of programming work to do and because I got a new iPad mini I thought maybe I can read code on my iPad.

So after a few hours(yes, hours...) googling and trying Apps from App Store, I got frustrated, most good applications are not free, some free applications are either too bad to use, or need an in-app-purchase to be used decently. Then I found [Vim](https://itunes.apple.com/us/app/vim/id492668168?mt=8), yes, and it is free and it supports vimscript, so I gave it a try, but the first try really sucks(In fact I deleted it after trying it and went back to find other applications). But when I realise I can't find a decent free application to browse code on my iPad, I downloaded Vim again. I'm going to share my ios-vim config, in fact it works pretty well:) hope it's useful for you.


### Vim on iOS's limitations
If you have been already googling for vim on iOS, you must know that there are some limitations

    - Vim on iOS can only modify things in your home directory.
    - Vim on iOS doesn't have keyboard support of special keys like ctrl alt esc arrows etc..
    - It can't call external commands such as grep, and don't even think about ctags, but if you find a way to install ctags and call it in Vim on iOS, please let me know.
    - Don't know why, mappings like nnoremap jk <ESC> isn't working for me. But seems like someone have this working.
    
for more information, [here's](http://applidium.com/en/applications/vim/support/) the official FAQ, you can also get it by `:help ios`.
    
So with all these limitations, how can I setup vim to

    0. Syntax highlighting for source code.
    1. Find definitions of local and global symbols.
    2. grep things.
    3. navigate through files.
    
### The basic setup
<div class="message">
  The default ESC key is bounded to \.
</div>

<div class="message">
  Clicking and panning with a single finger will generate click and drag events. Panning with two fingers will generate scrollwheel events (horizontal and vertical). 
</div>

After downloading Vim from App Store, you can open Vim and use vanilla Vim, and as I said previously, there are no *ctrl* *alt* *esc* *arrow* keys. So let's begin to config Vim on iOS.

First we need a `.vimrc` file, using *:!touch .vimrc* raises an error, I believe this is some sort of "iOS protection", so open your computer, create a `.vimrc` file, then edit the file on your computer(you won't want to write it on iPad, it took me about 2 hours and finally I deleted it). Then when you think it's good to go, open iTunes and drag `.vimrc` into `Vim` under the `Apps`'s `File Sharing`. Note that it won't appear in it since it's a hidden file, but don't worry, it's there. And a dialog would prompt if you do it again asking you if you want to replace the old `.vimrc` or not.


{% highlight vim %}
syntax enable
syntax on
set encoding=utf-8
set noswapfile
set nobackup
set ignorecase
set incsearch
set hlsearch
set number
colorscheme torte
set guifont=Courier:h20

" Tab and indent settings
set autoindent
set cindent
set tabstop=4
set softtabstop=4
set shiftwidth=4
set shiftround
set expandtab

nnoremap j gj
nnoremap k gk
{% endhighlight %}

Sorry that I'm not going to explain these settings since these are all basic settings and you can find help information of these by `:h <whatever>`

You can now drag your source code right into Vim via iTunes and fire up Vim.

### iOS special keybindings
After the previous basic settings, things will work. `:E`, `:ls`, `:bn`, `:bp`, `:Te`, `gt`, `gT`, and things which doesn't require plugins works, but you don't have the **CTRL** key, so here's some configs to help.

<div class="message">
  There is no ctags on your iPad, that means you can't generate tag indexes on your iPad, you need to generate it on your computer and drag it into your project folder. If you change code on the iPad, these indexes may be outdated and there is no way to recreate it on your iPad, you may need to copy the files out of your iPad, regenerate the tags, drag it back to iPad. So I mainly just use it to browse code, not to write code.
</div>

{% highlight vim %}
" Find definition
nnoremap T :ts <C-R><C-W> <CR>

" vimgrep
noremap <silent> <Space> :call Search_Word()<CR>:copen<CR>
function Search_Word()
    let w = expand("<cword>")
    execute ":noautocmd vimgrep " w "**"
endfunction

" Jump back and forward
nnoremap , <C-o>
nnoremap . <C-i>

" cnext cprev
nnoremap ? :cnext <CR>
nnoremap ! :cprev <CR>
{% endhighlight %}

The previous `.vimrc` maps several keybindings:
<table>
  <thead>
    <tr>
      <th>Key</th>
      <th>Function</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>T</td>
      <td>Jump to definition of the current symbol under cursor.</td>
    </tr>
    <tr>
      <td>Space</td>
      <td>vimgrep current symbol under cursor.</td>
    </tr>
    <tr>
      <td>,</td>
      <td>Jump back</td>
    </tr>
    <tr>
      <td>.</td>
      <td>Jump forward</td>
    </tr>
        <tr>
      <td>?</td>
      <td>Jump to next vimgrep result</td>
    </tr>
        </tr>
        <tr>
      <td>!</td>
      <td>Jump to previous vimgrep result</td>
    </tr>
  </tbody>
</table>

These keybindings are handy when using a virtual keyboard without special keys(`Ctrl` `ESC` etc..)

### Install plugins

Please note that Vim on iOS only supports plugins which is pure vimscript, it won't work if the plugins is written in `Python`, so this limits the range of plugins to use. Also the plugin can not call external binaries, so `TagBar` is not applicable because it needs to call `ctags`.

Currently I only use two plugins, `Pathogen` and `CtrlP`, they both pure vimscripts and I really like a fuzzy file finder since there is no `Tab` so no tab completion when entering file names.

just create a `.vim` directory on your computer, and then enter it, create a `bundle` directory. Then copy/paste [Pathogen](https://github.com/tpope/vim-pathogen) and [CtrlP](https://github.com/kien/ctrlp.vim) into `bundle`(Get more information from `Pathogen`'s readme). Now we just need to add some extra settings in our `.vimrc`.

{% highlight vim %}
" Get pathogen ready first
runtime bundle/vim-pathogen/autoload/pathogen.vim

" Init pathogen.vim
execute pathogen#infect()

set nocompatible

" CtrlP
let g:ctrlp_map = ';'


" CtrlP config

" Set this to 1 to set searching by filename (as opposed to full path) as the
" default: >
let g:ctrlp_by_filename = 1

" Set this to 1 to set regexp search as the default: >
let g:ctrlp_regexp = 1

" 1 - the parent directory of the current file.
" 2 - the nearest ancestor that contains one of these directories or files:
"     .git/ .hg/ .svn/ .bzr/ _darcs/
" 0 - don't manage working directory.
let g:ctrlp_working_path_mode = 0

" Set this to 1 to enable the lazy-update feature: only update the match window
" after typing been stopped for a certain amount of time: >
"
" If is 1, update after 250ms. If bigger than 1, the number will be used as the
" delay time in milliseconds.
let g:ctrlp_lazy_update = 1

" The maximum number of files to scan, set to 0 for no limit: >
let g:ctrlp_max_files = 0

" Set the maximum height of the match window: >
let g:ctrlp_max_height = 70

" In addition to |'wildignore'|, use this for files and directories you want only
" CtrlP to not show. Use regexp to specify the patterns: >
let g:ctrlp_custom_ignore = {
    \ 'dir':  '\.git$\|\.hg$\|\.svn$',
    \ 'file': '\.exe$\|\.so$\|\.dll$\|\.elf$\|\.o$\
               \|\.obj$\|\.class$\
               \|\.png$\|\.jpg$\|\.jpeg$\|\.bmp$\
               \|\.vsd$\|\.vsdx$\|\.doc$\|\.docx$\
               \|\.xls$\|\.xlsx$',
    \ 'link': '',
    \ }

" Set this to 0 to enable cross-session caching by not deleting the cache files
" upon exiting Vim: >
let g:ctrlp_clear_cache_on_exit = 0

{% endhighlight %}

OK I'll explain this a bit:), we don't have `ctrl` so I remapped `CtrlP`'s hotkey to `;`, Other `CtrlP`'s settings are identical as the one on my computer, so you can read the manual and find out what they are.

`Pathogen` settings must be at the beginning of `vimdc`, details can be found in `Pathogen`'s readme file.

`set nocompatible` is something some plugins require, I just put it here incase other plugins requires it.

### Sum up

Now we're all set, browse code on your iPad for free:), I'll list the keybinding table here again. And btw, [here](https://github.com/ShengYun/ios-vim-config) is my entire config repo.
<table>
  <thead>
    <tr>
      <th>Key</th>
      <th>Function</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>T</td>
      <td>Jump to definition of the current symbol under cursor.</td>
    </tr>
    <tr>
      <td>Space</td>
      <td>vimgrep current symbol under cursor.</td>
    </tr>
    <tr>
      <td>,</td>
      <td>Jump back</td>
    </tr>
    <tr>
      <td>.</td>
      <td>Jump forward</td>
    </tr>
        <tr>
      <td>?</td>
      <td>Jump to next vimgrep result</td>
    </tr>
        </tr>
        <tr>
      <td>!</td>
      <td>Jump to previous vimgrep result</td>
    </tr>
    </tr>
        </tr>
    <tr>
      <td>;</td>
      <td>Open CtrlP</td>
    </tr>    
  </tbody>
</table>
