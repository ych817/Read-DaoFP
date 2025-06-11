## 章节 06 类型的幂

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
% 打印常/变量名
\newcommand{\obj}[1][c]{{\sf #1}}              % 对象
\def\obji{\obj[{0}]}                           % 对象 : 始
\def\objt{\obj[{1}]}                           % 对象 : 终
\newcommand{\cat}[1][C]{{\sf #1}}              % 范畴 : C(默认)
\def\catCat{\cat[Cat]}                         % 范畴 : Cat
\def\catSet{\cat[Set]}                         % 范畴 : Set
\def\catHask{\cat[Hask]}                       % 范畴 : Hask — 笛卡尔闭范畴 (+/× 都在里面)
\newcommand{\catcirc}[1][\cat]{                % 范畴 C 中的复合运算
  \catbfunc[#1]{\circ}}
\newcommand{\catufunc}[2][\cat]{\smash{        % 范畴 C 中的函子 : 一元
  \overset{\mclap{\small\pila #1}}{#2}}}
\newcommand{\catbfunc}[2][\cat]{\mbin{\smash{  % 范畴 C 中的函子 : 二元
  \overset{\mclap{\small\pila #1}}{#2}}}}
\newcommand{\catbrel}[2][\cat]{\mrel{\smash{   % 范畴 C 中的同构
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
\newcommand{\catcong}[1][\cat]{                % 范畴 C 中的同构
  \catbrel[#1]{\cong}}
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

### 泛性质

默认函子 $\cathom:\cat\cattimes[\catCat]\cat\cathom[\catCat]\cat$ 在范畴 $\cat$ 中有下述性质 : 

- $\underline{\smash[b]{(\obj[a]\cattimes \obj[x])\cathom\obj[b]}}\cong \underline{\smash[b]{\obj[x] \cathom(\obj[a]\cathom \obj[b])}}\cong \underline{\smash[b]{\obj[a]\cathom(\obj[x]\cathom \obj[b])}}$ , $\obj[x]$ 为任意 $\cat$ 中对象
  —— **泛性质** , 指数与加乘法运算间的关系 。 下图便于理解证明 : 

  $\vcenter{\begin{xy}\xymatrix@!C=2cm{
  {\obj[a]\cathom \obj[b]\pila}
  & 
  {\obj[a]\cattimes (\obj[a]\cathom\obj[b])\pila} 
  \ar[r]^{\varepsilon\pila} 
  &
  {\obj[b]\pila}
  \ar@{|->}@`{[]+/u+3pc/,[ll]+/u+3pc/}[ll]_{(\obj[a]\cathom\_)\pila}
  \\ 
  {\obj[x]\pila}
  \ar@[red]@{-->}[u]^[red]{h\pila} 
  \ar@{|->}@`{[]+/d+2pc/,[r]+/d+2pc/}[r]_{(\obj[a]\cattimes\_)\pila}
  \save[].[u]*+<3pt>[F-:<5pt>:ForestGreen]\frm{}
  !R*!L{\small\color{ForestGreen}\cat}\restore
  &  
  {\obj[a]\cattimes\obj[x]\pila}  
  \ar@[red]@{-->}[u]^[red]{\getid{\obj[a]}\catotimes h\pila} 
  \ar@[magenta][ur]_[magenta]{j\pila} 
  \save[].[u].[ur]*+<3pt>[F-:<5pt>:ForestGreen]\frm{}
  !R*!L{\small\color{ForestGreen}\cat}\restore
  &
  }\end{xy}}$ 

### 函子性

如何证明 $\cathom$ 构成函子呢 ? 请看

- $\cathom:(\getid{\obj[a_1]}\cons \getid{\obj[b_1]})\longmapsto \getid{\smash{(\obj[a_1] \cathom \obj[b_1])}}$ 
  —— 即函子 $\cathom$ 能**保持恒等箭头** ;

- $\cathom:(f_2\catcirc f_1\cons g_1\catcirc g_2)\longmapsto h_1\catcirc h_2$ 
  —— 即函子 $\cathom$ **保持箭头复合运算** 。
  下图有助于形象理解证明过程 : 

  $\begin{array}{l}
  \vcenter{\begin{xy}\xymatrix@!C=2cm{
  {\obj[a_3]\cathom\obj[b_3]\pila}
  &
  {\obj[a_3]\cattimes (\obj[a_3]\cathom\obj[b_3])\pila} 
  \ar[r]^{\qquad\varepsilon\pila} 
  &
  {\obj[b_3]\pila}
  \\   
  {\obj[a_2]\cathom\obj[b_2]\pila}
  \ar@[red]@{-->}[u]^[red]{h_2\pila} 
  \save[].[u]*+<3pt>[F-:<5pt>:ForestGreen]\frm{}
  !R*!L{\small\color{ForestGreen}\cat}\restore
  &
  {\obj[a_3]\cattimes(\obj[a_2]\cathom\obj[b_2])\pila}  
  \ar@[red]@{-->}[u]^[red]{\getid{\obj[a_3]}\catotimes h_2\pila} 
  \ar@[magenta][ur]_[magenta]{j_2\pila} 
  \save[].[u].[ur]*+<3pt>[F-:<5pt>:ForestGreen]\frm{}
  !R*!L{\small\color{ForestGreen}\cat}\restore
  &
  }\end{xy}}
  \\[-5pt]
  \vcenter{\begin{xy}\xymatrix@!C=2cm{
  {\obj[a_2]\cathom\obj[b_2]\pila}
  &
  {\obj[a_2]\cattimes (\obj[a_2]\cathom\obj[b_2])\pila} 
  \ar[r]^{\qquad\varepsilon\pila} 
  &
  {\obj[b_2]\pila}
  \\
  {\obj[a_1]\cathom\obj[b_1]\pila}
  \ar@[red]@{-->}[u]^[red]{h_1\pila} 
  \save[].[u]*+<3pt>[F-:<5pt>:ForestGreen]\frm{}
  !R*!L{\small\color{ForestGreen}\cat}\restore
  &
  {\obj[a_2]\cattimes(\obj[a_1]\cathom\obj[b_1])\pila}  
  \ar@[red]@{-->}[u]^[red]{\getid{\obj[a_2]}\catotimes h_1\pila} 
  \ar@[magenta][ur]_[magenta]{j_1\pila} 
  \save[].[u].[ur]*+<3pt>[F-:<5pt>:ForestGreen]\frm{}
  !R*!L{\small\color{ForestGreen}\cat}\restore
  &
  }\end{xy}}
  \end{array}$ $\qquad \vcenter{\begin{xy}\xymatrix@!C=2cm@!R=1.5cm{
  {\obj[a_1]\pila}
  \ar[rr]^(.75){\varphi_1: \obj[a_1]\cathom\obj[b_1]\pila} 
  & 
  \vph{\large x}
  \ar@{|-->}[d]_{h_1=f_1\cathom g_1\pila}
  & 
  {\obj[b_1]\pila}
  \ar[d]^{g_1\pila}
  \\
  {\obj[a_2]\pila}
  \ar[u]^{f_1\pila} 
  \ar[rr]^(.75){\varphi_2: \obj[a_2]\cathom\obj[b_2]\pila} 
  & 
  \vph{\large x}
  \ar@{|-->}[d]_{h_2=f_2\cathom g_2\pila}
  & 
  {\obj[b_2]\pila}
  \ar[d]^{g_2\pila} 
  \\
  {\obj[a_3]\pila}
  \ar[u]^{f_2\pila} 
  \ar[rr]^(.75){\varphi_3: \obj[a_3]\cathom\obj[b_3]\pila}
  \save[].[uu]*+<3pt>[F-:<5pt>:ForestGreen]\frm{} !UR*!L{\smash{\small\color{ForestGreen}\cat}}\restore 
  &  
  \vph{\large x}
  & 
  {\obj[b_3]\pila}
  \save[].[uu]*+<3pt>[F-:<5pt>:ForestGreen]\frm{}
  !UL*!R{\smash{\small\color{ForestGreen}\cat}}\restore 
  \\
  }\end{xy}}$ 

下图 ( 自上到下分别为图 1 和图 2 ) 后面会用到 。

$\hspace{175pt}\begin{xy}\xymatrix@!C=2cm@R=.5cm{
\obj[a_1]\pila 
\ar@`{[]+/r+3pc/,[drr]+/ul+3pc/}[drr]
^(.7){\varphi_1:\obj[a_1]\cathom\obj[b_1]}
_(.5){}="mid1"
&
&\vph{\obj[a_1]}
\\
\ar@{}@`{[]+/dl+5pc/,[]+/ul+5pc/}[]^{\ph{\getid{\obj[b_1]}} }
&
&
\obj[b_1]\pila
\ar@`{[]+/ur+5pc/,[]+/dr+5pc/}[]^{\getid{\obj[b_1]}}
\\
\obj[a_2]\pila 
\ar[uu]^{f_1\pila}
\ar@`{[]+/r+3pc/,[urr]+/dl+3pc/}[urr]
_(.7){(f_1\catcirc \varphi_1):\obj[a_2]\cathom\obj[b_3]}
^(.5){}="mid2"
\ar@{|-->} "mid1";"mid2"^{\obj[b_1]^{(f_1\catcirc\_)}}
\save[].[uu]*+<3pt>[F-:<5pt>:ForestGreen]\frm{} !UR*!L{\smash{\small\color{ForestGreen}\cat}}\restore 
& &\vph{\obj[a_2]}
\save[].[u].[uu]*+<3pt>[F-:<5pt>:ForestGreen]\frm{} !UL*!R{\smash{\small\color{ForestGreen}\cat}}\restore 
}\end{xy}$ 

$\hspace{175pt}\vcenter{\begin{xy}\xymatrix@!C=2cm@R=.5cm{ 
\vph{\obj[b_1]}
&  
&  
\obj[b_1]\pila \ar[dd]^{g_1\pila} 
\\ 
\obj[a_1]\pila 
\ar@`{[]+/dl+5pc/,[]+/ul+5pc/}[]^{\getid{\obj[a_1]}} 
\ar@`{[]+/ur+3pc/,[urr]+/l+3pc/}[urr] 
^(.7){\varphi_1:\obj[a_1]\cathom\obj[b_1]} 
_(.5){}="mid1" 
\ar@`{[]+/dr+3pc/,[drr]+/l+3pc/}[drr] 
_(.7){(\varphi_1\catcirc g_1):\obj[a_1]\cathom\obj[b_2]} 
^(.5){}="mid2" 
&
& 
\\ 
\vph{\obj[b_2]}
\save[].[u].[uu]*+<3pt>[F-:<5pt>:ForestGreen]\frm{} !UR*!L{\smash{\small\color{ForestGreen}\cat}}\restore 
&
&
\obj[b_2]\pila 
\ar@{|-->} "mid1";"mid2"^{\obj[a_1]^{(\_\catcirc g_1)}}
\save[].[uu]*+<3pt>[F-:<5pt>:ForestGreen]\frm{} !UL*!R{\smash{\small\color{ForestGreen}\cat}}\restore 
}\end{xy}}$

<div style="page-break-after: always"></div>

范畴 $\cat$ 内任意两对象 $\obj[a_1]$ 和 $\obj[b_1]$ 间的箭头构成一个集合 $\obj[a_1] \cathom\obj[b_1]$ , 
说明 $\cathom$ 只能将两个对象打到一个集合。下面使 $\cathom$ 升级为函子 : 
若还知道箭头 $f_1:\obj[a_2]\cathom\obj[a_1]$ 以及 $g_1:\obj[b_1]\cathom \obj[b_2]$ , 则规定

- $(\_\cathom\obj[b_1]):\getop\cat\!\!\cancel{\smash{{}\cattimes[\catCat]{}}\cat}\cathom[\catCat]\catSet$ 为函子且
  $(\_\cathom\obj[b_1]):\obj[a_1]\longmapsto (\obj[a_1]\cathom\obj[b_1])$ , 并且有
  $(\_\cathom\obj[b_1]):f_1\longmapsto (f_1\cathom \obj[b_1])=(f_1\cathom \getid{\obj[b_1]})=\obj[b_1]^{(f_1\catcirc \_)}$  

  图 1 有助于理解 。

  $(\_\cathom g_1):\getop\cat\!\!\cancel{\smash{{}\cattimes[\catCat]{}}\cat}\cathom[\catCat]\catSet$ ,
  $(\_\cathom g_1):\obj[a_1]\longmapsto (\obj[a_1]\cathom g_1)=(\getid{\obj[a_1]}\cathom g_1)=\obj[a_1]^{(\_\catcirc g_1)}$
  $(\_\cathom g_1): f_1\longmapsto (f_1\cathom g_1) = (f_1\catcirc \_)~~\catcirc[{\cat\cathom[]\catSet}]~~ (\_ \catcirc g_1)= (\_ \catcirc g_1)~~\catcirc[{\cat\cathom[]\catSet}]~~ (f_1\catcirc \_)$ 

  图 2 有助于理解 。 

  > [!note]
  >
  > 不难看出
  >
  > - $\begin{aligned}[t]
  >   \yoneda:{}&\cat\cathom[\catCat](\getop\cat\cathom[\catCat]\catSet) \\
  >           &\obj[b_1]\longmapsto (\_\cathom\obj[b_1]) &&\text{构成一个函子,称作预层} \\
  >           & g_1\longmapsto (\_\cathom g_1)=(\_\circ g_1) &&\text{构成一个函子间映射,即自然变换}
  >   \end{aligned}$ 
  >
  >   该函子称作是**米田嵌入** 。

- $(\obj[a_1]\cathom\_):\cancel{\getop\cat\cattimes[\catCat]}\cat\cathom[\catCat]\catSet$ 为函子且
  $(\obj[a_1]\cathom\_):\obj[b_1]\longmapsto (\obj[a_1]\cathom \obj[b_1])$ , 并且有
  $(\obj[a_1]\cathom\_):g_1\longmapsto (\obj[a_1]\cathom g_1)=(\getid{\obj[a_1]}\cathom g_1)=\obj[a_1]^{(\_\catcirc g_1)}$ 

  图 2 有助于理解 。  

  $(f_1\cathom\_):\cancel{\getop\cat{}\cattimes[\catCat]}\cat\cathom[\catCat]\catSet$ , 
  $(f_1\cathom\_):\obj[b_1]\longmapsto (f_1\cathom \obj[b_1])=(f_1\cathom \getid{\obj[b_1]})=\obj[b_1]^{(f_1\catcirc \_)}$
  $(f_1\cathom\_):g_1\longmapsto (f_1\cathom g_1)=(f_1\catcirc \_)~~\catcirc[{\cat\cathom[]\catSet}]~~ (\_ \catcirc g_1)= (\_ \catcirc g_1)~~\catcirc[{\cat\cathom[]\catSet}]~~ (f_1\catcirc \_)$ 

  图 1 有助于理解 。 

  > [!note] 
  >
  > 不难看出
  >
  > - $\begin{aligned}[t]
  >   \yoda:{}&\getop\cat\cathom[\catCat](\cat\cathom[\catCat]\catSet) \\
  >           &\obj[a_1]\longmapsto (\obj[a_1]\cathom\_) &&\text{构成一个函子} \\
  >           & f_1\longmapsto (f_1\cathom\_)=(f_1\circ \_) &&\text{构成一个函子间映射,即自然变换}
  >   \end{aligned}$ 
  >
  >   该函子戏称为**尤达嵌入** 。

### 积闭范畴

这里插个题外话 :

若范畴包含终对象 , 所有类型的积以及指数 , 则可将其称作**积闭范畴** ; 

若范畴包含始对象 , 所有类型的和 , 则可将其称作是**余积闭范畴** ; 

若范畴满足上述条件 , 则可称作**双积闭范畴** 。

很明显我们讨论的范畴 $\cat$ 就是**双积闭范畴** 。