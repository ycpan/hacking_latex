# mac使用
## 软件安装
1. Tex Live(首选)
官方网站[](https://www.tug.org/mactex/)
中文镜像网站[](https://mirrors.tuna.tsinghua.edu.cn/ctan/systems/mac/mactex/)
2. MiKTeX（CTeX 套装是 MiKTeX 的重新打包，宏包自动安装的功能也继承于它）
## 编译工具介绍
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
备注:pdfLaTeX是比较原始的版本，对Unicode的支持不是很好，所以显示汉字需要使用CJK宏包。它不支持操作系统的truetype字体(ttf)，只能使用type1字体。优点是支持的宏包比较多，有些老一点的宏包必须用pdfLaTeX来编译。     
XeLaTeX是新的Unicode版本，内建支持Unicode(UTF-8)，自然也包括汉字在内，而且可以调用操作系统的truetype字体。如果你的文档有汉字，那么推荐用XeLaTeX。缺点是不支持某一些宏包。     
3.文献引用
biblatex 有两种后端可以使用，分别是bibtex和biber。    
两者的基本信息是一致的，只是biber后端多了一些附加的输出。    

## 中文文本处理
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
参考：
1. https://blog.csdn.net/chen_shiqiang/article/details/52101836
2. https://www.zhihu.com/question/22906637
3. https://blog.csdn.net/xenonhu/article/details/87899868





