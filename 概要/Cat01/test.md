$$
% 杂项 ========================================================================
{\rm \LaTeX}\text{ Definitions are here.}
\let\ph=\phantom
\let\hph=\hphantom
\let\vph=\vphantom
\let\mrel=\mathrel
\let\mbin=\mathbin
\let\mllap=\mathllap
\let\mrlap=\mathrlap
\let\mclap=\mathclap
\def\verts#1{\lvert#1\rvert}
\def\pla{\vph{fg}}                              % 柱子, 用于指定盒子的最小高度
%\def{\bbox[0pt,red]{\,\vph{fg}}}               % 测试柱子是否被使用
\let\objectstyle=\pla                           % 交换图里所有对象都加上
\def\prs#1{(#1)}                                % 为表达式添加括号
\def\etc{\textrm{etc}}                          % 对应省略号 等等等等
\def\wld{\_}                                    % 对应通配符 _
% 值构造器 ====================================================================
\def\cons{\mbin{.}}                             % 对应积类型 cons
\def\ethr{\mbin{}}                             % 对应和类型 either
\def\concat{\mbin{\tt{:}}}                      % 对应列表类型的 concat
% 打印名称 ====================================================================
% 打印常变量 -------------------------------------------------------------------
\newcommand{\obj}[1][c]{{\sf #1}}               % 对象
\def\obji{\obj[0]}                              % 对象 : 始
\def\objt{\obj[1]}                              % 对象 : 终
\newcommand{\cat}[1][C]{{\sf #1}}               % 范畴 : C默认
\def\catCat{\cat[Cat]}                          % 范畴 : Cat
\def\catSet{\cat[Set]}                          % 范畴 : Set
\def\catHask{\cat[Hask]}                        % 范畴 : Hask — 笛卡尔闭范畴 +/× 都在里面
\newcommand{\arr}[1][f]{\pla \smash{#1}}        % 箭头
\newcommand{\arr}[1][f]{\bbox[0pt, violet]{\pla \smash{#1}}} % 测试箭头是否被使用
\newcommand{\fct}[1][F]{\pla \smash{#1}}        % 函子
\newcommand{\fct}[1][F]{\bbox[0pt,orange]{\pla \smash{#1}}}  % 测试函子是否被使用
\newcommand{\ntf}[1][\eta]{\pla \smash{#1}}     % 自然变换
\newcommand{\ntf}[1][\eta]{\bbox[0pt,pink]{\pla \smash{#1}}} % 测试自然变换是否被使用
% 打印方法名 ------------------------------------------------------------------
\newcommand{\opr}[2][\cat]{\smash{              % 方法的名称 形式 1
  \overset{\mclap{\small #1}}{#2}}}
\def\rst#1undr#2{                               % 方法的名称 形式 2
  {}^{}_{\smash{:#2}}{#1}}       
\newcommand{\id}[1][\obj]{                      % 对象的 id
  \rst{\textrm{id}}undr#1}
\newcommand{\absurd}[1][\obj]{                  % 对象的 absurd
  \rst{{\large\textexclamdown\hspace{-3px}}}undr#1}
\newcommand{\bang}[1][\obj]{                    % 对象的 bang
  \rst{\textrm{!}}undr#1}
\newcommand{\src}[1][\cat]{                     % 箭头的源头
  \opr[#1]{\textrm{src}}}
\newcommand{\tar}[1][\cat]{                     % 箭头的目标
  \opr[#1]{\textrm{tar}}}
\def\dom{\textrm{dom}}                          % 箭头的定义域
\def\img{\textrm{img}}                          % 箭头的值域
\newcommand{\Id}[1][\cat]{                      % 范畴的 ID
  \rst{\textrm{Id}}undr#1}
\def\Obj{\textrm{Obj}}                          % 范畴的所有对象
\def\Arr{\textrm{Arr}}                          % 范畴的所有箭头
\def\op{\textrm{op}}                            % 范畴的对偶
\newcommand{\catplus}[1][\cat]{                 % 范畴 C 中的运算 + 
  \opr[#1]{+}}
\newcommand{\cattimes}[1][\cat]{                % 范畴 C 中的运算 ×
  \opr[#1]{\times}}
\newcommand{\catotimes}[1][\cat]{               % 范畴 C 中的运算 ⊗
  \opr[#1]{\otimes}}
\newcommand{\catcirc}[1][\cat]{                 % 范畴 C 中的运算 ○
  \opr[#1]{\circ}}
\newcommand{\cathom}[1][\cat]{\smash{           % 范畴 C 中的运算 →
  \xrightarrow{\small #1}}}
\newcommand{\catcong}[1][\cat]{\smash{          % 范畴 C 中的同构 ≅
  \opr[#1]{\cong}}}
\newcommand{\Di}[2][\cat]{                      % 对角函子
  \smash[b]{\underset{\small #2}{\opr[#1]{\textrm{Di}}}}}
\newcommand{\I}[1][F]{                          % 函子的 ID 自然变换
  \rst{\iota}undr#1}
\def\yoneda{{\raise{-1px}{                      % 米田嵌入
  \hspace{-1px}\smash{よ}\vph{fgh}\hspace{-1px}}}}
\def\yoda{                                      % 尤达嵌入
  \texttt{尤}}
% 用方法求值 -------------------------------------------------------------------
\newcommand{\evlcry}[3][\prs]{                  % 用方法求值 柯里化
  \bbox[border: 1px solid Orchid]{%              % 针对的方法有
    #1{#3{#2}}                                    % Id id bang absurd
  }
}                                                                                     
\newcommand{\evlcrytxt}[3][\prs]{               % 用方法求值 柯里化
  %\bbox[border: 1px solid Orchid]{%              % 针对的方法有 
	  #1{#3~{#2}}                                 % Di Obj Arr src dom img                     
  %}
}	                                              
\newcommand{\evlcrynat}[3][\prs]{               % 用方法求值 柯里化
  \bbox[border: 1px solid Orchid]{%              % 针对的方法 自然变换 有 
    #1{#3^{#2}}                                   % η θ
  }
}
\def\evlbig#1#2#3{                              % 用方法求值 大算符
  \bbox[border: 1px solid Turquoise]{%            % 针对的方法 大算符 有 
    #2\rst{#1}undr#3%                             % ∑ ∏ ⨿  
  }
}
\newcommand{\evlbin}[4][\prs]{                  % 用方法求值 二元运算
  \bbox[border: 1px solid red]{%                 % 针对的方法 二元运算 有
    #1{#3 \mbin{#2} #4}%                          % ＋ × ⊗ ○ →
  }
}
$$

### 自然变换

如果还知道 $\fct[F']:\evlbin[]{\cathom[\catCat]}
    \cat
    {\cat[D]}$ 为函子 , 那么

- $\ntf[\eta] : \evlbin[]{\cathom[{\evlbin[]{\cathom[\catCat]}
    \cat
    {\cat[D]}}]}
      {\fct[F]}
      {\fct[F']}$ 为自然变换当且仅当对任意 
  $\cat$ 中对象 $\obj[c]$ , $\obj[c']$ 始终都会有下述交换图成立 : 

  $\vcenter{\begin{xy}\xymatrix@!R=1cm@!C=2cm{
  {\evlcry[]{\bbox[LightGreen]{\fct[F]}}
  {\obj[c]}} 
  \ar[r]^{\evlcrynat[]{\ntf[\eta]}
  {\obj[c]}} 
  \ar[d]_{\evlcry[]{\bbox[LightGreen]{\fct[F]}}
  {\arr[f_1]}} &
  {\evlcry[]{\bbox[LightGreen]{\fct[F']}}
  {\obj[c]}} 
  \ar[d]^{\evlcry[]{\bbox[LightGreen]{\fct[F']}}
  {\arr[f_1]}}  \\
  {\evlcry[]{\bbox[LightGreen]{\fct[F]}}
  {\obj[c']}} 
  \ar[r]_{\evlcrynat[]{\ntf[\eta]}
  {\obj[c']}} 
  \save[].[u]*+<3pt>[F-:<5pt>:ForestGreen]\frm{} !D*!U{\small\color{ForestGreen}\evlcry[]{\bbox[LightGreen]{\fct[F]}}
  {\cat}}\restore
  &
  {\evlcry[]{\bbox[LightGreen]{\fct[F']}}
  {\obj[c']}}  
  \save[].[u]*+<3pt>[F-:<5pt>:ForestGreen]\frm{} !D*!U{\small\color{ForestGreen}\evlcry[]{\bbox[LightGreen]{\fct[F']}}
  {\cat}}\restore
  \save[u].[].[l]*+<10pt>[F-:<8pt>:ForestGreen]\frm{} !U*!D!R(7){\small\color{ForestGreen}\cat[D]}\restore 
  }\end{xy}}$ $\quad \vcenter{\begin{xy}\xymatrix@!R=1cm@!C=2cm{ 
  \cat[D]
  \ar@{<-}@`{[]+/l+3pc/,[d]+/l+3pc/}[d]^(.5){}="mid1"|{\fct[F]}
  \ar@{<-}@`{[]+/r+3pc/,[d]+/r+3pc/}[d]_(.5){}="mid2"|{\fct[F']}
  \\
  \cat
  \ar@2{>} "mid1";"mid2"^{\ntf[\eta]}
  }\end{xy}}$ 

### 自然变换的复合

若已知 $\ntf[\eta] : \evlbin[]{\cathom[{\evlbin[]{\cathom[\catCat]}
    \cat
    {\cat[D]}}]}
      {\fct[F]}
      {\fct[F']}$ 构成自然变换且
还知道 $\ntf[\eta'] : \evlbin[]{\cathom[{\evlbin[]{\cathom[\catCat]}
    \cat
    {\cat[D]}}]}
      {\fct[F']}
      {\fct[F'']}$ 为自然变换则

- $\evlbin[]{\catcirc[{\cat\cathom[\catCat]\cat[D]}]}
    {\ntf[\eta]~~}
    {~~\ntf[\eta']}: \evlbin[]{\cathom[{\evlbin[]{\cathom[\catCat]}
      \cat
      {\cat[D]}}]}
        {\fct[F]}
        {\fct[F'']}$ 为自然变换 , 
  称作 $\ntf[\eta]$ 和 $\ntf[\eta']$ 的**纵复合** 。

  $\vcenter{\begin{xy}\xymatrix@!R=1cm@!C=2cm{
  {\evlcry[]{\bbox[LightGreen]{\fct[F]}}
  {\obj[c]}} 
  \ar[r]^{\evlcrynat[]{\ntf[\eta]}
  {\obj[c]}} 
  \ar[d]_{\evlcry[]{\bbox[LightGreen]{\fct[F]}}
  {\arr[f_1]}} &
  {\evlcry[]{\bbox[LightGreen]{\fct[F']}}
  {\obj[c]}}
  \ar[r]^{\evlcrynat[]{\ntf[\eta']}
  {\obj[c]}} 
  \ar[d]^{\evlcry[]{\bbox[LightGreen]{\fct[F']}}
  {\arr[f_1]}} & 
  {\evlcry[]{\bbox[LightGreen]{\fct[F'']}}
  {\obj[c]}} 
  \ar[d]^{\evlcry[]{\bbox[LightGreen]{\fct[F'']}}
  {\arr[f_1]}} & 
  \\
  {\evlcry[]{\bbox[LightGreen]{\fct[F]}}
  {\obj[c']}} 
  \ar[r]_{\evlcrynat[]{\ntf[\eta]}
  {\obj[c']}} 
  \save[].[u]*+<3pt>[F-:<5pt>:ForestGreen]\frm{} !D*!U
  {\small\color{ForestGreen}\evlcry[]{\bbox[LightGreen]{\fct[F]}}
  {\cat}}\restore
  &
  {\evlcry[]{\bbox[LightGreen]{\fct[F']}}
  {\obj[c']}}  
  \ar[r]_{\evlcrynat[]{\ntf[\eta']}
  {\obj[c']}} 
  \save[].[u]*+<3pt>[F-:<5pt>:ForestGreen]\frm{} !D*!U
  {\small\color{ForestGreen}\evlcry[]{\bbox[LightGreen]{\fct[F']}}
  {\cat}}\restore
  & 
  {\evlcry[]{\bbox[LightGreen]{\fct[F'']}}
  {\obj[c']}}
  \save[].[u]*+<3pt>[F-:<5pt>:ForestGreen]\frm{} !D*!U
  {\small\color{ForestGreen}\evlcry[]{\bbox[LightGreen]{\fct[F'']}}
  {\cat}}\restore
  \save[u].[].[ll]*+<10pt>[F-:<8pt>:ForestGreen]\frm{} !U*!D!R(13)
  {\small\color{ForestGreen}\cat[D]}\restore 
  }\end{xy}}\quad 
  \vcenter{\begin{xy}\xymatrix@!R=1cm@!C=2cm{ 
  \cat[D]
  \\
  \cat[C]
  \ar@`{[]+/l+3pc/,[u]+/l+3pc/}[u]_(.5){}="mid1"|{\fct[F]}
  \ar@`{[]+/r+0pc/,[u]+/r+0pc/}[u]^(.5){}="mid2a"_(.5){}="mid2b"|{\fct[F']}
  \ar@`{[]+/r+3pc/,[u]+/r+3pc/}[u]^(.5){}="mid3"|{\fct[F'']}
  \ar@2{>} "mid1";"mid2a"^{\ntf[\eta]}
  \ar@2{>} "mid2b";"mid3"^{\ntf[\eta']}
  }\end{xy}}$ 

如果还知道 $\fct[G']:\evlbin[]{\cathom[\catCat]}
  {\cat[D]}
  {\cat[E]}$ 也是个函子
及自然变换 ${\ntf[\theta]}: \evlbin[]{\cathom[{\evlbin[]{\cathom[\catCat]}
  {\cat[D]}
  {\cat[E]}}]}{\fct[G]}{\fct[G']}$ 那么便有

- $\evlbin[]\circ
    {\ntf[\eta]}
    {\ntf[\theta]} : 
  \evlbin[]{\cathom[{\cat\cathom[\catCat]\cat[E]}]}
    {\evlbin[]{\catcirc[\catCat]}
      {\fct[F]}
      {\fct[G]}}
    {\evlbin[]{\catcirc[\catCat]}
      {\fct[F']}
      {\fct[G']}}$ 为
  自然变换 , 称作 $\ntf[\eta]$ 和 $\ntf[\theta]$ 的**横复合** 。

  $\vcenter{\begin{xy}\xymatrix@!R=1cm@!C=2cm{
  {\evlcry[]{\bbox[LightGreen]{\fct[G]}}
  {\evlcry[]{\bbox[LightGreen]{\fct[F]}}
    {\obj[c]}}} 
  \ar[r]^{\evlcry[]{\bbox[LightGreen]{\fct[G]}}
  {\evlcrynat[]{\ntf[\eta]}
    {\obj[c]}}} 
  \ar[d]_{\mathllap{\evlcry[]{\bbox[LightGreen]{\fct[G]}}
  {\evlcry[]{\bbox[LightGreen]{\fct[F]}}
    {\arr[f_1]}}}} 
  \ar@[gray][drr]|(.7)[gray]{\evlcrynat[]{\ntf[\theta]}
  {\evlcry{\fct[F]}
    {\obj[c]}}} &
  {\evlcry[]{\bbox[LightGreen]{\fct[G]}}
  {\evlcry[]{\bbox[LightGreen]{\fct[F']}}
    {\obj[c]}}} 
  \ar[d]^{\mathrlap{\evlcry[]{\bbox[LightGreen]{\fct[G]}}
  {\evlcry[]{\bbox[LightGreen]{\fct[F']}}
    {\arr[f_1]}}}} 
  \ar@[gray][drr]|(.3)[gray]{\evlcrynat[]{\ntf[\theta]}
  {\evlcry{\fct[F']}
    {\obj[c]}}} \\
  {\evlcry[]{\bbox[LightGreen]{\fct[G]}}
  {\evlcry[]{\bbox[LightGreen]{\fct[F]}}
    {\obj[c']}}} 
  \ar[r]_{\evlcry[]{\bbox[LightGreen]{\fct[G]}}
  {\evlcrynat[]{\ntf[\eta]}
    {\obj[c']}}} 
  \ar@[gray][drr]|(.7)[gray]{\evlcrynat[]{\ntf[\theta]}
  {\evlcry{\fct[F]}
    {\obj[c']}}} &
  {\evlcry[]{\bbox[LightGreen]{\fct[G]}}
  {\evlcry[]{\bbox[LightGreen]{\fct[F']}}
    {\obj[c']}}}  
  \ar@[gray][drr]|(.3)[gray]{\evlcrynat[]{\ntf[\theta]}
  {\evlcry{\fct[F']}
    {\obj[c']}}}
  \save[ul].[]*+<10pt>[F-:<8pt>:ForestGreen]\frm{} !U*!D!L(7){\small\color{ForestGreen}\cat[E]}\restore &
  {\evlcry[]{\bbox[LightGreen]{\fct[G']}}
  {\evlcry[]{\bbox[LightGreen]{\fct[F]}}
    {\obj[c]}}} 
  \ar[r]^{\evlcry[]{\bbox[LightGreen]{\fct[G']}}
  {\evlcrynat[]{\ntf[\eta]}
    {\obj[c]}}} 
  \ar[d]_{\mathllap{\evlcry[]{\bbox[LightGreen]{\fct[G']}}
  {\evlcry[]{\bbox[LightGreen]{\fct[F]}}
    {\arr[f_1]}}}} &
  {\evlcry[]{\bbox[LightGreen]{\fct[G']}}
  {\evlcry[]{\bbox[LightGreen]{\fct[F']}}
    {\obj[c]}}} 
  \ar[d]^{\mathrlap{\evlcry[]{\bbox[LightGreen]{\fct[G']}}
  {\evlcry[]{\bbox[LightGreen]{\fct[F']}}
    {\arr[f_1]}}}}  \\
  & & 
  {\evlcry[]{\bbox[LightGreen]{\fct[G']}}
  {\evlcry[]{\bbox[LightGreen]{\fct[F]}}
    {\obj[c']}}} 
  \ar[r]_{\evlcry[]{\bbox[LightGreen]{\fct[G']}}
  {\evlcrynat[]{\ntf[\eta]}
    {\obj[c']}}} &
  {\evlcry[]{\bbox[LightGreen]{\fct[G']}}
  {\evlcry[]{\bbox[LightGreen]{\fct[F']}}
    {\obj[c']}}}  
  \save[ul].[]*+<10pt>[F-:<8pt>:ForestGreen]\frm{} !U*!D!L(7){\small\color{ForestGreen}\cat[E]}\restore 
  \\
  &
  {\evlcry[]{\bbox[LightGreen]{\fct[F]}}
  {\obj[c]}} 
  \ar[r]^{\evlcrynat[]{\ntf[\eta]}
  {\obj[c]}} 
  \ar[d]_{\mathllap{\evlcry[]{\bbox[LightGreen]{\fct[F]}}
  {\arr[f_1]}}} 
  \ar@{->}@[lightgray][uuul]|[lightgray]{\fct[G]} 
  \ar@{->}@[lightgray][uur]|[lightgray]{\fct[G']} 
  &
  {\evlcry[]{\bbox[LightGreen]{\fct[F']}}
  {\obj[c]}} 
  \ar[d]^{\mathrlap{\evlcry[]{\bbox[LightGreen]{\fct[F']}}
  {\arr[f_1]}}} 
  \ar@{->}@[lightgray][uuul]|[lightgray]{\fct[G]} 
  \ar@{->}@[lightgray][uur]|[lightgray]{\fct[G']} 
  & \\
  &
  {\evlcry[]{\bbox[LightGreen]{\fct[F]}}
  {\obj[c']}} 
  \ar[r]_{\evlcrynat[]{\ntf[\eta]}
  {\obj[c']}} 
  \ar@{->}@[lightgray][uuul]|[lightgray]{\fct[G]} 
  \ar@{->}@[lightgray][uur]|[lightgray]{\fct[G']} &
  {\evlcry[]{\bbox[LightGreen]{\fct[F']}}
  {\obj[c']}}
  \ar@{->}@[lightgray][uuul]|[lightgray]{\fct[G]}
  \ar@{->}@[lightgray][uur]|[lightgray]{\fct[G']} 
  \save[ul].[]*+<10pt>[F-:<8pt>:ForestGreen]\frm{} !D*!U!L(6){\small\color{ForestGreen}\cat[D]}\restore  & &
  }\end{xy}}$ $\quad \vcenter{\begin{xy}\xymatrix@!R=1cm@!C=2cm{ 
  \cat[E]
  \ar@{<-}@`{[]+/l+3pc/,[d]+/l+3pc/}[d]^(.5){}="mida1"|{\fct[G]}
  \ar@{<-}@`{[]+/r+3pc/,[d]+/r+3pc/}[d]_(.5){}="mida2"|{\fct[G']}
  \\
  \cat[D]
  \ar@2{>} "mida1";"mida2"^{{\ntf[\theta]}}
  \ar@{<-}@`{[]+/l+3pc/,[d]+/l+3pc/}[d]^(.5){}="midb1"|{\fct[F]}
  \ar@{<-}@`{[]+/r+3pc/,[d]+/r+3pc/}[d]_(.5){}="midb2"|{\fct[F']}
  \\
  \cat
  \ar@2{>} "midb1";"midb2"^{\ntf[\eta]}
  }\end{xy}}$ 

若 ${\ntf[\theta']}: \evlbin[]{\cathom[{\evlbin[]{\cathom[\catCat]}
  {\cat[D]}
  {\cat[E]}}]}{\fct[G]}{\fct[G']}$ 为自然变换则

- $\evlbin[]{\catcirc[{\cat\cathom[\catCat]\cat[E]}]}
      {\evlbin\circ
        {\ntf[\eta]}
        {\ntf[\theta]}~~}
      {~~\evlbin\circ
        {\ntf[\eta']}
        {\ntf[\theta']}} = 
      \evlbin[]\circ
        {\evlbin{\catcirc[{\cat\cathom[\catCat]\cat[D]}]}
          {\ntf[\eta]~~}  
          {~~\ntf[\eta']}}
        {\evlbin{\catcirc[{\cat[D]\cathom[\catCat]\cat[E]}]}
          {\ntf[\theta]~~}  
          {~~\ntf[\theta']}}$ , 
  即便改变横纵复合先后顺序也不影响最终结果 。

  $\vcenter{\begin{xy}\xymatrix@!R=1cm@!C=2cm{ 
  \cat[E]
  \ar@{<-}@`{[]+/l+3pc/,[d]+/l+3pc/}[d]^(.5){}="mida1"|{\fct[G]}
  \ar@{<-}@`{[]+/r+0pc/,[d]+/r+0pc/}[d]_(.5){}="mida2a"^(.5){}="mida2b"|{\fct[G']}
  \ar@{<-}@`{[]+/r+3pc/,[d]+/r+3pc/}[d]_(.5){}="mida3"|{\fct[G'']}
  \\
  \cat[D]
  \ar@2{>} "mida1";"mida2a"^{{\ntf[\theta]}}
  \ar@2{>} "mida2b";"mida3"^{{\ntf[\theta']}}
  \ar@{<-}@`{[]+/l+3pc/,[d]+/l+3pc/}[d]^(.5){}="midb1"|{\fct[F]}
  \ar@{<-}@`{[]+/r+0pc/,[d]+/r+0pc/}[d]_(.5){}="midb2a"^(.5){}="midb2b"|{\fct[F']}
  \ar@{<-}@`{[]+/r+3pc/,[d]+/r+3pc/}[d]_(.5){}="midb3"|{\fct[F']'}
  \\
  \cat
  \ar@2{>} "midb1";"midb2a"^{\ntf[\eta]}
  \ar@2{>} "midb2b";"midb3"^{\ntf[\eta']}
  }\end{xy}}$

<div style="page-break-after: always"></div>

### 恒等自然变换

同样对于自然变换也有恒等映射 。

- $\id[{\fct[F]}]:\evlbin[]{\cathom[{\evlbin{\cathom[\catCat]}
    {\cat[C]}
    {\cat[D]}}]}
      {\fct[F]}
      {\fct[F]}$ 为恒等自然变换当且仅当
  对范畴 $\cat$ 中任意对象 $\obj[x]$ 都有下述交换图成立 :

  $\vcenter{\begin{xy}\xymatrix@!R=1cm@!C=2cm{
  {\evlcry[]{\bbox[LightGreen]{\fct[F]}}
  {\obj[c]}} 
  \ar[r]^{\evlcrynat[]{\ntf[\eta]}
  {\obj[c]}=\id[{\obj[c]}]} 
  \ar[d]_{\evlcry[]{\bbox[LightGreen]{\fct[F]}}
  {\arr[f_1]}} &
  {\evlcry[]{\bbox[LightGreen]{\fct[F']}}
  {\obj[c]}} 
  \ar[d]^{\evlcry[]{\bbox[LightGreen]{\fct[F']}}
  {\arr[f_1]}}  \\
  {\evlcry[]{\bbox[LightGreen]{\fct[F]}}
  {\obj[c']}} 
  \ar[r]_{\evlcrynat[]{\ntf[\eta]}
  {\obj[c']}=\id[{\obj[c']}]} 
  \save[].[u]*+<3pt>[F-:<5pt>:ForestGreen]\frm{} !D*!U{\small\color{ForestGreen}\evlcry[]{\bbox[LightGreen]{\fct[F]}}
  {\cat}}\restore
  &
  {\evlcry[]{\bbox[LightGreen]{\fct[F']}}
  {\obj[c']}}  
  \save[].[u]*+<3pt>[F-:<5pt>:ForestGreen]\frm{} !D*!U{\small\color{ForestGreen}\evlcry[]{\bbox[LightGreen]{\fct[F']}}
  {\cat}}\restore
  \save[ul].[]*+<10pt>[F-:<8pt>:ForestGreen]\frm{} !U*!D!L(6){\small\color{ForestGreen}\cat[D]}\restore 
  }\end{xy}}$ $\quad \vcenter{\begin{xy}\xymatrix@!R=1cm@!C=2cm{ 
  \cat[D]
  \ar@{<-}@`{[]+/l+0pc/,[d]+/l+0pc/}[d]|{\fct[F]}^{}="mid"
  \\
  \cat
  \save "mid" 
  \ar@2@`{"mid"+/ur+5pc/,"mid"+/dr+5pc/}^{\ntf[\eta]}"mid"
  \restore
  }\end{xy}}$ 

### 自然同构

自然同构与你想象中的同构不太像 。

- $\ntf[\eta] : \evlbin[]{\cathom[{\evlbin[]{\cathom[\catCat]}
    \cat
    {\cat[D]}}]}
      {\fct[F]}
      {\fct[F']}$ 为**自然同构**当且仅当
  $\evlcrynat[]{\ntf[\eta]}
    {\obj[x]}$ 总是同构 , 这里 $\obj[x]$ 为任意 $\cat$ 中对象 。

  此时 $\fct[F]$ , $\fct[F']$ 的关系可用 $\evlbin[]{\catcong[{\evlbin[]{\cathom[\catCat]}
    \cat
    {\cat[D]}}]}
      {\fct[F]~}
      {~\fct[F']}$ 表示

### 范畴等价的定义

我们用自然同构来定义范畴的等价 。

- $\evlbin[]{\catcong[\catCat]}
    {\cat[C]}
    {\cat[D]}$ 当且仅当
  存在函子 $\fct[F]:\evlbin[]{\cathom[\catCat]}
    \cat
    {\cat[D]}$ 及 $\fct[F']: \evlbin[]{\cathom[\catCat]}
      {\cat[D]}
      \cat$ 

  使 $\evlbin[]{\catcong[{\cat\cathom[\catCat]\cat[C]}]}
    {\evlbin[]{\catcirc[\catCat]}
      {\fct[F]}
      {\fct[F']}}
    {\id[\cat]}$ 并且有 $\evlbin[]{\catcong[{\cat[D]\cathom[\catCat]\cat[D]}]}
      {\evlbin[]{\catcirc[\catCat]}
        {\fct[F']}
        {\fct[F]}}
      {\id[{\cat[D]}]}$ 。
