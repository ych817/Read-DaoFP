## 10 伴随函子

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
\def\pla{\vph{(fg)}}                            % 柱子, 用于指定盒子的最小高度
%\def\pla{\bbox[0pt,red]{\,\vph{fg}}}            % 测试柱子是否被使用
%\let\objectstyle=\pla                           % 交换图里所有对象都加上
\def\prs#1{(#1)}                                % 为表达式添加括号
\def\etc{\textrm{etc}}                          % 对应省略号 等等等等
\def\wld{\_}                                    % 对应通配符 _
% 值构造器 ====================================================================
\def\cons{\mbin{.}}                             % 对应积类型 cons
\def\ethr{\mbin{}}                              % 对应和类型 either
\def\concat{\mbin{\tt{:}}}                      % 对应列表类型的 concat
% 打印名称 ====================================================================
% 打印常变量 -------------------------------------------------------------------
\newcommand{\obj}[1][c]{\pla \smash{\sf #1}}    % 对象
\def\obji{\obj[0]}                              % 对象 : 始
\def\objt{\obj[1]}                              % 对象 : 终
\newcommand{\cat}[1][C]{\pla \smash{\sf #1}}    % 范畴 : C默认
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
\newcommand{\opr}[2][\cat]{\pla \smash{         % 方法的名称 形式 1
  \overset{\mclap{\small #1}}{#2}}}
\def\rst#1undr#2{                               % 方法的名称 形式 2
  {}^{}_{\smash{:#2}}{\pla \smash{#1}}}       
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
\def\dom{\pla \textrm{dom}}                     % 箭头的定义域
\def\img{\pla \textrm{img}}                     % 箭头的值域
\newcommand{\Id}[1][\cat]{                      % 范畴的 ID
  \rst{\textrm{Id}}undr#1}
\def\Obj{\pla \textrm{Obj}}                     % 范畴的所有对象
\def\Arr{\pla \textrm{Arr}}                     % 范畴的所有箭头
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
\newcommand{\catcong}[1][\cat]{                 % 范畴 C 中的同构 ≅
  \opr[#1]{\cong}}
\newcommand{\Di}[2][\cat]{\pla \smash[b]{       % 对角函子
  \underset{\small #2}{\opr[#1]{\textrm{Di}}}}}
\newcommand{\I}[1][F]{                          % 函子的 ID 自然变换
  \rst{\iota}undr#1}
\def\yoneda{{\raise{-1px}{                      % 米田嵌入
  \hspace{-1px}\pla\smash{よ}\hspace{-1px}}}}
\def\yoda{\pla \smash{                          % 尤达嵌入
  尤}}
\def\lim{%                                      % 极限
  \textrm{lim}}
\def\colim{%                                    % 余极限
  \textrm{colim}}                      
% 用方法求值 -------------------------------------------------------------------
\newcommand{\evlcry}[3][\prs]{                  % 用方法求值 柯里化
  \bbox[border: 1px solid Orchid]{%              % 针对的方法有
    #1{#3{#2}}                                    % Id id bang absurd
  }
} 
\newcommand{\evlcrytxt}[3][\prs]{               % 用方法求值 柯里化
  \bbox[border: 1px solid Orchid]{%              % 针对的方法有 
	  #1{#3~{#2}}                                 % Di Obj Arr src dom img
  }
}	                                              
\newcommand{\evlcrynat}[3][\prs]{               % 用方法求值 柯里化
  \bbox[border: 1px solid Orchid]{%              % 针对的方法 自然变换 有 
    #1{#3^{#2}}                                   % η θ
  }
}
\newcommand{\evlbin}[4][\prs]{                  % 用方法求值 二元运算
  \bbox[border: 1px solid Orchid]{%              % 针对的方法 二元运算 有
    #1{#3 \mbin{#2} #4}%                          % ＋ × ⊗ ○ →
  }
}
\newcommand{\evlbig}[4][\prs]{                  % 用方法求值 二元运算
  \bbox[border: 1px solid Orchid]{%              % 针对的方法 二元运算 有
    #1{#4\rst{#2}undr{#3}}%                       % ＋ × ⊗ ○ →
  }
}
$$

若有函子 $\fct[L]:\evlbin[]{\cathom[\catCat]}{\cat[D]}{\cat[C]}$ 
以及函子 $\fct[R]:\evlbin[]{\cathom[\catCat]}{\cat}{\cat[D]}$ , 即

$\qquad \begin{xy}\xymatrix@!C=2cm{
\cat
\ar@`{[]+/dr+2pc/,[r]+/dl+2pc/}[r]_{\fct[R]}
\ar@`{[]+/ul+5pc/,[]+/ur+5pc/}[]^{\Id}
&
\cat[D]
\ar@`{[]+/ul+2pc/,[l]+/ur+2pc/}[l]_{\fct[L]}
\ar@`{[]+/ul+5pc/,[]+/ur+5pc/}[]^{\Id[{\cat[D]}]}
}\end{xy}$

### 伴随函子的第一种定义

那么规定

- $\fct[L]\dashv \fct[R]$ 当且仅当
  函子 ${\evlbin{\cathom}
      {\evlcry[]{\fct[L]}{\bbox[white]{\pla\wld}}}
      {\bbox[white]{\pla\wld}}}$ 和 ${\evlbin{\cathom[{\cat[D]}]}
      {\bbox[white]{\pla\wld}}
      {\evlcry[]{\fct[R]}{\bbox[white]{\pla\wld}}}}$ 
  间存在着一个二元的**自然同构** 。

假如确实有 $\fct[L]\dashv \fct[R]$ , 那么不难得知

<div style="page-break-after: always"></div>

- 这里蕴含着一个二元的自然同构 $\ntf[\phi_2]$ , 见下 :

  $\qquad\begin{aligned}[t]
  \ntf[\phi_2]:{}&
  \evlbin[]{\cathom[{
    \evlbin[]\cathom
      {\evlbin\cattimes{\cat[D]}{\cat}}
      {\catSet}}]}
    {\evlbin{\cathom[{\cat[D]}]}
      {\wld}
      {\evlcry[]{\fct[R]}{\wld}}}
    {\evlbin{\cathom}
      {\evlcry[]{\fct[L]}{\wld}}
      {\wld}}
  \\
  \evlcrynat[]{\ntf[\phi_2]}{\evlbin\cons{\wld}{\bbox[pink]{\obj[c]}}}:{}&
  \evlbin[]{\cathom[{
    \evlbin[]\cathom
      {\cat[D]}
      {\catSet}}]}
    {\evlbin{\cathom[{\cat[D]}]}
      {\wld}
      {\evlcry[]{\fct[R]}{\obj[c]}}}
    {\evlbin{\cathom}
      {\evlcry[]{\fct[L]}{\wld}}
      {\obj[c]}}
  \\
  \evlcrynat[]{\ntf[\phi_2]}{\evlbin\cons{\bbox[pink]{\obj[d]}}{\wld}}:{}&
  \evlbin[]{\cathom[{
    \evlbin[]\cathom
      {\cat}
      {\catSet}}]}
    {\evlbin{\cathom[{\cat[D]}]}
      {\obj[d]}
      {\evlcry[]{\fct[R]}{\wld}}}
    {\evlbin{\cathom}
      {\evlcry[]{\fct[L]}{\obj[d]}}
      {\wld}}
  \end{aligned}$

套用反变米田引理我们便可获得

$\qquad\evlbin[]{\catcong[\catSet]}
{\underbracket[.4pt]
  {\evlbin{\cathom[{\evlbin[]{\cathom[\catCat]}
    {\evlcrynat[]\op{\cat[D]}}
    {\catSet}}]}
      {\bbox[LightGreen]{\evlbin[]{\cathom[{\cat[D]}]}
        {\bbox[white]{\pla\wld}}
        {\evlcry[]{\fct[R]}{\obj[c]}}}}
      {\bbox[YellowGreen]{\evlbin{\cathom[{\cat}]}
        {\evlcry[]{\fct[L]}
          {\bbox[white]{\pla\wld}}}
        {\obj[c]}}}}_
   {\text{一堆自然变换}}}
{\underbracket[.4pt]
  {\bbox[YellowGreen]{\evlbin\cathom
    {\evlcry[]{\fct[L]}
      {\evlcry[]{\fct[R]}
        {\obj[c]}}}
    {\obj[c]}}}_
  {\text{一堆元素}}}$ 

由反变米田引理的证明可知 : 对每个左侧集合中的自然同构 $\evlcrynat[]{\ntf[\phi_2]}{\evlbin\cons{\wld}{\bbox[pink]{\obj[c]}}}$ 
右侧集合中都有一个箭头与之对应 , 即 $\bbox[LightGray]{\evlcry[]{\evlcrynat[]{\ntf[\phi_2]}
{\evlbin\cons{\evlcry[]{\fct[R]}{\obj[c]}}{\bbox[pink]{\obj[c]}}}}{\id[{\evlcry[]{\fct[R]}{\obj[c]}}]}}=\bbox[LightGray]{\evlcrynat[]{\ntf[\varepsilon]}{\obj[c]}}$ 。如此

- $\ntf[\varepsilon]:\evlbin[]{\cathom[{\evlbin[]{\cathom[\catCat]}{\cat[C]}{\cat[C]}}]}{\evlbin[]{\catcirc[\catCat]}{\fct[R]}{\fct[L]}}{\Id[{\cat[C]}]}$ 构成自然变换 。

  > 考虑任意 $\evlcrynat[]\op{\arr[f]}:\evlbin[]\cathom{\obj[c']}{\obj[c]}$ :
  >
  > $\vcenter{\begin{xy}\xymatrix@!R=1cm@!C=3cm{
  > {\bbox[LightGreen]{\evlbin[]{\cathom[{\cat[D]}]}
  >      {\evlcry[]{\fct[R]}{\bbox[white]{\obj[c]}}}
  >      {\evlcry[]{\fct[R]}{\obj[c]}}}}
  > \ar[r]^{\evlcrynat[]{\ntf[\phi_2]}
  > {\evlbin\cons{\evlcry[]{\fct[R]}{\obj[c]}}{\bbox[pink]{\obj[c]}}}} 
  > \ar[d]_{\bbox[LightGreen]{\evlbin[]{\cathom[{\cat[D]}]}
  >      {\evlcry[]{\fct[R]}{\bbox[white]{\evlcrynat[]\op{\arr[f]}}}}
  >      {\evlcry[]{\fct[R]}{\obj[c]}}}} 
  > &
  > {\bbox[LightGreen]{\evlbin[]{\cathom[{\cat}]}
  >      {\evlcry[]{\fct[L]}{\evlcry[]{\fct[R]}{\bbox[white]{\obj[c]}}}}
  >      {\obj[c]}}}
  > \ar[d]^{\bbox[LightGreen]{\evlbin[]{\cathom[{\cat}]}
  >      {\evlcry[]{\fct[L]}{{\evlcry[]{\fct[R]}{\bbox[white]{\evlcrynat[]\op{\arr[f]}}}}}}
  >      {\obj[c]}}}
  > \\
  > {\bbox[LightGreen]{\evlbin[]{\cathom[{\cat[D]}]}
  >      {\evlcry[]{\fct[R]}{\bbox[white]{\obj[c']}}}
  >      {\evlcry[]{\fct[R]}{\bbox[white]{\obj[c]}}}}}
  > \ar[r]|{\evlcrynat[]{\ntf[\phi_2]}
  > {\evlbin\cons{\evlcry[]{\fct[R]}{\obj[c']}}{\bbox[pink]{\obj[c]}}}} 
  > &
  > {\bbox[LightGreen]{\evlbin[]{\cathom[{\cat}]}
  >      {\evlcry[]{\fct[L]}{\evlcry[]{\fct[R]}{\bbox[white]{\obj[c']}}}}
  >      {\bbox[white]{\obj[c]}}}}
  > \\
  > {\bbox[LightGreen]{\evlbin[]{\cathom[{\cat[D]}]}
  > {\evlcry[]{\fct[R]}{\obj[c']}}
  > {\evlcry[]{\fct[R]}{\bbox[white]{\obj[c']}}}}}
  > \ar[r]_{\evlcrynat[]{\ntf[\phi_2]}
  > {\evlbin\cons{\evlcry[]{\fct[R]}{\obj[c']}}{\bbox[pink]{\obj[c']}}}} 
  > \ar[u]^{\bbox[LightGreen]{\evlbin[]{\cathom[{\cat[D]}]}
  > {\evlcry[]{\fct[R]}{\obj[c']}}
  > {\evlcry[]{\fct[R]}{\bbox[white]{\evlcrynat[]\op{\arr[f]}}}}}}
  > %\save[].[uu]*+<3pt>[F-:<5pt>:ForestGreen]\frm{}
  > %!D*!U{\small\color{ForestGreen}
  > %  \bbox[LightGreen]{\evlbin[]{\cathom[{\cat[D]}]}
  > %    {\bbox[white]{\cat[D]}}
  > %    {\evlcry[]{\fct[R]}{\obj[c]}}}
  > %}\restore 
  > %\save[].[uu].[r]*+<10pt>[F-:<8pt>:ForestGreen]\frm{}!D*!U!L(6)
  > %{\small\color{ForestGreen}
  > %\cat[Set]
  > %}\restore 
  > &
  > {\bbox[LightGreen]{\evlbin[]{\cathom[{\cat}]}
  > {\evlcry[]{\fct[L]}{\evlcry[]{\fct[R]}{\obj[c']}}}
  > {\bbox[white]{\obj[c']}}}}
  > \ar[u]_{\bbox[LightGreen]{\evlbin[]{\cathom[{\cat}]}
  > {\evlcry[]{\fct[L]}{\evlcry[]{\fct[R]}{\obj[c']}}}
  > {\bbox[white]{\evlcrynat[]\op{\arr[f]}}}}}
  > %\save[].[uu]*+<3pt>[F-:<5pt>:ForestGreen]\frm{}!D*!U
  > %{\small\color{ForestGreen}
  > %  \bbox[LightGreen]{\evlbin[]{\cathom[{\cat}]}
  > %    {\evlcry[]{\fct[L]}{\bbox[white]{\cat[D]}}}
  > %    {\obj[c]}}
  > %}\restore
  > }\end{xy}}
  > \qquad
  > \vcenter{\begin{xy}\xymatrix@!R=1cm@!C=3cm{
  > {\id[{\evlcry[]{\fct[R]}{\obj[c]}}]} 
  > \ar@{|->}[r]^{\evlcrynat[]{\ntf[\phi_2]}
  >  {\evlbin\cons{\evlcry[]{\fct[R]}{\obj[c]}}{\bbox[pink]{\obj[c]}}}} 
  > \ar@{|->}[d]_{\bbox[LightGreen]{\evlbin[]{\cathom[{\cat[D]}]}
  > {\evlcry[]{\fct[R]}{\bbox[white]{\evlcrynat[]\op{\arr[f]}}}}
  > {\evlcry[]{\fct[R]}{\obj[c]}}}} 
  > &
  > {\pla\smash{\bbox[LightGray]{\evlcry[]
  > {\evlcrynat[]{\ntf[\phi_2]}
  >  {\evlbin\cons{\evlcry[]{\fct[R]}{\obj[c]}}{\bbox[pink]{\obj[c]}}}}
  > {\id[{\evlcry[]{\fct[R]}{\obj[c]}}]}}\mrlap{= \bbox[LightGray]{\evlcrynat[]{\ntf[\varepsilon]}{\obj[c]}}}}}
  > \ar@{|->}[d]^{\bbox[LightGreen]{\evlbin[]{\cathom[{\cat}]}
  > {\evlcry[]{\fct[L]}{{\evlcry[]{\fct[R]}{\bbox[white]{\evlcrynat[]\op{\arr[f]}}}}}}
  > {\obj[c]}}\mrlap{{}=\evlcrynat[]{\evlbin\catcirc
  > {\evlcry[]{\fct[L]}{\evlcry[]{\fct[R]}{\bbox[white]{\evlcrynat[]\op{\arr[f]}}}}}
  >  {\wld}}
  >  {\obj[c]}}}  \\
  > {\evlcry[]{\fct[R]}{\evlcrynat[]\op{\arr[f]}}} 
  > \ar@{|->}[r]|{\evlcrynat[]{\ntf[\phi_2]}
  >  {\evlbin\cons{\evlcry[]{\fct[R]}{\obj[c']}}{\bbox[pink]{\obj[c]}}}} 
  > &
  > \evlbin[]\catcirc
  > {\evlcry[]{\fct[L]}{\evlcry[]{\fct[R]}{\bbox[white]{\evlcrynat[]\op{\arr[f]}}}}}
  > {\bbox[LightGray]{\evlcrynat[]{\ntf[\varepsilon]}{\obj[c]}}}\mrlap{{}=
  > \evlbin[]{\catcirc[{\cat[C]}]}
  > {\bbox[LightGray]{\evlcrynat[]{\ntf[\varepsilon]}{\obj[c']}}}
  > {\bbox[white]{\evlcrynat[]\op{\arr[f]}}}}
  > %\save[].[u]*+<3pt>[F-:<5pt>:ForestGreen]\frm{}\restore 
  > \\
  > {\id[{\evlcry[]{\fct[R]}{\obj[c']}}]} 
  > \ar@{|->}[u]^{\bbox[LightGreen]{\evlbin[]{\cathom[{\cat[D]}]}
  > {\evlcry[]{\fct[R]}{\obj[c']}}
  > {\evlcry[]{\fct[R]}{\bbox[white]{\evlcrynat[]\op{\arr[f]}}}}}}
  > \ar@{|->}[r]_{\evlcrynat[]{\ntf[\phi_2]}
  > {\evlbin\cons{\evlcry[]{\fct[R]}{\obj[c']}}{\bbox[pink]{\obj[c']}}}} 
  > &
  > {\pla\smash{\bbox[LightGray]{\evlcry[]
  > {\evlcrynat[]{\ntf[\phi_2]}
  >  {\evlbin\cons{\evlcry[]{\fct[R]}{\obj[c']}}{\bbox[pink]{\obj[c']}}}}
  > {\id[{\evlcry[]{\fct[R]}{\obj[c']}}]}}\mrlap{{}=\bbox[LightGray]{\evlcrynat[]{\ntf[\varepsilon]}{\obj[c']}}}}}
  > \ar@{|->}[u]_{\bbox[LightGreen]{\evlbin[]{\cathom[{\cat[C]}]}
  > {\evlcry[]{\fct[L]}{\evlcry[]{\fct[R]}{\obj[c']}}}
  > {\bbox[white]{\evlcrynat[]\op{\arr[f]}}}}\mrlap{{}=
  > \evlcrynat[]{\evlbin{\catcirc[{\cat[C]}]}
  >  {\wld}
  >  {\bbox[white]{\evlcrynat[]\op{\arr[f]}}}}
  >  {\evlcry{\fct[L]}{\evlcry[]{\fct[R]}{\obj[c']}}}}}
  > }\end{xy}}$
  >
  > 上方右图的第二行的第二个节点说明了一切 。这两张图
  > 其实就是反变米田引理证明的两个图拼在一起后的结果 。

----

- 这里蕴含着一个二元的自然同构 $\ntf[\phi_1]$ , 见下 :

  $\qquad\begin{aligned}[t]
  \ntf[\phi_1]:{}&
  \evlbin[]{\cathom[{
    \evlbin[]\cathom
      {\evlbin\cattimes{\cat[D]}{\cat}}
      {\catSet}}]}
    {\evlbin{\cathom}
      {\evlcry[]{\fct[L]}{\wld}}
      {\wld}}
    {\evlbin{\cathom[{\cat[D]}]}
      {\wld}
      {\evlcry[]{\fct[R]}{\wld}}}
  \\
  \evlcrynat[]{\ntf[\phi_1]}{\evlbin\cons{\wld}{\bbox[pink]{\obj[c]}}}:{}&
  \evlbin[]{\cathom[{
    \evlbin[]\cathom
      {\cat[D]}
      {\catSet}}]}
    {\evlbin{\cathom}
      {\evlcry[]{\fct[L]}{\wld}}
      {\obj[c]}}
    {\evlbin{\cathom[{\cat[D]}]}
      {\wld}
      {\evlcry[]{\fct[R]}{\obj[c]}}}
  \\
  \evlcrynat[]{\ntf[\phi_1]}{\evlbin\cons{\bbox[pink]{\obj[d]}}{\wld}}:{}&
  \evlbin[]{\cathom[{
    \evlbin[]\cathom
      {\cat}
      {\catSet}}]}
    {\evlbin{\cathom}
      {\evlcry[]{\fct[L]}{\obj[d]}}
      {\wld}}
    {\evlbin{\cathom[{\cat[D]}]}
      {\obj[d]}
      {\evlcry[]{\fct[R]}{\wld}}}
  \end{aligned}$

套用协变米田引理我们便可获得

$\qquad\evlbin[]{\catcong[\catSet]}
{\underbracket[.4pt]
  {\evlbin{\cathom[{\evlbin[]{\cathom[\catCat]}
    {\cat}
    {\catSet}}]}
      {\bbox[LightGreen]{\evlbin\cathom
        {\evlcry[]{\fct[L]}{\obj[d]}}
        {\bbox[white]{\pla\wld}}}}
      {\bbox[YellowGreen]{\evlbin{\cathom[{\cat[D]}]}
        {\obj[d]}
        {\evlcry[]{\fct[R]}{\bbox[white]{\pla\wld}}}}}}_
   {\text{一堆自然变换}}}
{\underbracket[.4pt]
  {\bbox[YellowGreen]{\evlbin{\cathom[{\cat[D]}]}
        {\obj[d]}
        {\evlcry[]{\fct[R]}{\evlcry[]{\fct[L]}{\obj[d]}}}}}_
  {\text{一堆元素}}}$

由协变米田引理的证明可知 : 对每个左侧集合中的自然同构 $\evlcrynat[]{\ntf[\phi_1]}{\evlbin\cons{\bbox[pink]{\obj[d]}}{\wld}}$ 
右侧集合中都有一个箭头与之对应 , 即 $\bbox[LightGray]{\evlcry[]{\evlcrynat[]{\ntf[\phi_1]}
  {\evlbin\cons{\bbox[pink]{\obj[d]}}{\evlcry[]{\fct[L]}{\obj[d]}}}}{\id[{\evlcry[]{\fct[L]}{\obj[d]}}]}}=\bbox[LightGray]{\evlcrynat[]{\ntf[\eta]}{\obj[d]}}$ 。如此 。

- $\ntf[\eta]:\evlbin[]{\cathom[{\evlbin[]{\cathom[\catCat]}{\cat[D]}{\cat[D]}}]}{\Id[{\cat[D]}]}{\evlbin[]{\catcirc[\catCat]}{\fct[L]}{\fct[R]}}$ 构成自然变换 。

  > 考虑任意 $\arr[g]:\evlbin[]{\cathom[{\cat[D]}]}{\obj[d]}{\obj[d']}$ :
  >
  > $\vcenter{\begin{xy}\xymatrix@!R=1cm@!C=3cm{
  > {\bbox[LightGreen]{\evlbin[]\cathom
  > {\evlcry[]{\fct[L]}{\obj[d]}}
  > {\evlcry[]{\fct[L]}{\bbox[white]{\obj[d]}}}}}
  > \ar[r]^{\evlcrynat[]
  > {\ntf[\phi_1]}
  > {\evlbin\cons
  >  {\bbox[pink]{\obj[d]}}
  >  {\evlcry[]{\fct[L]}{\obj[d]}}}} 
  > \ar[d]_{\bbox[LightGreen]{\evlbin[]\cathom
  > {\evlcry[]{\fct[L]}{\obj[d]}}
  > {\evlcry[]{\fct[L]}{\bbox[white]{\arr[g]}}}}}
  > &
  > {\bbox[LightGreen]{\evlbin[]{\cathom[{\cat[D]}]}
  > {\obj[d]}
  > {\evlcry[]{\fct[R]}{\evlcry[]{\fct[L]}{\bbox[white]{\obj[d]}}}}}}
  > \ar[d]^{\bbox[LightGreen]{\evlbin[]{\cathom[{\cat[D]}]}
  > {\obj[d]}
  > {\evlcry[]{\fct[R]}{\evlcry[]{\fct[L]}{\bbox[white]{\arr[g]}}}}}}  
  > \\
  > {\bbox[LightGreen]{\evlbin[]\cathom
  > {\evlcry[]{\fct[L]}{\bbox[white]{\obj[d]}}}
  > {\evlcry[]{\fct[L]}{\bbox[white]{\obj[d']}}}}}
  > \ar[r]|{\evlcrynat[]
  > {\ntf[\phi_1]}
  > {\evlbin\cons
  >  {\bbox[pink]{\obj[d]}}
  >  {\evlcry[]{\fct[L]}{\obj[d']}}}}
  > &
  > {\bbox[LightGreen]{\evlbin[]{\cathom[{\cat[D]}]}
  > {\bbox[white]{\obj[d]}}
  > {\evlcry[]{\fct[R]}{\evlcry[]{\fct[L]}{\bbox[white]{\obj[d']}}}}}}
  > \\
  > {\bbox[LightGreen]{\evlbin[]\cathom
  > {\evlcry[]{\fct[L]}{\bbox[white]{\obj[d']}}}
  > {\evlcry[]{\fct[L]}{\obj[d']}}}}
  > \ar[r]_{\evlcrynat[]
  > {\ntf[\phi_1]}
  > {\evlbin\cons
  >  {\bbox[pink]{\obj[d']}}
  >  {\evlcry[]{\fct[L]}{\obj[d']}}}} 
  > \ar[u]^{\bbox[LightGreen]{\evlbin[]\cathom
  > {\evlcry[]{\fct[L]}{\bbox[white]{\arr[g]}}}
  > {\evlcry[]{\fct[L]}{\obj[d']}}}}
  > &
  > {\bbox[LightGreen]{\evlbin[]{\cathom[{\cat[D]}]}
  > {\bbox[white]{\obj[d']}}
  > {\evlcry[]{\fct[R]}{\evlcry[]{\fct[L]}{\obj[d']}}}}}
  > \ar[u]_{\bbox[LightGreen]{\evlbin[]{\cathom[{\cat[D]}]}
  > {\bbox[white]{\arr[g]}}
  > {\evlcry[]{\fct[R]}{\evlcry[]{\fct[L]}{\obj[d']}}}}}
  > }\end{xy}}
  > \qquad
  > \vcenter{\begin{xy}\xymatrix@!R=1cm@!C=3cm{
  > {\id[{\evlcry[]{\fct[L]}{\obj[d]}}]}
  > \ar@{|->}[r]^{\evlcrynat[]
  > {\ntf[\phi_1]}
  > {\evlbin\cons
  >  {\bbox[pink]{\obj[d]}}
  >  {\evlcry[]{\fct[L]}{\obj[d]}}}} 
  > \ar@{|->}[d]_{\bbox[LightGreen]{\evlbin[]\cathom
  > {\evlcry[]{\fct[L]}{\obj[d]}}
  > {\evlcry[]{\fct[L]}{\bbox[white]{\arr[g]}}}}}
  > &
  > {\pla\smash{\bbox[LightGray]{\evlcry[]{\evlcrynat[]{\ntf[\phi_1]}
  > {\evlbin\cons
  >  {\bbox[pink]{\obj[d]}}
  >  {\evlcry[]{\fct[L]}{\obj[d]}}}}
  > {\id[{\evlcry[]{\fct[L]}{\obj[d]}}]}}\mrlap{{}=
  > \bbox[LightGray]{\evlcrynat[]
  > {\ntf[\eta]}
  > {\obj[d]}}}}}
  > \ar@{|->}[d]^{\bbox[LightGreen]{\evlbin[]{\cathom[{\cat[D]}]}
  > {\obj[d]}
  > {\evlcry[]{\fct[R]}{\evlcry[]{\fct[L]}{\bbox[white]{\arr[g]}}}}}\mrlap{{}=
  > \evlcrynat[]
  > {\evlbin{\catcirc[{\cat[D]}]}
  >  {\wld}
  >  {\evlcry[]{\fct[R]}{\evlcry[]{\fct[L]}{\bbox[white]{\arr[g]}}}}}
  > {\obj[d]}}}  
  > \\
  > {\evlcry[]{\fct[L]}{\bbox[white]{\arr[g]}}}
  > \ar@{|->}[r]|{\evlcrynat[]
  > {\ntf[\phi_1]}
  > {\evlbin\cons
  >  {\bbox[pink]{\obj[d]}}
  >  {\evlcry[]{\fct[L]}{\obj[d']}}}}
  > &
  > {\evlbin[]{\catcirc[{\cat[D]}]}
  > {\bbox[LightGray]{\evlcrynat[]
  >  {\ntf[\eta]}
  >  {\obj[d]}}}
  > {\evlcry[]{\fct[R]}{\evlcry[]{\fct[L]}{\bbox[white]{\arr[g]}}}}\mrlap{{}=
  > \evlbin[]{\catcirc[{\cat[D]}]}
  > {\bbox[white]{\arr[g]}}
  > {\bbox[LightGray]{\evlcrynat[]
  >  {\ntf[\eta]}
  >  {\obj[d']}}}
  > }}
  > \\
  > {\id[{\evlcry[]{\fct[L]}{\obj[d']}}]}
  > \ar@{|->}[r]_{\evlcrynat[]
  > {\ntf[\phi_1]}
  > {\evlbin\cons
  >  {\bbox[pink]{\obj[d']}}
  >  {\evlcry[]{\fct[L]}{\obj[d']}}}} 
  > \ar@{|->}[u]^{\bbox[LightGreen]{\evlbin[]\cathom
  > {\evlcry[]{\fct[L]}{\bbox[white]{\arr[g]}}}
  > {\evlcry[]{\fct[L]}{\obj[d']}}}}
  > &
  > {\pla\smash{\bbox[LightGray]{\evlcry[]{\evlcrynat[]{\ntf[\phi_1]}
  > {\evlbin\cons
  >  {\bbox[pink]{\obj[d']}}
  >  {\evlcry[]{\fct[L]}{\obj[d']}}}}
  > {\id[{\evlcry[]{\fct[L]}{\obj[d']}}]}}\mrlap{{}=
  > \bbox[LightGray]{\evlcrynat[]
  > {\ntf[\eta]}
  > {\obj[d']}}}}}
  > \ar@{|->}[u]_{\bbox[LightGreen]{\evlbin[]{\cathom[{\cat[D]}]}
  > {\bbox[white]{\arr[g]}}
  > {\evlcry[]{\fct[R]}{\evlcry[]{\fct[L]}{\obj[d']}}}}\mrlap{{}=
  > \evlcrynat[]
  > {\evlbin{\catcirc[{\cat[D]}]}
  >  {\bbox[white]{\arr[g]}}
  >  {\wld}}
  > {\evlcry{\fct[R]}{\evlcry[]{\fct[L]}{\obj[d']}}}}}
  > }\end{xy}}
  > $
  >
  > 上方右图的第二行的第二个节点说明了一切 。这两张图
  > 其实就是协变米田引理证明的两个图拼在一起后的结果 。

<div style="page-break-after: always"></div>

对于前面的 $\ntf[\varepsilon]$ 和 $\ntf[\eta]$ 我们有下述交换图成立 :

- $\vcenter{\begin{xy}\xymatrix@!C=2cm{
  {\fct[L]}
  \ar[dr]_{\I[{\fct[L]}]}
  \ar[r]^{\evlbin[]{\catcirc[???]}{\ntf[\eta]}{\I[{\fct[L]}]}}
  &
  {\evlbin[]{\catcirc[\catCat]}
    {\fct[L]}
    {\evlbin[]{\catcirc[\catCat]}
      {\fct[R]}
      {\fct[L]}}}
  \ar[d]^{\evlbin[]{\catcirc[???]}{\I[{\fct[L]}]}{\ntf[\varepsilon]}}
  \\
  &
  {\fct[L]}
  }\end{xy}}$ $\qquad\vcenter{\begin{xy}\xymatrix@!R=1cm@!C=2cm{ 
  \cat
  \ar@{<-}@`{[]+/l+3pc/,[d]+/l+3pc/}[d]^(.5){}="midb1"|{\fct[L]}
  \ar@{<-}@`{[]+/r+3pc/,[d]+/r+3pc/}[d]_(.5){}="midb2"|{\fct[L]}
  \ar@2{>} "midb1";"midb2"^{\I[{\fct[L]}]}
  \\
  \cat[D]
  \ar@{<-}@`{[]+/l+3pc/,[d]+/l+3pc/}[d]^(.5){}="mida1"|{\Id[{\cat[D]}]}
  \ar@{<-}@`{[]+/r+3pc/,[d]+/r+3pc/}[d]_(.5){}="mida2"|{{\evlbin[]{\catcirc[\catCat]}
      {\fct[L]}
      {\fct[R]}}}
  \ar@2{>} "mida1";"mida2"^{{\ntf[\eta]}}
  \\
  \cat[D]
  \\
  }\end{xy}}
  \quad 
  \vcenter{\begin{xy}\xymatrix@!R=1cm@!C=2cm{ 
  \cat[C]
  \ar@{<-}@`{[]+/l+3pc/,[d]+/l+3pc/}[d]^(.5){}="midb1"|{{\evlbin[]{\catcirc[\catCat]}
      {\fct[R]}
      {\fct[L]}}}
  \ar@{<-}@`{[]+/r+3pc/,[d]+/r+3pc/}[d]_(.5){}="midb2"|{\Id[{\cat[C]}]}
  \ar@2{>} "midb1";"midb2"^{\ntf[\varepsilon]}
  \\
  \cat
  \ar@{<-}@`{[]+/l+3pc/,[d]+/l+3pc/}[d]^(.5){}="mida1"|{\fct[L]}
  \ar@{<-}@`{[]+/r+3pc/,[d]+/r+3pc/}[d]_(.5){}="mida2"|{\fct[L]}
  \ar@2{>} "mida1";"mida2"^{\I[{\fct[L]}]}
  \\
  \cat[D]
  }\end{xy}}$

- $\vcenter{\begin{xy}\xymatrix@!C=2cm{
  {\fct[R]}
  \ar[dr]_{\I[{\fct[R]}]}
  \ar[r]^{\evlbin[]{\catcirc[???]}{\I[{\fct[R]}]}{\ntf[\eta]}}
  &
  {\evlbin[]{\catcirc[\catCat]}
    {\fct[R]}
    {\evlbin[]{\catcirc[\catCat]}
      {\fct[L]}
      {\fct[R]}}}
  \ar[d]^{\evlbin[]{\catcirc[???]}{\ntf[\varepsilon]}{\I[{\fct[R]}]}}
  \\
  &
  {\fct[R]}
  }\end{xy}}$ $\qquad\vcenter{\begin{xy}\xymatrix@!R=1cm@!C=2cm{ 
  \cat[D]
  \ar@{<-}@`{[]+/l+3pc/,[d]+/l+3pc/}[d]^(.5){}="mida1"|{\Id[{\cat[D]}]}
  \ar@{<-}@`{[]+/r+3pc/,[d]+/r+3pc/}[d]_(.5){}="mida2"|{{\evlbin[]{\catcirc[\catCat]}
      {\fct[L]}
      {\fct[R]}}}
  \\
  \cat[D]
  \ar@2{>} "mida1";"mida2"^{{\ntf[\eta]}}
  \ar@{<-}@`{[]+/l+3pc/,[d]+/l+3pc/}[d]^(.5){}="midb1"|{\fct[R]}
  \ar@{<-}@`{[]+/r+3pc/,[d]+/r+3pc/}[d]_(.5){}="midb2"|{\fct[R]}
  \\
  \cat
  \ar@2{>} "midb1";"midb2"^{\I[{\fct[R]}]}
  }\end{xy}}
  \quad \vcenter{\begin{xy}\xymatrix@!R=1cm@!C=2cm{ 
  \cat[D]
  \ar@{<-}@`{[]+/l+3pc/,[d]+/l+3pc/}[d]^(.5){}="mida1"|{\fct[R]}
  \ar@{<-}@`{[]+/r+3pc/,[d]+/r+3pc/}[d]_(.5){}="mida2"|{\fct[R]}
  \\
  \cat[C]
  \ar@2{>} "mida1";"mida2"^{\I[{\fct[R]}]}
  \ar@{<-}@`{[]+/l+3pc/,[d]+/l+3pc/}[d]^(.5){}="midb1"|{{\evlbin[]{\catcirc[\catCat]}
      {\fct[R]}
      {\fct[L]}}}
  \ar@{<-}@`{[]+/r+3pc/,[d]+/r+3pc/}[d]_(.5){}="midb2"|{\Id[{\cat[C]}]}
  \\
  \cat
  \ar@2{>} "midb1";"midb2"^{\ntf[\varepsilon]}
  }\end{xy}}$

### 伴随函子的第二种定义

假设我们不知道 $\fct[L]$ 和 $\fct[R]$ 构成一对伴随函子并且有自然变换 
 $\ntf[\varepsilon]:\evlbin[]{\cathom[{\evlbin[]{\cathom[\catCat]}{\cat[C]}{\cat[C]}}]}{\evlbin[]{\catcirc[\catCat]}{\fct[R]}{\fct[L]}}{\Id[{\cat[C]}]}$ 和 $\ntf[\eta]:\evlbin[]{\cathom[{\evlbin[]{\cathom[\catCat]}{\cat[D]}{\cat[D]}}]}{\Id[{\cat[D]}]}{\evlbin[]{\catcirc[\catCat]}{\fct[L]}{\fct[R]}}$ 能同时满足
上页开头的两幅交换图 , 即

 $\qquad \vcenter{\begin{xy}\xymatrix@!C=2cm{
{\fct[L]}
\ar[dr]_{\I[{\fct[L]}]}
\ar[r]^{\evlbin[]{\catcirc[???]}{\ntf[\eta]}{\I[{\fct[L]}]}}
&
{\evlbin[]{\catcirc[\catCat]}
  {\fct[L]}
  {\evlbin[]{\catcirc[\catCat]}
    {\fct[R]}
    {\fct[L]}}}
\ar[d]^{\evlbin[]{\catcirc[???]}{\I[{\fct[L]}]}{\ntf[\varepsilon]}}
\\
&
{\fct[L]}
}\end{xy}}$ $\qquad\vcenter{\begin{xy}\xymatrix@!C=2cm{
{\fct[R]}
\ar[dr]_{\I[{\fct[R]}]}
\ar[r]^{\evlbin[]{\catcirc[???]}{\I[{\fct[R]}]}{\ntf[\eta]}}
&
{\evlbin[]{\catcirc[\catCat]}
  {\fct[R]}
  {\evlbin[]{\catcirc[\catCat]}
    {\fct[L]}
    {\fct[R]}}}
\ar[d]^{\evlbin[]{\catcirc[???]}{\ntf[\varepsilon]}{\I[{\fct[R]}]}}
\\
&
{\fct[R]}
}\end{xy}}$

那么

- 对任意 $\cat$ 中对象 $\obj[c]$ 
  及任意 $\cat[D]$ 中对象 $\obj[d]$ 
  及任意 $\evlcrynat[]\op{\arr[\varphi]}:\evlbin[]{\cathom[{\cat[C]}]}{\evlcry[]{\fct[L]}{\obj[d]}}{\obj[c]}$ 始终存在
  唯一的 $\arr[\gamma]:\evlbin[]{\cathom[{\cat[D]}]}{\obj[d]}{\evlcry[]{\fct[R]}{\obj[c]}}$ 使下图交换 。
  如此有 $\evlbin[]{\catcong[\catSet]}{\evlbin{\cathom}
      {\evlcry[]{\fct[L]}{\obj[d]}}
      {\obj[c]}}
    {\evlbin{\cathom[{\cat[D]}]}
      {\obj[d]}
      {\evlcry[]{\fct[R]}{\obj[c]}}}$ 。
  
  $\vcenter{\begin{xy}\xymatrix@!C=2cm{
  {\evlcry[]{\fct[R]}{\obj[c]}}
  & 
  {\evlcry[]{\fct[L]}{\evlcry[]{\fct[R]}{\obj[c]}}} 
  \ar[r]^{\evlcrynat[]{\ntf[\varepsilon]}{\obj[c]}} 
  &
  {\obj[c]}
  \ar@{->}@`{[]+/u+3pc/,[ll]+/u+3pc/}[ll]_{\fct[R]}
  \\ 
  {\obj[d]}
  \ar@[red]@{-->}[u]^[red]{\arr[\gamma]}
  \ar@{->}@`{[]+/d+2pc/,[r]+/d+2pc/}[r]_{\fct[L]}
  \save[].[u]*+<3pt>[F-:<5pt>:ForestGreen]\frm{}
  !R*!L{\small\color{ForestGreen}\cat[D]}\restore
  &  
  {\evlcry[]{\fct[L]}
    {\obj[d]}}  
  \ar@[red]@{-->}[u]^[red]{\evlcry[]{\fct[L]}{\arr[\gamma]}}
  \ar@[magenta][ur]_[magenta]{\evlcrynat[]\op{\arr[\varphi]}}
  \save[].[u].[ur]*+<3pt>[F-:<5pt>:ForestGreen]\frm{}
  !R*!L{\small\color{ForestGreen}\cat}\restore
  &
  }\end{xy}}$ 
  
- 对任意 $\cat$ 中对象 $\obj[c]$ 
  及任意 $\cat[D]$ 中对象 $\obj[d]$ 
  及任意 $\arr[\gamma]:\evlbin[]{\cathom[{\cat[D]}]}{\obj[d]}{\evlcry[]{\fct[R]}{\obj[c]}}$ 始终都会存在
  唯一的 $\evlcrynat[]\op{\arr[\varphi]}:\evlbin[]{\cathom[{\cat[C]}]}{\evlcry[]{\fct[L]}{\obj[d]}}{\obj[c]}$ 使下图交换 。
  如此有 $\evlbin[]{\catcong[\catSet]}{\evlbin{\cathom}
      {\evlcry[]{\fct[L]}{\obj[d]}}
      {\obj[c]}}
    {\evlbin{\cathom[{\cat[D]}]}
      {\obj[d]}
      {\evlcry[]{\fct[R]}{\obj[c]}}}  $ 。
  
  $\vcenter{\begin{xy}\xymatrix@!C=2cm{
  {\evlcry[]{\fct[L]}{\obj[d]}}
  \ar@{-->}@[red][d]_[red]{\evlcrynat[]\op{\arr[\varphi]}} 
  & 
  {\evlcry[]{\fct[R]}{
    \evlcry[]{\fct[L]}
      {\obj[d]}}}
  \ar@[red]@{-->}[d]_[red]{\evlcry[]{\fct[R]}{\evlcrynat[]\op{\arr[\varphi]}}}
  &
  {\obj[d]}
  \ar@[magenta][dl]^[magenta]{\arr[\gamma]}  
  \ar[l]_{\evlcrynat[]{\ntf[\eta]}{\obj[d]}}
  \ar@{->}@`{[]+/u+3pc/,[ll]+/u+3pc/}[ll]_{\fct[L]} 
  \\ 
  {\obj[c]}
  \ar@{->}@`{[]+/d+2pc/,[r]+/d+2pc/}[r]_{\fct[R]} 
  \save[].[u]*+<3pt>[F-:<5pt>:ForestGreen]\frm{}!R*!L
  {\small\color{ForestGreen}\cat}\restore
  &  
  {\evlcry[]{\fct[R]}
    {\obj[c]}} 
  \save[].[u].[ur]*+<3pt>[F-:<5pt>:ForestGreen]\frm{}!R*!L
  {\small\color{ForestGreen}\cat[D]}\restore
  &
  }\end{xy}}$ 

<div style="page-break-after: always"></div>

> 现证明上页的头两条定理 。
>
> 我们将下图称作图 1 。图 1 上半部分即为上页第一幅图 ,  而
> 图 1 下半部分可由 $\ntf[\varepsilon]$ 为自然变换得出 。两图拼在一起即可得
> 图 1 右侧部分 。
> 
>$\qquad\begin{array}{c}
> \vcenter{\begin{xy}\xymatrix@!R=1cm@!C=2cm{
> {\evlcry[]{\fct[L]}{\obj[d]}}
> \ar[d]_{\evlcry[]{\fct[L]}{\evlcrynat[]{\ntf[\eta]}{\obj[d]}}}
> \ar[dr]^{\id[{\evlcry[]{\fct[L]}{\obj[d]}}]}
> \\
> {\evlcry[]{\fct[L]}
> {\evlcry[]
> {\fct[R]}
> {\evlcry[]
> {\fct[L]}
> {\obj[d]}}}}
>   \ar[r]_{\evlcrynat[]{\ntf[\varepsilon]}
> {\evlcry{\fct[L]}{\obj[d]}}} 
> &
> \evlcry[]{\fct[L]}
> {\obj[d]}
> \save[].[l].[lu]*+<3pt>[F-:<5pt>:ForestGreen]\frm{}
> !R*!L{\small\color{ForestGreen}\cat}\restore
> }\end{xy}}
> \\
> \vcenter{\begin{xy}\xymatrix@!R=1cm@!C=2cm{
> {\bbox[LightGreen]{\evlcry[]{\fct[L]}
> {\evlcry[]
> {\fct[R]}
> {\evlcry[]
> {\fct[L]}
> {\bbox[white]{\obj[d]}}}}}}
>   \ar[r]^{\evlcrynat[]{\ntf[\varepsilon]}
> {\evlcry{\fct[L]}{\obj[d]}}} 
> \ar[d]_{\bbox[LightGreen]{\evlcry[]
> {\fct[L]}
> {\evlcry[]
> {\fct[R]}
> {\bbox[white]{\evlcrynat[]\op{\arr[\varphi]}}}}}} 
> &
> {\bbox[LightGreen]{\evlcry[]{\fct[L]}
> {\bbox[white]{\obj[d]}}}}
> \ar[d]^{\bbox[white]{\evlcrynat[]\op{\arr[\varphi]}}}
> \\
> {\bbox[LightGreen]{\evlcry[]
> {\fct[L]}{\evlcry[]
> {\fct[R]}
> {\bbox[white]{\obj[c]}}}}}
> \ar[r]_{\evlcrynat[]{\ntf[\varepsilon]}
> {\obj[c]}}
> \save[].[u]*+<3pt>[F-:<5pt>:ForestGreen]\frm{}
> !D*!U{\small\color{ForestGreen}\bbox[LightGreen]{
> \evlcry[]{\fct[L]}{\evlcry[]{\fct[R]}
> {\cat[C]}}}}\restore 
> \save[].[u].[ur]*+<10pt>[F-:<8pt>:ForestGreen]\frm{}
> !R*!L{\small\color{ForestGreen}\cat[C]}\restore 
> &
> {\pla\bbox[white]{\obj[c]}}
> \save[].[u]*+<3pt>[F-:<5pt>:ForestGreen]\frm{}
> !D*!U{\small\color{ForestGreen}\bbox[LightGreen]{
> \evlcry[]{\Id[{\cat[C]}]}
> {\cat[C]}}}\restore 
> }\end{xy}}
> \end{array} \vcenter{{}\Longrightarrow{}} \vcenter{\begin{xy}\xymatrix@!R=1cm@!C=2cm{
> {\obj[d]}
> \ar[d]_{\evlcrynat[]{\ntf[\eta]}{\obj[d]}}
> \ar@{->}@`{[]+/u+2pc/,[r]+/u+2pc/}[r]^{\fct[L]}
> \ar@{->}@`{[]+/l+2pc/,[dd]+/l+2pc/}[dd]_{\begin{array}{l}\arr[\gamma]~或\\[-3pt]\arr[\gamma']\end{array}}
> &
> {\evlcry[]{\fct[L]}{\obj[d]}}
> \ar[d]_{\evlcry[]{\fct[L]}{\evlcrynat[]{\ntf[\eta]}{\obj[d]}}}
> \ar[dr]^{\id[{\evlcry[]{\fct[L]}{\obj[d]}}]}
> \ar@[red]@{->}@`{[]+/l+2pc/,[dd]+/l+2pc/}[dd]_{\begin{array}{l}\evlcry[]{\fct[L]}{\arr[\gamma]}~或\\[-3pt]\evlcry[]{\fct[L]}{\arr[\gamma']}\end{array}}
> \\
> {\evlcry[]
> {\fct[R]}
> {\evlcry[]
> {\fct[L]}
> {\obj[d]}}}
> \ar[d]_{\begin{array}{l}
> \evlcry[]{\fct[R]}{\evlcrynat[]\op{\arr[\varphi]}}%~或\\[-3pt]
> %\evlcry[]{\fct[R]}{\evlcrynat[]\op{\arr[\varphi']}}
> \end{array}}
> &
> {\evlcry[]{\fct[L]}
> {\evlcry[]
> {\fct[R]}
> {\evlcry[]
> {\fct[L]}
> {\obj[d]}}}}
>   \ar[r]|{\evlcrynat[]{\ntf[\varepsilon]}
> {\evlcry{\fct[L]}{\obj[d]}}} 
> \ar[d]_{\begin{array}{l}
> \evlcry[]{\fct[L]}{\evlcry[]{\fct[R]}{\evlcrynat[]\op{\arr[\varphi]}}}%~或\\[-3pt]
> %\evlcry[]{\fct[L]}{\evlcry[]{\fct[R]}{\evlcrynat[]\op{\arr[\varphi']}}}
> \end{array}}
> &
> \evlcry[]{\fct[L]}
> {\obj[d]}
> \ar[d]^{\begin{array}{l}
> \evlcrynat[]\op{\arr[\varphi]}%~或\\[-3pt]
> %\evlcrynat[]\op{\arr[\varphi']}
> \end{array}}
> \\
> \evlcry[]
> {\fct[R]}
> {\obj[c]}
> \save[].[u].[uu]*+<3pt>[F-:<5pt>:ForestGreen]\frm{}
> !R*!L{\small\color{ForestGreen}\cat[D]}\restore
> &
> \evlcry[]
> {\fct[L]}{\evlcry[]
> {\fct[R]}
> {\obj[c]}}
> \ar@[red][r]_{\evlcrynat[]{\ntf[\varepsilon]}
> {\obj[c]}}
> &
> {\obj[c]}
> \ar@{->}@`{[]+/d+3pc/,[ll]+/d+3pc/}[ll]^{\fct[R]}
> \save[].[u].[ul].[ulu]*+<3pt>[F-:<5pt>:ForestGreen]\frm{}
> !R*!L{\small\color{ForestGreen}\cat}\restore
> }\end{xy}}$
> 
>我们将下图称作图 2 。图 2 下半部分即为上页第二幅图 ,  而
> 图 2 上半部分可由 $\ntf[\eta]$ 为自然变换得出 。两图拼在一起即可得
> 图 2 右侧部分 。
> 
> $\qquad\begin{array}{c}
>\vcenter{\begin{xy}\xymatrix@!R=1cm@!C=2cm{
> {\pla\bbox[white]{\obj[d]}}
> \ar[r]^{\evlcrynat[]{\ntf[\eta]}
> {\obj[c]}}
> \ar[d]_{\bbox[white]{\arr[\gamma]}}
> &
> {\bbox[LightGreen]{\evlcry[]
> {\fct[R]}{\evlcry[]
> {\fct[L]}
> {\bbox[white]{\obj[d]}}}}}
> \ar[d]^{\bbox[LightGreen]{\evlcry[]
> {\fct[R]}
> {\evlcry[]
> {\fct[L]}
> {\bbox[white]{\arr[\gamma]}}}}}
> \\
> {\bbox[LightGreen]{\evlcry[]{\fct[R]}
> {\bbox[white]{\obj[c]}}}}
> \ar[r]_{\evlcrynat[]{\ntf[\eta]}
> {\evlcry{\fct[R]}{\obj[c]}}} 
> \save[].[u]*+<3pt>[F-:<5pt>:ForestGreen]\frm{}
> !U*!D{\small\color{ForestGreen}\bbox[LightGreen]{
> \evlcry[]{\Id[{\cat[D]}]}
> {\cat[D]}}}\restore 
> &
> {\bbox[LightGreen]{\evlcry[]{\fct[R]}
> {\evlcry[]
> {\fct[L]}
> {\evlcry[]
> {\fct[R]}
> {\bbox[white]{\obj[c]}}}}}}
> \save[].[u]*+<3pt>[F-:<5pt>:ForestGreen]\frm{}
>   !U*!D{\small\color{ForestGreen}\bbox[LightGreen]{
> \evlcry[]{\fct[R]}{\evlcry[]{\fct[L]}
> {\cat[D]}}}}\restore 
> \save[].[u].[l]*+<10pt>[F-:<8pt>:ForestGreen]\frm{}
> !R*!L{\small\color{ForestGreen}\cat[D]}\restore 
> }\end{xy}}
> \\
> \vcenter{\begin{xy}\xymatrix@!R=1cm@!C=2cm{
> \evlcry[]{\fct[R]}
> {\obj[c]}
> \ar[r]^{\evlcrynat[]{\ntf[\eta]}
> {\evlcry{\fct[R]}{\obj[c]}}}
> \ar[dr]_{\id[{\evlcry[]{\fct[R]}{\obj[c]}}]}
> &
> {\evlcry[]{\fct[R]}
> {\evlcry[]
> {\fct[L]}
> {\evlcry[]
> {\fct[R]}
> {\obj[c]}}}}
> \ar[d]^{\evlcry[]{\fct[R]}{\evlcrynat[]{\ntf[\varepsilon]}{\obj[c]}}}
>   \\
> &
> {\evlcry[]{\fct[R]}{\obj[c]}}
> \save[].[u].[ul]*+<3pt>[F-:<5pt>:ForestGreen]\frm{}
> !R*!L{\small\color{ForestGreen}\cat[D]}\restore
> }\end{xy}}
> \end{array} \vcenter{{}\Longrightarrow{}}\qquad 
> \vcenter{\begin{xy}\xymatrix@!R=1cm@!C=2cm{
> {\pla\obj[d]}
> \ar[r]^{\evlcrynat[]{\ntf[\eta]}
> {\obj[c]}}
> \ar[d]_{\begin{array}{l}
> \arr[\gamma]~或\\[-3pt]
> \arr[\gamma']
> \end{array}}
> \ar@`{[]+/u+3pc/,[rr]+/u+3pc/}[rr]^{\fct[L]}
> &
> {\evlcry[]
> {\fct[R]}{\evlcry[]
> {\fct[L]}
> {\obj[d]}}}
> \ar@[red][d]^{\begin{array}{l}
> \evlcry[]{\fct[R]}{\evlcry[]{\fct[L]}{\arr[\gamma]}}~或\\[-3pt]
> \evlcry[]{\fct[R]}{\evlcry[]{\fct[L]}{\arr[\gamma']}}
> \end{array}}
> \ar@`{[]+/r+2pc/,[dd]+/r+2pc/}[dd]^{\begin{array}{l}
> \evlcry[]{\fct[R]}{\evlcrynat[]\op{\arr[\varphi]}}%~或\\[-3pt]
> %\evlcrynat[]\op{\arr[\varphi']}
> \end{array}}
> &
> {\evlcry[]{\fct[L]}{\obj[d]}}
> \ar[d]^{\evlcry[]{\fct[L]}{\arr[\gamma]}}
> \ar@{->}@`{[]+/r+2pc/,[dd]+/r+2pc/}[dd]^{\begin{array}{l}
> \evlcrynat[]\op{\arr[\varphi]}%~或\\[-3pt]
> %\evlcrynat[]\op{\arr[\varphi']}
> \end{array}}
> \\
> \evlcry[]{\fct[R]}
> {\obj[c]}
> \ar[r]|{\evlcrynat[]{\ntf[\eta]}
> {\evlcry{\fct[R]}{\obj[c]}}}
> \ar[dr]_{\id[{\evlcry[]{\fct[R]}{\obj[c]}}]}
> &
> {\evlcry[]{\fct[R]}
> {\evlcry[]
> {\fct[L]}
> {\evlcry[]
> {\fct[R]}
> {\obj[c]}}}}
> \ar@[red][d]^{\evlcry[]{\fct[R]}{\evlcrynat[]{\ntf[\varepsilon]}{\obj[c]}}}
>   &
> {\evlcry[]
> {\fct[L]}{\evlcry[]
> {\fct[R]}
> {\obj[c]}}}
> \ar[d]^{\evlcrynat[]{\ntf[\varepsilon]}{\obj[c]}}
> \\
> &
> {\evlcry[]{\fct[R]}{\obj[c]}}
> \save[].[u].[ul].[uul]*+<3pt>[F-:<5pt>:ForestGreen]\frm{}
> !R*!L{\small\color{ForestGreen}\cat[D]}\restore
> &
> {\obj[c]}
> \ar@`{[]+/d+2pc/,[l]+/d+2pc/}[l]^{\fct[R]}
> \save[].[u].[uu]*+<3pt>[F-:<5pt>:ForestGreen]\frm{}
> !R*!L{\small\color{ForestGreen}\cat[C]}\restore
> }\end{xy}}$ 
> 
> 为何 $\arr[\gamma]$ 唯一呢 ?  若 $\arr[\gamma']$ 亦满足上图 —— 即不论是 $\arr[\gamma]$ 还是 $\arr[\gamma']$
>图 1 右侧部分中 L 形走向红色路径的复合结果都为 $\evlcrynat[]\op{\arr[\varphi]}$ ; 故
> 图 2 右侧部分中红色路径的复合结果也是一致的 ; 如此根据
> 图 2 右侧部分即可知 $\arr[\gamma]=\arr[\gamma']$ 。
> 
> 另一侧同理 , 这里不再赘述 。

<div style="page-break-after: always"></div>

### 伴随函子的第三种定义

假设我们不知道 $\fct[L]$ 和 $\fct[R]$ 构成一对伴随函子并且有自然变换 
 $\ntf[\varepsilon]:\evlbin[]{\cathom[{\evlbin[]{\cathom[\catCat]}{\cat[C]}{\cat[C]}}]}{\evlbin[]{\catcirc[\catCat]}{\fct[R]}{\fct[L]}}{\Id[{\cat[C]}]}$ 和 $\ntf[\eta]:\evlbin[]{\cathom[{\evlbin[]{\cathom[\catCat]}{\cat[D]}{\cat[D]}}]}{\Id[{\cat[D]}]}{\evlbin[]{\catcirc[\catCat]}{\fct[L]}{\fct[R]}}$ , 那么我们有

- 若对任意 $\cat$ 中对象 $\obj[c]$ 
  及对任意 $\cat[D]$ 中对象 $\obj[d]$ 
  及对任意 $\evlcrynat[]\op{\arr[\varphi]}:\evlbin[]{\cathom[{\cat[C]}]}{\evlcry[]{\fct[L]}{\obj[d]}}{\obj[c]}$ 始终都会
  有唯一的 $\arr[\gamma]:\evlbin[]{\cathom[{\cat[D]}]}{\obj[d]}{\evlcry[]{\fct[R]}{\obj[c]}}$ 使下图交换 , 
  
  $\qquad\vcenter{\begin{xy}\xymatrix@!C=2cm{
  {\evlcry[]{\fct[R]}{\obj[c]}}
  & 
  {\evlcry[]{\fct[L]}{\evlcry[]{\fct[R]}{\obj[c]}}} 
  \ar[r]^{\evlcrynat[]{\ntf[\varepsilon]}{\obj[c]}} 
  &
  {\obj[c]}
  \ar@{->}@`{[]+/u+3pc/,[ll]+/u+3pc/}[ll]_{\fct[R]}
  \\ 
  {\obj[d]}
  \ar@[red]@{-->}[u]^[red]{\arr[\gamma]}
  \ar@{->}@`{[]+/d+2pc/,[r]+/d+2pc/}[r]_{\fct[L]}
  \save[].[u]*+<3pt>[F-:<5pt>:ForestGreen]\frm{}
  !R*!L{\small\color{ForestGreen}\cat[D]}\restore
  &  
  {\evlcry[]{\fct[L]}
    {\obj[d]}}  
  \ar@[red]@{-->}[u]^[red]{\evlcry[]{\fct[L]}{\arr[\gamma]}}
  \ar@[magenta][ur]_[magenta]{\evlcrynat[]\op{\arr[\varphi]}}
  \save[].[u].[ur]*+<3pt>[F-:<5pt>:ForestGreen]\frm{}
  !R*!L{\small\color{ForestGreen}\cat}\restore
  &
  }\end{xy}}$
  
  那么
  
  $\qquad\begin{aligned}[t]
  \ntf[\phi_2]:{}&
  \evlbin[]{\cathom[{
    \evlbin[]\cathom
      {\evlbin\cattimes{\cat[D]}{\cat}}
      {\catSet}}]}
    {\evlbin{\cathom[{\cat[D]}]}
      {\wld}
      {\evlcry[]{\fct[R]}{\wld}}}
    {\evlbin{\cathom}
      {\evlcry[]{\fct[L]}{\wld}}
      {\wld}}
  \\
  \evlcrynat[]{\ntf[\phi_2]}{\evlbin\cons{\wld}{\bbox[pink]{\obj[c]}}}:{}&
  \evlbin[]{\cathom[{
    \evlbin[]\cathom
      {\cat[D]}
      {\catSet}}]}
    {\evlbin{\cathom[{\cat[D]}]}
      {\wld}
      {\evlcry[]{\fct[R]}{\obj[c]}}}
    {\evlbin{\cathom}
      {\evlcry[]{\fct[L]}{\wld}}
      {\obj[c]}}
  \\
  \evlcrynat[]{\ntf[\phi_2]}{\evlbin\cons{\bbox[pink]{\obj[d]}}{\wld}}:{}&
  \evlbin[]{\cathom[{
    \evlbin[]\cathom
      {\cat}
      {\catSet}}]}
    {\evlbin{\cathom[{\cat[D]}]}
      {\obj[d]}
      {\evlcry[]{\fct[R]}{\wld}}}
    {\evlbin{\cathom}
      {\evlcry[]{\fct[L]}{\obj[d]}}
      {\wld}}
  \end{aligned}$
  
  将构成自然同构 。
  
- 若对任意 $\cat$ 中对象 $\obj[c]$ 
  及对任意 $\cat[D]$ 中对象 $\obj[d]$ 
  及对任意 $\arr[\gamma]:\evlbin[]{\cathom[{\cat[D]}]}{\obj[d]}{\evlcry[]{\fct[R]}{\obj[c]}}$ 始终都存在
  唯一的 $\evlcrynat[]\op{\arr[\varphi]}:\evlbin[]{\cathom[{\cat[C]}]}{\evlcry[]{\fct[L]}{\obj[d]}}{\obj[c]}$ 使下图交换 , 

  $\qquad\vcenter{\begin{xy}\xymatrix@!C=2cm{
  {\evlcry[]{\fct[L]}{\obj[d]}}
  \ar@{-->}@[red][d]_[red]{\evlcrynat[]\op{\arr[\varphi]}} 
  & 
  {\evlcry[]{\fct[R]}{
    \evlcry[]{\fct[L]}
      {\obj[d]}}}
  \ar@[red]@{-->}[d]_[red]{\evlcry[]{\fct[R]}{\evlcrynat[]\op{\arr[\varphi]}}}
  &
  {\obj[d]}
  \ar@[magenta][dl]^[magenta]{\arr[\gamma]}  
  \ar[l]_{\evlcrynat[]{\ntf[\eta]}{\obj[d]}}
  \ar@{->}@`{[]+/u+3pc/,[ll]+/u+3pc/}[ll]_{\fct[L]} 
  \\ 
  {\obj[c]}
  \ar@{->}@`{[]+/d+2pc/,[r]+/d+2pc/}[r]_{\fct[R]} 
  \save[].[u]*+<3pt>[F-:<5pt>:ForestGreen]\frm{}!R*!L
  {\small\color{ForestGreen}\cat}\restore
  &  
  {\evlcry[]{\fct[R]}
    {\obj[c]}} 
  \save[].[u].[ur]*+<3pt>[F-:<5pt>:ForestGreen]\frm{}!R*!L
  {\small\color{ForestGreen}\cat[D]}\restore
  &
  }\end{xy}}$

  那么

  $\qquad\begin{aligned}[t]
  \ntf[\phi_1]:{}&
  \evlbin[]{\cathom[{
    \evlbin[]\cathom
      {\evlbin\cattimes{\cat[D]}{\cat}}
      {\catSet}}]}
    {\evlbin{\cathom}
      {\evlcry[]{\fct[L]}{\wld}}
      {\wld}}
    {\evlbin{\cathom[{\cat[D]}]}
      {\wld}
      {\evlcry[]{\fct[R]}{\wld}}}
  \\
  \evlcrynat[]{\ntf[\phi_1]}{\evlbin\cons{\wld}{\bbox[pink]{\obj[c]}}}:{}&
  \evlbin[]{\cathom[{
    \evlbin[]\cathom
      {\cat[D]}
      {\catSet}}]}
    {\evlbin{\cathom}
      {\evlcry[]{\fct[L]}{\wld}}
      {\obj[c]}}
    {\evlbin{\cathom[{\cat[D]}]}
      {\wld}
      {\evlcry[]{\fct[R]}{\obj[c]}}}
  \\
  \evlcrynat[]{\ntf[\phi_1]}{\evlbin\cons{\bbox[pink]{\obj[d]}}{\wld}}:{}&
  \evlbin[]{\cathom[{
    \evlbin[]\cathom
      {\cat}
      {\catSet}}]}
    {\evlbin{\cathom}
      {\evlcry[]{\fct[L]}{\obj[d]}}
      {\wld}}
    {\evlbin{\cathom[{\cat[D]}]}
      {\obj[d]}
      {\evlcry[]{\fct[R]}{\wld}}}
  \end{aligned}$

  将构成自然同构 。

<div style="page-break-after: always"></div>

$\qquad\begin{array}{c}
\vcenter{\begin{xy}\xymatrix@!R=1cm@!C=2cm{
{\evlcry[]{\fct[L]}{\obj[d]}}
\ar[d]_{\evlcry[]{\fct[L]}{\evlcrynat[]{\ntf[\eta]}{\obj[d]}}}
\ar[dr]^{\evlcrynat[]\op{\arr[\varphi]}}
\\
{\evlcry[]{\fct[L]}
{\evlcry[]
{\fct[R]}
{\obj[c]}}}
\ar[r]_{\evlcrynat[]{\ntf[\varepsilon]}
{\obj[c]}} 
&
{\obj[c]}
\save[].[l].[lu]*+<3pt>[F-:<5pt>:ForestGreen]\frm{}
!R*!L{\small\color{ForestGreen}\cat}\restore
}\end{xy}}
\\
\vcenter{\begin{xy}\xymatrix@!R=1cm@!C=2cm{
{\bbox[LightGreen]{\evlcry[]{\fct[L]}
{\evlcry[]
{\fct[R]}
{\bbox[white]{\obj[c]}}}}}
\ar[r]^{\evlcrynat[]{\ntf[\varepsilon]}
{\obj[c]}} 
\ar[d]_{\bbox[LightGreen]{\evlcry[]
{\fct[L]}
{\evlcry[]
{\fct[R]}
{\bbox[white]{\arr[f]}}}}} 
&
{\bbox[white]{\obj[c]}}
\ar[d]^{\bbox[white]{\arr[f]}}
\\
{\bbox[LightGreen]{\evlcry[]
{\fct[L]}{\evlcry[]
{\fct[R]}
{\bbox[white]{\obj[c']}}}}}
\ar[r]_{\evlcrynat[]{\ntf[\varepsilon]}
{\obj[c']}}
\save[].[u]*+<3pt>[F-:<5pt>:ForestGreen]\frm{}
!D*!U{\small\color{ForestGreen}\bbox[LightGreen]{
\evlcry[]{\fct[L]}{\evlcry[]{\fct[R]}
{\cat[C]}}}}\restore 
\save[].[u].[r]*+<10pt>[F-:<8pt>:ForestGreen]\frm{}
!R*!L{\small\color{ForestGreen}\cat[C]}\restore 
&
{\pla\bbox[white]{\obj[c']}}
\save[].[u]*+<3pt>[F-:<5pt>:ForestGreen]\frm{}
!D*!U{\small\color{ForestGreen}\bbox[LightGreen]{
\evlcry[]{\Id[{\cat[C]}]}
{\cat[C]}}}\restore 
}\end{xy}}
\end{array} 
\vcenter{{}\Longrightarrow{}} 
\vcenter{\begin{xy}\xymatrix@!R=1cm@!C=2cm{
{\obj[d]}
\ar[d]_{\evlcrynat[]{\ntf[\eta]}{\obj[d]}}
\ar@{->}@`{[]+/u+2pc/,[r]+/u+2pc/}[r]^{\fct[L]}
\ar@{->}@`{[]+/l+2pc/,[dd]+/l+2pc/}[dd]_{\arr[\gamma]}
&
{\evlcry[]{\fct[L]}{\obj[d]}}
\ar[d]_{\evlcry[]{\fct[L]}{\evlcrynat[]{\ntf[\eta]}{\obj[d]}}}
\ar[dr]^{\evlcrynat[]\op{\arr[\varphi]}}
\ar@[red]@{->}@`{[]+/l+2pc/,[dd]+/l+2pc/}[dd]_{\evlcry[]{\fct[L]}{\arr[\gamma]}}
\\
{\evlcry[]
{\fct[R]}
{\evlcry[]
{\fct[L]}
{\obj[d]}}}
\ar[d]_{\begin{array}{l}
\evlcry[]{\fct[R]}{\arr[f]}
\end{array}}
&
{\evlcry[]{\fct[L]}
{\evlcry[]
{\fct[R]}
{\obj[c]}}}
  \ar[r]|{\evlcrynat[]{\ntf[\varepsilon]}{\obj[c]}} 
\ar[d]_{\evlcry[]{\fct[L]}{\evlcry[]{\fct[R]}{\arr[f]}}}
&
{\obj[c]}
\ar[d]^{\arr[f]}
\\
\evlcry[]
{\fct[R]}
{\obj[c]}
\save[].[u].[uu]*+<3pt>[F-:<5pt>:ForestGreen]\frm{}
!R*!L{\small\color{ForestGreen}\cat[D]}\restore
&
\evlcry[]
{\fct[L]}{\evlcry[]
{\fct[R]}
{\obj[c']}}
\ar@[red][r]_{\evlcrynat[]{\ntf[\varepsilon]}{\obj[c']}}
&
{\obj[c']}
\ar@{->}@`{[]+/d+3pc/,[ll]+/d+3pc/}[ll]^{\fct[R]}
\save[].[u].[ul].[ulu]*+<3pt>[F-:<5pt>:ForestGreen]\frm{}
!R*!L{\small\color{ForestGreen}\cat}\restore
}\end{xy}}
$

