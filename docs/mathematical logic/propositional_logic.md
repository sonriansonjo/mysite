# 命题逻辑（零阶逻辑）

## 形式语言

**定义1.1（初始符号集）** 命题逻辑初始符号集 $\Sigma=\Phi\cup\{\neg,\land,\lor,\to,\leftrightarrow,),(\}$ .其中：

- $\Phi=\{p_n\mid n\in \mathbb{N}\}$ 是可数无穷的原子命题集，其元素称为原子命题；
- $\neg,\land,\lor,\to,\leftrightarrow$ 被称为逻辑联结词，其中 $\neg$ 是一元联结词，$\land,\lor,\to,\leftrightarrow$ 是二元联结词；
- $),($ 是标点符号。

**定义1.2（形式语言）** 

**1. （生成规则）** 命题逻辑形式语言 $\mathcal{L}_0$ 的公式由初始符号集 $\Sigma=\Phi\cup\{\lnot,\land,\lor,\to,\leftrightarrow,),(\}$ 和以下生成规则构成：

   - 若 $p\in\Phi$ ，则 $p$ 是公式；
   - 若 $\varphi$ 是公式，则 $\neg\varphi$ 是公式；
   - 若 $\varphi_1$ 和 $\varphi_2$ 是公式，则 $(\varphi_1\land\varphi_2)$ 是公式；
   - 若 $\varphi_1$ 和 $\varphi_2$ 是公式，则 $(\varphi_1\lor\varphi_2)$  是公式；
   - 若 $\varphi_1$ 和 $\varphi_2$ 是公式，则 $(\varphi_1\to\varphi_2)$  是公式；
   - 若 $\varphi_1$ 和 $\varphi_2$ 是公式，则 $(\varphi_1\leftrightarrow\varphi_2)$  是公式；
   - 除由上述规则形成的公式，没有其他公式。

**2. （巴科斯-诺尔范式）** 给定原子命题集$\Phi=\{p_n\mid n\in \mathbb{N}\}$，命题逻辑形式语言 $\mathcal{L}_0$ 定义如下：

$$
   \mathcal{L}_0\ni\varphi::= p\mid\neg \varphi\mid(\varphi_1\land\varphi_2)\mid(\varphi_1\lor\varphi_2)\mid(\varphi_1\to\varphi_2)\mid(\varphi_1\leftrightarrow\varphi_2)
$$
   
   其中$p\in\Phi$。

**3. （归纳闭包）** 给定初始符号集 $\Sigma=\Phi\cup\{\lnot,\land,\lor,\to,\leftrightarrow,),(\}$ ，$\Sigma^{*}=\bigcup_{n\in\mathbb{N}}\Sigma^{n}$ 是 $\Sigma$ 中符号形成的所有有穷字符串构成的集合，$\Sigma^{*}$上的公式构造函数集 $F=\{c_{\neg},c_{\land},c_{\lor},c_{\to},c_{\leftrightarrow}\}$ 定义如下：

   - $c_{\neg}(\varphi):=\neg\varphi$；
   - $c_{\land}(\varphi_1,\varphi_2):=(\varphi_1\land\varphi_2)$；
   - $c_{\lor}(\varphi_1,\varphi_2):=(\varphi_1\lor\varphi_2)$；
   - $c_{\to}(\varphi_1,\varphi_2):=(\varphi_1\to\varphi_2)$；
   - $c_{\leftrightarrow}(\varphi_1,\varphi_2):=(\varphi_1\leftrightarrow\varphi_2)$.
    
   公式集 $\Sigma_n$ 定义如下：
   
   - $\Sigma_0:=\Phi$；
   - $\Sigma_{n+1}:=\Sigma_{n}\cup F(\Sigma_n)$.
   
   命题逻辑形式语言 $\mathcal{L}_0:=F^{+}(\Phi)=\bigcup_{n\in \mathbb{N}}\Sigma_n$，即 $\mathcal{L}_0$ 是在公式构造函数集 $F$ 下的归纳闭包，是满足前述形成规则的最小集合。

**4. （公式构造序列）** 公式构造序列$\langle\varepsilon_1,\varepsilon_2,...,\varepsilon_n\rangle \in (\Sigma^{*})^{*}$ 是字符串集$\Sigma^{*}$ 上的有限序列（即对任意的$i\in\{1,2,..,n\}$，$\varepsilon_i\in\Sigma^{*}$），其中对于任意$i\in\{1,2,...,n\}$， $\varepsilon_i$ 满足以下情形之一：

   - 要么 $\varepsilon_i\in\Phi$ ；
   - 要么存在 $j\in\{1,2,...,i\}$ 使得 $\varepsilon_i=c_{\neg}(\varepsilon_j)$ ；
   - 要么存在 $j,k\in\{1,2,...,i\}$ 使得 $\varepsilon_i=c_{\land}(\varepsilon_j,\varepsilon_k)$ ；
   - 要么存在 $j,k\in\{1,2,...,i\}$ 使得 $\varepsilon_i=c_{\lor}(\varepsilon_j,\varepsilon_k)$ ；
   - 要么存在 $j,k\in\{1,2,...,i\}$ 使得 $\varepsilon_i=c_{\to}(\varepsilon_j,\varepsilon_k)$ ；
   - 要么存在 $j,k\in\{1,2,...,i\}$ 使得 $\varepsilon_i=c_{\leftrightarrow}(\varepsilon_j,\varepsilon_k)$ .

   字符串 $\varepsilon\in\Sigma^{*}$ 是公式，当且仅当存在公式构造序列 $\langle\varepsilon_1,\varepsilon_2,...,\varepsilon_n,\varepsilon\rangle$.

**定理1.3（结构归纳法）** 对任意公式 $\varphi\in\mathcal{L}_0$，$\varphi$ 具有性质 $P$ 当且仅当：

  1. 对任意公式  $\varphi\in\Phi$ ，$\varphi$ 具有性质 $P$ ；并且
  2. 对任意公式  $\varphi\in\mathcal{L}_0$，若 $\varphi$ 具有性质 $P$，则 $\neg\varphi$ 具有性质 $P$ ；并且
  3. 对任意公式 $\varphi_1,\varphi_2\in\mathcal{L}_0$，若 $\varphi_1,\varphi_2$ 具有性质 $P$，则 $(\varphi_1\land\varphi_2)$具有性质 $P$；并且
  4. 对任意公式 $\varphi_1,\varphi_2\in\mathcal{L}_0$，若 $\varphi_1,\varphi_2$ 具有性质 $P$，则 $(\varphi_1\lor\varphi_2)$具有性质 $P$；并且
  5. 对任意公式 $\varphi_1,\varphi_2\in\mathcal{L}_0$，若 $\varphi_1,\varphi_2$ 具有性质 $P$，则 $(\varphi_1\to\varphi_2)$具有性质 $P$；并且
  6. 对任意公式 $\varphi_1,\varphi_2\in\mathcal{L}_0$，若 $\varphi_1,\varphi_2$ 具有性质 $P$，则 $(\varphi_1\leftrightarrow\varphi_2)$具有性质 $P$.

**定理1.4（唯一可读性）** 任意公式 $\varphi\in\mathcal{L}_0$ 恰好满足以下情形之一：
    
  - $\varphi\in\Phi$；
  - 存在唯一 $\psi\in\mathcal{L}_0$，使得 $\varphi=\neg\psi$；
  - 存在唯一 $\varphi_1,\varphi_2\in\mathcal{L}_0$，使得 $\varphi=(\varphi_1\land\varphi_2)$；
  - 存在唯一 $\varphi_1,\varphi_2\in\mathcal{L}_0$，使得 $\varphi=(\varphi_1\lor\varphi_2)$；
  - 存在唯一 $\varphi_1,\varphi_2\in\mathcal{L}_0$，使得 $\varphi=(\varphi_1\to\varphi_2)$；
  - 存在唯一 $\varphi_1,\varphi_2\in\mathcal{L}_0$，使得 $\varphi=(\varphi_1\leftrightarrow\varphi_2)$.

**记号1.5（括号省略）**  为书写简便，在不引起歧义时省略部分括号。约定如下：

  1. 最外层括号可省略； 
  2. 联结词优先级从高到低为：$\neg$ $\succ$ $\land$ $\succ$ $\lor$ $\succ$ $\to$ $\succ$ $\leftrightarrow$ ；
  3. 结合省略约定：
     - $\land,\lor$ 左结合；
     - $\to$ 右结合。

**定义1.6（原子命题出现）** 对任意公式 $\varphi$，其出现的原子命题集 $\mathrm{Var}(\varphi)$ 递归定义如下：

   * $\mathrm{Var}(p)=\{p\}$；
   * $\mathrm{Var}(\neg\varphi)=\mathrm{Var}(\varphi)$；
   * $\mathrm{Var}((\varphi\land\psi))=\mathrm{Var}(\varphi)\cup\mathrm{Var}(\psi)$；
   * $\mathrm{Var}((\varphi\lor\psi))=\mathrm{Var}(\varphi)\cup\mathrm{Var}(\psi)$；
   * $\mathrm{Var}((\varphi\to\psi))=\mathrm{Var}(\varphi)\cup\mathrm{Var}(\psi)$；
   * $\mathrm{Var}((\varphi\leftrightarrow\psi))=\mathrm{Var}(\varphi)\cup\mathrm{Var}(\psi)$.

**定义1.7（子公式）** 对任意公式 $\varphi\in\mathcal{L}_0$，其子公式集 $\mathrm{Sub}(\varphi)$ 递归定义如下：

  - 若 $p\in\Phi$，则 $\mathrm{Sub}(p)=\{p\}$；
  - 若 $\varphi=\neg\psi$，则 $\mathrm{Sub}(\neg\psi)=\mathrm{Sub}(\psi)\cup\{\neg\psi\}$；
  - 若 $\varphi=(\varphi_1\land\varphi_2)$，则 $\mathrm{Sub}((\varphi_1\land\varphi_2))=
  \mathrm{Sub}(\varphi_1)\cup\mathrm{Sub}(\varphi_2)\cup\{(\varphi_1\land\varphi_2)\}$；
  - 若 $\varphi=(\varphi_1\lor\varphi_2)$，则 $\mathrm{Sub}((\varphi_1\lor\varphi_2))=
  \mathrm{Sub}(\varphi_1)\cup\mathrm{Sub}(\varphi_2)\cup\{(\varphi_1\lor\varphi_2)\}$；
  - 若 $\varphi=(\varphi_1\to\varphi_2)$，则 $\mathrm{Sub}((\varphi_1\to\varphi_2))=
  \mathrm{Sub}(\varphi_1)\cup\mathrm{Sub}(\varphi_2)\cup\{(\varphi_1\to\varphi_2)\}$；
  - 若 $\varphi=(\varphi_1\leftrightarrow\varphi_2)$，则 $\mathrm{Sub}((\varphi_1\leftrightarrow\varphi_2))=
  \mathrm{Sub}(\varphi_1)\cup\mathrm{Sub}(\varphi_2)\cup\{(\varphi_1\leftrightarrow\varphi_2)\}$.
  
  若 $\psi\in\mathrm{Sub}(\varphi)$ 且 $\psi\ne\varphi$，则称 $\psi$ 为 $\varphi$ 的真子公式。记为$\mathrm{Sub}^-(\varphi)=\mathrm{Sub}(\varphi)\setminus\{\varphi\}$.

  **注记1.8（表达法）** 表达法是指表示公式的方法，同一个公式可以有不同的表达方式，不同表达方式之间可相互定义。关于二元联结词$\land,\lor,\to,\leftrightarrow$ ：

   - 中缀表达法：将二元联结词写在它所联结的两个子公式间，如 $(\varphi\land\psi)$，这种表达法容易阅读，但是长串公式必须在联结词的辖域上增加括号以消除歧义。
   - 前缀表达法：将二元联结词写在它所联结的两个子公式前，如 $\land\varphi\psi$，这种表达法不会面临优先级问题，长串公式没有歧义，从而无需括号。**波兰式**就采用前缀表达法，此外$\lnot,\land,\lor,\to,\leftrightarrow$ 分别使用 $N,K,A,C,E$ 表示，如 $\land\varphi\psi$ 波兰式表示为$K\varphi\psi$.
   - 后缀表达法：将二元联结词写在它所联结的两个子公式后，如 $\varphi\psi\land$，和前缀表达法一样，长串公式也没有歧义。

所以，初始符号集中标点符号 $\{),(\}$ 是不必要的，我们可以采用前缀表达法或后缀表达法，再将中缀表达法和标点符号作为方便记号用前缀或后缀表达法定义。

**注记1.9（永真与永假）** 永真（$\top$）和永假（$\bot$）是两个零元真值联结词，是可选的初始符号，也可分别作为重言式和矛盾式的简写，比如如下常见的定义方式：

   - $\top:=p\lor\neg p$；
   - $\bot:=p\land\neg p$.

## 真值语义

**定义2.1（真值集）** 真值集$\mathbb{B}=\{0,1\}$，称 $0$ 为假值，$1$ 为真值。

**定义2.2（赋值）** $v:\Phi\to\mathbb{B}$ 是一个赋值，它为每个原子命题指派了一个真假值。

**定义2.3（满足关系）** 任给赋值 $v$ 和公式 $\varphi,\psi\in\mathcal{L}_0$，满足关系 $\models$ 定义如下：

  - $v\models p :\iff v(p)=1\text{，其中}p\in\Phi$；
  - $v\models \neg\varphi :\iff v\not\models\varphi$；
  - $v\models\varphi\land\psi:\iff v\models\varphi \text{ 并且 } v\models\psi$；
  - $v\models\varphi\lor\psi:\iff v\models\varphi \text{ 或者 } v\models\psi$；
  - $v\models\varphi\to\psi:\iff v\not\models\varphi \text{ 或者 } v\models\psi$；
  - $v\models\varphi\leftrightarrow\psi:\iff v\models\varphi \text{ 当且仅当 } v\models\psi$.

关于两个逻辑常量：

  - $v\models \top$；
  - $v\not\models\bot$.

对于公式集 $\Gamma\subseteq\mathcal{L}_0$，$v\models\Gamma:\iff \text{对于任意 }\varphi\in\Gamma\text{，}v\models\varphi$.

**定义2.4（重言式、可满足式、矛盾式）** 

1. 对于任意 $\varphi\in\mathcal{L}_0$，$\varphi$ 是重言式 $:\iff$ 对于任意赋值 $v$，$v\models\varphi$ .
2. 对于任意 $\varphi\in\mathcal{L}_0$，$\varphi$ 是矛盾式 $:\iff$ 对于任意赋值 $v$，$v\not\models\varphi$ .
3. 对于任意 $\varphi\in\mathcal{L}_0$，$\varphi$ 是偶然式 $:\iff$ $\varphi$ 不是重言式，并且 $\varphi$ 不是矛盾式。
4. 对于任意 $\varphi\in\mathcal{L}_0$，$\varphi$ 是可满足的 $:\iff$ 存在赋值 $v$，$v\models\varphi$ .
5. 对于任意 $\Gamma\subseteq\mathcal{L}_0$，$\Gamma$ 是可满足的 $:\iff$ 存在赋值 $v$，$v\models\Gamma$ .
6. 偶然式是可满足的，重言式是可满足的，矛盾式是不可满足的。

易知 $\top$ 是重言式，$\bot$ 是矛盾式。
 
**定义2.5（真值函数）** 函数 $f:\mathbb{B}^n\to\mathbb{B}$ 称为n元真值函数。以下是常见真值函数：
   
   - $f_{\neg}(x)=\begin{cases}1,\quad x=0\\0,\quad{\rm 否则}\end{cases}$
   - $f_{\land}(x,y)=\begin{cases}1,\quad x=y=1\\0,\quad{\rm 否则}\end{cases}$
   - $f_{\lor}(x,y)=\begin{cases}0,\quad x=y=0\\1,\quad{\rm 否则}\end{cases}$
   - $f_{\to}(x,y)=\begin{cases}0,\quad x=1{\rm 并且 }y=0\\1,\quad{\rm 否则}\end{cases}$
   - $f_{\leftrightarrow}(x,y)=\begin{cases}1,\quad x=y\\0,\quad{\rm 否则}\end{cases}$
   - $f_{\mid}(x,y)=\begin{cases}0,\quad x=y=1\\1,\quad{\rm 否则}\end{cases}$
   - $f_{\downarrow}(x,y)=\begin{cases}1,\quad x=y=0\\0,\quad{\rm 否则}\end{cases}$

以下**真值函数表**罗列了常见真值函数所有输入和对应的输出：

| $x$ | $y$ | $f_{\neg}(x)$ | $f_{\land}(x,y)$ | $f_{\lor}(x,y)$ | $f_{\to}(x,y)$ | $f_{\leftrightarrow}(x,y)$ | $f_{\mid}(x,y)$ | $f_{\downarrow}(x,y)$ |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| 0 | 0 | 1 | 0 | 0 | 1 | 1 | 1 | 1 |
| 0 | 1 | 1 | 0 | 1 | 1 | 0 | 1 | 0 |
| 1 | 0 | 0 | 0 | 1 | 0 | 0 | 1 | 0 |
| 1 | 1 | 0 | 1 | 1 | 1 | 1 | 0 | 0 |

符号$\mid$ 称为谢弗尔竖，符号$\downarrow$ 称为皮尔士箭头。

**定义2.6（赋值函数）** 给定赋值 $v:\Phi\to\mathbb{B}$，赋值函数 $\hat{v}:\mathcal{L}_0\to\mathbb{B}$ 递归定义如下：

   - $\hat{v}(p):=v(p)$，其中$p\in\Phi$；
   - $\hat{v}(\neg \varphi):=f_{\neg}[\hat{v}(\varphi)]$；
   - $\hat{v}(\varphi\land\psi):=f_{\land}[\hat{v}(\varphi),\hat{v}(\psi)]$；
   - $\hat{v}(\varphi\lor\psi):=f_{\lor}[\hat{v}(\varphi),\hat{v}(\psi)]$；
   - $\hat{v}(\varphi\to\psi):=f_{\to}[\hat{v}(\varphi),\hat{v}(\psi)]$；
   - $\hat{v}(\varphi\leftrightarrow\psi):=f_{\leftrightarrow}[\hat{v}(\varphi),\hat{v}(\psi)]$.

对于两个逻辑常量：
   - $\hat{v}(\top):=1$；
   - $\hat{v}(\bot):=0$.

**定理2.7（赋值函数与满足关系）** 给定公式 $\varphi\in\mathcal{L}_0$ 和赋值 $v$， $v\models\varphi\iff \hat{v}(\varphi)=1$. 

这意味着除了**定义2.3**，我们还可以选择使用赋值函数定义赋值 $v$ 的满足关系。

**定理2.8（局部确定性）** 任给赋值 $v_1$ 和 $v_2$，对于任意 $p\in\mathrm{Var}(\varphi)$，若$v_1(p)=v_2(p)$，则 $v_1 \models \varphi \iff v_2 \models\varphi$. 也就是说，公式的真值只依赖于其中出现的原子命题。

**定义2.9（语义后承）** 对于$\Gamma\subseteq\mathcal{L}_0,\varphi\in\mathcal{L}_0$，$\Gamma\models\varphi:\iff {\rm 对所有的赋值}v {，若} v\models\Gamma {，则}v\models\varphi$.

   - $\varphi$ 是重言式$\iff \emptyset\models\varphi$.  通常将 $\emptyset\models\varphi$ 简记为$\models\varphi$.

**定义2.10（语义等值）** 对于 $\varphi,\psi\in\mathcal{L}_0$，$\varphi\equiv\psi:\iff\{\varphi\}\models\psi\text{ 并且 }\{\psi\}\models\varphi$，或者等价地，$\varphi\equiv\psi:\iff\models\varphi\leftrightarrow\psi$.

## 自然演绎系统

## 希尔伯特公理系统

## 可靠性和完全性