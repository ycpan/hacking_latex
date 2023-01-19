# mac使用
## 一、软件安装
### Tex Live（首选）
[官方网站](https://www.tug.org/mactex/)   
[中文镜像网站](https://mirrors.tuna.tsinghua.edu.cn/ctan/systems/mac/mactex/)   
mac安装后会有几个工具:   
1. LaTeXiT，mac上编辑工具用的，使用command+T，可以预览效果。   
2. BibDesk，管理参考文献的。   
3. Tex Live Unity管理包的。   
4. TexShop，编辑器。   

###  MiKTeX（CTeX 套装是 MiKTeX 的重新打包，宏包自动安装的功能也继承于它）
## 二、编译工具介绍
1. 预备知识    
TeX：一种宏语言。
Plain Tex：Tex中的一个最基本的宏集合与TeX的基础语言构成的一种格式。   
LaTex：Tex中的一个宏集合，构成一种与 Plain TeX 不一样的格式。    
2. tex命令    
tex:Tex程序中的编译命令。tex命令默认用Plain TeX格式进行排版。也就是说tex命令后面默认跟的tex文件应该是用Plain Tex格式写的。    
latex:tex命令加上某一个选项使用，就会用LaTeX 格式进行排版，也就是说此时后面跟的tex文件应该是用LaTex格式写的。为方便，就把tex 命令与对应编译选项合成为一个命令，叫latex命令。    
pdflatex:用来编译laTeX格式写的tex文件。     
pdftex:用来编译用Plain TeX格式写的tex文件。     
xetex:TeX语言的新的实现，针对plain tex格式。    
xelatex:TeX语言的新的实现，即把Tex语言转换为排版的一个新程序。支持Unicode 编码和直接访问操作系统字体。针对latex格式。     
备注:pdfLaTeX是比较原始的版本，对Unicode的支持不是很好，所以显示汉字需要使用CJK宏包。它不支持操作系统的truetype字体（ttf），只能使用type1字体。优点是支持的宏包比较多，有些老一点的宏包必须用pdfLaTeX来编译。     
XeLaTeX是新的Unicode版本，内建支持Unicode（UTF-8），自然也包括汉字在内，而且可以调用操作系统的truetype字体。如果你的文档有汉字，那么推荐用XeLaTeX。缺点是不支持某一些宏包。     
3. 文献引用    
biblatex 有两种后端可以使用，分别是bibtex和biber。    
两者的基本信息是一致的，只是biber后端多了一些附加的输出。    

## 三、中文文本处理
### 方案一，使用指定的字体包
```
\documentclass[12pt]{article}
\usepackage{fontspec}
\setmainfont[Mapping=tex-text]{Kaiti SC} % {STSong}
\begin{document}
\begin{center}
舟夜书所见\\
月黑见渔灯，孤光一点萤。\\
微微风簇浪，散作满河星。\\
\end{center}
\end{document}
```
上述代码中，“Kaiti SC”表示“楷体”，SC表示“simplified Chinese（简体中文的简写）。被注释的{STSong}就表示”宋体“。这些字体名称可以在mac中的”字体册“找到（不要后面的Regular标记）      
**上述编译命令**
```
xelatex 文件名#不用加后缀
pdflatex 文件名#会报错，因为使用系统字体？
```
### 方案二，使用ctex包
```
\documentclass[12pt]{article}
\usepackage[UTF8]{ctex}   %<-----------此处为重点！
\begin{document}
\begin{center}
{\kaishu 舟夜书所见 \\             %指定字体：楷书

月黑见渔灯，孤光一点萤。\\

微微风簇浪，散作满河星。\\
}
\end{center}
\end{document}
```
这里需要特注意的是，字体的指定格式：{\字体名称 文本}，如下代码所示:
```
\documentclass[12pt]{article}
\usepackage{ctex}
\begin{document}
\begin{center}
{\kaishu 舟夜书所见 } \\
{\songti 月黑见渔灯，} {\heiti 孤光一点萤。} \\
{\fangsong 微微风簇浪，} {\lishu 散作满河星。 } \\ % <----注意字体指定方式
\end{center}
\end{document}
```
**上述编译命令**
```
xelatex 文件名#不用加后缀
pdflatex 文件名#会报错，因为使用系统字体？
```
## 四、引用文献的说明
文献tex如下（使用第三章方案二）:
```
\documentclass{article}  
%\usepackage{CJKutf8}  
\usepackage{ctex}  
\usepackage{cite}
\begin{document} 
\title{My Article}
\author{Nobody Jr.}
\date{Today}
\maketitle
%\begin{CJK}{UTF8}{gkai}  
中文 
把Latex中的 Reference 写成\cite{name1}中文的"参考文献" \cite{name2}.
%Blablabla said Nobody ~\cite{Nobody06}.
%如果文档类是article之类的， 用\renewcommand\refname{参考文献} 
%如果文档类是book之类的， 用\renewcommand\bibname{参考文献} 
%\end{CJK}  
\renewcommand\refname{参考献} 
\bibliography{name1}{}
\bibliographystyle{plain} 
%\bibliography{ bibtex-example.bib} 
\end{document} 
```
编写参考文献，命名为name1.bib
```
@article{name1， 
author = {autohr作者， 多个作者用 and 连接}， 
title = {标题title}， 
journal = {期刊名fdss}， 
volume = {卷20}， 
number = {页码}， 
year = {年份}， 
abstract = {摘要， 这个主要是引用的时候自己参考的， 这一行不是必须的} 
} 
@book{name2， 
author ="作者autoee"， 
year="年份2008"， 
title="书名"， 
publisher ="出版社名称" 
} 
```
编译命令
```
xelatex 文件名# 可以不加tex后缀
bibtex 文件名#是tex的文件名（不加后缀），不是name1的文件名。
xelatex 文件名
xelatex 文件名#要两遍，没有第二遍的话，有引用文献，但引文标识为？。
```
参考：
1. https://blog.csdn.net/chen_shiqiang/article/details/52101836
2. https://www.zhihu.com/question/22906637
3. https://blog.csdn.net/xenonhu/article/details/87899868





