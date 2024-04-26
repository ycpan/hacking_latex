## 常用字体
需要引入
```
\usepackage{amsmath}%数据公式和矩阵常用包
```
## 数学集合
LaTeX 中 \mathbb 命令用于 typesetting blackboard bold letters，通常用于表示特定的数学集合，如自然数集合（\mathbb{N}）、整数集合（\mathbb{Z}）、有理数集合（\mathbb{Q}）和无理数集合（\mathbb{R}）, 需要引入
```latex
\usepackage{amssymb} % 或者 \usepackage{amsfonts}
```
如：
```latex
\documentclass{ctexart}
\usepackage{amsmath}
\usepackage{amssymb} % 或者 \usepackage{amsfonts}
\begin{document}
$$\boldsymbol{E} \in \mathbb{R}^{n \times d_\text{model}}$$
\end{document}

```
