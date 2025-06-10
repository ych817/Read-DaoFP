## 章节 08 - 09 函子与自然变换

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

### 一些特殊的范畴

现在规定几种特殊的范畴 。

- **离散范畴** : 只有对象不含箭头 ( 恒等箭头除外 ) 的范畴 。
- $\catSet$ : **所有集合构成的范畴** , 为局部小范畴 , 满足

  - $\catSet$ 中对象为任意集合 ;
  - $\catSet$ 中箭头为集合间映射 。
- $\catCat$ : **所有范畴构成的范畴** , 满足
  - $\catCat$ 中任何对象都构成一个范畴 ;
  - $\catCat$ 中任何箭头都构成一个函子 。

若 $\cat$ , $\cat[D]$ 为 $\catCat$ 中对象 , 则 :

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

- $\cat\cathom[\catCat]\cat[D]$ : **所有 $\cat$ 到 $\cat[D]$ 的函子的范畴** , 满足

  - $\cat\cathom[\catCat]\cat[D]$ 中任何对象
    都是 $\cat$ 到 $\cat[D]$ 的函子 ;
  - $\cat\cathom[\catCat]\cat[D]$ 中任何箭头
    都是函子间自然变换 。

- $\cat/\obj$ : **俯范畴** , 这里 $\obj$ 为任意 $\cat$ 中对象 ; 满足

  - $\cat/\obj$ 中对象皆形如 $\cancel{\smash[b]{\obj[x]\cons \objt\cons}} \phi$ , 其中 $\obj[x]$ 
    和 $\phi:\obj[x]\cathom \obj$ 分别为 $\cat$ 中任意的对象和箭头 ;

  - $\obj/\cat$ 中箭头皆形如 $f_1\!\cancel{\cons \getid{\obj}}\!$ 且满足下述交换图 , 其中
    $\obj[x_1]$ , $\obj[x_2]$ 为 $\cat$ 中任意对象且 $f_1$ , $\phi_1$ , $\phi_2$ 为 $\cat$ 中任意箭头 ; 

    $\vcenter{\begin{xy}\xymatrix@!R=1cm@!C=2cm{
    {\obj[x_2]\pila} 
    \ar[r]^{\phi_1\pila} &
    {\obj\pila}  \\
    {\obj[x_1]\pila} 
    \ar[r]_{\phi_2\pila}
    \ar[u]^{\mathllap{f_1\pila}} 
    \save[].[u]*+<3pt>[F-:<5pt>:ForestGreen]\frm{} !D*!U{\small\color{ForestGreen}\cat}\restore &
    {\obj\pila}
    \ar[u]_{\getid{\objt}\pila} 
    \save[].[u]*+<3pt>[F-:<5pt>:ForestGreen]\frm{} !D*!U{\small\color{ForestGreen}\cat[1](\obj\catdiag)}\restore
    \save[ul].[]*+<10pt>[F-:<8pt>:ForestGreen]\frm{} 
    !U*!D!L(8){\small\color{ForestGreen}\cat}\restore 
    }\end{xy}}$ $\quad\vcenter{\begin{xy}\xymatrix@!R=1cm@!C=2cm{
    {\obj[x_2]\bbox[LightGreen]{\getid{\cat}}\pila} 
    \ar[r]^{\phi_1\pila} &
    {\objt\bbox[LightGreen]{(\obj\catdiag)}\pila}  \\
    {\obj[x_1]\bbox[LightGreen]{\getid{\cat}}\pila} 
    \ar[r]_{\phi_2\pila} 
    \ar[u]^{\mathllap{f_1\bbox[LightGreen]{\getid{\cat}}\pila}} 
    \save[].[u]*+<3pt>[F-:<5pt>:ForestGreen]\frm{} !D*!U{\small\color{ForestGreen}\cat\bbox[LightGreen]{\getid{\cat}}}\restore 
    &
    {\objt\bbox[LightGreen]{(\obj\catdiag)}\pila}
    \ar[u]_{\mathrlap{\getid{\objt}\bbox[LightGreen]{(\obj\catdiag)}\pila}}  
    \save[].[u]*+<3pt>[F-:<5pt>:ForestGreen]\frm{} !D*!U{\small\color{ForestGreen}\cat[1](\bbox[LightGreen]{\obj\catdiag\pila})}\restore
    \save[ul].[]*+<10pt>[F-:<8pt>:ForestGreen]\frm{} !U*!D!L(8){\small\color{ForestGreen}\cat}\restore  
     } \end{xy}}$ $\quad \vcenter{\begin{xy}\xymatrix@!C=2cm{ 
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

- $\obj/\cat$ : **仰范畴** , 这里 $\obj$ 为任意 $\cat$ 中对象 ; 满足

  - $\obj/\cat$ 中对象皆形如 $\cancel{\smash[b]{\objt\cons \obj[x]\cons{}}}\! \phi$ , 其中 $\obj[x]$ 
    和 $\phi:\obj\cathom \obj[x]$ 分别为 $\cat$ 中对象和箭头 ;

  - $\cat/\obj$ 中箭头皆形如 $\!\cancel{\getid {\obj}\!\cons} g_1$ 且满足下述交换图 , 其中
    $\obj[x_1]$ , $\obj[x_2]$ 为 $\cat$ 中任意对象且 $g_1$ , $\phi_1$ , $\phi_2$ 为 $\cat$ 中任意箭头 ; 

    $\vcenter{\begin{xy}\xymatrix@!R=1cm@!C=2cm{
    {\obj\pila}
    \ar[r]^{\phi_1\pila}  
    \ar[d]_{\mathclap{\getid{\objt}\pila}}
    &
    {\obj[x_1]\pila} 
    \ar[d]^{g_1\pila} 
    \\
    {\obj\pila}
    \save[].[u]*+<3pt>[F-:<5pt>:ForestGreen]\frm{} !D*!U{\small\color{ForestGreen}\cat[1](\obj\catdiag)}\restore
    \ar[r]_{\phi_2\pila} 
    &
    {\obj[x_2]\pila} 
    \save[].[u]*+<3pt>[F-:<5pt>:ForestGreen]\frm{} !D*!U{\small\color{ForestGreen}\cat}\restore\save[ul].[]*+<10pt>[F-:<8pt>:ForestGreen]\frm{} 
    !U*!D!L(8){\small\color{ForestGreen}\cat}\restore  
    }\end{xy}}$ $\quad\vcenter{\begin{xy}\xymatrix@!R=1cm@!C=2cm{
    {\objt\bbox[LightGreen]{(\obj\catdiag)}\pila} 
    \ar[d]_{\mathllap{\getid{\objt}\bbox[LightGreen]{(\obj\catdiag)}\pila}}  
    \ar[r]^{\phi_1\pila}
    &
    {\obj[x_1]\bbox[LightGreen]{\getid{\cat}}\pila} 
    \ar[d]^{\mathrlap{g_1\bbox[LightGreen]{\getid{\cat}}\pila}} 
    \\
    {\objt\bbox[LightGreen]{(\obj\catdiag)}\pila}
    \ar[r]_{\phi_2\pila}  
    \save[].[u]*+<3pt>[F-:<5pt>:ForestGreen]\frm{} !D*!U{\small\color{ForestGreen}\cat[1](\bbox[LightGreen]{\obj\catdiag\pila})}\restore
    &
    {\obj[x_2]\bbox[LightGreen]{\getid{\cat}}\pila} 
    \save[].[u]*+<3pt>[F-:<5pt>:ForestGreen]\frm{} !D*!U{\small\color{ForestGreen}\cat\bbox[LightGreen]{\getid{\cat}}}\restore
    \save[ul].[]*+<10pt>[F-:<8pt>:ForestGreen]\frm{} !U*!D!L(8){\small\color{ForestGreen}\cat}\restore 
    }\end{xy}}$ $\quad \vcenter{\begin{xy}\xymatrix@!C=2cm{ 
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

### 函子

接下来我们来提供函子的正式定义 : 

- $P:\cat\cathom[\catCat]\cat[D]$ 为范畴当且仅当
  - 对任意 $\cat$ 中对象 $\obj$ , $\obj P$ 为 
    $\cat[D]$ 中对象且 $\getid {\obj}P=\getid{\obj P}$ ;
  - 对任意 $\cat$ 中箭头 $\phi_1:\obj[c_1]\cathom \obj[c_2]$ 和 $\phi_2:\obj[c_2]\cathom\obj[c_3]$ , 
    始终都有等式 $\,(\phi_1\catcirc \phi_2) P=\phi_1 P\catcirc[{\cat[D]}]\phi_2P$ 成立 。

### 函子的复合运算

假如刚才的 $P$ 确实构成一个函子
且 $Q: \cat[D]\cathom[\catCat]\cat[E]$ 也构成函子 , 那么

- $P\catcirc[\catCat] Q: \cat\cathom[\catCat] \cat[E]$ 
  也构成一个函子 。

### 恒等函子

对于函子我们也有恒等映射 , 即 :

- $\begin{aligned}[t]
  \getid{\cat}\catcirc[\catCat] P & = P \\
                                  & = P\catcirc[\catCat]\getid{\cat[D]}
  \end{aligned}$ 

### 忠实 , 完全和本质满函子

若 $\cat$ , $\cat[D]$ , $\cat[E]$ 皆为**局部小范畴** , 则

- $P$ 是**忠实的**当且仅当对任意 $\cat$ 中的对象 $\obj[c_1]$ , $\obj[c_2]$
  $(\obj[c_1]\cathom\obj[c_2])$ 与 $(\obj[c_1]P\cathom[{\cat[D]}]\obj[c_2]P)$ 之间始终存在单射 ;
- $P$ 是**完全的**当且仅当对任意 $\cat$ 中的对象 $\obj[c_1]$ , $\obj[c_2]$
  $(\obj[c_1]\cathom\obj[c_2])$ 与 $(\obj[c_1]P\cathom[{\cat[D]}]\obj[c_2]P)$ 之间始终存在满射 ;
- $P$ 是**完全忠实的**当且仅当对任意 $\cat$ 中的对象 $\obj[c_1]$ , $\obj[c_2]$
  $(\obj[c_1]\cathom\obj[c_2])$ 与 $(\obj[c_1]P\cathom[{\cat[D]}]\obj[c_2]P)$ 之间始终存在双射 。

> [!note]
>
> 刚才提到的 “ 单 / 满 / 双射 ”
> 针对的都是范畴的箭头部分 。

- $P$ 是**本质满的**当且仅当对任意 $\cat[D]$ 中对象 $\obj[d]$
  都存在 $\cat$ 中对象 $\obj$ 使 $\obj P\cathom[{\cat[D]}]\obj[d]$ 之间有双射 。

> [!tip]
>
> 不难发现
>
> - 忠实函子的复合是忠实函子
> - 完全函子的复合是完全函子
> - 完全忠实函子的复合是完全忠实函子
> - 若两个函子中有一个是完全忠实函子 , 
>   且它们的复合也是一个完全忠实函子 , 
>   则剩下的那个函子也是完全忠实函子 。
> - 本质满函子的复合是本质满函子

<div style="page-break-after: always"></div>

### 自然变换

如果还知道 $P':\cat\cathom[\catCat]\cat[D]$ 为函子 , 那么

- $\eta : P\cathom[{\cat\cathom[\catCat]\cat[D]}]P'$ 为自然变换当且仅当对任意 
  $\cat$ 中对象 $\obj[x_1]$ , $\obj[x_2]$ 始终都会有下述交换图成立 : 

  $\vcenter{\begin{xy}\xymatrix@!R=1cm@!C=2cm{
  {\obj[x_1]\bbox[LightGreen]{P}\pila} 
  \ar[r]^{\obj[x_1]^{\eta}\pila} 
  \ar[d]_{f_1\bbox[LightGreen]{P}\pila} &
  {\obj[x_1]\bbox[LightGreen]{P'}\pila} 
  \ar[d]^{f_1\bbox[LightGreen]{P'}\pila}  \\
  {\obj[x_2]\bbox[LightGreen]{P}\pila} 
  \ar[r]_{\obj[x_2]^{\eta}\pila} 
  \save[].[u]*+<3pt>[F-:<5pt>:ForestGreen]\frm{} !D*!U{\small\color{ForestGreen}\cat P}\restore
  &
  {\obj[x_2]\bbox[LightGreen]{P'}\pila}  
  \save[].[u]*+<3pt>[F-:<5pt>:ForestGreen]\frm{} !D*!U{\small\color{ForestGreen}\cat P'}\restore
  \save[ul].[]*+<10pt>[F-:<8pt>:ForestGreen]\frm{} !U*!D!L(6){\small\color{ForestGreen}\cat[D]}\restore 
  }\end{xy}}$ $\quad \vcenter{\begin{xy}\xymatrix@!R=1cm@!C=2cm{ 
  \cat\pila
  \ar@`{[]+/l+3pc/,[d]+/l+3pc/}[d]^(.5){}="mid1"|{P\pila}
  \ar@`{[]+/r+3pc/,[d]+/r+3pc/}[d]_(.5){}="mid2"|{P'\pila}
  \\
  \cat[D]\pila
  \ar@2{>} "mid1";"mid2"^{\eta\pila}
  }\end{xy}}$ 

### 自然变换的复合

若已知 $\eta: P\cathom[{\cat\cathom[\catCat]\cat[D]}]P'$ 构成自然变换且
还知道 $\eta':P'\cathom[{\cat\cathom[\catCat]\cat[D]}]P''$ 为自然变换则

- $\eta~~\catcirc[{\cat\cathom[\catCat]\cat[D]}]~~\eta': P\cathom[{\cat\cathom[\catCat]\cat[D]}]P'$ 为自然变换 , 
  称作 $\eta$ 和 $\eta'$ 的**纵复合** 。
  
  $\vcenter{\begin{xy}\xymatrix@!R=1cm@!C=2cm{
  {\obj[x_1]\bbox[LightGreen]{P}\pila} 
  \ar[r]^{\obj[x_1]^{\eta}\pila} 
  \ar[d]_{f_1\bbox[LightGreen]{P}\pila} &
  {\obj[x_1]\bbox[LightGreen]{P'}\pila}
  \ar[r]^{\obj[x_1]^{\eta'}\pila} 
  \ar[d]^{f_1\bbox[LightGreen]{P'}\pila} & 
  {\obj[x_1]\bbox[LightGreen]{P''}\pila} 
  \ar[d]^{f_1\bbox[LightGreen]{P''}\pila} & 
  \\
  {\obj[x_2]\bbox[LightGreen]{P}\pila} 
  \ar[r]_{\obj[x_2]^{\eta}\pila} 
  \save[].[u]*+<3pt>[F-:<5pt>:ForestGreen]\frm{} !D*!U{\small\color{ForestGreen}\cat P}\restore
  &
  {\obj[x_2]\bbox[LightGreen]{P'}\pila}  
  \ar[r]_{\obj[x_2]^{\eta'}\pila} 
  \save[].[u]*+<3pt>[F-:<5pt>:ForestGreen]\frm{} !D*!U{\small\color{ForestGreen}\cat P'}\restore
  & 
  {\obj[x_2]\bbox[LightGreen]{P''}\pila}
  \save[].[u]*+<3pt>[F-:<5pt>:ForestGreen]\frm{} !D*!U{\small\color{ForestGreen}\cat P''}\restore
  \save[ull].[]*+<10pt>[F-:<8pt>:ForestGreen]\frm{} !U*!D!L(12){\small\color{ForestGreen}\cat[D]}\restore 
  }\end{xy}}$ $\quad \vcenter{\begin{xy}\xymatrix@!R=1cm@!C=2cm{ 
  \cat\pila
  \ar@`{[]+/l+3pc/,[d]+/l+3pc/}[d]^(.5){}="mid1"|{P\pila}
  \ar@`{[]+/r+0pc/,[d]+/r+0pc/}[d]_(.5){}="mid2a"^(.5){}="mid2b"|{P'\pila}
  \ar@`{[]+/r+3pc/,[d]+/r+3pc/}[d]_(.5){}="mid3"|{P''\pila}
  \\
  \cat[D]\pila
  \ar@2{>} "mid1";"mid2a"^{\eta\pila}
  \ar@2{>} "mid2b";"mid3"^{\eta'\pila}
  }\end{xy}}$ 

如果还知道 $Q':\cat[D]\cathom[\catCat]\cat[E]$ 也是个函子
以及自然变换 $\theta: Q\cathom[{\cat[D]\cathom[\catCat]\cat[E]}]Q'$  ,  则有

- $\eta\circ \theta : P\catcirc[\catCat]Q \cathom[{\cat\cathom[\catCat]\cat[E]}]P'\catcirc[\catCat]Q'$ 为自然变换 , 
  称作 $\eta$ 和 $\theta$ 的**横复合** 。
  
  $\vcenter{\begin{xy}\xymatrix@!R=1cm@!C=2cm{
  &
  {\obj[x_1]\bbox[LightGreen]{P}\pila} 
  \ar[r]^{\obj[x_1]^{\eta}\pila} 
  \ar[d]_{\mathllap{f_1\bbox[LightGreen]{P}\pila}} 
  \ar@{->}@[lightgray][ddl]|[lightgray]{Q} 
  \ar@{->}@[lightgray][dddr]|[lightgray]{Q'} 
  &
  {\obj[x_1]\bbox[LightGreen]{P'}\pila} 
  \ar[d]^{\mathrlap{f_1\bbox[LightGreen]{P'}\pila}} 
  \ar@{->}@[lightgray][ddl]|[lightgray]{Q} 
  \ar@{->}@[lightgray][dddr]|[lightgray]{Q'} 
  & \\
  &
  {\obj[x_2]\bbox[LightGreen]{P}\pila} 
  \ar[r]_{\obj[x_2]^{\eta}\pila} 
  \ar@{->}@[lightgray][ddl]|[lightgray]{Q} 
  \ar@{->}@[lightgray][dddr]|[lightgray]{Q'} &
  {\obj[x_2]\bbox[LightGreen]{P'}\pila}
  \ar@{->}@[lightgray][ddl]|[lightgray]{Q}
  \ar@{->}@[lightgray][dddr]|[lightgray]{Q'} 
  \save[ul].[]*+<10pt>[F-:<8pt>:ForestGreen]\frm{} !U*!D!L(6){\small\color{ForestGreen}\cat[D]}\restore  & & \\
  {\obj[x_1]\bbox[LightGreen]{PQ}\pila} 
  \ar[r]^{\obj[x_1]^{\eta}\bbox[LightGreen]{Q}\pila} 
  \ar[d]_{\mathllap{f_1\bbox[LightGreen]{PQ}\pila}} 
  \ar@[gray][drr]|(.7)[gray]{(\obj[x_1]P)^\theta\pila} &
  {\obj[x_1]\bbox[LightGreen]{P'Q}\pila} 
  \ar[d]^{\mathrlap{f_1\bbox[LightGreen]{P'Q}\pila}} 
  \ar@[gray][drr]|(.3)[gray]{(\obj[x_1]P')^\theta\pila} \\
  {\obj[x_2]\bbox[LightGreen]{PQ}\pila} 
  \ar[r]_{\obj[x_2]^{\eta}\bbox[LightGreen]{Q}\pila} 
  \ar@[gray][drr]|(.7)[gray]{(\obj[x_2]P)^\theta\pila} &
  {\obj[x_2]\bbox[LightGreen]{P'Q}\pila}  
  \ar@[gray][drr]|(.3)[gray]{(\obj[x_2]P')^\theta\pila}
  \save[ul].[]*+<10pt>[F-:<8pt>:ForestGreen]\frm{} !D*!U!L(7){\small\color{ForestGreen}\cat[E]}\restore &
  {\obj[x_1]\bbox[LightGreen]{PQ'}\pila} 
  \ar[r]^{\obj[x_1]^{\eta}\bbox[LightGreen]{Q'}\pila} 
  \ar[d]_{\mathllap{f_1\bbox[LightGreen]{PQ'}\pila}} &
  {\obj[x_1]\bbox[LightGreen]{P'Q'}\pila} 
  \ar[d]^{\mathrlap{f_1\bbox[LightGreen]{P'Q'}\pila}}  \\
  & & 
  {\obj[x_2]\bbox[LightGreen]{PQ'}\pila} 
  \ar[r]_{\obj[x_2]^{\eta}\bbox[LightGreen]{Q'}\pila} &
  {\obj[x_2]\bbox[LightGreen]{P'Q'}\pila}  
  \save[ul].[]*+<10pt>[F-:<8pt>:ForestGreen]\frm{} !D*!U!L(7){\small\color{ForestGreen}\cat[E]}\restore 
  }\end{xy}}$ $\quad \vcenter{\begin{xy}\xymatrix@!R=1cm@!C=2cm{ 
  \cat\pila
  \ar@`{[]+/l+3pc/,[d]+/l+3pc/}[d]^(.5){}="mida1"|{P\pila}
  \ar@`{[]+/r+3pc/,[d]+/r+3pc/}[d]_(.5){}="mida2"|{P'\pila}
  \\
  \cat[D]\pila
  \ar@2{>} "mida1";"mida2"^{\eta\pila}
  \ar@`{[]+/l+3pc/,[d]+/l+3pc/}[d]^(.5){}="midb1"|{Q\pila}
  \ar@`{[]+/r+3pc/,[d]+/r+3pc/}[d]_(.5){}="midb2"|{Q'\pila}
  \\
  \cat[E]\pila
  \ar@2{>} "midb1";"midb2"^{\theta\pila}
  }\end{xy}}$

若 $\theta': Q'\cathom[{\cat[D]\cathom[\catCat]\cat[E]}]Q''$ 为自然变换则

- $(\eta\circ\theta)~~\catcirc[{\cat\cathom[\catCat]\cat[E]}]~~(\eta'\circ\theta') = (\eta ~~\catcirc[{\cat\cathom[\catCat]\cat[D]}]~~ \eta')\circ (\theta ~~\catcirc[{\cat[D]\cathom[\catCat]\cat[E]}]~~\theta')$ , 
  改变横纵复合的先后顺序也不会影响最终结果 。

  $\vcenter{\begin{xy}\xymatrix@!R=1cm@!C=2cm{ 
  \cat\pila
  \ar@`{[]+/l+3pc/,[d]+/l+3pc/}[d]^(.5){}="mida1"|{P\pila}
  \ar@`{[]+/r+0pc/,[d]+/r+0pc/}[d]_(.5){}="mida2a"^(.5){}="mida2b"|{P'\pila}
  \ar@`{[]+/r+3pc/,[d]+/r+3pc/}[d]_(.5){}="mida3"|{P''\pila}
  \\
  \cat[D]\pila
  \ar@2{>} "mida1";"mida2a"^{\eta\pila}
  \ar@2{>} "mida2b";"mida3"^{\eta'\pila}
  \ar@`{[]+/l+3pc/,[d]+/l+3pc/}[d]^(.5){}="midb1"|{Q\pila}
  \ar@`{[]+/r+0pc/,[d]+/r+0pc/}[d]_(.5){}="midb2a"^(.5){}="midb2b"|{Q'\pila}
  \ar@`{[]+/r+3pc/,[d]+/r+3pc/}[d]_(.5){}="midb3"|{Q''\pila}
  \\
  \cat[E]\pila
  \ar@2{>} "midb1";"midb2a"^{\theta\pila}
  \ar@2{>} "midb2b";"midb3"^{\theta'\pila}
  }\end{xy}}$

<div style="page-break-after: always"></div>

### 恒等自然变换

同样对于自然变换也有恒等映射 。

- $\begin{aligned}[t]
  \getid{P}&:P\cathom[{\cat[C]\cathom[\catCat] \cat[D]}] P \\
  \obj[x]^{\getid{P}}&: \obj[x]P\cathom[{\cat[D]}] \obj[x]P \\
  \obj[x]^{\getid{P}}&:= \getid{\obj[x_1]P}
  \end{aligned}$ , 并且对范畴 $\cat$ 中任意对象 $\obj[x]$ 都会有

### 自然同构

在范畴论中我们更关心的是自然同构 。

- $\eta : P\cathom[{\cat\cathom[\catCat]\cat[D]}]P'$ 为**自然同构**当且仅当
  $\obj[x]^\eta$ 总是同构 , 这里 $\obj[x]$ 为任意 $\cat$ 中对象 。

<div style="page-break-after: always"></div>

---

- 函子 $P:\cat\cathom[\catCat] \cat[D]$ ,
  函子 $Q:\cat\cathom[\catCat]\cat[D]$ , 
  函子的复合 : $P\circ Q$ 
- 自然变换 $\eta_1:P_1\cathom[\catCat] Q_1$ , 
  自然变换 $\eta_2: P_1\cathom[\catCat] Q_1$ ,
  自然变换 $\theta_1: Q_1\cathom[\catCat]R_1$ 
  自然变换的纵复合 : $\eta_1\circ_\rm v\eta_2$ ,
  自然变换的横复合 : $\eta_1\circ_{\rm h}\theta_1$ , 
