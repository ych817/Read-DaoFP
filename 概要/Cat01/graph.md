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
%\def\pla{\vph{fg}}                              % 柱子, 用于指定盒子的最小高度
\def\pla{\bbox[0pt,red]{\,\vph{fg}}}            % 测试柱子是否被使用
\def\etc{\textrm{etc}}                          % 对应省略号 (等等等等)
\def\wld{\_}                                    % 对应通配符 _
% 值构造器 ====================================================================
\def\cons{\mbin{.}}                             % 对应积类型 cons
\def\ethr{\mbin{|}}                             % 对应和类型 either
\def\concat{\mbin{\tt{:}}}                      % 对应列表类型的 concat
% 打印名称 ====================================================================
% 打印常变量 -------------------------------------------------------------------
\newcommand{\obj}[1][c]{{\sf #1}}               % 对象
\def\obji{\obj[0]}                              % 对象 : 始
\def\objt{\obj[1]}                              % 对象 : 终
\newcommand{\cat}[1][C]{{\sf #1}}               % 范畴 : C(默认)
\def\catCat{\cat[Cat]}                          % 范畴 : Cat
\def\catSet{\cat[Set]}                          % 范畴 : Set
\def\catHask{\cat[Hask]}                        % 范畴 : Hask — 笛卡尔闭范畴 (+/× 都在里面)
\newcommand{\arr}[1][f]{{#1}}                   % 箭头
\newcommand{\fct}[1][F]{{#1}}                   % 函子
\newcommand{\ntf}[1][\eta]{{#1}}                % 自然变换
% 打印方法名 ------------------------------------------------------------------
\newcommand{\opr}[2][\cat]{\smash{              % 方法的名称 (形式 1)
  \overset{\mclap{\small\pla #1}}{#2}}}
\def\rst#1undr#2{                               % 方法的名称 (形式 2)
  {}^{}_{\smash{:#2\pla}}{#1}}       
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
  \xrightarrow{\small\pla #1}}}
\newcommand{\catcong}[1][\cat]{\smash{          % 范畴 C 中的同构 ≅
  \opr[#1]{\cong}}}
\newcommand{\Di}[2][\cat]{                      % 对角函子
  \smash[b]{\pla\underset{\small #2}{\opr[#1]{\textrm{Di}}}}}
\newcommand{\I}[1][F]{                          % 函子的 ID (自然变换)
  \rst{\iota}undr#1}
\def\yoneda{{\raise{-1px}{                      % 米田嵌入
  \hspace{-1px}\smash{よ}\vph{(fgh)}\hspace{-1px}}}}
\def\yoda{                                      % 尤达嵌入
  \texttt{尤}}
% 用方法求值 -------------------------------------------------------------------
\def\evlcry#1#2{                                % 用方法求值 (柯里化)
    #2{#1}}                                       % 针对的方法有
                                                  % Id id bang absurd
\def\evlcrytxt#1#2{                             % 用方法求值 (柯里化)
	#2~{#1}}                                        % 针对的方法有 
	                                                % Di Obj Arr src dom img
\def\evlcrynat#1#2{                             % 用方法求值 (柯里化)
    #2^{#1}}                                      % 针对的方法 (自然变换) 有 
                                                  % η θ
\def\evlbig#1#2#3{                              % 用方法求值 (大算符)
    #2\rst{#1}undr#3}                             % 针对的方法 (大算符) 有 
                                                  % ∑ ∏ ⨿
\def\evlbin#1#2#3{                              % 用方法求值 (二元运算)
    #2 \mbin{#1} #3}                              % 针对的方法 (二元运算) 有
                                                  % ＋ × ⊗ ○ →
$$

上一页的第二条定理若用交换图表示则应为

$\qquad\vcenter{\begin{xy}\xymatrix@!R=1cm@!C=2cm{
{\pla\bbox[LightGreen]{\evlbin\cathom
  {\obj[c_1]}
  {{}}}\obj[c]} 
\ar[r]^{\pla\evlcrynat{\ntf[\eta_1]}
  {\obj[c]}} 
\ar[d]_{\bbox[LightGreen]{\pla\evlbin\cathom
  {\obj[c_1]}
  {{}}}\arr} &
{\pla\bbox[LightGreen]{\evlbin\cathom
  {\obj[c_1']}
  {{}}}\obj[c]} 
\ar[d]^{\bbox[LightGreen]{\pla\evlbin\cathom
  {\obj[c_1]}
  {{}}}\arr}  \\
{\pla\bbox[LightGreen]{\evlbin\cathom
  {\obj[c_1]}
  {{}}}\obj[c']} 
\ar[r]_{\pla\evlcrynat{\ntf[\eta_1]}
  {\obj[c']}} 
\save[].[u]*+<3pt>[F-:<5pt>:ForestGreen]\frm{} !D*!U
{\small\pla\color{ForestGreen}\bbox[LightGreen]{\evlbin\cathom
  {\obj[c_1]}
  {{}}}\cat}\restore &
{\bbox[LightGreen]{\pla\evlbin\cathom
  {\obj[c_1']}
  {{}}}\obj[c']} 
\save[].[u]*+<3pt>[F-:<5pt>:ForestGreen]\frm{} !D*!U
{\small\pla\color{ForestGreen}\bbox[LightGreen]{\evlbin\cathom
  {\obj[c_1']}
  {{}}}\cat}\restore 
\save[ul].[]*+<10pt>[F-:<8pt>:ForestGreen]\frm{}
!U*!D!L(4){\small\pla\color{ForestGreen}\cat[Set]}\restore 
}\end{xy}}$

$\Rightarrow$ 易证 , $\Leftarrow$ 用到了米田技巧 ( 考虑特殊情况 )

$\qquad\vcenter{\begin{xy}\xymatrix@!R=1cm@!C=2cm{
{\bbox[LightGreen]{\pla\evlbin\cathom
  {\obj[c_1]}
  {{}}}\obj[c_1]} 
\ar[r]^{\pla\evlcrynat{\ntf[\eta_1]}
  {\obj[c]}} 
\ar[d]_{\pla\bbox[LightGreen]{\evlbin\cathom
  {\obj[c_1]}
  {{}}}\arr} &
{\pla\bbox[LightGreen]{\evlbin\cathom
  {\obj[c_1']}
  {{}}}\obj[c_1]} 
\ar[d]^{\pla\bbox[LightGreen]{\evlbin\cathom
  {\obj[c_1]}
  {{}}}\arr}  \\
{\pla\bbox[LightGreen]{\evlbin\cathom
  {\obj[c_1]}
  {{}}}\obj[c']} 
\ar[r]_{\pla\evlcrynat{\ntf[\eta_1]}
  {\obj[c']}} &
{\pla\bbox[LightGreen]{\evlbin\cathom
  {\obj[c_1']}
  {{}}}\obj[c']}
}\end{xy}}
\qquad
\vcenter{\begin{xy}\xymatrix@!R=1cm@!C=2cm{
{\pla\id[{\obj[c_1]}]}
\ar@{|->}[r]^{\pla\evlcrynat{\ntf[\eta_1]}
  {\obj[c]}} 
\ar@{|->}[d]_{\pla\bbox[LightGreen]{\evlbin\cathom
  {\obj[c_1]}
  {{}}}\arr} &
{\pla\smash[h]{\bbox[LightGray]{\id[{\obj[c_1]}](\evlcrynat{\ntf[\eta_1]}
  {\obj[c]})}}} 
\ar@{|->}[d]^{\pla\bbox[LightGreen]{\evlbin\cathom
  {\obj[c_1]}
  {{}}}\arr}  \\
{\pla\arr}
\ar@{|->}[r]_{\pla\evlcrynat{\ntf[\eta_1]}
  {\obj[c']}} &
{\pla\bbox[LightGray]{(\etc)}\circ\arr}
}\end{xy}}$

为了方便就用 $\bbox[LightGray]{(\etc)}$ 表示 $\bbox[LightGray]{\evlcry{(\evlcrynat{\ntf[\eta_1]}
  {\obj[c]})}
    {\id[{\obj[c_1]}]}}$ 。由上图
知 $\evlcry{(\evlcrynat{\ntf[\eta_1]}
  {\obj[c']})}{\arr}=\evlbin\catcirc
  {\bbox[LightGray]{(\etc)}}
  \arr$ , 故 $\evlcrynat{\ntf[\eta_1]}
  {\obj[c']}=\bbox[LightGray]{(\etc)}\bbox[LightBlue]{\evlbin\cathom
  {{}}
  {\obj[c']}}$ ;
而 $\evlcrynat{\ntf[\eta_1]}
  {\obj[c']}=\bbox[LightGray]{(\etc)}\bbox[LightBlue]{\evlbin\cathom
  {{}}
  {\obj[c']}}=\obj[c']^{(\evlbin\catcirc
  {\bbox[LightGray]{(\etc)}}
  \wld)}$是同构, 从而
知 $(\evlbin\catcirc
  \wld
  {\bbox[LightGray]{(\etc)}})$ 是同构 , ==$\bbox[LightGray]{(\etc)}:\evlbin\cathom
    {\obj[c_1]}
    {\obj[c_1']}$ 也是== 。

> 高亮部分省去了部分推理过程 , 
> 具体在米田嵌入处会详细介绍 。