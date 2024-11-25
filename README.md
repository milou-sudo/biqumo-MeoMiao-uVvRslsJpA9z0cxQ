
　　本文主要记录研究中用到的与泛函和变分法相关的知识点，推导过程不会严谨考虑所有特殊情况，重在直觉理解。


# 1  泛函（Functional）


　　泛函数（Functional，简称泛函）$J$是以函数为自变量的函数，它将一个定义在某函数空间$Y$中的自变量函数映射到实数域$\\mathcal{R}$或复数域$\\mathcal{C}$，即$J:Y\\rightarrow \\mathcal{R}$或$J:Y\\rightarrow \\mathcal{C}$。本文仅讨论实变函数，即值域与定义域都在实数集$\\mathcal{R}$内。


　　利用积分，对于函数$y(x)\\in Y$，泛函$J\[y]$可表示为：


$\\displaystyle J\[y] \= \\int\_{a}^bF(x,y,y',y'',...)dx$


　　$F$是一个关于$x,y$和$y$的各阶导数的函数。实际上，不仅仅是利用积分，只要是能将函数映射到实数的操作都能用于泛函的映射，如：极值、卷积、特定点函数值，甚至是随机过程等。本文主要以积分举例。


## 1\.1  泛函方程


　　当我们想要找到某个$y$以使$J\[y]$满足特定值$C$时，可以建立泛函方程：


$\\displaystyle J\[y] \= \\int\_{a}^bF(x,y,y',y'',...)dx\=C$


　　泛函方程种类较多，等式的左右还能添加额外的函数从而产生更复杂的情况，这里仅讨论简单情况。以上方程并不好直接求解，因为泛函方程的解是函数而非数值。通常利用拉格朗日乘数法将对该方程的求解转换为优化问题：


$\\displaystyle \\mathcal{L}\[y,\\lambda] \=  \\int\_{a}^bF(x,y,y',y'',...)dx \+  \\lambda(\\int\_{a}^b F(x,y,y',y'',...)dx \- C) $


　　再利用变分法找使以上新泛函$\\mathcal{L}\[y,\\lambda]$取极值的$y(x)$。


# 2  变分法（Calculus of Variations）


　　变分优化研究如何解决涉及泛函的极值问题，会用到各种方法，如变分法、数值优化、凸优化等，而其中**变分法**是求解变分优化问题的核心方法。**变分法**通过研究一个泛函在函数上的微小变化（即变分, variation），找到使这个泛函达到极值的函数，从而将泛函优化问题转化为数学上可求解的微分方程问题。其核心思想类似“导数为零是极值点”的概念。


　　对于泛函（为了简化，本文仅考虑一阶导$y'$）


$\\displaystyle  J\[y] \= \\int\_{a}^bF(x,y,y')dx$


　　我们期望找到一个$y(x)$，使$J\[y]$达到极值。变分法假设$y(x)$是一个可能的解，考虑其微小扰动：


$\\displaystyle  \\tilde{y}(x)\\rightarrow y(x) \+ \\epsilon \\eta (x)$


　　其中$\\epsilon$是一个微小的标量，$\\eta(x)$为任意满足边界条件的光滑函数，有$\\eta(a) \= \\eta(b) \= 0$。将上式代入得到扰动后的泛函：


$\\displaystyle  J\[\\tilde{y}] \= J\[y \+ \\epsilon \\eta ] \= \\int\_{a}^bF(x,y \+ \\epsilon \\eta, y' \+ \\epsilon \\eta')dx$


　　针对$\\epsilon$将上式在$\\epsilon\=0$处泰勒展开：


\\begin{equation\*} \\begin{aligned} J\[\\tilde{y}] \& \= \\left.J\[\\tilde{y}] \\right\|\_{\\epsilon \= 0} \+ \\left.\\frac{\\partial J\[\\tilde{y}] }{\\partial \\epsilon}\\right\|\_{\\epsilon \= 0} \\cdot \\epsilon \+ \\left.\\frac{\\partial^2 J\[\\tilde{y}] }{\\partial \\epsilon^2}\\right\|\_{\\epsilon \= 0} \\cdot \\frac{\\epsilon^2}{2!} \+ \\dots \\\\ \& \= J\[y] \+ \\tilde{J}\_1 \\epsilon \+ \\tilde{J}\_2 \\epsilon^2 \+ \\dots\\\\ \\end{aligned} \\end{equation\*}


　　其中，定义$\\delta J \= \\tilde{J}\_1$为一阶变分，类似地，定义$\\delta J^2 \= \\tilde{J}\_2 $为二阶变分。一阶变分描述了泛函沿扰动方向（即$\\eta$）的线性变化率。


　　我们假定$J\[\\tilde{y}] $在$\\epsilon\=0$时取极值，但这是假定的条件，并不能用于后续计算。因此，进一步要用到泛函极值点的定义：如果某个函数$y(x)$使$J\[y]$在其小范围内的值总是大于或小于其它函数值，则称$y(x)$是泛函的一个极值点。也就是说，对于任意的扰动函数$\\eta(x)$，我们用趋近于$0$的$\\epsilon$稍微增强该扰动，如果都有$J\[\\tilde{y}]\\leq J\[y]$或$J\[\\tilde{y}]\\geq J\[y]$，则可以判断$y(x)$此时取到极值。


　　以上定义，可以判断$J\[\\tilde{y}]$关于$\\epsilon$的左右导数$\\lim\\limits\_{\\epsilon\\rightarrow 0^\+}\\frac{\\partial J\[\\tilde{y}]}{\\partial \\epsilon }$和$\\lim\\limits\_{\\epsilon\\rightarrow 0^\-}\\frac{\\partial J\[\\tilde{y}]}{\\partial \\epsilon }$不同号。根据前面假定的光滑性，可得$\\lim\\limits\_{\\epsilon\\rightarrow 0}\\frac{\\partial J\[\\tilde{y}]}{\\partial \\epsilon } \= 0$，即一阶变分$\\delta J\= \\left.\\frac{\\partial J\[\\tilde{y}] }{\\partial \\epsilon}\\right\|\_{\\epsilon \= 0}\=0$。即解方程：


\\begin{equation\*} \\begin{aligned} \\left.\\int\_{a}^b\\frac{\\partial \\tilde F}{\\partial \\tilde{y}}\\frac{\\partial \\tilde{y}}{\\partial \\epsilon} \+ \\frac{\\partial \\tilde F}{\\partial \\tilde{y}'} \\frac{\\partial \\tilde{y}'}{\\partial \\epsilon}dx \\right\|\_{\\epsilon \= 0}\&\= 0\\\\ \\left.\\int\_{a}^b\\frac{\\partial \\tilde F}{\\partial \\tilde{y}}\\eta \+ \\frac{\\partial \\tilde F}{\\partial \\tilde{y}'} \\eta'dx\\right\|\_{\\epsilon \= 0} \&\= 0\\\\ \\end{aligned} \\end{equation\*}


　　由于$\\epsilon\\rightarrow 0$时，$\\tilde F \\rightarrow F, \\tilde y \\rightarrow y, \\tilde y' \\rightarrow y'$，得


$\\displaystyle  \\int\_{a}^b\\frac{\\partial  F}{\\partial y}\\eta \+ \\frac{\\partial  F}{\\partial y'} \\eta'dx \= 0$


　　利用分部积分将第二项中的$\\eta'$转换为$\\eta$，得


$\\displaystyle  \\int\_{a}^b\\left(\\frac{\\partial  F}{\\partial y} \- \\frac{d}{dx}\\left(\\frac{\\partial F}{\\partial y'}\\right)\\right)\\eta dx \+ \\left.\\frac{\\partial F}{\\partial y'}\\eta\\right\|^b\_a\= 0$


　　根据边界条件$\\eta(a)\=\\eta(b) \= 0$，上式可去除去第二项得


$\\displaystyle  \\int\_{a}^b\\left(\\frac{\\partial  F}{\\partial y} \- \\frac{d}{dx}\\left(\\frac{\\partial F}{\\partial y'}\\right)\\right)\\eta dx \= 0$


　　由于$\\eta$是任意满足边界条件的光滑函数，为了保证上式成立，积分表达式的系数必须为零，从而得到**欧拉\-拉格朗日方程（Euler\-Lagrange equation）**：


$\\displaystyle  \\frac{\\partial  F}{\\partial y} \- \\frac{d}{dx}\\left(\\frac{\\partial F}{\\partial y'}\\right) \= 0$


 　　欧拉\-拉格朗日方程提供了泛函驻点的必要条件，其解包含了所有可能的极值点$y(x)$。解出欧拉\-拉格朗日方程后，可能需要进一步分析解的性质，比如利用二阶变分分析问题的凸性以判断是否全局最优。


## 2\.1  实例——最短路径问题


　　在二维平面上，寻找两点$(x\_1,y\_1\)$和$(x\_2,y\_2\)$之间路径最短的曲线$y(x)$。定义路径长度为：


$\\displaystyle  L\[y] \= \\int\_{x\_1}^{x\_2} \\sqrt{1\+y'^2} dx$


　　列出欧拉\-拉格朗日方程


$\\displaystyle  \- \\frac{d}{dx}\\left(\\frac{y'}{\\sqrt{1\+y'^2}}\\right) \= 0$


　　左右积分得


\\begin{equation\*} \\begin{aligned} \\frac{y'}{\\sqrt{1\+y'^2}} \= C\\\\ y' \= \\pm\\sqrt{\\frac{C^2}{1\-C^2}} \\end{aligned} \\end{equation\*}


　　导数$y'$为常数，说明$y(x)$为线性函数，为直线。


 


 本博客参考[楚门加速器](https://shexiangshi.org)。转载请注明出处！
