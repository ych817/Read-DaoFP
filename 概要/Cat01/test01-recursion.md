
$$
\def\expandafter#1#2{
  #2 #1
}

% mathjax 中无法使用 if then else
\newcommand{\fact}[2][%
  \times{}\fact
]{
  (#2 #1
}
\fact8765432[]1
$$

$$
\def\prstt#1{\texttt{(}#1\texttt{)}}               % 为表达式添加圆括号 \tt
\newcommand{\localenv}[3][\prstt]{{#1{#2}^{#3}}}   % 后面会用到
\newcommand{\scomb}[1]{\localenv{#1}{\mathrlap{}}} % S-exp 组合式
\newcommand{\sexplist}[2][%
  \ \sexplist 
]{
  {\tt #2} #1
}
\scomb{\sexplist{add}1[]2}
$$

想到一个事情 :

- $\lambda x.f ~x$ 完全可以写成 $x\mapsto {(x~f)}$ 
