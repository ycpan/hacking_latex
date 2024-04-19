## 说明文档
tlmgr-intro-zh-cn.pdf
## ubuntu 安装
```
install texlive-full instead of texlive + texlive-tlmgr  # 如果tlmgr无法安装包，用apt安装texlive-full来代替texlive + texlive-tlmgr
#sudo apt install texlive
#sudo apt install texlive-latex-recommended
#sudo apt install texlive-extra-utils(没有这个命令可能会出现:/usr/bin/tlmgr: unexpected return value from verify_checksum: -5,穿线这个问题，是默认需要验证官方源的sum，加一个参数可以不让验证，如tlmgr install latexindent --verify-repo=none)
```
安装整个texlive的方法
```
sudo apt update
sudo apt install texlive-full -y
```
# 上述的能安装成功，但是tlmgr 安装包的时候，出现verify_checksum: -5错误
针对这个问题，tlmgr前面加个参数即可 --verify-repo=none    
1. https://tug.org/texlive/acquire.html  官方    
2. 选择Installing TeX Live over the Internet     
3. 如果是linux，选择install-tl-unx.tar.gz ，解压，就要安装文件，直接运行就好，用sudo模式。
如果是windows，选择install-tl-windows.exe 模式即可。   
## 重新安装最新版本的 texlive 软件包
此时您有三个选择：    
重新安装最新版本的 texlive 软件包（不是您的 Linux 发行版提供的软件包，请参阅谷歌搜索详细信息

``
texlive install
``

或 放弃 tlmgr 并安装 texlive 包，猜测包含该包的正确 texlive 包

``
sudo apt install texlive-guesswhich
``


放弃 tlmgr 并安装所有 texlive 软件包 

``
sudo apt install texlive-full
``
## 安装ctex
```
tlmgr init-usertree #命令来初始化用户模式下的texmf目录，如果之前使用过，这条命令可以省略
tlmgr install ctex
```
## 更新源
```
# update --all 参数可根据需要修改
tlmgr update --all --repository https://mirrors.aliyun.com/CTAN/systems/texlive/tlnet
# 长期更换
tlmgr option repository https://mirrors.aliyun.com/CTAN/systems/texlive/tlnet

```
