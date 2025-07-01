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
\def\pla{\vph{fg()}}                                 % 柱子, 用于指定盒子的最小高度
%\def\pla{\bbox[0px, red]{\hspace{1px}\vph{(fg)}}}   % 测试柱子是否被使用
\let\objectstyle=\pla                                % xyjax 中所有对象都加上 \pla
\def\prs#1{\left( #1 \right)}                        % 为表达式添加圆括号
\def\verts#1{\lvert #1 \rvert}                       % 为表达式添加竖线
\def\etc{\pla\textrm{etc}}                           % 对应省略号 等等等等
\def\wld{\pla\_}                                     % 对应通配符 _
% 值构造器 ====================================================================
\def\cons{{\pla \tt{.}}}                             % 对应积类型 cons
\def\ethr{{\pla \tt{|}}}                             % 对应和类型 either
\def\concat{{\pla \tt{:}}}                           % 对应列表类型的 concat
% 打印名称 ====================================================================
% 打印常变量 -------------------------------------------------------------------
\newcommand{\obj}[1][c]{{\pla\sf #1}}                % 对象
\def\obji{\obj[0]}                                   % 对象 : 始
\def\objt{\obj[1]}                                   % 对象 : 终
\newcommand{\cat}[1][C]{{\pla\sf #1}}                % 范畴 : C默认
\def\catCat{\cat[Cat]}                               % 范畴 : Cat
\def\catSet{\cat[Set]}                               % 范畴 : Set
\def\catHask{\cat[Hask]}                             % 范畴 : Hask — 笛卡尔闭范畴 +/× 都在里面
\newcommand{\arr}[1][f]{{\pla #1}}                   % 箭头
\newcommand{\arr}[1][f]{\bbox[0pt, violet]{\pla #1}} % 测试箭头是否被使用
\newcommand{\fct}[1][F]{{\pla #1}}                   % 函子
\newcommand{\fct}[1][f]{\bbox[0pt,orange]{\pla #1}}  % 测试函子是否被使用
\newcommand{\ntf}[1][\eta]{{\pla #1}}                % 自然变换
\newcommand{\ntf}[1][f]{\bbox[0pt,red]{\pla #1}}     % 测试自然变换是否被使用
% 打印方法名 ------------------------------------------------------------------
\newcommand{\opr}[2][\cat]{\pla\smash{               % 方法的名称 形式 1
  \overset{\mclap{\small\pla #1}}{#2}}}
\def\rst#1undr#2{\pla                                % 方法的名称 形式 2
  {}^{}_{\smash{:#2\pla}}{#1}}       
\newcommand{\id}[1][\obj]{                           % 对象的 id
  \rst{\textrm{id}}undr#1}
\newcommand{\absurd}[1][\obj]{                       % 对象的 absurd
  \rst{{\large\textexclamdown\hspace{-3px}}}undr#1}
\newcommand{\bang}[1][\obj]{                         % 对象的 bang
  \rst{\textrm{!}}undr#1}
\newcommand{\src}[1][\cat]{                          % 箭头的源头
  \opr[#1]{\textrm{src}}}
\newcommand{\tar}[1][\cat]{                          % 箭头的目标
  \opr[#1]{\textrm{tar}}}
\def\dom{\pla\textrm{dom}}                           % 箭头的定义域
\def\img{\pla\textrm{img}}                           % 箭头的值域
\newcommand{\Id}[1][\cat]{                           % 范畴的 ID
  \rst{\textrm{Id}}undr#1}
\def\Obj{\pla\textrm{Obj}}                           % 范畴的所有对象
\def\Arr{\pla\textrm{Arr}}                           % 范畴的所有箭头
\def\op{\pla\textrm{op}}                             % 范畴的对偶
\newcommand{\catplus}[1][\cat]{                      % 范畴 C 中的运算 + 
  \opr[#1]{+}}
\newcommand{\cattimes}[1][\cat]{                     % 范畴 C 中的运算 ×
  \opr[#1]{\times}}
\newcommand{\catotimes}[1][\cat]{                    % 范畴 C 中的运算 ⊗
  \opr[#1]{\otimes}}
\newcommand{\catcirc}[1][\cat]{                      % 范畴 C 中的运算 ○
  \opr[#1]{\circ}}
\newcommand{\cathom}[1][\cat]{\pla\smash{            % 范畴 C 中的运算 →
  \xrightarrow{\small\pla #1}}}
\newcommand{\catcong}[1][\cat]{                      % 范畴 C 中的同构 ≅
  \opr[#1]{\cong}}
\newcommand{\Di}[2][\cat]{\pla\smash[b]{             % 对角函子
  \underset{\small #2}{\opr[#1]{\textrm{Di}}}}}
\newcommand{\I}[1][F]{                               % 函子的 ID 自然变换
  \rst{\iota}undr#1}
\def\yoneda{{\pla\raise{-1px}{                       % 米田嵌入
  \hspace{-1px}\smash{よ}\hspace{-1px}}}}
\def\yoda{{\pla                                      % 尤达嵌入
  \texttt{尤}}}
% 用方法求值 -------------------------------------------------------------------
\newcommand{\evlcry}[3][\prs]{                       % 用方法求值 柯里化
  #1{#3{#2}}}                                          % 针对的方法有
                                                       % Id id bang absurd
\newcommand{\evlcrytxt}[3][\prs]{                    % 用方法求值 柯里化
	#1{#3~{#2}}}                                         % 针对的方法有 
	                                                     % Di Obj Arr src dom img
\newcommand{\evlcrynat}[3][\prs]{\pla                % 用方法求值 柯里化
  #1{\smash{#3^{#2}}}}                                 % 针对的方法 自然变换 有 
                                                       % η θ
\def\evlbig#1#2#3{                                   % 用方法求值 大算符
  #2\rst{#1}undr#3}                                    % 针对的方法 大算符 有 
                                                       % ∑ ∏ ⨿
\newcommand{\evlbin}[4][\prs]{\pla                   % 用方法求值 二元运算
  %\bbox[border: 1px solid Orchid]{%                   % 针对的方法 二元运算 有
    #1{\smash{#3 \mbin{#2} #4}}%                   % ＋ × ⊗ ○ →
  %}
  }
$$

- $\obj[c_1]/\cat$ : **仰范畴** , 这里 $\obj$ 为任意 $\cat$ 中对象 ; 满足

  - $\obj[c_1]/\cat$ 中对象皆形如 $\cancel{
    \smash[b]{
    \evlbin[]\cons
      {\evlbin[]\cons
        {\obj[1]}
        {\obj[c]}}
      {{}}}\!}
    {\arr[i]}$ , 其中 $\obj[c]$ 和 
    $\arr[i]:\evlbin[]\cathom
      {\obj[c_1]}
      {\obj[c]}$ 分别为 $\cat$ 中任意的对象和箭头 ;

  - $\cat/\obj[c_1]$ 中箭头皆形如 $\!\cancel{\smash[b]{\evlbin[]\cons
    {\id[{\obj[c_1]}]}
    {{}}}} \arr[f]$ 且满足下述交换图 , 其中
    $\obj[c']$ , $\obj[c]$ 为 $\cat$ 中任意对象且 $\arr[f]$ , $\arr[i']$ , $\arr[i]$ 为 $\cat$ 中任意箭头 ; 

    $\vcenter{\begin{xy}\xymatrix@!R=1cm@!C=2cm{
    {\obj[c_1]}
    \ar[r]^{\arr[i]}
    &
    {\obj[c]} 
    \\
    {\obj[c_1]}
    \ar[r]_{\arr[i']}  
    \ar[u]^{\id[{\obj[c_1]}]}
    \save[].[u]*+<3pt>[F-:<5pt>:ForestGreen]\frm{} !D*!U
    {\small\color{ForestGreen}
    \evlcry[]{\bbox[LightGreen]{\evlcrytxt{\Di{\cat[①]}}
      {\obj[c_1]}}}
        {\cat[①]}
    }\restore
    &
    {\obj[c']} 
    \ar[u]_{\arr[f]}
    \save[].[u]*+<3pt>[F-:<5pt>:ForestGreen]\frm{} !D*!U
    {\small\color{ForestGreen}\cat}\restore
    \save[ul].[]*+<10pt>[F-:<8pt>:ForestGreen]\frm{} 
    !U*!D!L(8)
    {\small\color{ForestGreen}\cat}\restore 
    \\
    }\end{xy}}
    \quad
    \vcenter{\begin{xy}\xymatrix@!R=1cm@!C=2cm{
    {\evlcry[]{\bbox[LightGreen]{\evlcrytxt{\Di{\cat[①]}}
      {\obj[c_1]}}}
        {\obj[1]}} 
    \ar[r]^{\arr[i]}
    &
    {\obj[c]\bbox[LightGreen]{\Id[{\cat}]}}
    \\
    {\evlcry[]{\bbox[LightGreen]{\evlcrytxt{\Di{\cat[①]}}
      {\obj[c_1]}}}
        {\obj[1]}} 
    \ar[u]^{\evlcry[]{\bbox[LightGreen]{\evlcrytxt{\Di{\cat[①]}}
      {\obj[c_1]}}}
        {\id[{\obj[1]}]}}  
    \ar[r]_{\arr[i']}
    \save[].[u]*+<3pt>[F-:<5pt>:ForestGreen]\frm{} !D*!U
    {\small\color{ForestGreen}\evlcry[]{\bbox[LightGreen]{\evlcrytxt{\Di{\cat[①]}}
      {\obj[c_1]}}}
        {\cat[①]}}\restore
    &
    {\obj[c']\bbox[LightGreen]{\Id[{\cat}]}} 
    \ar[u]_{\evlcry[]{\bbox[LightGreen]{\Id[{\cat}]}}
      {\arr[f]}} 
    \save[].[u]*+<3pt>[F-:<5pt>:ForestGreen]\frm{} !D*!U
    {\small\color{ForestGreen}\cat\bbox[LightGreen]{\Id[{\cat}]}}\restore
    \save[ul].[]*+<10pt>[F-:<8pt>:ForestGreen]\frm{} !U*!D!L(8)
    {\small\color{ForestGreen}\cat}\restore
    }\end{xy}}
    \quad
    \vcenter{\begin{xy}\xymatrix@!C=2cm{ 
    &  
    {\cat}
    &
    \\
    {\cat[1]}
    \ar[ur]_{\evlcrytxt{\Di{\cat[①]}}
      {\obj[c_1]}}
    & &  
    {\cat}
    \ar[ul]^{\Id[{\cat}]}
    }\end{xy}}$ 