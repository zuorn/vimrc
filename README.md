# vimrc

![](https://i.loli.net/2019/06/23/5d0e64fa470df37298.jpg)

## 安装

安装插件管理工具：

```sh
curl -fLo ~/.vim/autoload/plug.vim --create-dirs \
    https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim
```

将配置文件拷贝到 ～ 目录：
 
```
cp vimrc/.vimrc ~/
```
安装其他插件：

```
进入 vim
：PlugInstall
```
安装完成后重启 vim。

## 配置项

### 基本配置

```
syntax on " 开启语法高亮

set nu " 显示行号
set t_Co=256 "启用256色。
filetype indent on "开启文件类型检查，并且载入与该类型对应的缩进规则。
set autoindent "按下回车键后，下一行的缩进会自动跟上一行的缩进保持一致。
set shiftwidth=4 " 按下 Tab 键时，Vim 显示的空格数。
set expandtab " 由于 Tab 键在不同的编辑器缩进不一致，该设置自动将 Tab 转为空格。
set cursorline " 光标所在的当前行高亮。
set wrap " 自动折行，即太长的行分成几行显示。
set showmatch " 光标遇到圆括号、方括号、大括号时，自动高亮对应的另一个圆括号、方括号和大括号。
"'让vimrc配置变更立即生效'
autocmd BufWritePost $MYVIMRC source $MYVIMRC
" 语法搜索结果高亮
hi Search term=standout ctermfg=0 ctermbg=3 
"语言设置
set langmenu=zh_CN.UTF-8
set helplang=cn
```

### 插件：

```
" Specify a directory for plugins
" - For Neovim: ~/.local/share/nvim/plugged
" - Avoid using standard Vim directory names like 'plugin'
call plug#begin('~/.vim/plugged')

" 修改启动界面
Plug 'mhinz/vim-startify'

" 状态栏美化
Plug 'vim-airline/vim-airline'
Plug 'vim-airline/vim-airline-themes'

" 添加代码缩进线
Plug 'yggdroot/indentline'

" 文件目录树
Plug 'scrooloose/nerdtree'

" 快速搜索
Plug 'kien/ctrlp.vim'

" 快速定位
Plug 'easymotion/vim-easymotion'

" 主题商店
"Plug 'flazz/vim-colorschemes'

" docker 
"Plugin 'ekalinin/Dockerfile.vim'

" 代码补全
if has('nvim')
 Plug 'Shougo/deoplete.nvim', { 'do': ':UpdateRemotePlugins' }
else
 Plug 'Shougo/deoplete.nvim'
 Plug 'roxma/nvim-yarp'
 Plug 'roxma/vim-hug-neovim-rpc'

Plug 'deoplete-plugins/deoplete-docker'
endif

" Initialize plugin system
call plug#end()
```

### 快捷键映射和插件配置


```
" 设置 leader 键为 ,
let mapleader=';'

" -------------------- 文件目录 ----------------------------
" 打开文件所在位置
nnoremap <leader>v :NERDTreeFind<cr>
" 打开文件目录树或隐藏
nnoremap <leader>f :NERDTreeToggle<cr>


"--------------------  快速搜索 ----------------------------
" 快速搜索快捷键
let g:ctrlp_map = '<c-p>'

" ------------------- 快速定位 -----------------------------
nmap s <Plug>(easymotion-s2)


"-------------------- 代码补全 -----------------------------
set completeopt-=previe
let g:deoplete#enable_at_startup = 1
```


### 常见问题
如果主题不生效请把 ～/vim/plugged/vim-colorschemes/colors 移动到 ～/.vim 目录下。


```
mv ～/vim/plugged/vim-colorschemes/colors ～/.vim
```