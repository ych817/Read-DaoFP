## 章节 07 递归类型

$$
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
\def\pila{\vph{fg}}                   % 柱子 , 用于指定盒子的最小高度
% ------------------------------------------------------------------
% 类型运算
\def\cons{\mrel{.}}                   % 对应积类型 concatenation 
\def\ethr{\mrel{|}}                   % 对应和类型 either
\def\etc{{\rm etc}}
% ------------------------------------------------------------------
% + 的值构造器
\def\Lft{{\tt Lft}}                   % 对象 + 构造器 Left
\def\Rht{{\tt Rht}}	                  % 对象 + 构造器 Right
% × 的接口
\def\fst{{\tt fst}}                   % 对象 × - first
\def\snd{{\tt snd}}                   % × - second
% N 的值构造器
\def\zero{0}                          % N - zero
\def\succ{{\tt succ}}                 % N - successor
% ------------------------------------------------------------------
% 打印方法名
\def\id{\textrm{id}}                           % 对象的 id
\def\absurd{{\rm\large\textexclamdown}\hspace{-3px}} % 对象的 absurd
\def\bang{{\rm\small !}}                       % 对象的 bang
\def\dom{\textrm{dom}}                         % 箭头的定义域
\def\img{\textrm{img}}                         % 箭头的值域
\def\src{\textrm{src}}                         % 箭头的源头
\def\tar{\textrm{tar}}                         % 箭头的目标
\def\ID{\textrm{ID}}                           % 范畴的 ID
\def\Obj{\textrm{Obj}}                         % 范畴的对象
\def\Arr{\textrm{Arr}}                         % 范畴的箭头
\def\circH{\mbin{\overline\circ}}              % 自然变换的横复合
\def\circV{\mbin{\circ}}                       % 自然变换的纵复合
% 打印常/变量名
\newcommand{\obj}[1][c]{{\sf #1}}              % 对象
\def\obji{\obj[0]}                             % 对象 : 始
\def\objt{\obj[1]}                             % 对象 : 终
\newcommand{\cat}[1][C]{\mathcal{#1}}          % 范畴 : C(默认)
\def\catCat{\cat[Cat]}                         % 范畴 : Cat
\def\catSet{\cat[Set]}                         % 范畴 : Set
\def\catHask{\cat[Hask]}                       % 范畴 : Hask — 笛卡尔闭范畴 (+/× 都在里面)
\newcommand{\catcirc}[1][\cat]{                % 范畴 C 中的复合运算
  \catbfunc[#1]{\circ}}
\newcommand{\catufunc}[2][\cat]{\smash{        % 范畴 C 中的函子 : 一元
  \overset{\mclap{\small\pila #1}}{#2}}}
\newcommand{\catbfunc}[2][\cat]{\mbin{\smash{  % 范畴 C 中的函子 : 二元
  \overset{\mclap{\small\pila #1}}{#2}}}}
\newcommand{\catdiag}[1][\cat]{                % 范畴 C 中的函子 : 对角
  \catufunc[#1]{\Delta}}
\newcommand{\cathom}[1][\cat]{\mbin{\smash{    % 范畴 C 中的函子 : Hom
  \xrightarrow{\small #1}}}}
\newcommand{\catplus}[1][\cat]{                % 范畴 C 中的函子 : +
  \catbfunc[#1]{+}}
\newcommand{\cattimes}[1][\cat]{               % 范畴 C 中的函子 : ×
  \catbfunc[#1]{\times}}
\newcommand{\catotimes}[1][\cat]{              % 范畴 C 中的张量积
  \catbfunc[#1]{\otimes}}
\newcommand{\list}[1]{                         % 范畴 Hask 中的函子 List
	\texttt{[\(#1\)]}}
\def\nil{{\tt []}}                             % 范畴 Hask 中的函子 List 的值构造器 nil
\def\concat{\mbin{:}}                          % 范畴 Hask 中的函子 List 的值构造器 concat
\def\yoneda{{\raise{-1px}{               % 米田嵌入
  \hspace{-1px}\smash{よ}\vph{(fgh)}\hspace{-1px}}}}
\def\yoda{                                     % 尤达嵌入
  \texttt{尤}}
\def\limit#1{{\rm lim}}                        % 极限
\def\colimit#1{{\rm colim}}                    % 余极限
% 用方法求值
\def\getid#1{{}_{:#1}\id}                      % 获取对象的 id
\def\getabsurd#1{{}_{:#1}\absurd}              % 获取对象的 absurd
\def\getbang#1{{}_{:#1}\bang}                  % 获取对象的 bang
\def\getdom#1{#1\textrm{ dom}}                 % 获取箭头的定义域
\def\getimg#1{#1\textrm{ img}}                 % 获取箭头的值域
\def\getsrc#1{#1~\src}                         % 获取箭头的源头
\def\gettar#1{#1~\tar}                         % 获取箭头的目标
\def\getrst#1undr#2{{}^{\vph{fg}}_{:#2}{#1}}   % 获取箭头在对象下的限制 
\def\getID#1{{}_{:#1}\ID}                      % 获取范畴的 ID
\def\getObj#1{#1~\Obj}                         % 获取范畴的对象
\def\getArr#1{#1~\Arr}                         % 获取范畴的箭头
\def\getop#1{#1^{\rm op}}                      % 获取范畴的对偶
\def\getlimit#1{#1\textrm{ lim}}               % 获取极限
\def\getcolimit#1{#1\textrm{ colim}}           % 获取余极限
$$

### 自然数与列表的泛性质

默认对象 $\obj[N]$ 在范畴 $\cat$ 中有下述性质 :

- $(\objt\cathom\obj[x])\cattimes[\catCat] (\obj[x]\cathom\obj[x])\cong (\obj[N]\cathom \obj[x])$ , $\obj[x]$ 为任意 $\cat$ 中对象
  —— **泛性质** 。`rec` 即对应的同构 ( 上式从左至右 ) 。

  $\vcenter{\begin{xy}\xymatrix@!C=2cm{
  {\obj[N]\pila}
  \ar@[red]@{-->}[d]_[red]{h\pila}
  & 
  {\obj[N]\catdiag\pila}
  \ar@[red]@{-->}[d]_[red]{h\catdiag\pila}
  &
  {\objt\cons \obj[N]\pila}
  \ar[l]_{\eta=\eta_i \cons \eta_s\pila}
  \ar@[red]@{-->}[d]^[red]{\getid {\objt}\cons h\pila}
  \\
  {\obj[x]\pila}
  \save[].[u]*+<3pt>[F-:<5pt>:ForestGreen]\frm{} !R*!L{\small\color{ForestGreen}\cat}\restore 
  & 
  {\obj[x]\catdiag\pila}
  &
  {\objt \cons \obj[x]\pila}
  \ar@[magenta][l]^[magenta]{i\cons s}
  \save[].[lu]*+<3pt>[F-:<5pt>:ForestGreen]\frm{} !R*!L{\small\color{ForestGreen}\cat\cattimes[\catCat]\cat}\restore 
  }\end{xy}}$ $\qquad\quad \vcenter{\begin{xy}\xymatrix@!C=2cm{
  {\objt\pila} 
  \ar[r]^{\eta_i=\zero\pila}
  \ar@[magenta][dr]_[magenta]{i\pila}
  & 
  {\obj[N]\pila} 
  \ar@[red]@{-->}[d]_[red]{h\pila}
  &
  {\obj[N]\pila}
  \ar[l]_{\eta_s=\succ\pila}
  \ar@[red]@{-->}[d]_[red]{h\pila}
  \\
  & 
  {\obj[x]\pila}
  \save[].[lu]*+<3pt>[F-:<5pt>:ForestGreen]\frm{} !L*!R{\small\color{ForestGreen}\cat\cattimes[\catCat]\cat}\restore  
  &
  {\obj[x]\pila}
  \ar@[magenta][l]^[magenta]{s}
  \save[].[u]*+<3pt>[F-:<5pt>:ForestGreen]\frm{} !R*!L{\small\color{ForestGreen}\cat}\restore }\end{xy}}$



默认函子 $\list{\_}:\cat\cathom[\catCat]\cat$ 在范畴 $\cat$ 中有下述性质 : 

- $(\objt\cathom \obj[x])\cattimes[\catCat]((\obj[x]\cattimes\obj[b])\cathom\obj[x])\cong (\list{\obj[b]}\cathom\obj[x])$ , $\obj[x]$ 为任意 $\cat$ 中对象
  —— **泛性质** 。`foldr` 即对应的同构 ( 上述等式从左至右 ) 。

  $\vcenter{\begin{xy}\xymatrix@!C=2cm{
  {\list{\obj[b]}\pila}
  \ar@[red]@{-->}[d]_[red]{h\pila}
  & 
  {\list{\obj[b]}\catdiag\pila}
  \ar@[red]@{-->}[d]_[red]{h\catdiag\pila}
  &
  {\objt \cons \list{\obj[b]}\cattimes\obj[b]\pila}
  \ar[l]_{\kappa = \kappa_i\cons \kappa_s\pila}
  \ar@[red]@{-->}[d]^[red]{\getid {\objt}\cons h \catotimes\getid {\obj[b]}\pila}
  \\
  {\obj[x]\pila}
  \save[].[u]*+<3pt>[F-:<5pt>:ForestGreen]\frm{}
  !R*!L{\small\color{ForestGreen}\cat}\restore
  & 
  {\obj[x]\catdiag\pila}
  &
  {\objt \cons \obj[x]\cattimes\obj[b]\pila}
  \ar@[magenta][l]^[magenta]{i\cons s} 
  \save[].[lu]*+<3pt>[F-:<5pt>:ForestGreen]\frm{}
  !R*!L{\small\color{ForestGreen}\cat\cattimes[\catCat]\cat}\restore
  }\end{xy}}$ $\qquad \vcenter{\begin{xy}\xymatrix@!C=2cm{
  {\objt\pila} 
  \ar[r]^{\kappa_i=\nil\pila}
  \ar@[magenta][dr]_[magenta]{i\pila}
  & 
  {\list{\obj[b]}\pila} 
  \ar@[red]@{-->}[d]_[red]{h\pila}
  &
  {\list{\obj[b]}\cattimes\obj[b]\pila}
  \ar[l]_{\kappa_s={\tt (\concat)}\pila}
  \ar@[red]@{-->}[d]^[red]{h \catotimes\getid {\obj[b]}\pila}
  \\
  & 
  {\obj[x]\pila}
  \save[].[lu]*+<3pt>[F-:<5pt>:ForestGreen]\frm{} !L*!R{\small\color{ForestGreen}\cat\cattimes[\catCat]\cat}\restore   
  &
  {\obj[x]\cattimes\obj[b]\pila}
  \ar@[magenta][l]^[magenta]{s}
  \save[].[u]*+<3pt>[F-:<5pt>:ForestGreen]\frm{} !R*!L{\small\color{ForestGreen}\cat}\restore   
  }\end{xy}}$ 

### 列表的函子性

如何证明 $\list{\_}$ 构成函子呢 ? 请看

- $\list{\_}:\getid {\obj[b_1]}\longmapsto \getid {\list{\obj[b_1]}}$ 
  —— $\list{\_}$ **保持恒等箭头** ;

- $\list{\_}:(g_1\catcirc g_2)\longmapsto (h_1\catcirc h_2)$
  —— $\list{\_}$ **保持箭头复合运算** 。
  下图便于形象理解证明过程 。

  $\vcenter{\begin{xy}\xymatrix@!C=2cm@R=.75cm{
  {\list{\obj[b_1]}\pila}
  \ar@[red]@{-->}[dd]_[red]{h_1\pila}
  & 
  {\list{\obj[b_1]}\catdiag\pila}
  \ar@[red]@{-->}[dd]_[red]{h_1\catdiag\pila}
  &
  {\objt \cons \list{\obj[b_1]}\cattimes\obj[b_1]\pila}
  \ar[l]_{\kappa\pila}
  \ar@[red]@{-->}[d]^[red]{\getid {\objt}\cons h_1\catotimes\getid {\obj[b_1]}\pila}
  \\
  & 
  &
  {\objt \cons \list{\obj[b_2]}\cattimes\obj[b_1]\pila}
  \ar@[magenta][d]^[magenta]{\getid {\objt}\cons g_1 \catotimes\getid {\list{\obj[b_2]}}\pila}
  \\
  {\list{\obj[b_2]}\pila}
  \ar@[red]@{-->}[dd]_[red]{h_2\pila}
  &
  {\list{\obj[b_2]}\catdiag\pila}
  \ar@[red]@{-->}[dd]_[red]{h_2\catdiag\pila}
  &
  {\objt\cons \list{\obj[b_2]}\cattimes \obj[b_2] \pila}
  \ar[l]_{\kappa}
  \ar@[red]@{-->}[d]^[red]{\getid {\objt}\cons h_2\catotimes\getid {\obj[b_2]}\pila}
  \\
  & 
  &
  {\objt \cons \list{\obj[b_3]}\cattimes\obj[b_2]\pila}
  \ar@[magenta][d]^[magenta]{\getid {\objt}\cons g_2 \catotimes\getid {\list{\obj[b_3]}}\pila}
  \\
  {\list{\obj[b_3]}\pila}
  \save[].[uuuu]*+<3pt>[F-:<5pt>:ForestGreen]\frm{}
  !R*!L{\small\color{ForestGreen}\cat}\restore 
  &
  {\list{\obj[b_3]}\catdiag\pila}
  &
  {\objt\cons \list{\obj[b_3]}\cattimes \obj[b_3] \pila}
  \ar[l]_{\kappa}
  \save[].[luuuu]*+<3pt>[F-:<5pt>:ForestGreen]\frm{}
  !R*!L{\small\color{ForestGreen}\cat\cattimes[\catCat]\cat}\restore 
  }\end{xy}}$ 