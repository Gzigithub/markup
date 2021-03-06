# ubuntu安装后的优化

参考： 
Ubuntu 16.04 安装后优化

# ======================卸载=========================
1.卸载不必要的软件
# 删除libreoffice
$ sudo apt-get remove libreoffice-style-galaxy 
# 删除亚马逊链接
$ sudo apt-get remove unity-webapps-common 
# 删除邮件客户端
$ sudo apt-get remove thunderbird
# 删除不必要的包
$ sudo apt-get remove  totem  rhythmbox simple-scan gnome-mahjongg aisleriot gnome-mines  transmission-common gnome-orca webbrowser-app gnome-sudoku onboard deja-dup 
# 清理缓存
$ sudo apt-get autoremove
$ sudo apt-get autoclean 
# =====================源=============================
2.修改镜像源
#修改为163的源
$ sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
$ sudo vi /etc/apt/sources.list
# 添加如下163 ubuntu16.04源
deb http://mirrors.163.com/ubuntu/ xenial main restricted universe multiverse
deb http://mirrors.163.com/ubuntu/ xenial-security main restricted universe multiverse
deb http://mirrors.163.com/ubuntu/ xenial-updates main restricted universe multiverse
deb http://mirrors.163.com/ubuntu/ xenial-proposed main restricted universe multiverse
deb http://mirrors.163.com/ubuntu/ xenial-backports main restricted universe multiverse
deb-src http://mirrors.163.com/ubuntu/ xenial main restricted universe multiverse
deb-src http://mirrors.163.com/ubuntu/ xenial-security main restricted universe multiverse
deb-src http://mirrors.163.com/ubuntu/ xenial-updates main restricted universe multiverse
deb-src http://mirrors.163.com/ubuntu/ xenial-proposed main restricted universe multiverse
deb-src http://mirrors.163.com/ubuntu/ xenial-backports main restricted universe multiverse
# 添加优麒麟的源
$ echo deb http://archive.ubuntukylin.com:10006/ubuntukylin trusty main | sudo tee /etc/apt/sources.list.d/ubuntukylin.list 
# 更新源
$ sudo apt-get update 
# 注:如果提示没有公钥,无法验证下列数字签名 xxx
$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-　keys xxxx
$ sudo apt-get update


# ======================软件安装========================
# 更新源
$ sudo apt-get update
# 安装最新的vim
$ sudo add-apt-repository ppa:jonathonf/vim
$ sudo apt update
$ sudo apt install vim
$ sudo apt ctags
$ sudo apt vim-docsuta
已编译，支持python3
# 安装typora(markdown编辑器)
$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys BA300B7755AFCFAE
$ sudo add-apt-repository 'deb http://typora.io linux/'
$ sudo apt-get update
$ sudo apt-get install typora
# 安装R语言开发环境
$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E084DAB9
$ sudo sh -c "echo deb http://mirror.bjtu.edu.cn/cran/bin/linux/ubuntu precise/ >>/etc/apt/sources.list"
$ sudo apt-get install r-base
$ sudo apt-get install r-base-dev
$ sudo apt-get update
# 安装wine-de(windows软件运行环境)
$ sudo add-apt-repository ppa:wine/wine-builds
$ sudo apt-get update
$ sudo apt-get install wine-devel
$ sudo apt install winehq-devel
# 安装最新版的Thunderbird邮件客户端
$ sudo add-apt-repository ppa:ubuntu-mozilla-security/ppa
$ sudo apt-get update
$ sudo apt-get install thunderbird
# 安装最新版的gimp图片处理工具
$ sudo add-apt-repository ppa:otto-kesselgulasch/gimp
$ sudo apt-get update
$ sudo apt-get install gimp
# (可选)卸载gimp
$ sudo apt-get install ppa-purge
$ sudo ppa-purge ppa:otto-kesselgulasch/gimp
# 安装chrome浏览器
$ wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb 
$ sudo apt-get install libappindicator1 libindicator7 
$ sudo dpkg -i google-chrome-stable_current_amd64.deb 
# 自动安装依赖
$ sudo apt-get -f install 
# 卸载火狐浏览器
$ sudo apt-get purge firefox
# 安装VLC音频视频播放器
$ sudo apt-get install vlc
# 状态栏系统监控插件安装
# 安装完成后打开indicator-sysmonitor，设置开机启动，定制规则
$ sudo add-apt-repository ppa:fossfreedom/indicator-sysmonitor 
$ sudo apt-get update 
$ sudo apt-get install indicator-sysmonitor
# 安装硬盘分区管理工具
$ sudo apt-get install gparted
# 安装搜狗输入法
# 如果重启后只有搜狗输入法,则在命令行使用fcitx-configtool命令,添加系统输入法
$ sudo apt-get install sogoupinyin
# 安装wps
$ sudo apt-get install wps-office 
# 1. 下载缺失的字体文件
# 国外下载地址：https://www.dropbox.com/s/lfy4hvq95ilwyw5/wps_symbol_fonts.zip
# 国内下载地址：https://pan.baidu.com/s/1eS6xIzo
# 解压并进入目录中，继续执行：
sudo cp * /usr/share/fonts
# 2. 执行以下命令,生成字体的索引信息：
sudo mkfontscale
sudo mkfontdir
# 3. 运行fc-cache命令更新字体缓存。
sudo fc-cache
# 4. 重启wps即可，字体缺失的提示不再出现。
# 安装git
$ sudo apt-get install git
# 安装rar
$ sudo apt-get install unrar 
# 设置开启小键盘
$ sudo apt-get install numlockx
$ sudo gedit /usr/share/lightdm/lightdm.conf.d/50-unity-greeter.conf
# 在配置文件最后添加：
greeter-setup-script=/usr/bin/numlockx on
# 修改时间同步，与Windows双系统时间一致
$ sudo timedatectl set-local-rtc 1  
$ sudo apt-get install ntpdate
$ sudo ntpdate time.windows.com
$ sudo hwclock --localtime --systohc

# 安装mysql
$ sudo apt-get install mysql-server
$ sudo libmysqld-dev 
$ sudo libmysqlclient-dev 
# 安装redis
$ sudo apt-get install software-properties-common
$ sudo apt-add-repository ppa:chris-lea/redis-server
$ sudo apt-get update
$ sudo apt-get install redis-server
# 安装nginx
$ sudo apt-get install nginx

# 重启系统
$ sudo reboot 

# ===========================yq=========================
# 下载remarkable（一款优秀的markdown编辑器）
$ wget https://remarkableapp.github.io/files/remarkable_1.87_all.deb
$ sudo dpkg -i remarkable_1.87_all.deb
$ sudo apt-get -f install 
# 安装Nodepadqq(notepad++替代)
$ sudo add-apt-repository ppa:notepadqq-team/notepadqq
$ sudo apt-get update
$ sudo apt-get install notepadqq


# 安装polipo，socket5代理转换为http
$ sudo apt-get install polipo
# 停止服务
$ sudo service polipo stop
# 修改配置文件
$ sudo vi /etc/polipo/config
# 新增如下两个配置
socksParentProxy = localhost:1080
proxyPort = 8787
# 启动服务
$ sudo service polipo start
# 添加命令代理别名
$ cd
$ vi .bashrc
# 添加配置如下
 alias http_proxy='export http_proxy=http://127.0.0.1:8787/'
alias https_proxy='export https_proxy=http://127.0.0.1:8787/'
# 生效配置
$ source .bashrc 
# 安装curl
$ sudo apt install curl
# 安装ss-qt5
# github地址：https://github.com/shadowsocks/shadowsocks-qt5/releases
# 使用命令下载
$ wget https://github-production-release-asset-2e65be.s3.amazonaws.com/18427187/04086db8-f3cd-11e7-9c68-2b0d4b4dbe5b?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAIWNJYAX4CSVEH53A%2F20180112%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20180112T150901Z&X-Amz-Expires=300&X-Amz-Signature=73c91b88196b277e49f46a9d0874d4d76384c6b35d33861b3c9b55a4396b03f7&X-Amz-SignedHeaders=host&actor_id=0&response-content-disposition=attachment%3B%20filename%3DShadowsocks-Qt5-3.0.0-x86_64.AppImage&response-content-type=application%2Foctet-stream

# 启动ss-qt5客户端，添加配置，启动服务
# 测试代理
$ http_proxy
$ https_proxy
$ curl http://ip.cn
# 安装pac manager（xshell替代）
$ wget https://astuteinternet.dl.sourceforge.net/project/pacmanager/pac-4.0/pac-4.5.5.7-all.deb
$ sudo dpkg -i pac-4.5.5.7-all.deb 
$ sudo apt-get install -f
$ sudo apt-get install libgtk2-appindicator-perl
# ============================another one=====================================
# 安装git和vpnc
$ sudo apt-get install git vpnc
# 安装openssh-server
$ sudo apt-get install openssh-server
# 安装gdb-dashboard
 $ wget -P ~ git.io/.gdbinit
 $ mv ~/.gdbinit ~/.gdb-dashboard
 然后在使用gdb调试的时候可以在gdb界面调用gdb-dashboard
 (gdb) source ~/.gdb-dashboard
 也可以直接修改~/.gdbinit,加入source ~/.gdb-dashboard使gdb在载入时自动加载gdb-dashboard
# 安装VMWare
 永久许可证秘钥： 
VMware Workstation v12 for Windows 
5A02H-AU243-TZJ49-GTC7K-3C61
VMware Workstation v11 for Windows 
1F04Z-6D111-7Z029-AV0Q4-3AEH8
VMware Workstation v10 for Windows 
1Z0G9-67285-FZG78-ZL3Q2-234JG 
4C4EK-89KDL-5ZFP9-1LA5P-2A0J0 
HY086-4T01N-CZ3U0-CV0QM-13DNU 
# =============================end=================================

# 添加vim配置文件
$ vim .vimrc
""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
" 显示相关 
""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
set shortmess=atI   " 启动的时候不显示那个援助乌干达儿童的提示 
winpos 5 5         " 设定窗口位置 
set lines=30 columns=85    " 设定窗口大小 
set nu              " 显示行号 
set go=             " 不要图形按钮 
"color asmanian2     " 设置背景主题 
set guifont=Courier_New:h10:cANSI   " 设置字体 
syntax on           " 语法高亮 
autocmd InsertLeave * se nocul  " 用浅色高亮当前行 
autocmd InsertEnter * se cul    " 用浅色高亮当前行 
set ruler           " 显示标尺 
set showcmd         " 输入的命令显示出来，看的清楚些 
set cmdheight=1     " 命令行（在状态行下）的高度，设置为1 
"set whichwrap+=<,>,h,l   " 允许backspace和光标键跨越行边界(不建议) 
set scrolloff=3     " 光标移动到buffer的顶部和底部时保持3行距离 
set novisualbell    " 不要闪烁(不明白) 
set statusline=%F%m%r%h%w\ [FORMAT=%{&ff}]\ [TYPE=%Y]\ [POS=%l,%v][%p%%]\ %{strftime(\"%d/%m/%y\ -\ %H:%M\")}   "状态行显示的内容 
set laststatus=1    " 启动显示状态行(1),总是显示状态行(2) 
set foldenable      " 允许折叠 
set foldmethod=manual   " 手动折叠 
set background=dark "背景使用黑色 
set nocompatible  "去掉讨厌的有关vi一致性模式，避免以前版本的一些bug和局限 
" 显示中文帮助
if version >= 603
    set helplang=cn
    set encoding=utf-8
endif
" 设置配色方案
"colorscheme murphy
"字体 
"if (has("gui_running")) 
"   set guifont=Bitstream\ Vera\ Sans\ Mono\ 10 
"endif 


set fencs=utf-8,ucs-bom,shift-jis,gb18030,gbk,gb2312,cp936
set termencoding=utf-8
set encoding=utf-8
set fileencodings=ucs-bom,utf-8,cp936
set fileencoding=utf-8

"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
"""""新文件标题""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
"新建.c,.h,.sh,.java文件，自动插入文件头 
autocmd BufNewFile *.cpp,*.[ch],*.sh,*.java exec ":call SetTitle()" 
""定义函数SetTitle，自动插入文件头 
func SetTitle() 
    "如果文件类型为.sh文件 
    if &filetype == 'sh' 
        call setline(1,"\#########################################################################") 
        call append(line("."), "\# File Name     : ".expand("%")) 
        call append(line(".")+1, "\# Author        : enjoy5512") 
        call append(line(".")+2, "\# mail          : enjoy5512@163.com") 
        call append(line(".")+3, "\# Created Time  : ".strftime("%c")) 
        call append(line(".")+4, "\#########################################################################") 
        call append(line(".")+5, "") 
        call append(line(".")+6, "\#!/bin/bash") 
    call append(line(".")+7, "")
    call append(line(".")+8, "")
    else 
        call setline(1, "/*************************************************************************") 
        call append(line("."), "    > File Name       : ".expand("%")) 
        call append(line(".")+1, "    > Author          : enjoy5512") 
        call append(line(".")+2, "    > Mail            : enjoy5512@163.com ") 
        call append(line(".")+3, "    > Created Time    : ".strftime("%c")) 
        call append(line(".")+4, " ************************************************************************/") 
        call append(line(".")+5, "")
    endif
    if &filetype == 'cpp'
        call append(line(".")+6, "#include<iostream>")
    call append(line(".")+7, "")
        call append(line(".")+8, "using namespace std;")
        call append(line(".")+9, "")
        call append(line(".")+10, "int main(int argc,char *argv[])")
        call append(line(".")+11, "{")
        call append(line(".")+12, "     ")
        call append(line(".")+13, "    return 0;")
        call append(line(".")+14, "}")
    endif
    if &filetype == 'c'
        call append(line(".")+6, "#include<stdio.h>")
        call append(line(".")+7, "")
        call append(line(".")+8, "int main(int argc,char *argv[])")
        call append(line(".")+9, "{")
        call append(line(".")+10, "     ")
        call append(line(".")+11, "    return 0;")
        call append(line(".")+12, "}")
    autocmd BufNewFile * 12 j
    endif
endfunc
""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
"键盘命令
""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
"C，C++ 按F5编译运行
map <F5> :call CompileRunGcc()<CR>
func! CompileRunGcc()
    exec "w"
    if &filetype == 'c'
        exec "!gcc % -o %<"
        exec "! ./%<"
    elseif &filetype == 'cpp'
        exec "!g++ % -o %<"
        exec "! ./%<"
    elseif &filetype == 'sh'
        :!./%
    endif
endfunc
"C,C++的调试
map <C-F5> :call Rungdb()<CR>
func! Rungdb()
    exec "w"
    if &filetype == 'c'
        exec "!gcc % -g -o %<"
        exec "!gdb -tui ./%<"
    elseif &filetype == 'cpp'
        exec "!g++ % -g -o %<"
        exec "!gdb -tui ./%<"
    endif
endfunc
""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
""实用设置
"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
" 设置当文件被改动时自动载入
set autoread
" quickfix模式
autocmd FileType c,cpp map <buffer> <leader><space> :w<cr>:make<cr>
"代码补全 
set completeopt=preview,menu 
"允许插件 
filetype plugin on
"共享剪贴板 
set clipboard+=unnamed 
"从不备份 
set nobackup
"自动保存
set autowrite
set ruler                   " 打开状态栏标尺
set cursorline              " 突出显示当前行
set magic                   " 设置魔术
set guioptions-=T           " 隐藏工具栏
set guioptions-=m           " 隐藏菜单栏
set foldcolumn=0
set foldmethod=indent 
set foldlevel=3 
set foldenable              " 开始折叠
" 不要使用vi的键盘模式，而是vim自己的
set nocompatible
" 语法高亮
set syntax=on
" 去掉输入错误的提示声音
set noeb
" 在处理未保存或只读文件的时候，弹出确认
set confirm
" 自动缩进
set autoindent
set cindent
" Tab键的宽度
set tabstop=4
" 统一缩进为4
set softtabstop=4
set shiftwidth=4
"禁止生成临时文件
set nobackup
set noswapfile
"搜索忽略大小写
set ignorecase
"搜索逐字符高亮
set hlsearch
set incsearch
"行内替换
set gdefault
"编码设置
set enc=utf-8
set fencs=utf-8,ucs-bom,shift-jis,gb18030,gbk,gb2312,cp936
"语言设置
set langmenu=zh_CN.UTF-8
set helplang=cn
" 我的状态行显示的内容（包括文件类型和解码）
set statusline=%F%m%r%h%w\ [FORMAT=%{&ff}]\ [TYPE=%Y]\ [POS=%l,%v][%p%%]\ %{strftime(\"%d/%m/%y\ -\ %H:%M\")}
"set statusline=[%F]%y%r%m%*%=[Line:%l/%L,Column:%c][%p%%]
"set statusline=\ %<%F[%1*%M%*%n%R%H]%=\ %y\ %0(%{&fileformat}\ %{&encoding}\ %c:%l/%L%)\
" 总是显示状态行
set laststatus=2
" 命令行（在状态行下）的高度，默认为1，这里是2
set cmdheight=2
" 侦测文件类型
filetype on
" 载入文件类型插件
filetype plugin on
" 为特定文件类型载入相关缩进文件
filetype indent on
" 保存全局变量
set viminfo+=!
" 在被分割的窗口间显示空白，便于阅读
set fillchars=vert:\ ,stl:\ ,stlnc:\
" 高亮显示匹配的括号
set showmatch
" 匹配括号高亮的时间（单位是十分之一秒）
set matchtime=1
" 光标移动到buffer的顶部和底部时保持3行距离
set scrolloff=3
" 为C程序提供自动缩进
set smartindent
" 高亮显示普通txt文件（需要txt.vim脚本）
au BufRead,BufNewFile *  setfiletype txt
"自动补全
":inoremap ( ()<ESC>i
":inoremap ) <c-r>=ClosePair(')')<CR>
:inoremap { {<CR>}<ESC>O
:inoremap } <c-r>=ClosePair('}')<CR>
":inoremap [ []<ESC>i
":inoremap ] <c-r>=ClosePair(']')<CR>
":inoremap " ""<ESC>i
":inoremap ' ''<ESC>i
function! ClosePair(char)
    if getline('.')[col('.') - 1] == a:char
        return "\<Right>"
    else
        return a:char
    endif
endfunction
filetype plugin indent on 
"打开文件类型检测, 加了这句才可以用智能补全
set completeopt=longest,menu
