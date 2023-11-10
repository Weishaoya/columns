
[toc]



# 一、分块矩阵

使用 `arydshln` 宏包， `|` 代表竖实线， `:` 代表竖虚线， `hline` 和 `hdashline` 分别代表横向实线和虚线。

```latex
% \usepackage{arydshln}
\[
    \left(\begin{array}{c|c:c}
        1 & 2 & 5\\
        \hline
        3 & 4 & 6\\
        \hdashline
        7 & 8 & 9
    \end{array}\right)
\]
```

$$
\left(\begin{array}{c|c:c}
		1 & 2 & 5\\
		\hline
		3 & 4 & 6\\
		\hdashline
		7 & 8 & 9
	\end{array}\right)
$$



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

