---
layout: post
title: Switching from Atom to Vim
date: 2017-08-16 23:37 +0100
categories: technical
---
I recently decided to return to Vim. Because it is fast, light and highly customizable. I have reproduced with the modules a similar configuration to the one I had with Atom.


## First step
First of all, we need to install a plugin manager.

I choosed VimPlug. [github.com/junegunn/vim-plug](https://github.com/junegunn/vim-plug)

{% highlight shell %}
  curl -fLo ~/.vim/autoload/plug.vim --create-dirs 'https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim'
{% endhighlight %}

*~/.vimrc*

{% highlight Vim Script %}
  " Specify a directory for plugins
  " - For Neovim: ~/.local/share/nvim/plugged
  " - Avoid using standard Vim directory names like 'plugin'
  call plug#begin('~/.vim/plugged')

  " Make sure you use single quotes

  " Shorthand notation; fetches https://github.com/junegunn/vim-easy-align
  Plug 'junegunn/vim-easy-align'

  " Any valid git URL is allowed
  Plug 'https://github.com/junegunn/vim-github-dashboard.git'

  " Multiple Plug commands can be written in a single line using | separators
  Plug 'SirVer/ultisnips' | Plug 'honza/vim-snippets'

  " On-demand loading
  Plug 'scrooloose/nerdtree', { 'on':  'NERDTreeToggle' }
  Plug 'tpope/vim-fireplace', { 'for': 'clojure' }

  " Using a non-master branch
  Plug 'rdnetto/YCM-Generator', { 'branch': 'stable' }

  " Using a tagged release; wildcard allowed (requires git 1.9.2 or above)
  Plug 'fatih/vim-go', { 'tag': '*' }

  " Plugin options
  Plug 'nsf/gocode', { 'tag': 'v.20150303', 'rtp': 'vim' }

  " Plugin outside ~/.vim/plugged with post-update hook
  Plug 'junegunn/fzf', { 'dir': '~/.fzf', 'do': './install --all' }

  " Unmanaged plugin (manually installed and updated)
  Plug '~/my-prototype-plugin'

  " Initialize plugin system
  call plug#end()
{% endhighlight %}

In Vim :

{% highlight Vim Script %}
  :w
  :source %
  :PLugInstall
{% endhighlight %}
  Step two
  Install plugins. I search for the most of plugins that will reproduce atom feature
{% highlight Vim Script %}
  set encoding=utf-8
  set number
  set ruler
  syntax on
  set smartindent
  set autoindent
  set cindent
  set mouse=a
  set t_Co=256
  set autoread
  set errorbells
  set ttyfast
  set novisualbell
  set laststatus=2
  set backspace=2
  set tabstop=2
  set shiftwidth=2
  set expandtab
  set softtabstop=2
  set noswapfile
  set colorcolumn=80
  set linespace=3

  call plug#begin('~/.vim/plugged')

    Plug 'mustache/vim-mustache-handlebars' "Ember handlebar
    Plug 'pangloss/vim-javascript'
    Plug 'bling/vim-airline' "Bottom bar custom
    Plug 'vim-airline/vim-airline-themes'
    Plug 'scrooloose/nerdcommenter' "Comment multiple lines : Visual + \ + c + c
    Plug 'joshdick/onedark.vim' "Theme similar atom
    Plug 'jistr/vim-nerdtree-tabs'
    Plug 'jiangmiao/auto-pairs'
    Plug 'terryma/vim-multiple-cursors'
    Plug 'airblade/vim-gitgutter'
    Plug 'junegunn/vim-easy-align'
    Plug 'https://github.com/junegunn/vim-github-dashboard.git'
    Plug 'SirVer/ultisnips' | Plug 'honza/vim-snippets'
    Plug 'scrooloose/nerdtree', { 'on':  'NERDTreeToggle' }
    Plug 'tpope/vim-fireplace', { 'for': 'clojure' }
    Plug 'rdnetto/YCM-Generator', { 'branch': 'stable' }
    Plug 'fatih/vim-go', { 'tag': '*' }
    Plug 'nsf/gocode', { 'tag': 'v.20150303', 'rtp': 'vim' }
    Plug 'junegunn/fzf', { 'dir': '~/.fzf', 'do': './install --all' }
    Plug '~/my-prototype-plugin'
    Plug 'scrooloose/nerdtree', { 'on': 'NERDTreeToggle' }
    Plug 'junegunn/vim-github-dashboard', { 'on': ['GHDashboard', 'GHActivity'] }
    Plug 'tpope/vim-fireplace', { 'for': 'clojure' }
    Plug 'kovisoft/paredit', { 'for': ['clojure', 'scheme'] }
    Plug 'junegunn/vader.vim',  { 'on': 'Vader', 'for': 'vader' }
    Plug 'Shougo/vimproc.vim', { 'do': 'make' }
    Plug 'Valloric/YouCompleteMe', { 'do': './install.py' }

  call plug#end()

  colorscheme onedark
{% endhighlight %}
