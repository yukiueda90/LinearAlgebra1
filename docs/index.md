# 線形代数I メモ
4/2 15:15
<a id="section1"></a>
# 1: 行列
<a id="section1-1"></a>
## 1.1: 行列の定義
##### <u>定義</u> (行列)
縦に$m$個, 横に$n$個の数を長方形状に並べたものを$m\times n$ 型の**行列** (**matrix**) という.

---

##### <u>例</u> 
\[A = \begin{pmatrix}a_{11}&a_{12}\cr a_{21}&a_{22}\end{pmatrix},\qquad B=\begin{pmatrix}b_{11}&b_{12}&b_{13}\cr b_{21}&b_{22}&b_{32}\end{pmatrix}.\]

* 行列を構成する$mn$個の数を行列の**成分** (**element**) という
* 行列を構成する要素たちを横に並べた部分を**行** (**row**), 縦に並べた部分を**列** (**column**)という
* 上から $i$ 番目の行を**第 $i$ 行**, 左から $j$ 番目の列を**第 $j$ 列**という.
* 第 $i$ 行, 第 $j$ 列にある成分を **$ (i,j) $ 成分**という.
    * 以降, 断りの無い限り, 行列は大文字のアルファベットで表記し, 例えば行列 $A$ の $ (i,j) $ 成分を $ (A)_{ij} $ もしくは小文字のアルファベットを用いて $ a_{ij} $ と表す. 
    * また, $(i,j)$ 成分が $a_{ij}$ である行列を $(a_{ij})$ と表す.

---

##### <u>例</u>
\[A = \begin{pmatrix}a_{11}&a_{12} \cr a_{21}&a_{22}\end{pmatrix}.\]
* この行列 $A$ の第 $1$ 行は $(a_{11},a_{12})$.
* この行列 $A$ の第 $2$ 列は $\begin{pmatrix}a_{12}\cr a_{22}\end{pmatrix}$.
* この行列 $A$ の $(1,2)$ 成分は $a_{12}$.

---

* 全ての成分が実数である行列を**実行列** (**real matrix**)という.
    * 行列 $A$ が $m\times n$ 型の実行列であるとき, $A\in \mathbb{R}^{m\times n}$ と表記する.
* 全ての成分が複素数である行列を**複素行列** (**real matrix**)という.
    * 行列 $A$ が $m\times n$ 型の複素行列であるとき, $A\in \mathbb{C}^{m\times n}$ と表記する.
* $1\times n$ 型の行列を**行ベクトル** (**row vector**)という.
* $m\times 1$ 型の行列を**列ベクトル** (**column vector**)という.
* $1\times 1$ 型の行列は, そのただ$１$つの成分である実数 (もしくは複素数) と同一視される.

---

##### <u>例</u>
* $A = \begin{pmatrix}a_{11}&a_{12}\cr a_{21}&a_{22}\end{pmatrix} \in \mathbb{R}^{2\times 2}.$
* $\bm{x} = (x_1,x_2,x_3)\in\mathbb{R}^{1\times3}$, &emsp; $\boldsymbol{x}$ は行ベクトル.
* $\boldsymbol{v} = \begin{pmatrix}v_1\cr v_2\cr v_3\end{pmatrix}\in\mathbb{R}^{3\times1}$, &emsp; $\boldsymbol{v}$ は列ベクトル.
* $\begin{pmatrix}a\end{pmatrix}\in\mathbb{R}^{1\times1}$ は $a\in\mathbb{R}$ と同一視される.

---

## 1.2 行列の演算
##### <u>定義</u>
$2$つの行列 $A=(a_{ij})$, $B=(b_{ij})$ について, $A$ と $B$ が同じ型であって, 全ての $i,j$ に対して \[a_{ij} = b_{ij}\] となるとき, $A$ と $B$ は等しいといい, \[A=B\] と表記する. $A=B$ でない場合は, $A\neq B$ と表記する.

---

##### <u>例</u>
\[A=\begin{pmatrix}1&2\cr 3&4\end{pmatrix},\quad B=\begin{pmatrix}1&2\cr 3&4\end{pmatrix},\quad C=\begin{pmatrix}1&2\cr 3&0\end{pmatrix},\quad D=\begin{pmatrix}1&2\cr 3&4\cr 0&0\end{pmatrix}.\]
* 行列の型が同じで, 全ての成分が等しいため $A=B$.
* $(2,2)$ 成分が異なるため $A\neq C$. 
* 行列の型が異なるため $A\neq D$.

---

##### <u>定義</u> (行列の和)
同じ型の$2$つの行列 $A=(a_{ij})$, $B=(b_{ij})$ に対し, $(i,j)$ 成分が $a_{ij}+b_{ij}$ である行列を $A$ と $B$ の和といい, $A+B$ と表記する.

---

##### <u>例</u>
\[A=\begin{pmatrix}1&2\cr 3&4\end{pmatrix},\quad B=\begin{pmatrix}1&2\cr 3&4\end{pmatrix},\quad C=\begin{pmatrix}1&2\cr 3&0\end{pmatrix},\quad D=\begin{pmatrix}1&2\cr 3&4\cr 0&0\end{pmatrix}.\]
* $A+B = \begin{pmatrix}1&2\cr 3&4\end{pmatrix}+\begin{pmatrix}1&2\cr 3&4\end{pmatrix} = \begin{pmatrix}2&4\cr 6&8\end{pmatrix}$ 
* $A+C = \begin{pmatrix}1&2\cr 3&4\end{pmatrix} + \begin{pmatrix}1&2\cr 3&0\end{pmatrix} = \begin{pmatrix}2&4\cr 6&4\end{pmatrix}$
* 行列の型が異なるため, $A+D$ は定義されていない. 

---

##### <u>定義</u> (行列のスカラー倍)
行列 $A=(a_{ij})$ と複素数 $\lambda$ に対し, $(i,j)$ 成分が $\lambda a_{ij}$ である行列を $\lambda A$ と表記する.
##### <u>例</u>
\[A=\begin{pmatrix}1&2\cr 3&4\end{pmatrix}, \quad C=\begin{pmatrix}1&2\cr 3&0\end{pmatrix}.\]
* $2A = 2\begin{pmatrix}1&2\cr 3&4\end{pmatrix} = \begin{pmatrix}2&4\cr 6&8\end{pmatrix} = A+A$
* $A - C = A + (-1)C = \begin{pmatrix}1&2\cr 3&4\end{pmatrix} + \begin{pmatrix}-1&-2\cr -3&0\end{pmatrix} = \begin{pmatrix}0&0\cr 0&4\end{pmatrix}$

---

##### <u>定義</u> (行列の積)
$\ell\times m$ 型行列 $A=(a_{ij})$と, $m\times n$ 型行列 $B=(b_{ij})$ に対し, $(i,j)$ 成分が $\displaystyle\sum_{k=1}^m a_{ik}b_{kj}$ である $\ell \times n$ 型行列を $A$ と $B$ の**積**といい, $AB$ と表記する. 

---

##### <u>注意</u>
行列積 $AB$ は, 左側の行列 (この場合は$A$) の列の数と, 右側の行列 (この場合は$B$) の行の数が等しいこときに限り定義される.  

---

##### <u>例</u>
\[\boldsymbol{x} = (x_1,x_2)\in\mathbb{R}^{1\times2},\qquad \boldsymbol{y} = \begin{pmatrix}y_1\cr y_2\end{pmatrix}\in\mathbb{R}^{2\times1}.\]
* $\boldsymbol{x}\boldsymbol{y}\in\mathbb{R}^{1\times1}$ の $(1,1)$ 成分は $\displaystyle\sum_{k=1}^2 x_ky_k$.
* つまり $\bm{x}\bm{y} = x_1y_1+x_2y_2$.
* これはベクトル $\vec{x}=(x_1,x_2)$ と $\vec{y}=(y_1,y_2)$ の内積 \[\vec{x}\cdot\vec{y} = x_1y_1+x_2y_2\] に等しい.

---

##### <u>例</u>
\[A = \begin{pmatrix}a_{11}&a_{12}\cr a_{21}&a_{22}\end{pmatrix}\in\mathbb{R}^{2\times 2},\qquad B = \begin{pmatrix}b_{11}&b_{12}\cr b_{21}&b_{22}\end{pmatrix}\in\mathbb{R}^{2\times 2}.\]
* $AB = \begin{pmatrix}a_{11}b_{11}+a_{12}b_{21}&a_{11}b_{12}+a_{12}b_{22}\cr a_{21}b_{11}+a_{22}b_{21}&a_{21}b_{12}+a_{22}b_{22}\end{pmatrix}$
* $A$ の第 $i$ 行のみ取り出した行ベクトル $ \boldsymbol{a}_i = (a_{i1},a_{i2}) $と, $B$ の第 $j$ 列のみ取り出した $ \boldsymbol{b}_j = \begin{pmatrix}b_{1j}\cr b_{2j}\end{pmatrix} $ について, $AB$ の $ (i,j) $ 成分が $\boldsymbol{a}_i\boldsymbol{b}_j$ となる: \[AB = \begin{pmatrix}\boldsymbol{a}_1\boldsymbol{b}_1&\boldsymbol{a}_1\boldsymbol{b}_2\cr \boldsymbol{a}_2\boldsymbol{b}_1&\boldsymbol{a}_2\boldsymbol{b}_2\end{pmatrix}.\]

> ##### <u>例</u>
> \[A = \begin{pmatrix}1&2\cr 3&4\end{pmatrix},\qquad B =  \begin{pmatrix}2&3\cr 4&5\end{pmatrix}.\]
> * $AB = \begin{pmatrix}1\cdot2 + 2\cdot4 & 1\cdot3+2\cdot5\cr 3\cdot2+4\cdot4&3\cdot3+4\cdot5\end{pmatrix} = \begin{pmatrix}10&13\cr 22&29\end{pmatrix}$.
> * $BA = \begin{pmatrix}2\cdot1+3\cdot3&2\cdot2+3\cdot4\cr 4\cdot1+5\cdot3&4\cdot2+5\cdot4\end{pmatrix} = \begin{pmatrix}11&16\cr 19&28\end{pmatrix}$
> * このように $AB$ と $BA$ は一般には等しくならない.

##### <u>例</u>    
\[A = \begin{pmatrix}1&2\cr 3&4\end{pmatrix},\qquad B = \begin{pmatrix}2&3&0\cr 4&5&0\end{pmatrix}.\]
* $AB = \begin{pmatrix}10&13&0\cr 22&29&0\end{pmatrix}$.
* 一方, $BA$ は定義できない ($B$ の列の数は$3$, $A$ の行の数は $2$ で異なっている). このように, $AB$ が定義されたとしても $BA$ が定義されるとは限らない.

##### <u>命題</u> (結合則)
|行列 $A$, $B$, $C$ がそれぞれ $(k,\ell)$ 型, $(\ell,m)$ 型, $(m,n)$ 型であるならば, $$(AB)C = A(BC)$$ が成立する.|
|:---|


証明: 
$1$
```math
\frac{1}{2}
```
|これはテスト|
|:--|