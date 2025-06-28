上一页的第一条定理若用交换图表示则应为

$\qquad\vcenter{\begin{xy}\xymatrix@!R=1cm@!C=2cm{
{\obj[c]\bbox[LightGreen]{{}\cathom\obj[c_2]}\pla} 
\ar[r]^{\obj[c]^\beta\pla} 
\ar[d]_{f_1\bbox[LightGreen]{{}\cathom\obj[c_2]}\pla} &
{\obj[c]\bbox[LightGreen]{{}\cathom\obj[c_2']}\pla} 
\ar[d]^{f_1\bbox[LightGreen]{{}\cathom\obj[c_2']}\pla} \\
{\obj[c']\bbox[LightGreen]{{}\cathom\obj[c_2]}\pla} 
\ar[r]_{\obj[c']^\beta\pla} 
\save[].[u]*+<3pt>[F-:<5pt>:ForestGreen]\frm{}
!D*!U{\small\color{ForestGreen}\cat\bbox[LightGreen]{{}\cathom\obj[c_2]}}\restore &
{\obj[c']\bbox[LightGreen]{{}\cathom\obj[c_2']}\pla}
\save[].[u]*+<3pt>[F-:<5pt>:ForestGreen]\frm{}
!D*!U{\small\color{ForestGreen}\cat\bbox[LightGreen]{{}\cathom\obj[c_2']}}\restore 
\save[ul].[]*+<10pt>[F-:<8pt>:ForestGreen]\frm{}
!U*!D!L(4){\small\color{ForestGreen}\cat[Set]}\restore 
}\end{xy}}$

$\Rightarrow$ 易证 , $\Leftarrow$ 用到了米田技巧 ( 考虑特殊情况 )

$\qquad\vcenter{\begin{xy}\xymatrix@!R=1cm@!C=2cm{
{\obj[c_2]\bbox[LightGreen]{{}\cathom\obj[c_2]}\pla} 
\ar[r]^{\obj[c_2]^\beta\pla} 
\ar[d]_{f_1\bbox[LightGreen]{{}\cathom\obj[c_2]}\pla} &
{\obj[c_2]\bbox[LightGreen]{{}\cathom\obj[c_2']}\pla} 
\ar[d]^{f_1\bbox[LightGreen]{{}\cathom\obj[c_2']}\pla}  \\
{\obj[c']\bbox[LightGreen]{{}\cathom\obj[c_2]}\pla} 
\ar[r]_{\obj[c']^\beta\pla} &
{\obj[c']\bbox[LightGreen]{{}\cathom\obj[c_2']}\pla}  
}\end{xy}}$ $\qquad\vcenter{\begin{xy}\xymatrix@!R=1cm@!C=2cm{
{\getid {\obj[c_2]}\pla} 
\ar@{|->}[r]^{\obj[c_2]^\beta\pla} 
\ar@{|->}[d]_{f_1\bbox[LightGreen]{{}\cathom\obj[c_2]}\pla} &
{\smash[h]{\bbox[LightGray]{\getid {\obj[c_2]}(\obj[b_1^\beta])}}\pla} 
\ar@{|->}[d]^{f_1\bbox[LightGreen]{{}\cathom\obj[c_2']}\pla}  \\
{f_1\pla} 
\ar@{|->}[r]_{\obj[c']^\beta\pla} &
{f_1\circ\bbox[LightGray]{(\etc)}\pla}  
}\end{xy}}$

为了方便就用 $\bbox[LightGray]{(\etc)}$ 表示 $\bbox[LightGray]{\getid {\obj[c_2]}(\obj[b_1^\beta])}$ 。 由上图可
知 $f_1(\obj[c']^\beta)=f_1\catcirc \bbox[LightGray]{(\etc)}$ , 故 $\obj[c']^\beta = \bbox[LightBlue]{\obj[c']\cathom{}}\bbox[LightGray]{(\etc)}$ ; 
而 $\obj[c']^\beta = \bbox[LightBlue]{\obj[c']\cathom{}}\bbox[LightGray]{(\etc)}=\obj[c']^{(\_\catcirc \bbox[LightGray]{(\etc)})}$是同构 , 从而
知 $(\bbox[LightGray]{(\etc)}\circ \_)$ 是同构 , ==$\bbox[LightGray]{(\etc)} : \obj[c_2]\cathom \obj[c_2']$ 也是== 。

> 高亮部分省去了部分推理过程 , 
> 具体在米田嵌入处会详细介绍 。