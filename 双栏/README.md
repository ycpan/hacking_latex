## 双栏
1. 双栏可以分为全局双栏或者部分双栏，全局双栏比较容易，直接引用`\documentclass[UTF8,twocolumn]{ctexart}`即可
2. 部分双栏比较麻烦，有两种方案
2.1 如果不插入图片，表格之类的，可以使用`\begin{multicols}{2}`即可。   
2.2 如果使用图片，表格，用2.1的方法，表格和图片显示不出来。可以用全局双栏中，部分为单栏的思路[^1]。如下：    
```
\begin{document}
\title{烟台新能源产业报告}
\author{产业AI助手}
\date{\today}
\twocolumn[
\begin{@twocolumnfalse}%全局双栏中部分单栏，非常重要
\maketitle
{\kaishu【摘要】杭州市人工智能产业近年来呈现出显著的增长趋势，自2017年的10家企业增长到2022年的160家企业，增长了16倍。在160家人工智能企业中，有10家上市企业，20家小巨人企业和30家专精特新企业。这些企业分布在西湖区、上城区、萧山区、余杭区、钱塘区和富阳区，显示出杭州市在人工智能产业布局上的均衡性。随着技术的不断进步和市场需求的不断扩大，杭州市人工智能产业有望继续保持高速发展的态势，成为全球人工智能领域的重要力量。}

\hspace{1.5cm}
\end{@twocolumnfalse}
]
双栏内容
\end{document}
```
该方法详见report.tex

## 关于双栏中排版问题
[图片的排版](https://www.littlewaterdrop.com/cs/latex/figures)

[表格的排版](https://www.littlewaterdrop.com/cs/latex/tables)

【参考文献】
[^1]:(https://zhuanlan.zhihu.com/p/392284625)
