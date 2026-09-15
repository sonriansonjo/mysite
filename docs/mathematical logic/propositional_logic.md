# 命题逻辑（零阶逻辑）

## 形式语言

**定义1.1（初始符号集）** 命题逻辑初始符号集 $\Sigma=\Phi\cup\{\neg,\lor,\land,\to,\leftrightarrow,),(\}$ .其中：

- $\Phi=\{p_n\mid n\in \mathbb{N}\}$ 是可数无穷的原子命题集，其元素称为原子命题；
- $\lnot,\lor,\land,\to,\leftrightarrow$ 被称为逻辑联结词；
- $),($ 是标点符号。

**定义1.2（形式语言）** 

1. （生成规则）命题逻辑形式语言 $\mathcal{L}_0$ 的公式由初始符号集 $\Sigma=\Phi\cup\{\lnot,\lor,\land,\to,\leftrightarrow,),(\}$ 和以下生成规则构成：

    - 若 $p\in\Phi$ ，则 $p$ 是公式；
    - 若 $\varphi$ 是公式，则 $\neg\varphi$ 是公式；
    - 若 $\varphi_1$ 和 $\varphi_2$ 是公式，则 $(\varphi_1\land\varphi_2)$ 是公式；
    - 若 $\varphi_1$ 和 $\varphi_2$ 是公式，则 $(\varphi_1\lor\varphi_2)$  是公式；
    - 若 $\varphi_1$ 和 $\varphi_2$ 是公式，则 $(\varphi_1\to\varphi_2)$  是公式；
    - 若 $\varphi_1$ 和 $\varphi_2$ 是公式，则 $(\varphi_1\leftrightarrow\varphi_2)$  是公式；
    - 除由上述规则形成的公式，没有其他公式。

2. （巴科斯-诺尔范式）给定原子命题集$\Phi=\{p_n\mid n\in \mathbb{N}\}$，命题逻辑形式语言 $\mathcal{L}_0$ 定义如下：
    $$
\mathcal{L}_0\ni\varphi::= p\mid\neg \varphi\mid(\varphi_1\land\varphi_2)\mid(\varphi_1\lor\varphi_2)\mid(\varphi_1\to\varphi_2)\mid(\varphi_1\leftrightarrow\varphi_2)
  $$

     其中$p\in\Phi$。

3. （归纳闭包）给定初始符号集 $\Sigma=\Phi\cup\{\lnot,\lor,\land,\to,\leftrightarrow,),(\}$ ，$\Sigma^{*}=\bigcup_{n\in\mathbb{N}}\Sigma^{n}$ 是 $\Sigma$ 中符号形成的所有有穷字符串构成的集合，$\Sigma^{*}$上的公式构造函数集 $F=\{c_{\neg},c_{\land},c_{\lor},c_{\to},c_{\leftrightarrow}\}$ 定义如下：

    - $c_{\neg}(\varphi):=\neg\varphi$；
    - $c_{\land}(\varphi_1,\varphi_2):=(\varphi_1\land\varphi_2)$；
    - $c_{\lor}(\varphi_1,\varphi_2):=(\varphi_1\lor\varphi_2)$；
    - $c_{\to}(\varphi_1,\varphi_2):=(\varphi_1\to\varphi_2)$；
    - $c_{\leftrightarrow}(\varphi_1,\varphi_2):=(\varphi_1\leftrightarrow\varphi_2)$. 公式集 $\Sigma_n$ 定义如下： &emsp;$\Sigma_0:=\Phi$；&emsp;$\Sigma_{n+1}:=\Sigma_{n}\cup F(\Sigma_n)$.

    命题逻辑形式语言 $\mathcal{L}_0:=F^{+}(\Phi)=\bigcup_{n\in \mathbb{N}}\Sigma_n$，即 $\mathcal{L}_0$ 是在公式构造函数集 $F$ 下的归纳闭包，是满足前述形成规则的最小集合。

4. （公式构造序列）公式构造序列$\langle\varepsilon_1,\varepsilon_2,...,\varepsilon_n\rangle \in (\Sigma^{*})^{*}$ 是字符串集$\Sigma^{*}$ 上的有限序列（即对任意的$i\in\{1,2,..,n\}$，$\varepsilon_i\in\Sigma^{*}$），其中对于任意$i\in\{1,2,...,n\}$， $\varepsilon_i$ 满足以下情形之一：

    - 要么 $\varepsilon_i\in\Phi$ ；
    - 要么存在 $j\in\{1,2,...,i\}$ 使得 $\varepsilon_i=c_{\neg}(\varepsilon_j)$ ；
    - 要么存在 $j,k\in\{1,2,...,i\}$ 使得 $\varepsilon_i=c_{\land}(\varepsilon_j,\varepsilon_k)$ ；
    - 要么存在 $j,k\in\{1,2,...,i\}$ 使得 $\varepsilon_i=c_{\lor}(\varepsilon_j,\varepsilon_k)$ ；
    - 要么存在 $j,k\in\{1,2,...,i\}$ 使得 $\varepsilon_i=c_{\to}(\varepsilon_j,\varepsilon_k)$ ；
    - 要么存在 $j,k\in\{1,2,...,i\}$ 使得 $\varepsilon_i=c_{\leftrightarrow}(\varepsilon_j,\varepsilon_k)$ .

    字符串 $\varepsilon\in\Sigma^{*}$ 是公式，当且仅当存在公式构造序列$\langle\varepsilon_1,\varepsilon_2,...,\varepsilon_n,\varepsilon\rangle$.

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

**定义1.6（子公式）** 对任意公式 $\varphi\in\mathcal{L}_0$，其子公式集 $\mathrm{Sub}(\varphi)$ 递归定义如下：

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

## 真值语义

**定义2.1（真值集）** 真值集$\mathbb{B}=\{0,1\}$，称 $0$ 为假值，$1$ 为真值。

**定义2.2（赋值）** $v:\Phi\to\mathbb{B}$ 是一个赋值，它为每个原子命题指派了一个真假值。

**定义2.3（满足关系）** 任给赋值 $v$ 和公式 $\varphi,\psi\in\mathcal{L}_0$，满足关系 $\models$ 定义如下：

  - $v\models p :\iff v(p)=1\text{，其中}p\in\Phi$；
  - $v\models \neg\varphi :\iff v\not\models\varphi$；
  - $v\models\varphi\land\psi:\iff v\models\varphi \text{ 并且 } v\models\psi$；
  - $v\models\varphi\lor\psi:\iff v\models\varphi \text{ 或者 } v\models\psi$；
  - $v\models\varphi\to\psi:\iff v\models\varphi \text{ 蕴含 } v\models\psi$；
  - $v\models\varphi\leftrightarrow\psi:\iff v\models\varphi \text{ 当且仅当 } v\models\psi$.

**定义2.4（真值函数）** 函数 $f:\mathbb{B}^n\to\mathbb{B}$ 称为n元真值函数。以下是五个常见真值函数：

**定义2.5 （赋值函数）** 给定赋值 $v:\Phi\to\mathbb{B}$，赋值函数 $\overline{v}:\mathcal{L}_0\to\mathbb{B}$ 递归定义如下：

## 自然演绎系统

## 希尔伯特公理系统

## 可靠性和完全性