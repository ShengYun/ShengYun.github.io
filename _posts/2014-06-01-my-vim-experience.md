---
layout: post
title: How did I learn VIM
---

<div class="message">
    This is the experience of how I learn VIM and finally get addicted to it, also I would like to share some plugins I use.
</div>

### The first time I meet VIM
The first time I heard about VIM is my linux course in university, I though linux was awesome and like to learn anything which seems to be cool. So that was the first time I tried to use VIM, and what I did was literally open VIM in terminal, and struggled to close it. Although it was not a delightful experience, I still have some fantasy to learn VIM.

After several months, I tried to walk through VIM's tutorial, which is, kind of useful, but still can't help me do my job. I was spoiled by Visual Studio, I though VIM was just some hard to use ancient tool. The most important thing is, the guys I work with, they don't know how to use VIM either, everyone is happy with Visual Studio and using VIM is, Umm... zhuangbility behaviour:)

So I didn't try to learn VIM later, but one day I found a blog which shows VIM's power and teaches people how to learn VIM progressively, so I read the blog, and finally got some clue about VIM, [here](http://yannesposito.com/Scratch/en/blog/Learn-Vim-Progressively/) is the link of that blog, if you can read Chinese, click [here](http://coolshell.cn/articles/5426.html) for a Chinese version.

I believe in China, VIM users are more than emacs users, because when I tried to learn emacs yesterday, I can't find much useful information about how to turn my emacs into an useable IDE, on the contrary, there are lots of information about how to turn my VIM into an IDE, the one I read was [this](http://blog.csdn.net/fbfsber008/article/details/7055842) article, really simple, and you can setup your VIM step by step. Although this article is somehow outdated now, it can still give you a felling about how VIM's plugins works, and maybe some simple concepts about how to config plugins. *(Please let me know if there is a similar emacs tutorial)*.

### Things you must know about a VIM plugin
VIM's plugin system *was* a mess, you need to copy paste separate plugin files into different directories. The world became simple after *Tim Pop* created the [`Pathogen`](http://TODO) plugin, it simplifies the way how we install VIM's plugins, in short, you just create a folder called `bundle` and copy the plugins into it, most plugins have a *pathogen ready* version, which allows you to simply `git clone` the plugin's repository in the `bundle` folder. There's another similar plugin called `Vundle` I haven't tried it yet, but seems that it has it's own fans:) anyway, you can try both and find the one which suites you best.

#### Where are my VIM's configuration files?
To customize your VIM*(either vanilla VIM or to config your plugins)*, you should write your settings in a file called **vimrc**, there could be may `vimrc` files in your system, the system's `vimrc`, the user's `vimrc` etc. But when people online refers a `vimrc` file, they mostly mean yourselves `vimrc`, which is usually located in your **HOME** directory, on Unix systems, a typical `vimrc` file will be `~/.vimrc`, note that you can also have a `~/.vim` folder which contains a `bundle` folder for `Pathogen`.

For Windows users, your `vimrc` will be at `%HOME%\_vimrc`, and the counterpart of `~/.vim/bundle` will be `%HOME%\vimfiles\bundle`

<div class="message">
    If you don't have the files or directories in your system, just create one yourself. And please RTFM!
</div>

#### Install and config a plugin
I am not going to talk much about `vim scripts` since I myself can't handle it very well, if you are really interested in it, click [here](http://TODO) for a great tutorial.

For now, just understand everything you wrote in a `vimrc` file would be executed before VIM is started. Just like an extra initialisation process for VIM.

Let's begin by installing `Pathogen`. RTFM first, so it basically says:

1. copy the entire `Pathogen` repository to `~/.vim/bundle` or `%HOME%\vimfiles\bundle`
2. Add the following lines at the beginning of your `vimrc`
" TODO
{% highlight vim %}
runtime bundle/vim-pathogen/autoload/pathogen.vim
execute pathogen#infect()
syntax on
filetype plugin indent on
{% endhighlight %}

3. copy paste other `Pathogen` ready plugins to your `bundle` directory.

In vim, `:h xxx` is usually how to read the documentation, say if I want to know more information of the `:colorscheme` command, simply type `:h :colorscheme` would help. `Pathogen` provides a way to add your plugins documentation, after executed `:Helptags`, you can read the plugin's documentation by `:h plugin-name or function`, so if you installed the `tagbar` plugin, reading it's documentation would be `:h tagbar`.

To config your plugin, read it's documentation carefully, usually there will be a section to tell you how to config it, and maybe some recommend key-bindings. Say if I installed the `molokai` colour scheme, and I'd like to change the background back to original, I'll add `let g:molokai_original = 1` in my `vimrc` file.


### Plugins I use
<div class="message">
    My work machine is Windows and my personal computer is Mac, I sometimes may need to use a linux(ubuntu) machine, so I'd like my plugins be as general as possible.
</div>

[Here's](https://github.com/ShengYun/dbsvim/tree/master/bundle) a list of my plugins.
