## 脚注
脚注就是在页面底部显示
在LaTeX中添加脚注，可以使用`\footnote`命令。以下是一个简单的例子：
```latex
\documentclass{article}
\begin{document}
这是一个例子\footnote{这里是一个脚注}。
\end{document}
```
在这个例子中，`这是一个例子`是正文的文本，而`这里是一个脚注`是脚注的内容。当你编译这段LaTeX代码时，脚注会出现在当前页面的底部。
如果你想在脚注中包含特殊字符（如#、%、 etc.）或者想在脚注中使用其他LaTeX命令，需要使用`\protect`命令来避免错误。例如：
```latex
\documentclass{article}
\begin{document}
这是一个例子\footnote{这里是一个脚注，包含一个百分比符号：\protect\%}。
\end{document}
```
此外，LaTeX还允许自定义脚注的样式。例如，你可以使用`\footnotemark`和`\footnotetext`命令来创建一个无序号的脚注：
```latex
\documentclass{article}
\begin{document}
这是一个例子\footnotemark。
\footnotetext{这里是一个无序号的脚注。}
\end{document}
```
在这个例子中，脚注不会显示序号。但请注意，`\footnotemark`和`\footnotetext`命令必须在同一页面上使用，否则脚注可能不会正确地出现在页面的底部。
## 边注
边注是部分显示，不是一个垂直竖线
```
\documentclass{ctexart}
\usepackage[margin=0.5in]{geometry}
\usepackage{marginnote}
\usepackage{mdframed}
\usepackage{xcolor} % 用于设置边框颜色

% 定义一个带边框的边注环境
\newmdenv[
  linecolor=gray, % 边框颜色
  linewidth=0.5pt, % 边框线宽
  innermargin=5pt, % 边注与边框的内部边距
  outermargin=5pt, % 边注与页面的外部边距
  leftmargin=0pt, % 边注的左边距
  rightmargin=0pt, % 边注的右边距
  topline=false, % 不显示上边框
  bottomline=false, % 不显示下边框
  rightline=false, % 显示右边框
  leftline=true, % 不显示左边框
]{mymarginnote}

\begin{document}

这是一个例子\marginnote{%
  \begin{mymarginnote}
    这里是一个带竖线分隔的边注。
  \end{mymarginnote}
}。

\end{document}

```
## 脚注+边注+控制显示脚注
控制显示主要使用条件语句来进行判断
```latex
\documentclass[twoside]{article} % Note: uses twoside option
\usepackage[a4paper, marginparwidth=75pt, total={10cm, 10cm}]{geometry} % To create a small page
% 定义一个控制边注显示的变量
%\newif\ifshowmarginnotes
% 默认情况下显示边注
\showmarginnotestrue
% 如果要隐藏边注，使用
\showmarginnotesfalse
\usepackage{hyperref} % To use the \url command (in the footnote)
\usepackage{marginnote}
\begin{document}
\section{Lorem Ipsum}
\footnote{Source text: Wikipedia (\url{https://en.wikipedia.org/wiki/Lorem_ipsum})}But I must explain to you how all this mistaken idea of reprobating pleasure and extolling pain arose. To do so, I will give you a complete account of the system, and expound the actual teachings of the great explorer of the truth, the master-builder of human happiness. 
% 根据条件显示边注
\ifshowmarginnotes
\marginpar[c]{Note 1: text for right-hand side of pages, it is set justified.}
\else
  % 如果不显示边注，可以在这里放置其他内容，或者留空
\fi

No one rejects, dislikes or avoids pleasure itself, because it is pleasure, but because those who do not know how to pursue pleasure rationally encounter consequences that are extremely painful. Nor again is there anyone who loves or pursues or desires to obtain pain of itself, because it is pain, but occasionally circumstances occur in which toil and pain can procure him some great pleasure.  
% 根据条件显示边注
\ifshowmarginnotes
\marginpar{\raggedright Note 2: text for right-hand side of pages, it is not justified, but uses \texttt{\string\raggedright}.} 
\else
  % 如果不显示边注，可以在这里放置其他内容，或者留空
\fi
To take a trivial example, which of us ever undertakes laborious physical exercise, except to obtain some advantage from it? But who has any right to find fault with a man who chooses to enjoy a pleasure that has no annoying consequences, or one who avoids a pain that produces no resultant pleasure? 
\end{document}

```
## 注释
注释，就是不显示，不是注解。
```
\begin{comment}
... （需要被注释段落）
\end{comment}
```
这个最方便，不需要添加宏包，在需要被注释的段落前后添加
```latex
\iffalse
... （需要被注释段落）
\fi
```


