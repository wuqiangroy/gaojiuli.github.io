---
layout: post
title:  "我的开发环境搭建"
tags: Python
categories: 后端
---

>  工欲善其事，必先利其器。既好用又好看的开发环境不仅让人工作愉快，还能提高质量和效率。

---

## Git

```
sudo apt install git

sudo apt-get install git-flow
```

## Oh My Zsh

```
sudo apt-get install zsh

chsh -s $(which zsh)

curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh | bash

plugins=(git zsh-completions zsh-autosuggestions zsh-syntax-highlighting last-working-dir git-flow)
```

## Pyenv

```
apt-get install -y make build-essential libssl-dev zlib1g-dev libbz2-dev \
libreadline-dev libsqlite3-dev wget curl llvm libncurses5-dev libncursesw5-dev \
xz-utils tk-dev

curl -fsSL https://raw.githubusercontent.com/pyenv/pyenv-installer/master/bin/pyenv-installer | bash

v=3.5.2 | wget http://mirrors.sohu.com/python/$v/Python-$v.tar.xz -P ~/.pyenv/cache/;pyenv install $v
```

## Pip加速

```
md ~/.pip

echo "[global]
trusted-host =  mirrors.aliyun.com
index-url = http://mirrors.aliyun.com/pypi/simple" > ~/.pip/pip.conf
```

## PyCharm

- 下载地址: [PyCharm](https://www.jetbrains.com/pycharm/download/download-thanks.html?platform=linux)
- 注册服务器: `http://idea.iteblog.com/key.php`

## 自动化脚本

 ```shell
 cd ~/Desktop
apt install git
apt install zsh
chsh -s $(which zsh)
sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
curl -L https://raw.githubusercontent.com/pyenv/pyenv-installer/master/bin/pyenv-installer | bash


echo export 'PATH="~/.pyenv/bin:$PATH"
eval "$(pyenv init -)"
eval "$(pyenv virtualenv-init -)"'>>~/.zshrc
source ~/.zshrc

echo '[global]
trusted-host =  mirrors.aliyun.com
index-url = http://mirrors.aliyun.com/pypi/simple
'>~/.pip/pip.conf

v=3.6.2
wget http://mirrors.sohu.com/python/$v/Python-$v.tar.xz -P ~/.pyenv/cache/;
pyenv install $v

curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.33.4/install.sh | bash
echo 'export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && . "$NVM_DIR/nvm.sh"'>>~/.zshrc
source ~/.zshrc


wget https://download.jetbrains.com/python/pycharm-professional-2017.2.3.tar.gz -P ~/Desktop
wget https://www.google.com/chrome/browser/?platform=linux&extra=devchannel -P ~/Desktop
wget http://kdl1.cache.wps.com/ksodl/download/linux/a21//wps-office_10.1.0.5707~a21_amd64.deb -P ~/Desktop
wget http://pinyin.sogou.com/linux/download.php?f=linux&bit=64 -P ~/Desktop
git clone https://github.com/yurtaev/idea-one-dark-theme
git clone https://github.com/anmoljagetia/Flatabulous

apt remove libreoffice-common
apt remove unity-webapps-common
apt remove thunderbird totem rhythmbox empathy brasero simple-scan gnome-mahjongg aisleriot
apt remove onboard deja-dup

apt install rar
apt install unity-tweak-tool
add-repository ppa:noobslab/icons
apt update
apt install ultra-flat-icons
apt install fonts-wqy-microhei
apt install vim
apt install nginx
 ```