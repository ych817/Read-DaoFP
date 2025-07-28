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

### 伴随函子的 unit 与 counit

$\qquad \begin{xy}\xymatrix@!C=2cm{
\cat
\ar@`{[]+/dr+2pc/,[r]+/dl+2pc/}[r]_{\fct[R]}
\ar@`{[]+/ul+5pc/,[]+/ur+5pc/}[]^{\Id}
&
\cat[D]
\ar@`{[]+/ul+2pc/,[l]+/ur+2pc/}[l]_{\fct[L]}
\ar@`{[]+/ul+5pc/,[]+/ur+5pc/}[]^{\Id[{\cat[D]}]}
}\end{xy}$

伴随函子 : 对任意 $\obj[c]$ 和 $\obj[d]$ 有 $\evlbin[]{\catcong[\catSet]}
  {\evlbin{\cathom[{\cat[D]}]}
    {\obj[d]}
    {\evlcry[]{\fct[R]}{\obj[c]}}}  
  {\evlbin{\cathom}
    {\evlcry[]{\fct[L]}{\obj[d]}}
    {\obj[c]}}$ 。

不难看出这其实蕴含着一个二元的自然同构 $\ntf[\phi]$ , 见下 :

$\qquad\begin{aligned}[t]
\ntf[\phi]:{}&
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
\evlcrynat[]{\ntf[\phi]}{\evlbin\cons{\wld}{\bbox[pink]{\obj[c]}}}:{}&
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
\evlcrynat[]{\ntf[\phi]}{\evlbin\cons{\bbox[pink]{\obj[d]}}{\wld}}:{}&
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

如此一来

- 套用反变米田引理我们便可获得

  $\evlbin[]{\catcong[\catSet]}
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

  如此对每个左侧集合中的自然同构 $\evlcrynat[]{\ntf[\phi]}{\evlbin\cons{\wld}{\bbox[pink]{\obj[c]}}}$ 
  就会有一个右侧集合中的箭头与之相对应 , 即 $\evlcry[]{\evlcrynat[]{\ntf[\phi]}
    {\evlbin\cons{\evlcry[]{\fct[R]}{\obj[c]}}{\bbox[pink]{\obj[c]}}}}{\id[{\evlcry[]{\fct[R]}{\obj[c]}}]}$ 。
  接下来证明这群箭头将构成一个自然变换 。

  $\vcenter{\begin{xy}\xymatrix@!R=1cm@!C=2.5cm{
  {\bbox[LightGreen]{\evlbin[]{\cathom[{\cat[D]}]}
          {\bbox[white]{\evlcry[]{\fct[R]}{\obj[c]}}}
          {\evlcry[]{\fct[R]}{\obj[c]}}}}
  \ar[r]^{\evlcrynat[]{\ntf[\phi]}
    {\evlbin\cons{\evlcry[]{\fct[R]}{\obj[c]}}{\bbox[pink]{\obj[c]}}}} 
  \ar[d]_{\bbox[LightGreen]{\evlbin[]{\cathom[{\cat[D]}]}
          {\bbox[white]{\evlcrynat[]\op{\arr[g]}}}
          {\evlcry[]{\fct[R]}{\obj[c]}}}} 
  &
  {\bbox[LightGreen]{\evlbin[]{\cathom[{\cat}]}
          {\evlcry[]{\fct[L]}{\bbox[white]{\evlcry[]{\fct[R]}{\obj[c]}}}}
          {\obj[c]}}}
  \ar[d]^{\bbox[LightGreen]{\evlbin[]{\cathom[{\cat}]}
          {\evlcry[]{\fct[L]}{\bbox[white]{\evlcrynat[]\op{\arr[g]}}}}
          {\obj[c]}}}
  \\
  {\bbox[LightGreen]{\evlbin[]{\cathom[{\cat[D]}]}
          {\bbox[white]{\evlcry[]{\fct[R]}{\obj[c']}}}
          {\evlcry[]{\fct[R]}{\obj[c]}}}}
  \ar[r]_{\evlcrynat[]{\ntf[\phi]}
    {\evlbin\cons{\evlcry[]{\fct[R]}{\obj[c']}}{\bbox[pink]{\obj[c]}}}} 
  \save[].[u]*+<3pt>[F-:<5pt>:ForestGreen]\frm{}
  !D*!U{\small\color{ForestGreen}
    \bbox[LightGreen]{\evlbin[]{\cathom[{\cat[D]}]}
      {\bbox[white]{\cat[D]}}
      {\evlcry[]{\fct[R]}{\obj[c]}}}}\restore 
  \save[].[u].[r]*+<10pt>[F-:<8pt>:ForestGreen]\frm{}
  !D*!U!L(4){\small\color{ForestGreen}\cat[Set]}\restore 
  &
  {\bbox[LightGreen]{\evlbin[]{\cathom[{\cat}]}
          {\evlcry[]{\fct[L]}{\bbox[white]{\evlcry[]{\fct[R]}{\obj[c']}}}}
          {\obj[c]}}}
  \save[].[u]*+<3pt>[F-:<5pt>:ForestGreen]\frm{}!D*!U
  {\small\color{ForestGreen}
    \bbox[LightGreen]{\evlbin[]{\cathom[{\cat}]}
      {\evlcry[]{\fct[L]}{\bbox[white]{\cat[D]}}}
      {\obj[c]}}}\restore 
  }\end{xy}}$

- 套用协变米田引理我们便可获得

  $\evlbin[]{\catcong[\catSet]}
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

  如此对每个左侧集合中的自然同构 $\evlcrynat[]{\ntf[\phi]}{\evlbin\cons{\bbox[pink]{\obj[d]}}{\wld}}$ 
  就会有一个右侧集合中的箭头与之相对应 。
  接下来证明这一群箭头将会构成自然变换 。

----

$\qquad\begin{array}{c}
\vcenter{\begin{xy}\xymatrix@!R=1cm@!C=2cm{
{\bbox[LightGreen]{\evlbin[]{\cathom[{\cat[D]}]}
  {\obj[d]}
  {\evlcry[]{\fct[R]}{\bbox[white]{\obj[c']}}}}}
\ar[r]^{\evlcrynat[]{\ntf[\phi]}
  {\evlbin\cons{\bbox[pink]{\obj[d']}}{\obj[c']}}}
\save[].[d]*+<3pt>[F-:<5pt>:ForestGreen]\frm{}!U*!D
{\small\color{ForestGreen}
  \bbox[LightGreen]{\evlbin[]{\cathom[{\cat[D]}]}
  {\obj[d]}
  {\evlcry[]{\fct[R]}{\bbox[white]{\cat}}}}}\restore 
\save[].[d].[r]*+<10pt>[F-:<8pt>:ForestGreen]\frm{}
!U*!D!L(4){\small\color{ForestGreen}\cat[Set]}\restore
&
{\bbox[LightGreen]{\evlbin[]{\cathom[{\cat}]}
  {\evlcry[]{\fct[L]}{\obj[d]}}
  {\bbox[white]{\obj[c']}}}}
\save[].[d]*+<3pt>[F-:<5pt>:ForestGreen]\frm{}!U*!D
{\small\color{ForestGreen}
  \bbox[LightGreen]{\evlbin[]{\cathom[{\cat}]}
  {\evlcry[]{\fct[L]}{\obj[d]}}
  {\bbox[white]{\cat}}}}\restore 
\\
{\bbox[LightGreen]{\evlbin[]{\cathom[{\cat[D]}]}
  {\obj[d]}
  {\evlcry[]{\fct[R]}{\bbox[white]{\obj[c]}}}}}
\ar[r]_{\evlcrynat[]{\ntf[\phi]}
  {\evlbin\cons{\bbox[pink]{\obj[d]}}{\obj[c]}}} 
\ar[u]^{\bbox[LightGreen]{\evlbin[]{\cathom[{\cat[D]}]}
  {\obj[d]}
  {\evlcry[]{\fct[R]}{\bbox[white]{\arr[f]}}}}}  
&
{\bbox[LightGreen]{\evlbin[]{\cathom[{\cat}]}
  {\evlcry[]{\fct[L]}{\obj[d]}}
  {\bbox[white]{\obj[c]}}}}
\ar[u]_{\bbox[LightGreen]{\evlbin[]{\cathom[{\cat}]}
  {\evlcry[]{\fct[L]}{\obj[d]}}
  {\bbox[white]{\arr[f]}}}}
}\end{xy}}
\\
\vcenter{\begin{xy}\xymatrix@!R=1cm@!C=2cm{
{\bbox[LightGreen]{\evlbin[]{\cathom[{\cat[D]}]}
        {\bbox[white]{\obj[d]}}
        {\evlcry[]{\fct[R]}{\obj[c]}}}}
\ar[r]^{\evlcrynat[]{\ntf[\phi]}
  {\evlbin\cons{\obj[d]}{\bbox[pink]{\obj[c]}}}} 
\ar[d]_{\bbox[LightGreen]{\evlbin[]{\cathom[{\cat[D]}]}
        {\bbox[white]{\evlcrynat[]\op{\arr[g]}}}
        {\evlcry[]{\fct[R]}{\obj[c]}}}} 
&
{\bbox[LightGreen]{\evlbin[]{\cathom[{\cat}]}
        {\evlcry[]{\fct[L]}{\bbox[white]{\obj[d]}}}
        {\obj[c]}}}
\ar[d]^{\bbox[LightGreen]{\evlbin[]{\cathom[{\cat}]}
        {\evlcry[]{\fct[L]}{\bbox[white]{\evlcrynat[]\op{\arr[g]}}}}
        {\obj[c]}}}
\\
{\bbox[LightGreen]{\evlbin[]{\cathom[{\cat[D]}]}
        {\bbox[white]{\obj[d']}}
        {\evlcry[]{\fct[R]}{\obj[c]}}}}
\ar[r]_{\evlcrynat[]{\ntf[\phi]}
  {\evlbin\cons{\obj[d']}{\bbox[pink]{\obj[c]}}}} 
\save[].[u]*+<3pt>[F-:<5pt>:ForestGreen]\frm{}
!D*!U{\small\color{ForestGreen}
  \bbox[LightGreen]{\evlbin[]{\cathom[{\cat[D]}]}
    {\bbox[white]{\cat[D]}}
    {\evlcry[]{\fct[R]}{\obj[c]}}}}\restore 
\save[].[u].[r]*+<10pt>[F-:<8pt>:ForestGreen]\frm{}
!D*!U!L(4){\small\color{ForestGreen}\cat[Set]}\restore 
&
{\bbox[LightGreen]{\evlbin[]{\cathom[{\cat}]}
        {\evlcry[]{\fct[L]}{\bbox[white]{\obj[d']}}}
        {\obj[c]}}}
\save[].[u]*+<3pt>[F-:<5pt>:ForestGreen]\frm{}!D*!U
{\small\color{ForestGreen}
  \bbox[LightGreen]{\evlbin[]{\cathom[{\cat}]}
    {\evlcry[]{\fct[L]}{\bbox[white]{\cat[D]}}}
    {\obj[c]}}}\restore 
}\end{xy}}
\end{array}$

这里 

