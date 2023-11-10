
[toc]

使用 LaTeX 时总有些宏包和命令要经常使用，但是我又经常会忘记，一忘记就要去漫无目的地查资料，费时费力，故开此贴整合记录一下。



# 〇、内置命令

在公式中嵌入文字，可以使用 `\textnormal` 命令

```
$\textnormal{成功} = \textnormal{汗水} \times 99\% + \textnormal{灵感} \times 1\%$
```

$$
\textnormal{成功} = \textnormal{汗水} \times 99\% + \textnormal{灵感} \times 1\%
$$





# 一、enumitem宏包

label 为 (1) (2) (3) ... 的 `enumerate` 环境

```latex
\begin{enumerate}[label=(\arabic*)]
    \item 第一项
    \item 第二项
    \item 第三项
\end{enumerate}
```





# 笔记模板

```latex
% !TeX program = xelatex
\documentclass[
	border={25mm 20mm 25mm 30mm},  % 左下右上的页边距
	varwidth,  % 页面最大宽度
]{standalone}
\usepackage[heading]{ctex}  % 使用中文
\usepackage[
	colorlinks,  % 有色链接
	linkcolor=blue,  % 蓝色的目录链接
]{hyperref}  % 支持目录跳转
% 清除目录项的页号和分隔点
\usepackage{tocloft}
\cftpagenumbersoff{section}
\cftpagenumbersoff{subsection}
\cftpagenumbersoff{subsubsection}
\renewcommand{\cftdot}{}

\usepackage{graphicx}  % includegraphics
\usepackage{amsmath, amssymb, amsopn}  % 数学宏包

\usepackage[justification=centering]{caption}
\captionsetup{font=small,labelsep=space} % 图表标题设为五号字体、序号与图表名之间以空格分隔
\captionsetup[table]{font={small,bf},labelsep=space}  % 表标题设为五号加粗、表序与表名之间以空格分隔

%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%% begin

\title{标题}
\author{作者}
\date{\today}

\usepackage{enumitem}
\usepackage{listings}
\usepackage{amsmath}
\begin{document}
	\hspace*{\textwidth}
	\setlength{\parindent}{2em}
	
	\maketitle
	
	\tableofcontents

	\setlength{\parindent}{2em}
	\setcounter{section}{-1}
	
	\section{前言}
	
	\section{第一章}
	第一章的内容
	
	\section{第二章}
	第二章的内容

\end{document}

```

