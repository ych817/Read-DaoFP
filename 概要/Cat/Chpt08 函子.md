## 章节 08 函子

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
\def\nil{\texttt{[]}}                          % 范畴 Hask 中的函子 List 的值构造器 nil
\def\concat{\mbin{\tt{:}}}                  % 范畴 Hask 中的函子 List 的值构造器 concat
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

先规定几种特殊的范畴 : 

- **离散范畴** : 只有对象不含箭头 ( 恒等箭头除外 ) 的范畴 。

- $\catSet$ : **集合范畴** , 为局部小范畴 , 满足

  - $\catSet$ 中对象可以是任意集合
  - $\catSet$ 中箭头便是集合间映射 。

- $\getop\cat$ : **反范畴** , 满足

  - $\getop\cat$ 中对象皆形如 $\obj$ , 
    $\obj$ 为任意 $\cat$ 中的对象 ;
  - $\getop\cat$ 中箭头皆形如 $\getop\phi:\obj[c_2]\cathom[\getop\cat]\obj[c_1]$ , 
    $\phi:\obj[c_1]\cathom\obj[c_2]$ 可为任意 $\cat$ 中的箭头 。

- $\cat\cattimes[\catCat]\cat[D]$ : **积范畴** , 满足

  - $\cat\cattimes[\catCat]\cat[D]$ 中对象皆形如 $\obj\cons \obj[d]$ , 
    $\obj$ , $\obj[d]$ 为任意 $\cat$ , $\cat[D]$ 中的对象 ;
  - $\cat\cattimes[\catCat]\cat[D]$ 中箭头皆形如 $\phi\cons \psi$ , 
    $\phi$ , $\psi$ 为任意 $\cat$ , $\cat[D]$ 中的箭头 。

- $\cat/\obj$ : **俯范畴** , 这里 $\obj$ 为任意 $\cat$ 中对象 ; 满足

  - $\cat/\obj$ 中对象皆形如 $\cancel{\smash[b]{\obj[x]\cons \objt\cons}} \phi$ , 其中
    $\obj[x]$ 和 $\phi:\obj[x]\cathom \obj$ 分别为 $\cat$ 中对象和箭头 ;

  - $\obj/\cat$ 中箭头皆形如 $f_1\!\cancel{\cons \getid{\obj}}\!$ 且满足下述交换图 , 其中
    $\obj[x_1]$ , $\obj[x_2]$ 为 $\cat$ 中对象且 $\phi_1$ , $\phi_2$ , $f_1$ , $\getid{\objt}$ 皆为 $\cat$ 中箭头 ; 

    $\vcenter{\begin{xy}\xymatrix@!R=1cm@!C=2cm{
    {\obj[x_2]\pila} 
    \ar[r]^{\phi_1\pila} &
    {\obj\pila}  \\
    {\obj[x_1]\pila} 
    \ar[r]_{\phi_2\pila}
    \ar[u]^{f_1\pila} 
    \save[].[u]*+<3pt>[F-:<5pt>:ForestGreen]\frm{} !D*!U{\small\color{ForestGreen}\cat}\restore &
    {\obj\pila}
    \ar[u]_{\getid{\objt}\pila} 
    \save[].[u]*+<3pt>[F-:<5pt>:ForestGreen]\frm{} !D*!U{\small\color{ForestGreen}\cat[1](\obj\catdiag)}\restore
    }\end{xy}}$ $\vcenter{\begin{xy}\xymatrix@!R=1cm@!C=2cm{
    {\obj[x_2]\bbox[LightGreen]{\getid{\cat}}\pila} 
    \ar[r]^{\phi_1\pila} &
    {\objt\bbox[LightGreen]{(\obj\catdiag)}\pila}  \\
    {\obj[x_1]\bbox[LightGreen]{\getid{\cat}}\pila} 
    \ar[r]_{\phi_2\pila} 
    \ar[u]^{f_1\bbox[LightGreen]{\getid{\cat}}\pila} 
    \save[].[u]*+<3pt>[F-:<5pt>:ForestGreen]\frm{} !D*!U{\small\color{ForestGreen}\cat\getid{\cat}}\restore 
    &
    {\objt\bbox[LightGreen]{(\obj\catdiag)}\pila}
    \ar[u]_{\getid{\objt}\bbox[LightGreen]{(\obj\catdiag)}\pila}  
    \save[].[u]*+<3pt>[F-:<5pt>:ForestGreen]\frm{} !D*!U{\small\color{ForestGreen}\cat[1](\obj\catdiag)}\restore
    }\end{xy}}$ $\qquad \vcenter{\begin{xy}\xymatrix@!C=2cm{ 
    &  
    {\cat\pila}
    &
    \\
    {\cat\pila}
    \ar[ur]_{\getid{\cat}\pila}
    & &  
    {\cat[1]\pila}
    \ar[ul]^{\obj\catdiag\pila}
    }\end{xy}}$ 
  
- $\obj/\cat$ : **仰范畴** , 这里 $\obj$ 为任意 $\cat$ 中对象 ; 

  - $\obj/\cat$ 中对象皆形如 $\cancel{\smash[b]{\objt\cons \obj[x]\cons{}}}\! \phi$ , 其中
    $\obj[x]$ 和 $\phi:\obj\cathom \obj[x]$ 分别为 $\cat$ 中对象和箭头 ;

  - $\cat/\obj$ 中箭头皆形如 $\!\cancel{\getid {\obj}}\!\cons g_1$ 且满足下述交换图 , 其中
    $\obj[x_1]$ , $\obj[x_2]$ 为 $\cat$ 中对象且 $\phi_1$ , $\phi_2$ , $\getid {\objt}$ , $g_1$ 皆为 $\cat$ 中箭头 ; 

    $\vcenter{\begin{xy}\xymatrix@!R=1cm@!C=2cm{
    {\obj\pila}
    \ar[r]^{\phi_1\pila}  
    \ar[d]_{\getid{\objt}\pila}
    &
    {\obj[x_1]\pila} 
    \ar[d]^{g_1\pila} 
    \\
    {\obj\pila}
    \save[].[u]*+<3pt>[F-:<5pt>:ForestGreen]\frm{} !D*!U{\small\color{ForestGreen}\cat[1](\obj\catdiag)}\restore
    \ar[r]_{\phi_2\pila} 
    &
    {\obj[x_2]\pila} 
    \save[].[u]*+<3pt>[F-:<5pt>:ForestGreen]\frm{} !D*!U{\small\color{ForestGreen}\cat}\restore 
    }\end{xy}}$ $\vcenter{\begin{xy}\xymatrix@!R=1cm@!C=2cm{
    {\objt\bbox[LightGreen]{(\obj\catdiag)}\pila} 
    \ar[d]_{\getid{\objt}\bbox[LightGreen]{(\obj\catdiag)}\pila}  
    \ar[r]^{\phi_1\pila}
    &
    {\obj[x_1]\bbox[LightGreen]{\getid{\cat}}\pila} 
    \ar[d]^{g_1\bbox[LightGreen]{\getid{\cat}}\pila} 
    \\
    {\objt\bbox[LightGreen]{(\obj\catdiag)}\pila}
    \ar[r]_{\phi_2\pila}  
    \save[].[u]*+<3pt>[F-:<5pt>:ForestGreen]\frm{} !D*!U{\small\color{ForestGreen}\cat[1](\obj\catdiag)}\restore
    &
    {\obj[x_2]\bbox[LightGreen]{\getid{\cat}}\pila} 
    \save[].[u]*+<3pt>[F-:<5pt>:ForestGreen]\frm{} !D*!U{\small\color{ForestGreen}\cat\getid{\cat}}\restore 
    }\end{xy}}$ $\qquad \vcenter{\begin{xy}\xymatrix@!C=2cm{ 
    &  
    {\cat\pila}
    &
    \\
    {\cat[1]\pila}
    \ar[ur]_{\obj\catdiag\pila}
    & &  
    {\cat\pila}
    \ar[ul]^{\getid{\cat}\pila}
    }\end{xy}}$



考虑范畴 $\cat$ 和 $\cat[D]$ , 现提供函子定义 : 

- $\Phi:\cat\cathom[\catCat]\cat[D]$ 为范畴当且仅当
  - 对任意 $\cat$ 中对象 $\obj$ 
    $\obj\Phi$  为 $\cat[D]$ 中对象且
    $\getid {\obj}\Phi=\getid{\obj\Phi}$ ;
  - 对任意 $\cat$ 中箭头 $\phi_1:\obj[c_1]\cathom \obj[c_2]$ 和 $\phi_2:\obj[c_2]\cathom\obj[c_3]$ , 
    始终都有等式 $\,(\phi_1\catcirc \phi_2)\Phi=\phi_1\Phi\catcirc[{\cat[D]}]\phi_2\Phi\,$ 成立 。

假如 $\cat$ , $\cat[D]$ 皆为**局部小范畴** , 并且
刚才的 $\Phi$ 确实构成一个函子 ,   则

- $\Phi$ 是**忠实的**当且仅当对任意 $\cat$ 中对象 $\obj[c_1]$ 和 $\obj[c_2]$
  $(\obj[c_1]\cathom\obj[c_2])$ 与 $(\obj[c_1]\Phi\cathom[{\cat[D]}]\obj[c_2]\Phi)$ 之间始终存在单射 ;
- $\Phi$ 是**完全的**当且仅当对任意 $\cat$ 中对象 $\obj[c_1]$ 和 $\obj[c_2]$
  $(\obj[c_1]\cathom\obj[c_2])$ 与 $(\obj[c_1]\Phi\cathom[{\cat[D]}]\obj[c_2]\Phi)$ 之间始终存在满射 ;
- $\Phi$ 是**完全忠实的**当且仅当
  $\cathom$ 与 $\cathom[{\cat[D]}]$ 间存在自然同构 , 即
  $(\obj[c_1]\cathom\_)$ 与 $(\obj[c_1]\cathom[{\cat[D]}]\_)$ 间存在自然同构

----

若还知道 $F_1,F_2,G_1,G_2:\cat\cathom[\catCat]\cat[D]$ 
为函子 , 则有

- $\qquad\vcenter{\begin{xy}\xymatrix@!R=1cm@!C=2cm{
  {\obj[x_1]\bbox[LightGreen]{\Phi}\pila} 
  \ar[r]^{\obj[x_1]^\natural\pila} 
  \ar[d]_{f_1\bbox[LightGreen]{\Phi}\pila} &
  {\obj[x_1]\bbox[LightGreen]{\Psi}\pila} 
  \ar[d]^{f_2\bbox[LightGreen]{\Psi}\pila}  \\
  {\obj[x_2]\bbox[LightGreen]{\Phi}\pila} 
  \ar[r]_{\obj[x_2]^\natural\pila} 
  \save[].[u]*+<3pt>[F-:<5pt>:ForestGreen]\frm{} !D*!U{\small\color{ForestGreen}\cat \Phi}\restore
  &
  {\obj[x_2]\bbox[LightGreen]{\Psi}\pila}  
  \save[].[u]*+<3pt>[F-:<5pt>:ForestGreen]\frm{} !D*!U{\small\color{ForestGreen}\cat \Psi}\restore
  }\end{xy}}$ 

- $\cat$ 中的映射 : $\phi$ , $\cat$ 中对象 : $\obj$
  $\cat[D]$ 中的映射 : $\psi$ , $\cat[D]$ 中对象 : $\obj[d]$ 
  映射的复合 : $\phi_1\circ \phi_2$ , $\psi_1\circ\psi_2$ 
- 函子 $\Phi:\cat\cathom[\catCat] \cat[D]$ ,
  函子 $\Psi:\cat\cathom[\catCat]\cat[D]$ , 
  函子的复合 : $\Phi_1\circ \Phi_2$ , $\Psi_1\circ \Psi_2$
- 自然变换 $\natural:\Phi\cathom[]\Psi$ , 自然变换 $\sharp:\Psi\cathom[]\Upsilon$ 
  自然变换 $\natural_1 : \Phi_1\cathom[]\Phi_2$ , 自然变换 $\natural_2:\Phi_2\cathom[]\Phi_3$ 
  自然变换的纵复合 : $\natural\circ\sharp$ ,
  自然变换的横复合 : $\natural_1\circ_{\rm h}\natural_2$ , 

----

- 函子 $\Phi_1:\cat\cathom[\catCat]\cat[D]$
  函子 $\Phi_2: \cat\cathom[\catCat]\cat[D]$ 
  函子的复合 : $\Phi\circ\Psi\circ\Upsilon$ ,
- 自然变换 $\natural_1 : \Phi_1\cathom[]\Phi_2$ , 自然变换 $\natural_2:\Phi_1\cathom[]\Phi_2$ 
  自然变换的纵复合 : $\natural_1\circ\natural_2$ , 