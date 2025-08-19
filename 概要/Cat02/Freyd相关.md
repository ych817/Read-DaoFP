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
% 新增命令 --------------------------------------------------------------------
\newcommand{\adjarrowu}[1][{\arr[f]}]{%       % 伴随函子相继式写法 箭头
  \overset{#1}{\rightarrow}
}
\newcommand{\adjarrowd}[1][{\arr[f]}]{%       % 伴随函子相继式写法 箭头
  \underset{#1}{\rightarrow}
}
$$

## DaoFP 中的定义

- **弱终系 weak terminal set** :

  一族对象 $t_i$ , $i$ 属于指标集 $I$ , 满足
  对任意范畴 $C$ 中的对象 $c$ 
  都存在 $i\in I$ 使得箭头 $c\rightarrow t_i$ 存在 。

- **弱终对象 weak terminal set** :

  从任何对象打到弱始对象的箭头不是唯一的 。

- **定理** : 
  若范畴余完备且有弱始系
  则范畴必有终对象 。

  > 在这样的范畴中肯定可以构造出 $\coprod_{i\in I}t_i$ ,
  > 不难得知这个对象是个弱终对象 , 因为对任意 $c$ 总有 $c\to \coprod_{i\in I}t_i$ 。
  > 然后这个箭头又相当于 $c\to t_j\to \coprod_{i\in I}t_i$ 。
  >
  > 现在利用指标集 $I$ 构造出一个 $C$ 的一个子范畴 $J$ , 
  > 其中 $J$ 中对象即 $I$ 中对象 , $J$ 中箭头都属于某个 $\hom_C(t_i,t_j)$ , 这里 $C$ 为范畴。
  > 易知 $J$ 为小范畴 。
  >
  > 不难得知函子 ${\rm Id}: J\to C$ 是个嵌入 , 这个嵌入的余极限就是 $C$ 中的终对象 。

## 红糖的定义

- **弱始系 weak initial set** :

  ${\rm Ob}(E)$ 的一个非空小子集 $\Gamma$ , 满足
  对任意 $e'\in {\rm Ob}(E)$ 都存在 $e\in \Gamma$ 使
  $\hom_E(e,e')\neq \varnothing$ 。

- **弱始对象 weak terminal set** :

  如果弱始系是个**单元素集** , 
  那么称其元素为弱始对象 。

- **引理 1.5** :
  若范畴 $E$ 完备 complete 且有弱始系
  则范畴 $E$ 必有始对象 。