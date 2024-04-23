在LaTeX中插入代码，通常使用` listings`宏包，它允许您在文档中包含高亮显示的源代码。以下是如何在LaTeX文档中插入代码的基本步骤：
1. **在导言区导入listings宏包**：
```latex
\usepackage{xcolor}%下文有颜色定义，需要引入这个包
\usepackage{listings}
```
2. **设置listings宏包的参数**（可选）：
您可以在导言区设置listings宏包的全局参数，例如代码的字体、颜色、行号等。例如：
```latex

\lstset{
  language=C, % 设置语言
  basicstyle=\footnotesize\ttfamily, % 设置字体大小和样式
  numbers=left, % 显示行号
  numberstyle=\small, % 行号字体大小
  stepnumber=1, % 行号递增
  numbersep=5pt, % 行号和代码之间的距离
  backgroundcolor=\color{white}, % 代码背景颜色
  showspaces=false, % 不显示空格
  showstringspaces=false, % 不显示字符串中的空格
  showtabs=false, % 不显示制表符
  frame=single, % 显示边框
  rulecolor=\color{black}, % 边框颜色
  tabsize=2, % 设置制表符的宽度
  captionpos=b, % 设置标题位置
  breaklines=true, % 自动折行
  breakatwhitespace=false, % 只在空格处折行
  title=\lstname, % 显示文件名作为标题
  escapeinside={\%*}{*)} % 允许使用%*...*)进行LaTeX命令的转义
}
```
3. **在文档中插入代码**：
使用`\lstinputlisting`命令来插入外部代码文件，或者使用`lstlisting`环境来直接在LaTeX文档中嵌入代码。
例如，插入外部文件：
```latex
\lstinputlisting[language=Python]{path/to/your/code.py}
```
或者在文档中直接嵌入代码：
```latex
\begin{lstlisting}[language=Python]
def hello_world():
    print("Hello, World!")
\end{lstlisting}
```
请根据您的代码语言和需求调整`language`参数。如果您需要更多关于`listings`宏包的详细信息，可以查看其官方文档。
确保在编译包含`listings`宏包的LaTeX文档时，使用支持该宏包的编译器，如`pdflatex`。

