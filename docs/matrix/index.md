<a id="section1"></a>

# 1: 行列

<a id="section1-1"></a>
## 1.1: 行列の定義

#### <u>定義</u> (行列)
縦に$m$個, 横に$n$個の数を長方形状に並べたものを$m\times n$ 型の**行列** (**matrix**) という.

#### <u>例</u> 
\[A = \begin{pmatrix}a_{11}&a_{12}\cr a_{21}&a_{22}\end{pmatrix},\qquad B=\begin{pmatrix}b_{11}&b_{12}&b_{13}\cr b_{21}&b_{22}&b_{32}\end{pmatrix}.\]

---

* 行列を構成する$mn$個の数を行列の**成分** (**element**) という
* 行列を構成する要素たちを横に並べた部分を**行** (**row**), 縦に並べた部分を**列** (**column**)という
* 上から $i$ 番目の行を**第 $i$ 行**, 左から $j$ 番目の列を**第 $j$ 列**という.
* 第 $i$ 行, 第 $j$ 列にある成分を **$ (i,j) $ 成分**という.
    * 以降, 断りの無い限り, 行列は大文字のアルファベットで表記し, 例えば行列 $A$ の $(i,j)$ 成分を小文字のアルファベットを用いて $ a_{ij} $ と表す. 
    * 行列 $A$ の $(i,j)$ 成分は $(A)_{ij}$ と表記されることもある.
    * また, $(i,j)$ 成分が $a_{ij}$ である行列を $(a_{ij})$ と表す.

#### <u>例</u>
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
* $1\times 1$ 型の行列は, そのただ $1$ つの成分である実数 (もしくは複素数) と同一視される.

#### <u>例</u>
* $A = \begin{pmatrix}a_{11}&a_{12}\cr a_{21}&a_{22}\end{pmatrix} \in \mathbb{R}^{2\times 2}.$
* ${\boldsymbol x} = (x_1,x_2,x_3)\in\mathbb{R}^{1\times3}$, &emsp; ${\boldsymbol x}$ は行ベクトル.
* ${\boldsymbol v} = \begin{pmatrix}v_1\cr v_2\cr v_3\end{pmatrix}\in\mathbb{R}^{3\times1}$, &emsp; ${\boldsymbol v}$ は列ベクトル.
* $\begin{pmatrix}a\end{pmatrix}\in\mathbb{R}^{1\times1}$ は $a\in\mathbb{R}$ と同一視される.

---
* 行列 $A = (a_{ij})\in\mathbb{R}^{m\times n}$ は, 
\[
    {\boldsymbol a} _ i = (a _ {i1},a _ {i2},\dots, a _ {in})
\] という行ベクトルたちを縦に並べたものと見なすことができる:
\[
    A = \begin{pmatrix}
    a_{11}&a_{12}&\dots&a_{1n}\cr 
    a_{21}&a_{22}&\dots&a_{2n}\cr
    \vdots&\vdots&\ddots&\vdots\cr
    a_{m1}&a_{m2}&\dots&a_{mn}
    \end{pmatrix} = \begin{pmatrix}
    {\boldsymbol a}_1 \cr {\boldsymbol a}_2 \cr \vdots \cr {\boldsymbol a}_m
    \end{pmatrix}.
\] このとき, 各 ${\boldsymbol a}_i$ を行列 $A$ の**第 $i$ 行ベクトル**という.
* 同様に, 行列 $A\in\mathbb{R}^{m\times n}$ を
\[
    {\boldsymbol a}_ j = \begin{pmatrix}a_{1j} \cr a_{2j} \cr \vdots \cr a_{mj}\end{pmatrix}
\] という列ベクトルたちを横に並べたものと見なすことができる:
\[
    A = \begin{pmatrix}
    a_{11}&a_{12}&\dots&a_{1n}\cr 
    a_{21}&a_{22}&\dots&a_{2n}\cr
    \vdots&\vdots&\ddots&\vdots\cr
    a_{m1}&a_{m2}&\dots&a_{mn}
    \end{pmatrix} = \begin{pmatrix}
    {\boldsymbol a}_1&{\boldsymbol a}_2&\dots&{\boldsymbol a}_n
    \end{pmatrix}.
\] このとき, 各 ${\boldsymbol a}_j$ を行列 $A$ の**第 $j$ 列ベクトル**という.

---

<a id="section1-2"></a>

## 1.2： 行列の演算
#### <u>定義</u>
$2$つの行列 $A=(a_{ij})$, $B=(b_{ij})$ について, $A$ と $B$ が同じ型であって, 全ての $i,j$ に対して \[a_{ij} = b_{ij}\] となるとき, $A$ と $B$ は等しいといい, \[A=B\] と表記する. $A=B$ でない場合は, $A\neq B$ と表記する.

#### <u>例</u>
\[A=\begin{pmatrix}1&2\cr 3&4\end{pmatrix},\quad B=\begin{pmatrix}1&2\cr 3&4\end{pmatrix},\quad C=\begin{pmatrix}1&2\cr 3&0\end{pmatrix},\quad D=\begin{pmatrix}1&2\cr 3&4\cr 0&0\end{pmatrix}.\]
* 行列の型が同じで, 全ての成分が等しいため $A=B$.
* $(2,2)$ 成分が異なるため $A\neq C$. 
* 行列の型が異なるため $A\neq D$.

---

#### <u>定義</u> (行列の和)
同じ型の$2$つの行列 $A=(a_{ij})$, $B=(b_{ij})$ に対し, $(i,j)$ 成分が $a_{ij}+b_{ij}$ である行列を $A$ と $B$ の和といい, $A+B$ と表記する.

#### <u>例</u>
\[A=\begin{pmatrix}1&2\cr 3&4\end{pmatrix},\quad B=\begin{pmatrix}1&2\cr 3&4\end{pmatrix},\quad C=\begin{pmatrix}1&2\cr 3&0\end{pmatrix},\quad D=\begin{pmatrix}1&2\cr 3&4\cr 0&0\end{pmatrix}.\]
* $A+B = \begin{pmatrix}1&2\cr 3&4\end{pmatrix}+\begin{pmatrix}1&2\cr 3&4\end{pmatrix} = \begin{pmatrix}2&4\cr 6&8\end{pmatrix}$ 
* $A+C = \begin{pmatrix}1&2\cr 3&4\end{pmatrix} + \begin{pmatrix}1&2\cr 3&0\end{pmatrix} = \begin{pmatrix}2&4\cr 6&4\end{pmatrix}$
* 行列の型が異なるため, $A+D$ は定義されない. 

##### <u>性質 (行列の和の可換性)</u>  
行列 $A$, $B$ の型が等しいならば, $A+B$ も $B+A$ も定義され,
\[
    A+B = B+A
\] が成立する.

---

#### <u>定義</u> (行列のスカラー倍)
行列 $A=(a_{ij})$ と複素数 $\lambda$ に対し, $(i,j)$ 成分が $\lambda a_{ij}$ である行列を $\lambda A$ と表記する.
#### <u>例</u>
\[A=\begin{pmatrix}1&2\cr 3&4\end{pmatrix}, \quad C=\begin{pmatrix}1&2\cr 3&0\end{pmatrix}.\]
* $2A = 2\begin{pmatrix}1&2\cr 3&4\end{pmatrix} = \begin{pmatrix}2&4\cr 6&8\end{pmatrix} = A+A$
* $A - C = A + (-1)C = \begin{pmatrix}1&2\cr 3&4\end{pmatrix} + \begin{pmatrix}-1&-2\cr -3&0\end{pmatrix} = \begin{pmatrix}0&0\cr 0&4\end{pmatrix}$

---

#### <u>定義</u> (行列の積)
$\ell\times m$ 型行列 $A=(a_{ij})$と, $m\times n$ 型行列 $B=(b_{ij})$ に対し, $(i,j)$ 成分が $\displaystyle\sum_{k=1}^m a_{ik}b_{kj}$ である $\ell \times n$ 型行列を $A$ と $B$ の**積**といい, $AB$ と表記する. 

#### <u>注意</u>
行列積 $AB$ は, 左側の行列 (この場合は$A$) の列の数と, 右側の行列 (この場合は$B$) の行の数が等しいときに限り定義される.  

#### <u>例</u>
\[{\boldsymbol x} = (x_1,x_2)\in\mathbb{R}^{1\times2},\qquad {\boldsymbol y} = \begin{pmatrix}y_1\cr y_2\end{pmatrix}\in\mathbb{R}^{2\times1}.\]
* ${\boldsymbol x}{\boldsymbol y}\in\mathbb{R}^{1\times1}$ の $(1,1)$ 成分は $\displaystyle\sum_{k=1}^2 x_ky_k$.
* つまり行列 ${\boldsymbol x}{\boldsymbol y}$ は, そのただ $1$ つの成分である $x _ 1y _ 1+x _ 2y _ 2$ と同一視される.
* これはベクトル $\vec{x}=(x_1,x_2)$ と $\vec{y}=(y_1,y_2)$ の内積 \[\vec{x}\cdot\vec{y} = x_1y_1+x_2y_2\] に等しい.

#### <u>例</u>
\[A = \begin{pmatrix}a_{11}&a_{12}\cr a_{21}&a_{22}\end{pmatrix}\in\mathbb{R}^{2\times 2},\qquad B = \begin{pmatrix}b_{11}&b_{12}\cr b_{21}&b_{22}\end{pmatrix}\in\mathbb{R}^{2\times 2}.\]
* $AB = \begin{pmatrix}a_{11}b_{11}+a_{12}b_{21}&a_{11}b_{12}+a_{12}b_{22}\cr a_{21}b_{11}+a_{22}b_{21}&a_{21}b_{12}+a_{22}b_{22}\end{pmatrix}$.
* 行列 $AB$ の $(i,j)$ 成分は, $A$ の第 $i$ 行ベクトル ${\boldsymbol a}_ i$ と $B$ の第 $j$ 列ベクトルの積となる：
\[
    AB = \begin{pmatrix}
    {\boldsymbol a}_ 1{\boldsymbol b}_ 1&{\boldsymbol a}_ 1{\boldsymbol b}_ 2\cr 
    {\boldsymbol a}_ 2{\boldsymbol b}_ 1&{\boldsymbol a}_ 2{\boldsymbol b}_ 2
    \end{pmatrix},
\] ここで　${\boldsymbol{a}}_ i = (a_ {i1},a_ {i2})$,&emsp; ${\boldsymbol{b}}_ j = \begin{pmatrix}b_ {1j}\cr b_ {2j}\end{pmatrix}$ である. 実際に, 行列積 ${\boldsymbol{a}}_ i {\boldsymbol{b}}_ j$ (すなわち行列積 $AB$ の $(i,j)$ 成分) は
\[
    \vec{a}_ i = (a_{i1}, a_{i2}),\quad \vec{b}_ j = (b_{1j}, b_{2j})
\] の内積と同一視することができるので $(a_{i1} b_{1j} + a_{i2} b_{2j})$ である. 

#### <u>例</u>
\[A = \begin{pmatrix}1&2\cr 3&4\end{pmatrix},\qquad B =  \begin{pmatrix}2&3\cr 4&5\end{pmatrix}.\]
* $AB = \begin{pmatrix}1\cdot2 + 2\cdot4 & 1\cdot3+2\cdot5\cr 3\cdot2+4\cdot4&3\cdot3+4\cdot5\end{pmatrix} = \begin{pmatrix}10&13\cr 22&29\end{pmatrix}$.
* $BA = \begin{pmatrix}2\cdot1+3\cdot3&2\cdot2+3\cdot4\cr 4\cdot1+5\cdot3&4\cdot2+5\cdot4\end{pmatrix} = \begin{pmatrix}11&16\cr 19&28\end{pmatrix}$
* このように $AB$ と $BA$ は一般には等しくならない.

#### <u>例</u>    
\[A = \begin{pmatrix}1&2\cr 3&4\end{pmatrix},\qquad B = \begin{pmatrix}2&3&0\cr 4&5&0\end{pmatrix}.\]
* $AB = \begin{pmatrix}10&13&0\cr 22&29&0\end{pmatrix}$.
* 一方, $BA$ は定義できない ($B$ の列の数は$3$, $A$ の行の数は $2$ で異なっている). このように, $AB$ が定義されたとしても $BA$ が定義されるとは限らない.

#### <u>例</u>
\[A = \begin{pmatrix}1&2\cr 3&4\end{pmatrix},\qquad {\boldsymbol{x}} = \begin{pmatrix}x_1\cr x_2\end{pmatrix}.\]

* $A{\boldsymbol{x}} = \begin{pmatrix}x_2+2x_2\cr 3x_1+4x_2\end{pmatrix}$.
* このように, 行列と列ベクトルの積により列ベクトルが得られる.
* 実は連立 $1$ 次方程式は, 『与えられた行列 $A$ と列ベクトル ${\boldsymbol{b}}$ に対し, $A{\boldsymbol{x}} = {\boldsymbol{b}}$ を満たす列ベクトル ${\boldsymbol{x}}$ を求めよ』 という問題と同一視することができる (後の章で改めて説明する).

#### <u>例</u>
\[{\boldsymbol x} = (x_1,x_2)\in\mathbb{R}^{1\times2},\qquad {\boldsymbol y} = \begin{pmatrix}y_1\cr y_2\end{pmatrix}\in\mathbb{R}^{2\times1}.\]
* いま,
\[
    {\boldsymbol y}{\boldsymbol x} = \begin{pmatrix}y_1x_1&y_1x_2\cr y_2x_1&y_2x_2\end{pmatrix}\in\mathbb{R}^{2\times2 }
\] であり, これはベクトルの内積と同一視できない.
* ベクトルの内積と同一視できるのは, $(\text{行ベクトル})(\text{列ベクトル})$ という形をしたベクトル同士の行列積であり, 上のように $(\text{列ベクトル})(\text{行ベクトル})$ という形の積に関してはこの限りでは無いので注意.

---

#### <u>命題</u> (結合則)
行列 $A$, $B$, $C$ がそれぞれ $k\times\ell$ 型, $\ell\times m$ 型, $m\times n$ 型であるならば, \[(AB)C = A(BC)\] が成立する.

> 証明:
$ A=(a_{ip}) $, $ B=(b_{pq}) $, $ C=(c_{qj}) $ とする. 
行列 $(AB)\in\mathbb{R}^{k\times m}$ の $ (i,q) $ 成分は 
\[
    \displaystyle\sum_{p=1}^{\ell} a_{ip}b_{pq}
\] なので, 行列 $(AB)C$ の $ (i,j) $ 成分は 
\[
    \displaystyle\sum_{q=1}^m\left(\sum_{p=1}^{\ell}a_{ip}b_{pq}\right) c_{qj} = \sum_{p=1}^{\ell}\sum_{q=1}^ma_{ip}b_{pq}c_{qj} 
\] となる. 一方で, 行列 $(BC)\in\mathbb{R}^{\ell\times n}$ の $ (p,j) $ 成分は 
\[
    \sum_{q=1}^mb_{pq}c_{qj}
\] なので, 行列 $ A(BC) $ の $ (i,j) $ 成分は 
\[
    \sum_{p=1}^{\ell}a_{ip}\left(\sum_{q=1}^mb_{pq}c_{qj}\right) = \sum_{p=1}^{\ell}\sum_{q=1}^ma_{ip}b_{pq}c_{qj}
\] となる. 従って, $ (AB)C = A(BC) $ が得られる. 

---

#### <u>命題</u> (分配則)
* 行列 $A$, $B$, $C$ がそれぞれ $\ell\times m$ 型, $m\times n$ 型, $m\times n$ 型であるならば, 
\[
    A(B+C) = AB+AC
\] が成立する.
* 行列 $A$, $B$, $C$ がそれぞれ $\ell\times m$ 型, $\ell\times m$ 型, $m\times n$ 型であるならば, 
\[
    (A+B)C = AC+BC
\] が成立する.

> 証明:
上のみ証明する: $ A=(a_{ik}) $, $ B=(b_{kj}) $, $C=(c_{kj}) $ とする. このとき, 行列 $A(B+C) $ の $ (i,j)$ 成分は
\[
    \sum_{k=1}^ma_{ik}(b_{kj}+c_{kj})
\] である. 一方, 行列 $AB$, $AC$ の $ (i,j) $ 成分はそれぞれ
\[
    \sum_{k=1}^ma_{ik}b_{kj},\qquad \sum_{k=1}^ma_{ik}c_{kj}
\] なので $A(B+C) = AB+AC$ が得られる.

---
#### <u>定義</u> (複素共役行列)
行列 $A$ の各成分を, その複素共役で置き換えた行列を**複素共役行列**といい, $\overline{A}$ と表記する.

#### <u>命題</u> 
\[
    \overline{\overline{A}}=A, \quad 
    \overline{A+B} = \overline{A}+\overline{B}, \quad
    \overline{\lambda A} = \overline{\lambda}\ \overline{A}, \quad
    \overline{AB} = \overline{A}\ \overline{B}.
\]
証明略

---
#### <u>定義</u> (転置行列)
行列 $A=(a_{ij})$ に対し, 第 $(i,j)$ 成分が $a_{ji}$ である行列を $A$ の**転置行列** といい, $A^{\operatorname{T}}$, もしくは ${}^tA$ と表記する. 行列の転置行列をとる操作を**転置** (**transpose**) という.

#### <u>注意</u>
* 転置は行と列を入れ替える (つまり $i$ と $j$ を入れ替える) 操作である.
* $m\times n$ 型行列の転置は $n\times m$ 型行列になる

#### <u>例</u>   
* ${\boldsymbol x} = (x_1,x_2)$ のとき, ${\boldsymbol x}^{\operatorname{T}} = \begin{pmatrix}x_1\cr x_2\end{pmatrix}$
* $A = \begin{pmatrix} a_{11}&a_{12}\cr a_{21}&a_{22} \end{pmatrix}$ のとき, $A^{\operatorname{T}} = \begin{pmatrix} a_{11}&a_{21}\cr a_{12}&a_{22}\end{pmatrix}$
* $B = \begin{pmatrix}b_{11}&b_{12}&b_{13}\cr b_{21}&b_{22}&b_{23}\end{pmatrix}$ のとき, $B^{\operatorname{T}} = \begin{pmatrix}b_{11}&b_{21}\cr b_{12}&b_{22}\cr b_{13}&b_{23}\end{pmatrix}$.

#### <u>命題</u> 
\[
    (A^{\operatorname{T}})^{\operatorname{T}}=A, \quad 
    (A+B)^{\operatorname{T}} = A^{\operatorname{T}}+B^{\operatorname{T}}, \quad
    (AB)^{\operatorname{T}} = B^{\operatorname{T}}A^{\operatorname{T}}.
\]

> 証明:
最後の式のみ証明する: $A=(a_{ik})\in\mathbb{R}^{\ell\times m}$, $B=(b_{kj})\in\mathbb{R}^{m\times n}$ とすると, 行列 $AB\in\mathbb{R}^{m\times n}$ の $(i,j)$ 成分は
\[
    \sum_{k=1}^ma_{ik}b_{kj}
\] なので, $(AB)^{\operatorname{T}}$ の $(i,j)$ 成分は
\[
    \sum_{k=1}^ma_{jk}b_{ki}
\] となる. 一方, $B^{\operatorname{T}}$ の第 $i$ 行ベクトルは, $B$ の第 $i$ 列ベクトル ${\boldsymbol b} _ i$ の転置であり, $A^{\operatorname{T}}$ の第 $j$ 列ベクトルは, $A$ の第 $j$ 行ベクトル ${\boldsymbol a} _ j$ の転置である. 従って, 行列 $B^{\operatorname{T}} A^{\operatorname{T}}$ の $(i,j)$ 成分は
\[
    {\boldsymbol b} _ i^{\operatorname{T}}{\boldsymbol a} _ j^{\operatorname{T}} = (b _ {1i}, b _ {2i},\dots, b _ {mi})\begin{pmatrix}a_{j1}\cr a_{j2}\cr \cdots\cr a_{jm}\end{pmatrix} = \sum_{k=1}^m a_{jk} b_{ki}.
\]
従って $(AB)^{\operatorname{T}} = B^{\operatorname{T}}A^{\operatorname{T}}$ が得られる.

#### <u>例</u>
\[A = \begin{pmatrix}1&2&3\cr 4&5&6\end{pmatrix},\quad B=\begin{pmatrix}2&4\cr 6&8\cr 10&12\cr \end{pmatrix}.\]
* $AB = \begin{pmatrix}44& 56\cr 98&128\end{pmatrix}$.
* $A^{\mathrm{T}} = \begin{pmatrix}1&4\cr 2&5\cr 3&6\end{pmatrix}$, &emsp; $B^{\operatorname{T}} = \begin{pmatrix}2&6&10\cr 4&8&12\end{pmatrix}$.
* 従って, $B^{\operatorname{T}}A^{\operatorname{T}} = \begin{pmatrix}44&98\cr 56&128\end{pmatrix} = (AB)^{\operatorname{T}}$.

<a id="section1-3"></a>

## 1.3： 正方行列など

#### <u>定義</u> (零行列)
全ての成分が $0$ である行列を**零行列** (**zero matrix**) といい, $O$ と表記する.

#### <u>例</u>  
* $O = \begin{pmatrix}0\end{pmatrix}\in\mathbb{R}^{1\times 1}$. これは $0\in\mathbb{R}$ と同一視される.
* $O=\begin{pmatrix}0&0\cr 0&0\end{pmatrix}\in\mathbb{R}^{2\times2}$.

#### <u>性質</u>  
任意の行列 $A$ に対して, 以下が成立する:
* $A-A = O$. この $O$ は $A$ と同じ型になる.
* $A+O = A$, ただし $A$ と $O$ は同じ型とする.
* $0A =O$, この $O$ は $A$ と同じ型になる.
* 行列積 $AO$ が定義されるなら $AO=O$, ただし両辺の $O$ が同じ型とは限らない.
* 行列積 $OA$ が定義されるなら $OA=O$, ただし両辺の $O$ が同じ型とは限らない.

#### <u>例</u>  
\[A = \begin{pmatrix}1&2\cr 3&4\end{pmatrix}, \quad {\boldsymbol{x}} = \begin{pmatrix}x_1\cr x_2\end{pmatrix}.\]
* $(A-A){\boldsymbol{x}} = \begin{pmatrix}0&0\cr 0&0\end{pmatrix}{\boldsymbol{x}} = O{\boldsymbol{x}} = \begin{pmatrix}0\cr 0\end{pmatrix} = O$.

---

#### <u>定義</u> (正方行列)
$m\times n$ 型の行列 $A$ について, $m=n$ であるとき (つまり行と列の数が等しいとき) $A$ を**正方行列** (**square matrix**), もしくは $n$ 次正方行列という.

#### <u>注意</u> 
* $A=(a_{ij})$ が正方行列ならば, $A$ の成分 $a_{ii}$ たちは行列の左上から右下にかけての対角線上に位置している. これらの成分を**対角成分** (**main diagonal**) という.
* 正方行列 $A$ の転置行列 $A^{\mathrm{T}}$ は $A$ と同じ型の正方行列となり, それらの対角成分は一致する.
* $A$ が正方行列ならば, 行列積 $AA$ が定義できる. これを $A^2$ と表記する. 
* 同様に, $k$ 個の $A$ を掛け合わせた行列積 $A\cdots A$ を $A^k$ と表記する.

---

#### <u>定義</u> (対称行列)
正方行列 $A$ について, 
\[
    A=A^{\mathrm{T}}
\] が成立するとき, $A$ を**対称行列** (**symmetric matrix**) という. 

#### <u>注意</u> 
行列 $A$ の転置 $A^{\mathrm{T}}$ の定義より, 正方行列 $A = (a_{ij})$ が対称であることは, 任意の $i$, $j$ に対して
\[
    a_{ij} = a_{ji}
\] が成立することと同値である.

---

#### <u>定義</u> (歪対称行列)
正方行列 $A$ について, 
\[
    A=-A^{\mathrm{T}}
\] が成立するとき, $A$ を**歪対称行列** (**skew-symmetric matrix**) もしくは**交代行列** (**alternating matrix**) という. 

#### <u>注意</u> 
* 正方行列 $A = (a_{ij})$ が歪対称であることは, 任意の $i$, $j$ に対して
\[
    a_{ij} = -a_{ji}
\] が成立することと同値である.
* 正方行列 $A=(a_{ij})$ が歪対称行列ならば, 特に任意の $i$ に対して $a_{ii} = -a_{ii}$, すなわち 
\[
    a_{ii}=0
\] が成立する. つまり, 歪対称行列の対角成分は必ず $0$ である.

---

#### <u>定義</u> (対角行列)
正方行列 $A$ について, その対角成分以外が $0$ であるとき, $A$ を**対角行列** (**diagonal matrix**) という.

#### <u>例</u> 
* $A = \begin{pmatrix}a_1&0&0\cr 0&a_2&0\cr 0&0&a_3\end{pmatrix}$ は正方行列であり, 非対角成分が全て $0$ なので対角行列である.

#### <u>注意</u> 
* 以降,
\[
    \delta_{ij} = \cases{
    1 \quad\text{if}\quad i=j,\cr
    0 \quad\text{if}\quad i\neq j
    }
\]という表記を用いる (これを**クロネッカーのデルタ記号**, **Kronecker delta** という). これを用いると, 対角行列は
\[
    A = (a_i\delta_{ij})
\] と表記できる.

---

#### <u>定義</u> (単位行列)
対角成分が全て $1$ である対角行列を**単位行列** (**identity matrix**) といい, $I$ (もしくは $E$) と表記する.

#### <u>例</u>  
* $I = \begin{pmatrix}1\end{pmatrix}\in\mathbb{R}^{1\times 1}$. これは $1\in\mathbb{R}$ と同一視される.
* $I=\begin{pmatrix}1&0\cr 0&1\end{pmatrix}\in\mathbb{R}^{2\times2}$.

#### <u>性質</u> 
* クロネッカーのデルタを用いると, $I=(\delta_{ij})$ と表記できる.
* 行列積 $IA$ が定義されるなら $IA=A$.
* 行列積 $AI$ が定義されるなら $AI=A$.
* 任意の $n$ に対し, $I^n=I$.
* 全ての対角成分が $\lambda$ である対角行列は $\lambda I$ と表すことができる:
\[
    \lambda IA = \lambda A,\quad A(\lambda I) = \lambda A,\quad (\lambda I)^n = \lambda^n I.
\]

#### <u>定義</u> (標準基底)
単位行列の各列ベクトル
\[
    {\boldsymbol e}_1 = \begin{pmatrix}1\cr0\cr\vdots\cr0\end{pmatrix},\quad {\boldsymbol e}_2 = \begin{pmatrix}0\cr1\cr\vdots\cr0\end{pmatrix}, \quad \dots
\] を**標準基底** (**canonical basis**) という.

---

行列積の定義で述べたように, 行列積 $AB$ の $(i,j)$ 成分 は $A$ の第 $i$ 行ベクトルと $B$ の第 $j$ 列ベクトルの行列積を用いて表現することができる. これを一般化して行列の**区分け**による行列積の表現が可能である.

#### <u>例</u>    
\[A=\begin{pmatrix}1&2&3\cr 4&5&6\cr 7&8&9\end{pmatrix}, \quad B=\begin{pmatrix}2&3\cr4&5\cr6&7\end{pmatrix}, \quad AB = \begin{pmatrix}28&34\cr 64&79\cr 100&124\end{pmatrix}.\]
* 例えば, 行列 $A$ を, $2$ 行目と $3$ 行目の間, 及び　$2$ 列目と $3$ 列目の間で区切り, これに合わせて $B$ を $2$ 行目と $3$ 行目の間で区切ることを考える:
$ A = \left(\begin{array}{cc:c}1&2&3\cr 4&5&6\cr\hdashline 7&8&9\end{array}\right) = \begin{pmatrix}A_{11}&A_{12}\cr A_{21}&A_{22}\end{pmatrix}$, &emsp; $B=\begin{pmatrix}2&3\cr4&5\cr\hdashline 6&7\end{pmatrix} = \begin{pmatrix}B_{11}\cr B_{21}\end{pmatrix}$ 
    * この区分けを用いた場合, 形式的に $A$ は $2\times2$ 型, $B$ は $2\times1$ 型と思うことで行列積 $AB$ を計算できる.
* このとき, 
\[
    AB = \begin{pmatrix}A_{11}B_{11}+A_{12}B_{21}\cr A_{21}B_{11} + A_{22}B_{21}\end{pmatrix} = \begin{pmatrix}28&34\cr 64&79\cr\hdashline 100&124\end{pmatrix}
\] と表現することができる. 実際に計算してみると,
$A_{11}B_{11} = \begin{pmatrix}10&13\cr 28&37\end{pmatrix}$, &emsp; $A_{12}B_{21} = \begin{pmatrix}18&21\cr 36&42\end{pmatrix},$
$A_{21}B_{11} = \begin{pmatrix}46&61\end{pmatrix}$,&emsp; $A_{22}B_{21} = \begin{pmatrix}54&63\end{pmatrix}$
となる.
* 異なる区分けを用いても同じ結果が得られる. 例えば $A$ の区分けとして先ほどと同じものを考え, $B = \left(\begin{array}{c:c}2&3\cr 4&5\cr\hdashline 6&7\end{array}\right) = \begin{pmatrix}B_{11}&B_{12}\cr B_{21}&B_{22}\end{pmatrix}$ と思った場合も, 形式的に $2\times 2$ 型行列同士の行列積と思って
\[
    AB = \begin{pmatrix}A_{11}B_{11}+ A_{12}B_{21}&A_{11}B_{12}+A_{12}B_{22}\cr A_{21}B_{11}+A_{22}B_{21}&A_{21}B_{12}+A_{22}B_{22}\end{pmatrix} = \left(\begin{array}{c:c}28&34\cr 64&79\cr\hdashline 100&124\end{array}\right)
\] とみなすことができる.
* 一方で, 例えば $B = \left(\begin{array}{c:c}2&3\cr 4&5\cr 6&7\end{array}\right) = (B_ {11}, B_ {12})$ と区切ってしまうと, $2\times 2$ 型の行列と行ベクトルとの行列積は定義されないため, この区分けに基づく行列積の計算はできない.

区分けによる表記は, 単純な計算テクニックとしてはあまり有用ではない. しかしながら, 行列の区分けの一部が零行列や単位行列となる場合に, この表記を用いることがある:

#### <u>例</u>   
\[A = \begin{pmatrix}2&0&0\cr 0&2&0\cr 1&2&3\end{pmatrix},\quad {\boldsymbol{x}} = \begin{pmatrix}x_1\cr x_2\cr x_3\end{pmatrix}.\]
* 行列 $A$ に対して, $A=\left(\begin{array}{cc:c}2&0&0 \cr 0&2&0 \cr \hdashline 1&2&3\end{array}\right) = \begin{pmatrix}2I&O \cr A^\prime & 3\end{pmatrix}$ という区分けを考える, ここで　$A'=(1,2)$. 
* 対応して, ${\boldsymbol{x}} = \begin{pmatrix}x_ 1\cr x_ 2\cr\hdashline x_ 3\end{pmatrix}$ という区分けを考える. 
* このとき, $A{\boldsymbol{x}} = \begin{pmatrix}2I\begin{pmatrix}x_1\cr x_2\end{pmatrix} + Ox_3\cr A^\prime \begin{pmatrix}x_1\cr x_2\end{pmatrix}+3x_3\end{pmatrix} = \begin{pmatrix}2x_1\cr 2x_2\cr x _ 1+2x _ 2+3x _ 3\end{pmatrix}$

---

#### <u>定義</u> (正則行列と逆行列)
正方行列 $A$ に対して, 同じ型の正方行列 $B$ であって 
\[
    AB = BA = I
\] を満たすものが存在するならば, $B$ を $A$ の**逆行列** (**inverse matrix**) といい, $A^{-1}$ と表記する. 正方行列 $A$ の逆行列が存在するならば, $A$ を**正則行列** (**regular matrix**) もしくは**可逆行列** (**invertible matrix**) という.

#### <u>例</u> 
* 零行列 $O\in\mathbb{R}^{n\times n}$ の逆行列は存在しない.
* 単位行列 $I$ の逆行列は単位行列 $I$ である: &emsp; $I^{-1}=I$. 
* 対角行列
\[
    A = \begin{pmatrix}a_1&0&\dots&0\cr 0&a_2&\dots&0\cr \vdots&\vdots&\ddots&\vdots\cr 0&0&\dots&a_n\end{pmatrix}
\] は, 任意の $i$ に対し $a_i\neq0$ が成立するならば正則行列であり, 逆行列は
\[
    A^{-1} = \begin{pmatrix}1/a_1&0&\dots&0\cr 0&1/a_2&\dots&0\cr \vdots&\vdots&\ddots&\vdots\cr 0&0&\dots&1/a_n\end{pmatrix}
\] である.

* $A=\begin{pmatrix}1&2\cr 3&4\end{pmatrix}$ とする. ここで,
\[
    A\begin{pmatrix}-2&1\cr 3/2&-1/2\end{pmatrix} = I,\quad\begin{pmatrix}-2&1\cr 3/2&-1/2\end{pmatrix}A = I 
\] となるので, $A^{-1} = \begin{pmatrix}-2&1\cr 3/2&-1/2\end{pmatrix}$.
* $B = \begin{pmatrix}1&2\cr 2&4\end{pmatrix}$ の逆行列は存在しない. これは背理法で以下のように確かめられる: もしも \[
    B\begin{pmatrix}a&b\cr c&d\end{pmatrix} = I
    \] を満たす行列 $\begin{pmatrix}a&b\cr c&d\end{pmatrix}$ が存在したならば, 
    \[\cases{
        a+2c &= 1,\cr
        b+2d &= 0,\cr
        2a+4c &= 0,\cr
        2b+4d &= 1
    } \] となり矛盾する.

#### <u>命題</u> 
逆行列について以下が成立する:
* $A^{-1}$, $B^{-1}$ が存在するならば $(AB)^{-1} = B^{-1}A^{-1}$  
* $A^{-1}$ が存在するならば, $(A^{-1})^{-1} = A$.
* $A^{-1}$ は存在するならばただ$1$つに定まる.

> 証明:
>* \[
        (AB)(B^{-1}A^{-1}) = ABB^{-1}A^{-1} = AIA^{-1} = AA^{-1}=I,
    \]\[
       (B^{-1}A^{-1})(AB) = B^{-1}A^{-1}AB = B^{-1}IB = B^{-1}B=I. 
    \] 従って, 逆行列の定義より $(AB)^{-1} = B^{-1}A^{-1}$.
>* $I^{-1}=I$ と先ほどの結果から
    \[
    I = I^{-1} = (AA^{-1})^{-1} = (A^{-1})^{-1}A^{-1}.
    \] これを用いると
    \[
        (A^{-1})^{-1} = (A^{-1})^{-1}I=(A^{-1})^{-1}A^{-1}A = IA=A.
    \]
>* (背理法) $2$ つの異なる行列 $B$, $C$ に対して,
\[
    AB=BA=AC=CA=I
\] が成立すると仮定する. このとき,
\[
    B = BI = B(AC) = (BA)C = IC = C,
\] これは $B\neq C$ に矛盾する. 従って, 背理法より $A$ の逆行列はただ $1$ つに定まる.

#### <u>注意</u> 
* 上の結果より, 特に正則行列たちの積は正則行列になる.
* 実は, 正方行列 $A$ に対し $AB=I$ を満たす $B$ が存在すれば, そのような $B$ は $BA=I$ も満たす (つまり $B=A^{-1}$ となる).
* 同様に, $BA=I$ なる $B$ は, $B=A^{-1}$ となる.
* (与えられた行列に対する逆行列の計算方法については, 後の機会に改めて解説する)

#### <u>例</u> 
\[
    A=\begin{pmatrix}1&2\cr 3&4\end{pmatrix},\quad B= \begin{pmatrix}-2&1\cr 3/2&-1/2\end{pmatrix}.
\]
* いま, $AB = I$ となることだけ確かめれば, $BA=I$ も自動的に満たされるため, $B=A^{-1}$ であることがわかる.
* 同様に $BA=I$ となることだけ確かめれば, $AB=I$ も自動的に満たされるため, $B=A^{-1}$ であることがわかる.

---
