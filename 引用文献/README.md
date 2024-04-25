
1. 运行命令如下:
```bash
xelatex 引文文献
bibtex 引文文献
xelatex 引文文献
xelatex 引文文献
```
如果更新了引用方式，编译报错，需要清空缓存文件
```bash
rm -rf *.aux
```
然后重新运行上述命令
2. bibtex 编译时候，不需要写后缀，直接写主文件名称即可。
```
bibtex 引文文献
```
## 样例
引用网站文献，样例,bib和latex放在一起
```latex
\RequirePackage{filecontents}
\begin{filecontents}{mybib.bib}
@misc{OMS,
    author= {{World Health Organisation}},
    year  = {2017},
    title = {Vision impairment and blindness, {Fact Sheet N\textsuperscript{o}282}},
    note  = {\url{http://www.who.int/mediacentre/factsheets/fs282/fr/}, 
             Last accessed on 2017-11-30},
}
\end{filecontents}

\documentclass{article}
\bibliographystyle{plain}
\usepackage[hyphens,spaces]{url}

\begin{document}
\cite{OMS}
\bibliography{mybib}
\end{document}
```
## 使用排序，压缩等
使用排序压缩的话，就需要用到natbib,作为cite的替换。
在文档开始前加入下面命令:
```
\usepackage[numbers,sort&compress]{natbib}
```
由于natbib默认是auto-year的引用格式，即引用角标显示作者年份而不是数字，因此加入numbers，让其显示数字

这样不但可以压缩参考文献标号，还可以进行排序，即无论正文里面的顺序怎样，显示出来都是先后顺序

如：[6,7,8,9]变成[6-9]等

## 显示有上角标
方法：在文档开始前加上下面的语句命令
```latex
\newcommand{\upcite}[1]{\textsuperscript{\textsuperscript{\cite{#1}}}}
```
然后引用的时候使用`\upcite{}`的格式（一般的正常引用格式为`\cite{}`）

完整的latex如下:
```latex
\documentclass{article}
\usepackage{ctex}
\usepackage[numbers,sort&compress]{natbib} %参考文献右上角显示,那就不需要用cite了
\newcommand{\upcite}[1]{\textsuperscript{\textsuperscript{\cite{#1}}}}% 然后引用的时候使用 \upcite{}的格式（一般的正常引用格式为\cite{}）
\usepackage[hyphens,spaces]{url}
\bibliographystyle{plainnat}%这个不支持作者年份引用，下面的支持
\begin{document}
\title{My Article}
\author{Nobody Jr.}
\date{Today}
\maketitle
中文
把Latex中的 Reference 写成\upcite{name1}中文的"参考文献" \upcite{name2}.

这个是网站的引用测试\upcite{website_example1}
\renewcommand\refname{参考献}
\bibliography{name1}{}
\end{document}
```
name1.bib内容如下:
```latex
@article{name1, 
author = {autohr作者, 多个作者用 and 连接}, 
title = {标题title}, 
journal = {期刊名fdss}, 
volume = {卷20}, 
number = {页码}, 
year = {年份}, 
abstract = {摘要, 这个主要是引用的时候自己参考的, 这一行不是必须的} 
} 
@book{name2, 
author ="作者autoee", 
year="年份2008", 
title="书名", 
publisher ="出版社名称" 
}
@misc{website_example1,
    author = {Your Name},
    title = {Your Website Title},
    howpublished = {Web},
    year = {2023},
    note  = {\url{http://www.who.int/mediacentre/factsheets/fs282/fr/}, 
             Last accessed on 2017-11-30},
}
```
注意，编号会影响顺序，比如:
website_example1 在name2引用，但是2比1大，所以website_example1的编号要小一些。
