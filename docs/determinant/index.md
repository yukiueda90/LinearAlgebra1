<a id="section3"></a>

# 3: 行列式

<a id="section3-1"></a>

## 3.1: 逆行列の存在

ここでは, 行列 $A$ として常に正方行列を考えることにする. この行列 $A$ の逆行列について, ここまでの内容を以下にいくつか再掲する:

#### <u>定義</u> (正則行列と逆行列)
正方行列 $A$ に対して, 同じ型の正方行列 $B$ であって 
\[
    AB = BA = I
\] を満たすものが存在するならば, $B$ を $A$ の**逆行列** (**inverse matrix**) といい, $A^{-1}$ と表記する. 正方行列 $A$ の逆行列が存在するならば, $A$ を**正則行列** (**regular matrix**) もしくは**可逆行列** (**invertible matrix**) という.

#### <u>命題</u> 
逆行列について以下が成立する:
* $A^{-1}$, $B^{-1}$ が存在するならば $(AB)^{-1} = B^{-1}A^{-1}$  
* $A^{-1}$ が存在するならば, $(A^{-1})^{-1} = A$.
* $A^{-1}$ は存在するならばただ$1$つに定まる.

##### <u>注意</u> 
* 正則行列たちの積は正則行列になる.
* 正方行列 $A$ に対し $AB=I$ を満たす $B$ が存在すれば, そのような $B$ は $BA=I$ も満たす (つまり $B=A^{-1}$ となる).
* 同様に, $BA=I$ なる $B$ は, $B=A^{-1}$ となる.

#### <u>定理</u>
$A$ を $n$ 次正方行列とする. このとき, 以下が成立する:
\[
    \operatorname{rank}A = n \iff A \text{ は正則}.
\]

#### <u>系</u>
$A$ を $n$ 次正方行列とする. このとき, 以下が成立する:
\[
    A\text{ が正則}\iff A\text{ は基本行列の積で表現される}.
\]

---

ここまでの内容では, ある正方行列 $A$ に逆行列が存在するか否かを判定する方法として, 
* $AB=I$ (もしくは $BA=I$) を満たす行列 $B$ を見つける (もしくはそのような行列 $B$ が存在しないことを示す),
* $A$ の階数を計算する,
* $A$ と単位行列 $I$ を並べた拡大行列に対し, 掃き出し法を適用する

を紹介した (ちなみに, 階数の計算は拡大行列に対する掃き出し法とほぼ同じ計算であり, 逆行列が存在するときにそれを具体的に計算できるかどうかだけ異なる). 

ここでは, 逆行列の存在判定 (及び逆行列の具体的な計算) に用いられる基準として, **行列式** (**determinant**) を導入する. その定義, 性質や応用は改めて紹介するが, その内いくつかをあらかじめ簡単に述べておく:

* 正方行列 $A$ の行列式を, 
\[
    \det A \quad (\text{もしくは $|A|$}) 
\] と表記する.
* $A=(a_{ij})$ の行列式は,
\[\left\lvert\begin{array}{cccc}a_{11} & a_{12} & \dots & a_{1n} \cr a_{21} & a_{22} & \dots & a_{2n} \cr \vdots & \vdots & \ddots& \vdots\cr a_{n1} & a_{n2} &\dots& a_{nn}\end{array}\right\rvert\] などと表記することもある.
* 実正方行列の行列式は実数である.
* $n$ 次正方行列
\[
    F(r) =\begin{pmatrix}I_r&O\cr O&O\end{pmatrix} = \begin{pmatrix}1\cr&1\cr&&\ddots\cr&&&1\cr&&&&0\cr&&&&&\ddots\end{pmatrix}   
\] に対して, 
\[
    \det F(r) = \left\lbrace\begin{array}{rl}
    1&\text{if } r = n,\cr
    0&\text{if } r < n
    \end{array}\right.
\] が成立する.
* 基本行列 $P_{i,j}$, $Q_{i,\lambda}$, $R_{i,j,\lambda}$ に対して,
\[
    \det P_{i,j} \neq 0,\quad \det Q_{i,\lambda} \neq 0,\quad \det R_{i,j,\lambda} \neq 0   
\] が成立する.
* 二つの $n$ 次正方行列 $A$, $B$ に対して,
\[
    \det (AB) = (\det A)(\det B)
\] が成立する.

これらの性質を用いることで, 以下の性質を得ることができる:

#### <u>定理</u>
$A$ を $n$ 次正方行列とする. このとき, 以下が成立する:
\[
    \det A\neq 0\iff \operatorname{rank}A = n \iff A \text{ は正則}.
\]
> 証明
> 正方行列 $A$ は, 基本行列の積により表される行列 $P$, $Q$ を用いて $A = PF(r)Q$ と表されるのだった. これと行列式の性質より, 
\[
    \det A\neq 0 \iff \det F(r)\neq 0 \iff \operatorname{rank} A=n
\] が得られる.

すなわち, 正方行列 $A$ の逆行列が存在するか否か判定するには, $A$ の行列式を計算すれば良いことになる.

---

<a id="section3-2"></a>

## 3.2: 行列式の定義

ここでは, 行列式の定義を述べる. 行列式を上で述べた性質が満たされるよう構成するために, (唐突ではあるが) まずは**置換**という概念を導入する:

#### <u>定義 (置換)</u>
$n$ 個の元からなる集合を考える (ここでは, $\lbrace 1, 2, \dots, n\rbrace$ のみを考えることにする). これを並び替える操作を**置換** (**permutation**) という. いま, $\lbrace 1, 2, \dots n\rbrace を \lbrace \sigma(1), \sigma(2), \dots, \sigma(n)\rbrace$ に並び替える置換を
\[
    \sigma = \begin{bmatrix}1& 2& \dots & n\cr \sigma(1) & \sigma(2) & \dots & \sigma(n)\end{bmatrix}
\]
と表記する. $n$ 個に対する置換全体を $S_n$ と表記し, $\sigma$ が $n$ 個に対する置換であるとき $\sigma\in S_n$ と表記する.

#### <u>例</u>
$\lbrace 1,2,3\rbrace$ に対し, $1$ 番目と $2$ 番目を入れ替えると $\lbrace 2,1,3\rbrace$ という順序になるが, この並び替えは
\[
    \begin{bmatrix}1&2&3\cr 2&1&3\end{bmatrix}\in S_3
\] と表記される.

#### <u>例</u>
$\lbrace 1,2,3\rbrace$ に対し, $1$ 番目を $2$ 番目に, $2$ 番目を $3$ 番目に, $3$ 番目を $1$ 番目に取り替えると $\lbrace 2,3,1\rbrace$ という順序になるが, この並び替えは 
\[
    \begin{bmatrix}1&2&3\cr 2&3&1\end{bmatrix} \in S_3
\] と表記される.

#### <u>例</u>
$\lbrace 1,2,3\rbrace$ の置換 $S_n$ は以下の $6$ つからなる:
\[
    \begin{bmatrix}1& 2& 3\cr 1 & 2 & 3\end{bmatrix},\quad \begin{bmatrix}1& 2& 3\cr 2 & 1 & 3\end{bmatrix},\quad \begin{bmatrix}1& 2& 3\cr 1 & 3 & 2\end{bmatrix},
\] \[
    \begin{bmatrix}1& 2& 3\cr 3 & 2 & 1\end{bmatrix},\quad \begin{bmatrix}1& 2& 3\cr 2 & 3 & 1\end{bmatrix},\quad \begin{bmatrix}1& 2& 3\cr 3 & 1 & 2\end{bmatrix}.
\]

#### <u>定義 (置換の積)</u>
$2$ つの置換 $\sigma$, $\tau$ を合成したもの (つまり $\sigma$ により並び替えたものを $\tau$ によりさらに並び替えたもの) を置換の**積**といい, $\tau\sigma$ と表記する.

#### <u>例</u>
\[
    \sigma = \begin{bmatrix}1& 2& 3\cr 2 & 1 & 3\end{bmatrix}, \quad \tau = \begin{bmatrix}1& 2& 3\cr 1 & 3 & 2\end{bmatrix}.
\]
* $\lbrace 1,2,3\rbrace$ を $\sigma$ により並び替えると $\lbrace 2,1,3\rbrace$ となる.
* これをさらに $\tau$ により並び替える, つまり $\lbrace 2,1,3\rbrace$ の $2$ 番目と $3$ 番目を入れ替えると $\lbrace 2,3,1\rbrace$ となる.
* つまり $\sigma$ と $\tau$ の合成は $\lbrace 1,2,3\rbrace$ を $\lbrace 2,3,1\rbrace$ に並び替える置換になる.
* 従って $\tau\sigma = \begin{bmatrix}1&2&3\cr 2&3&1\end{bmatrix}$ となる.

#### <u>注意</u>
* 置換の積は右側から先に適用する. 先の例では, $\sigma$ により並び替えたものを $\tau$ で並び替える操作は $\tau\sigma$ と表記される.
* 一般には $\tau\sigma \neq \sigma\tau$ に注意. 上の例では, $\sigma\tau$ は $\lbrace 1,2,3\rbrace$ を $\lbrace 3,1,2\rbrace$ に並び替える操作であり,
\[
    \sigma\tau = \begin{bmatrix}1&2&3\cr 3&1&2\end{bmatrix} \neq \tau\sigma.
\] である.

#### <u>定義 (恒等置換と逆置換)</u>
* $\lbrace 1,2,\dots, n\rbrace$ を並び替えない操作を**恒等置換**といい, 
\[
    1_n = \begin{bmatrix}1&2&\dots &n\cr 1&2&\dots & n\end{bmatrix}
\] と表記する.
* 置換 $\sigma$ に対し, $\sigma\tau = \tau\sigma = 1_n$ を満たす置換 $\tau$ を $\sigma$ の**逆置換** といい, $\tau=\sigma^{-1}$ と表記する.

#### <u>定義 (互換)</u>
置換であって, $2$ つの入れ替えとして表現されるものを**互換** (**transposition**) という.

#### <u>例</u>
置換 $\begin{bmatrix}1&2&3\cr 2&1&3\end{bmatrix}$ は, $\lbrace 1,2,3\rbrace$ の $1$ 番目と $2$ 番目を入れ替えたものとみなせるので互換である.

#### <u>例</u>
置換 $\begin{bmatrix}1&2&3\cr 2&3&1\end{bmatrix}$ は, $\lbrace 1,2,3\rbrace$ の $2$ つのみ入れ替えたものとして表現できないため互換ではない.


#### <u>命題</u>
全ての置換は互換の積として表される.

証明略

#### <u>定義 (偶置換と奇置換)</u>
* 置換 $\sigma$ が恒等置換であるか, 偶数個の互換の積として表現されるならば, $\sigma$ を**偶置換** (**even permutation**)という.
* 置換 $\sigma$ が奇数個の互換の積として表現されるならば, $\sigma$ を**奇置換** (**odd permutation**)という.

#### <u>定義 (置換の符号)</u>
置換 $\sigma$ に対して,
\[
    \operatorname{sgn}\sigma = \left\lbrace\begin{array}{rl}
    1&\text{if }\sigma \text{ が偶置換},\cr
    -1&\text{if }\sigma \text{ が奇置換}
    \end{array}\right.
\] を置換 $\sigma$ の**符号**という.

つまり, 置換 $\sigma$ が $n$ 個の互換の積として表現されるならば 
\[\operatorname{sgn}\sigma = (-1)^n\] である.

#### <u>命題</u>
* $\operatorname{sgn} \sigma^{-1} = \operatorname{sgn}\sigma$.
* $\operatorname{sgn}(\tau\sigma) = (\operatorname{sgn}\sigma)(\operatorname{sgn}\tau)$.

証明略

---

置換の符号を用いることで, 正方行列に対する行列式の定義を記述することができる.

#### <u>定義 (行列式)</u>
$n$ 次正方行列 $A=(a_{ij})$ に対して,
\[
    \sum_{\sigma\in S_n}(\operatorname{sgn}\sigma) a_{1\sigma(1)} a_{2\sigma(2)}\dots a_{n\sigma(n)}
\] を $A$ の行列式といい, $\det A$ (もしくは $|A|$) と表記する.

#### <u>例</u>
$2$ 次正方行列 $A = (a_{ij}) = \begin{pmatrix}a&b\cr c&d\end{pmatrix}$ を考える. いま, $2$ 個に対する置換 $S_2$ は
\[
    \sigma_1 = \begin{bmatrix}1&2\cr 1&2\end{bmatrix},\quad \sigma_2 = \begin{bmatrix}1&2\cr 2&1\end{bmatrix}
\] からなる. ここで, 
\[
    \sigma_1(1) = 1,\quad \sigma_1(2)=2,\quad \operatorname{sgn}\sigma_1 = 1,
\]\[
    \sigma_2(1) = 2,\quad \sigma_2(2) = 1,\quad \operatorname{sgn} \sigma_2 = -1    
\] であることから,
\[
    \begin{array}{rl}
        \det A &= \operatorname{sgn}\sigma_1 a_{1\sigma_1(1)} a_{2\sigma_1(2)} + \operatorname{sgn}\sigma_2 a_{1\sigma_2(1)} a_{2\sigma_2(2)} \cr
        &= a_{11}a_{22} - a_{12}a_{21}\cr
        &= ad-bc
    \end{array}
\] となる. 計算中に行列 $A$ の $i\sigma_k(i)$ 成分を用いているが, $i$ と $\sigma_k(i)$ のペアは置換 $\sigma_k$ を行列とみなしたときの第 $i$ 列に一致することに注意.

#### <u>例</u>
$3$ 次正方行列 $A = (a_{ij}) = \begin{pmatrix}a&b&c\cr d&e&f\cr g&h&i\end{pmatrix}$ を考える. いま $S_3$ は先の例に挙げた 
\[
    \begin{bmatrix}1& 2& 3\cr 1 & 2 & 3\end{bmatrix},\quad \begin{bmatrix}1& 2& 3\cr 2 & 1 & 3\end{bmatrix},\quad \begin{bmatrix}1& 2& 3\cr 1 & 3 & 2\end{bmatrix},
\] \[
    \begin{bmatrix}1& 2& 3\cr 3 & 2 & 1\end{bmatrix},\quad \begin{bmatrix}1& 2& 3\cr 2 & 3 & 1\end{bmatrix},\quad \begin{bmatrix}1& 2& 3\cr 3 & 1 & 2\end{bmatrix}.
\] の$6$ つであり, それらを用いて計算すると
\[
    \begin{array}{rl}
        \det A &= a_{11} a_{22} a_{33} - a_{12} a_{21} a_{33} - a_{11} a_{23} a_{32} \cr
        &\qquad - a_{13} a_{22} a_{31} + a_{12} a_{23} a_{31} + a_{13} a_{21} a_{32}  \cr
        &= aei + bfg + cdh - ceg - bdi - afh
    \end{array}
\] となる.

#### <u>注意</u>
$4$ 次以上の正方行列に対しても上と同様にして行列式を計算することは可能だが, 実用上は (いくつかの特殊な場合を除いて) $2$ 次と $3$ 次の場合の行列式を公式として暗記すれば十分だろう:
\[
    A = \begin{pmatrix}a&b\cr c&d\end{pmatrix} \leadsto \det A = ad-bc.
\] \[
    A = \begin{pmatrix}a&b&c\cr d&e&f\cr g&h&i\end{pmatrix} \leadsto \det A =  aei + bfg + cdh - ceg - bdi - afh.
\]

---

<a id="section3-3"></a>

## 3.3: 行列式の性質

ここでは行列式の性質を列挙していく:

#### <u>命題</u>
対角行列の行列式は, その対角成分の積に等しい.

> 証明
> $A = (a_{ij})$ を対角行列とする, このとき
\[a_{ij} = 0 \quad \text{ if }\quad i\neq j\] である. 従って, 行列式の定義
\[
    \det A = \sum_{\sigma\in S_n}(\operatorname{sgn}\sigma) a_{1\sigma(1)} a_{2\sigma(2)}\dots a_{n\sigma(n)}
\] において, $\sigma(1)=1$, $\sigma(2)=2$, $\dots$, $\sigma(n)=n$ の場合を除き $a_{1\sigma(1)} a_{2\sigma(2)}\dots a_{n\sigma(n)}=0$ となる, すなわち, 対角行列 $A$ に対して
\[
    \det A = a_{11} a_{22} \dots a_{nn}
\] となる.

#### <u>例</u>
\[A = \begin{pmatrix}a&0&0\cr 0&b&0\cr 0&0&c\end{pmatrix}.\] このとき,
\[\begin{array}{rl}\det A &= abc + 0\cdot0\cdot0 + 0\cdot0\cdot0 \cr &\qquad - 0\cdot b\cdot0 -  0\cdot0\cdot c - a\cdot 0\cdot0 \cr & = abc\end{array}\]

#### <u>注意</u>
特に, $\det O = 0$ および $\det I = 1$ が成立する. 
#### <u>注意</u>
基本行列 $Q_{i,\lambda}$ について, $\det Q_{i,\lambda} = \lambda\neq0$ を確かめることができる. また, 
\[
    F(r) =\begin{pmatrix}I_r&O\cr O&O\end{pmatrix}\in\mathbb{R}^{n\times n}
\] について,
\[
    \det F(r) = \left\lbrace\begin{array}{rl}
    1&\text{if } r = n,\cr
    0&\text{if } r < n
    \end{array}\right.
\] も確かめられる.

---

#### <u>命題</u>
$n$ 次正方行列 $A$ と複素数 $\lambda$ に対し,
\[\det(\lambda A) = \lambda^n \det A\] が成立する.

> 証明
> 行列 $\lambda A$ の $(i,j)$ 成分は, $A$ の $(i,j)$ 成分の $\lambda$ 倍なので,
\[\begin{array}{rl}\det (\lambda A) &= \displaystyle\sum_{\sigma\in S_n}(\operatorname{sgn}\sigma) (\lambda a_{1\sigma(1)}) (\lambda a_{2\sigma(2)})\dots (\lambda a_{n\sigma(n)})\cr
&= \lambda^n \displaystyle\sum_{\sigma\in S_n}(\operatorname{sgn}\sigma) a_{1\sigma(1)} a_{2\sigma(2)}\dots a_{n\sigma(n)} = \lambda^n\det A
\end{array}\]

#### <u>例</u>
単位行列 $I\in\mathbb{R}^{n\times n}$ に対して $\det (-I) = (-1)^n$

---

#### <u>命題</u>
正方行列 $A$ に対し,
\[\det A^{\operatorname{T}} = \det A\] が成立する.

> 証明
> 全ての $\sigma\in S_n$ に対し, 対応する $\sigma^{-1}\in S_n$ が存在する. これと $\operatorname{sgn}\sigma = \operatorname{sgn}\sigma^{-1}$ を用いると,
\[\begin{array}{rl}\det A &= \displaystyle\sum_{\sigma\in S_n}(\operatorname{sgn}\sigma) a_{1\sigma(1)} a_{2\sigma(2)}\dots a_{n\sigma(n)} \cr
&= \displaystyle\sum_{\sigma\in S_n}(\operatorname{sgn}\sigma^{-1}) a_{1\sigma^{-1}(1)} a_{2\sigma^{-1}(2)} \dots a_{n\sigma^{-1}(n)} \cr
&= \displaystyle\sum_{\sigma\in S_n}(\operatorname{sgn}\sigma) a_{\sigma(1)1} a_{\sigma(2)2} \dots a_{\sigma(n)n}
\end{array}\] となる, ここで, $\sigma^{-1}(i) = j$ であるとき $a_{i\sigma^{-1}(i)} = a_{\sigma(j)j}$ であることを用い, また $a_{\sigma(j)j}$ たちの積の順序を入れ換えている. 
一方で, $A^{\operatorname{T}}$ の $(i,j)$ 成分を $\widetilde{a} _ {ij}$ とおくと, $\widetilde{a} _ {ij} = a_{ji}$ となるため,
\[\begin{array}{rl}\det A^{\operatorname{T}} &= \displaystyle\sum_{\sigma\in S_n}(\operatorname{sgn}\sigma) \widetilde{a} _ {1\sigma(1)} \widetilde{a} _ {2\sigma(2)}\dots \widetilde{a} _ {n\sigma(n)} \cr
&= \displaystyle\sum_{\sigma\in S_n}(\operatorname{sgn}\sigma) a_{\sigma(1)1} a_{\sigma(2)2} \dots a_{\sigma(n)n}
\end{array}\] である. 従って, $\det A = \det A^{\operatorname{T}}$ が得られる.

---

上の結果より, $A$ の行列式を考える際に $A$ の列に関する性質は, $A$ の行対しても同様に成立することがわかる. そこで, 行列 $A$ を列ベクトル $\mathbf{a}_j$ を横に並べたものとみなして行列式を考えてみる:
\[\det A = \det (\mathbf{a}_1, \mathbf{a}_2, \dots, \mathbf{a}_n).\]

#### <u>補題 (多重線形性)</u>

<!--
* $\begin{array}{rl}&\det (\mathbf{a}_1, \dots, \mathbf{a}_j + \widetilde{\mathbf{a}}_j, \dots, \mathbf{a}_n)\cr 
&\qquad = \det (\mathbf{a}_1, \dots, \mathbf{a}_j, \dots, \mathbf{a}_n) + \det (\mathbf{a}_1, \dots, \widetilde{\mathbf{a}}_j, \dots, \mathbf{a}_n)\end{array}$
-->

* $\det (\mathbf{a}_1, \dots, \mathbf{a}_j + \widetilde{\mathbf{a}}_j, \dots, \mathbf{a}_n)$
$\qquad = \det (\mathbf{a}_1, \dots, \mathbf{a}_j, \dots, \mathbf{a}_n) + \det (\mathbf{a}_1, \dots, \widetilde{\mathbf{a}}_j, \dots, \mathbf{a}_n)$,
* $\det (\mathbf{a}_1, \dots, \lambda\mathbf{a}_j, \dots, \mathbf{a}_n) = \lambda \det (\mathbf{a}_1, \dots, \mathbf{a}_j, \dots, \mathbf{a}_n)$

証明略

#### <u>注意</u>
基本行列 $R_{i,j,\lambda}$ に対して, \[\det R_{i,j,\lambda} = \det I + \det (\mathbf{0},\dots,\mathbf{0}, \lambda\mathbf{e}_i,\mathbf{0}, \dots\mathbf{0}) = 1\neq 0\] を確かめることができる. 

#### <u>補題 (交代性)</u>
置換 $\tau\in S_n$ に対し,
\[\det (\mathbf{a} _ {\tau(1)}, \dots, \mathbf{a} _ {\tau(n)}) = (\operatorname{sgn}\tau) \det (\mathbf{a}_1, \dots, \mathbf{a}_n)\]

> 全ての置換は互換の積として表されるため, $i$ 番目と $j$ 番目を入れ替える互換 $\tau$ を考えた際に
\[
    \det (\mathbf{a}_1, \dots, \mathbf{a}_i, \dots, \mathbf{a}_j, \dots, \mathbf{a}_n) = - \det (\mathbf{a}_1, \dots, \mathbf{a}_j, \dots, \mathbf{a}_i, \dots, \mathbf{a}_n)
\] となることを示せば良い. 互換 $\sigma\in S_n$ に対し, $\widetilde{\sigma} = \tau\sigma$ とおくと,
\[\begin{array}{rl}
    &\det (\mathbf{a}_1, \dots, \mathbf{a}_j, \dots, \mathbf{a}_i, \dots, \mathbf{a}_n) \cr
    &\quad= \displaystyle\sum_{\sigma\in S_n}(\operatorname{sgn}\sigma) a_{1\tau\sigma(1)} \dots a_{n\tau\sigma(n)} \cr
    &\quad= (\operatorname{sgn}\tau)\displaystyle\sum_{\widetilde{\sigma}\in S_n}(\operatorname{sgn}\widetilde{\sigma}) a_{1\widetilde{\sigma}(1)} \dots a_{n\widetilde{\sigma}(n)} \cr
    &\quad = - \det (\mathbf{a}_1, \dots, \mathbf{a}_i, \dots, \mathbf{a}_j, \dots, \mathbf{a}_n),
\end{array}\] ここで全ての $\sigma\in S_n$ についての足し合わせは, 全ての $\widetilde{\sigma}\in S_n$ についての足し合わせに等しいことを用いた.

#### <u>注意</u>
* 上の証明中にも言及しているが, ある正方行列 $A$ の第 $i$ 列と第 $j$ 列を入れ換えた行列を $\widetilde{A}$ とすると,
\[\det \widetilde{A} = -\det A\] が成立する.
* また, 上の結果は, 列に対する入れ換えを $k$ 回行った行列 $\widehat{A}$ に対して\[\det\widehat{A} = (-1)^k \det A\] となることを意味している.
* 転置を考えることで, 同様のことが行を入れ換えた場合にも成立することがわかる.
* 基本行列 $P_{i,j}$ に対して, $\det P_{i,j} = -\det I = -1\neq 0$ を確かめることができる

#### <u>系</u>
正方行列 $A$ の 異なる $2$ つの列 (もしくは行) が一致するならば $\det A=0$.

> 証明
> 第 $i$ 列ベクトルと第 $j$ 列ベクトルが等しいならば, それらを入れ換えた行列が $A$ に一致することから $\det A = -\det A$ が得られる.

#### <u>系</u>
正方行列 $A$ の第 $i$ 行 (もしくは列) に第 $j$ 行 (もしくは列) の $\lambda$ 倍を加えて得られる行列 $\widetilde{A}$ に対し, 
\[\det\widetilde{A} = \det A\] が成立する.

> 証明
> 列の場合のみ証明する. 行列 $A = (\mathbf{a}_1, \dots, \mathbf{a}_n)$ に対し, 
\[\widetilde{A} = (\mathbf{a}_1, \dots, \mathbf{a}_i + \lambda\mathbf{a}_j, \dots, \mathbf{a}_n)\] となるので,
\[\begin{array}{rl}
\det \widetilde{A} &= \det (\mathbf{a}_1, \dots, \mathbf{a}_i, \dots, \mathbf{a}_n) + \det (\mathbf{a}_1, \dots, \lambda\mathbf{a}_j, \dots, \mathbf{a}_n) \cr
&= \det A + \lambda \det (\mathbf{a}_1, \dots, \mathbf{a}_j, \dots, \mathbf{a}_j, \dots, \mathbf{a}_n).
\end{array}\] ここで, 第 $2$ 項の行列式は先の結果より $0$ となる.

#### <u>注意</u>
この結果は, 基本行列 $R_{i,j,\lambda}$ に対して
\[\det(R_{i,j,\lambda} A) = \det A,\qquad \det(AR_{i,j,\lambda}) = \det A\] であることを意味している.

#### <u>例</u>
\[A = \begin{pmatrix}1 & 11 & 111 \cr 0 & 1 & 11 \cr 0 & 0 & 1\end{pmatrix}.\] このとき, 
\[\begin{array}{rll}
\det A &= \det \begin{pmatrix}1 & 11 & 111 \cr 0 & 1 & 11 \cr 0 & 0 & 1\end{pmatrix} & \cr
&= \det \begin{pmatrix}1 & 0 & 111 \cr 0 & 1 & 11 \cr 0 & 0 & 1\end{pmatrix} & \text{(第 $2$ 列に第 $1$ 列の $-11$ 倍を加えた)} \cr
&= \det \begin{pmatrix}1 & 0 & 0 \cr 0 & 1 & 11 \cr 0 & 0 & 1\end{pmatrix} & \text{(第 $3$ 列に第 $1$ 列の $-111$ 倍を加えた)} \cr
&= \det \begin{pmatrix}1 & 0 & 0 \cr 0 & 1 & 0 \cr 0 & 0 & 1\end{pmatrix} & \text{(第 $3$ 列に第 $2$ 列の $-11$ 倍を加えた)} \cr
&= \det I = 1.
\end{array}\]


---

**3.1: 逆行列の存在** においてあらかじめ言及した行列式の性質のうち, 次が最後のものである:

#### <u>定理</u>
同じ型の $2$ つの正方行列 $A$, $B$ に対して\[\det (AB) = \det A\det B\] が成立する.

> 証明
> 行列 $B$ の第 $j$ 列ベクトルを $\mathbf{b}_j$ とする. また, 標準規定 $\mathbf{e}_i$ を用いて $\mathbf{b} _ j = \displaystyle\sum_{{i_j}=1}^n b _ {{i_j}j} \mathbf{e} _ {i_j}$ とする. このとき,
\[\det (AB) = \det (A\mathbf{b}_1, \dots, A\mathbf{b}_n).\] 多重線形性より
\[\begin{array}{rl}\det (A\mathbf{b} _ 1, \dots, A\mathbf{b} _ n) &= \displaystyle\sum _ {i_1}^n b_{{i_1}1}\det (A\mathbf{e}_{i_1}, A\mathbf{b} _ 2, \dots, A\mathbf{b} _ n) \cr
& =\dots\cr 
&= \displaystyle\sum_{i_1}^n\dots\sum_{i_n}^n b_{{i_1}1}\dots b_{{i_n}n} \det (A\mathbf{e} _ {i_1}, \dots, A\mathbf{e} _ {i_n}).
\end{array}\] ここで, もしも $i_1,\dots, i_n$ の内に同じものが複数あったならば, $2$ つの列が一致することになるため $\det (A\mathbf{e} _ {i_1}, \dots, A\mathbf{e} _ {i_n}) = 0$ となる. 一方, $i_1, \dots, i_n$ が全て異なる場合, そのような並び方と同一視できる置換 $\sigma\in S_n$ が存在する. まとめると, 上の式の足し合わせの中で $0$ でないものは $\sigma\in S_n$ を用いて表すことができるもののみであり, 具体的には
\[
    \det (A\mathbf{b} _ 1, \dots, A\mathbf{b} _ n) = \displaystyle\sum_{\sigma\in S_n} b _ {\sigma(1)1} \dots b _ {\sigma(n)n} \det (A\mathbf{e} _ {\sigma(1)}, \dots, A\mathbf{e} _ {\sigma(n)})
\] となる. ここで, 交代性より
\[\begin{array}{rl}\det (A\mathbf{e} _ {\sigma(1)}, \dots, A\mathbf{e} _ {\sigma(n)}) &= (\operatorname{sgn}\sigma) \det(A\mathbf{e} _ 1, \dots, A\mathbf{e} _ n)\cr 
&= (\operatorname{sgn}\sigma) \det A\end{array}\] となり, 以上より
\[\det (AB) = \det A \displaystyle\sum_{\sigma\in S_n} (\operatorname{sgn}\sigma) b_{\sigma(1)1} \dots b_{\sigma(n)n} = \det A\det B\] が得られる.

---

ここまでに示した性質を組み合わせることで, 以下が得られるのだった (既に証明済み):

#### <u>定理</u>
$A$ を $n$ 次正方行列とする. このとき, 以下が成立する:
\[
    \det A\neq 0\iff A \text{ は正則}.
\]

#### <u>例</u>
\[A = \begin{pmatrix}1&2\cr 3&4\end{pmatrix},\qquad B = \begin{pmatrix}1&2\cr 2&4\end{pmatrix}.\]
* $\det A = 1\cdot 4 - 2\cdot 3 = -2\neq0$, 従って逆行列が存在する.
    * 実際, $A^{-1} = \begin{pmatrix}-2&1\cr 3/2&-1/2\end{pmatrix}$ であることが確かめられる.
* 一方, $\det B = 1\cdot 4 - 2\cdot 2 = 0$ であり, 従って逆行列を持たない.

---

<a id="section3-4"></a>

## 3.4: 余因子行列とクラメルの公式

行列式を用いると, ある正方行列が正則であるか否かを比較的容易に判定することができる. ここでは, 行列式の計算する際のテクニックや, 行列式を用いて逆行列を計算する方法を紹介する.

#### <u>定義 (余因子)</u>
$n$ 次正方行列 $A$ に対し, その第 $i$ 行と第 $j$ 列を取り除くことで得られる $n-1$ 次正方行列の行列式を第 $(i,j)$ **小行列式** (**minor determinant**) という. また, $(i,j)$ 小行列式に $(-1)^{i+j}$ をかけたものを第 $(i,j)$ **余因子** (**cofactor**) という.

#### <u>例</u>
\[A = \begin{pmatrix}1&2&3\cr 4&5&6\cr 7&8&9\end{pmatrix}.\]
* この行列の第 $(1,1)$ 小行列式は \[\begin{pmatrix}\square & \square& \square \cr \square & 5 & 6\cr \square & 8& 9\end{pmatrix}, \quad \text{つまり} \quad \begin{pmatrix}5&6\cr 8&9\end{pmatrix}\] の行列式であり, 従って第 $(1,1)$ 余因子は
\[(-1)^2 \det\begin{pmatrix}5&6\cr 8&9\end{pmatrix} = 93.\]
* この行列の第 $(2,2)$ 小行列式は \[\begin{pmatrix}1 & \square& 3 \cr \square & \square & \square\cr 7 & \square& 9\end{pmatrix}, \quad \text{つまり} \quad \begin{pmatrix}1&3\cr 7&9\end{pmatrix}\] の行列式であり, 従って第 $(2,2)$ 余因子は
\[(-1)^4 \det\begin{pmatrix}1&3\cr 7&9\end{pmatrix} = 30.\]

特に余因子は, 行列式の定義の計算から一部分のみを切り取ったものになっており, これを用いて行列式の計算を簡略化できることがある. 

以降, 行列 $A$ の第 $(i,j)$ 小行列式を $d_{ij}$ と表記し, 第 $(i,j)$ 余因子を $\widetilde{a} _ {ij}$ と表記することにする.

#### <u>補題</u>
$n$ 次正方行列 $A=(a_{ij})$ の第 $(1,1)$ 余因子を $\widetilde{a}_{11}$ とする, つまり
\[\widetilde{a} _ {11} = (-1)^2 d_{11} = \det \begin{pmatrix}
    a_{22} & \dots & a_{2n} \cr
    \vdots & \ddots & \vdots \cr
    a_{n2} & \dots & a_{nn}    
    \end{pmatrix}.
\] このとき
* $A=\begin{pmatrix}a_{11} & a_{12} & \dots & a_{1n} \cr
0 & a_{22} & \dots & a_{2n} \cr
\vdots & \vdots & \ddots & \vdots \cr
0 & a_{n2} & \dots & a_{nn}\end{pmatrix}$ &emsp;なら &emsp; $\det A = a_{11}\widetilde{a} _ {11}$.
* $A=\begin{pmatrix}a_{11} & 0 & \dots & 0 \cr
a_{21} & a_{22} & \dots & a_{2n} \cr
\vdots & \vdots & \ddots & \vdots \cr
a_{n1} & a_{n2} & \dots & a_{nn}\end{pmatrix}$ &emsp;なら &emsp; $\det A = a_{11}\widetilde{a} _ {11}$.

> 証明:
> 行列 $A$ が上のいずれかの形をしている場合,
\[\det A = \sum_{\sigma\in S_n}(\operatorname{sgn}\sigma) a_{1\sigma(1)} a_{2\sigma(2)} \dots a_{n\sigma(n)}\] の足し合わせの項は, $\sigma(1) = 1$ である場合を除き $0$ となる. いま, $\sigma\in S_n$ であって $\sigma(1)=1$ であるものは, $\widetilde{\sigma}\in S_{n-1}$ と同一視することができる (ただし, $\widetilde{\sigma}$ は $\lbrace2,\dots,n\rbrace$ の置換とみなすことにする). この同一視に基づくと,
\[\det A = a_{11}\sum_{\widetilde{\sigma}\in S_{n-1}}(\operatorname{sgn}\widetilde{\sigma}) a_{2\widetilde{\sigma}(2)} \dots a_{n\widetilde{\sigma}(n)}\] となり, \[\displaystyle\sum_{\widetilde{\sigma}\in S_{n-1}}(\operatorname{sgn}\widetilde{\sigma}) a_{2\widetilde{\sigma}(2)} \dots a_{n\widetilde{\sigma}(n)}\] は \[\det\begin{pmatrix}
    a_{22} & \dots & a_{2n} \cr
    \vdots & \ddots & \vdots \cr
    a_{n2} & \dots & a_{nn}    
    \end{pmatrix} = d_{11} = (-1)^2d_{11},\] つまり $A$ の第 $(1,1)$ 余因子 $\widetilde{a} _ {11}$ と一致する.

#### <u>注意</u>
この結果は, 直感的には『正方行列 $A$ がたとえ巨大なサイズの行列であっても, その要素の多くが $0$ であるならば, よりサイズの小さい行列の行列式の計算に帰着できる (つまり $A$ の行列式の計算はそれほど大変ではない)』ことを意味しており, 非常に有用である.

#### <u>例</u>
\[A = \begin{pmatrix}0 & 3 & 0 & 0 \cr 2 & 4 & 1 & 4 \cr 0 & 2 & 1 & 2 \cr 0 & 6 & 0 & 2\end{pmatrix}.\] このとき,　交代性と先の補題を用いると, 例えば
\[\begin{array}{rll}\det A  &= \det \begin{pmatrix}0 & 3 & 0 & 0 \cr 2 & 4 & 1 & 4 \cr 0 & 2 & 1 & 2 \cr 0 & 6 & 0 & 2\end{pmatrix} & \cr
&= -\det \begin{pmatrix}3 & 0 & 0 & 0 \cr 4 & 2 & 1 & 4 \cr 2 & 0 & 1 & 2 \cr 6 & 0 & 0 & 2\end{pmatrix} & \text{(第 $1$ 列と第 $2$ 列を交換)} \cr
&= -3 \det\begin{pmatrix}2 & 1 & 4 \cr 0 & 1 & 2\cr 0 & 0 & 2\end{pmatrix} &\text{(補題より)}\cr
&= -6 \det\begin{pmatrix}1&2\cr 0&2\end{pmatrix} &\text{(補題より)} \cr
&= -12
\end{array}\] と計算できる.

#### <u>例</u>
\[A = \begin{pmatrix}
2 & -1 & 1 & 2 \cr
1 & 2 & 3 & 2 \cr
2 & 2 & 3 & 3 \cr
3 & -2 & -2 & 1
\end{pmatrix}.\] 基本行列 $R_{i,j,\lambda}$ による基本変形も用いると, 例えば
\[\begin{array}{rll}
\det A &= \det \begin{pmatrix}
2 & -1 & 1 & 2 \cr
1 & 2 & 3 & 2 \cr
2 & 2 & 3 & 3 \cr
3 & -2 & -2 & 1
\end{pmatrix} & \cr
& = -\det \begin{pmatrix}
1 & 2 & 3 & 2 \cr
2 & -1 & 1 & 2 \cr
2 & 2 & 3 & 3 \cr
3 & -2 & -2 & 1
\end{pmatrix} & \text{(第 $1$ 行と第 $2$ 行を交換)} \cr
&= -\det \begin{pmatrix}
1 & 2 & 3 & 2 \cr
0 & -5 & -5 & -2 \cr
0 & -2 & -3 & -1 \cr
0 & -8 & -11 & -5
\end{pmatrix} & \text{(第 $2$, $3$, $4$ 行に第 $1$ 行のスカラー倍を加えた)} \cr
&= -\det \begin{pmatrix}
-5 & -5 & -2 \cr
-2 & -3 & -1 \cr
-8 & -11 & -5
\end{pmatrix} & \text{(補題より)} \cr
&= -\det \begin{pmatrix}
-1 & -3 & -2 \cr
-2 & -5 & -5 \cr
-5 & -11 & -8
\end{pmatrix} & \text{(第 $1$ 行と第 $2$ 行を交換し, 第 $1$ 列と第 $3$ 列を交換)} \cr
&= -\det \begin{pmatrix}
-1 & -3 & -2 \cr
0 & 1 & -1 \cr
0 & 4 & 2
\end{pmatrix} & \text{(第 $3$, $4$ 行に第 $2$ 行のスカラー倍を加えた)} \cr
&= \det\begin{pmatrix}1&-1\cr 4&2\end{pmatrix} = 6
\end{array}\] などと計算できる.

#### <u>定理 (余因子展開)</u>
$n$ 次正方行列 $A=(a_{ij})$ の $(i,j)$ 余因子を $\widetilde{a}_{ij}$ とおく, このとき
* 任意の $j$ に対し, $\det A = a_{1j} \widetilde{a} _ {1j} + \dots + a_{nj} \widetilde{a} _ {nj} = \displaystyle\sum_{i=1}^n a_{ij} \widetilde{a} _ {ij},$
* 任意の $i$ に対し, $\det A = a_{i1} \widetilde{a} _ {i1} + \dots + a_{in} \widetilde{a} _ {in} = \displaystyle\sum_{j=1}^n a_{ij} \widetilde{a} _ {ij}$

が, それぞれ成立する.

> 証明
> 上のみ証明する.
> * $j=1$ のとき:
> 多重線形性より,
\[\begin{array}{rl}\det A &= \det\begin{pmatrix}
a_{11} & a_{12} & \dots & a_{1n} \cr
0 & a_{22} & \dots & a_{2n} \cr
\vdots & \vdots & \ddots & \vdots \cr
0 & a_{n2} & \dots & a_{nn} 
\end{pmatrix} \cr
&\qquad + 
\det\begin{pmatrix}
0 & a_{12} & \dots & a_{1n} \cr
a_{21} & a_{22} & \dots & a_{2n} \cr
\vdots & \vdots & \ddots & \vdots \cr
0 & a_{n2} & \dots & a_{nn} 
\end{pmatrix} \cr
& \qquad \qquad + \dots +
\det\begin{pmatrix}
0 & a_{12} & \dots & a_{1n} \cr
0 & a_{22} & \dots & a_{2n} \cr
\vdots & \vdots & \ddots & \vdots \cr
a_{n1} & a_{n2} & \dots & a_{nn} 
\end{pmatrix}
\end{array}\] となる. 第 $1$ 項は先の補題より $a_{11} d_{11}$, すなわち $a_{11}\widetilde{a} _ {11}$ に等しい. 第 $2$ 項は交代性を用いて
\[\begin{array}{rl}\det\begin{pmatrix}
0 & a_{12} & \dots & a_{1n} \cr
a_{21} & a_{22} & \dots & a_{2n} \cr
\vdots & \vdots & \ddots & \vdots \cr
0 & a_{n2} & \dots & a_{nn} 
\end{pmatrix} &= - \det\begin{pmatrix}
a_{21} & a_{22} & \dots & a_{2n} \cr
0 & a_{12} & \dots & a_{1n} \cr
\vdots & \vdots & \ddots & \vdots \cr
0 & a_{n2} & \dots & a_{nn} 
\end{pmatrix} \cr
&= -a_{21} d_{21} \cr
& = (-1)^3 a_{21} d_{21} = a_{21}\widetilde{a} _ {21}.\end{array}\] 同様に, 第 $i$ 項は $(-1)^{i+1}a_{i1} d_{i1}$, すなわち $a_{i1}\widetilde{a} _ {i1}$ に等しいので欲しい式が得られる. 
> * $j\neq1$ のとき:
> 第 $j$ 列と第 $j-1$ 列を入れ換え, その後に第 $j-1$ 列を第 $j-2$ 列と入れ換え, ... , 最後に第 $2$ 列と第 $1$ 列を入れ換えるという操作により, 第 $j$ 列を第 $1$ 列に移動することができ, またこの行列の行列式は $(-1)^{j-1}\det A$ となる. あとは上と同様に計算すると, 
\[(-1)^{j-1}\det A  = a_{1j}d_{1j} - a_{2j}d_{2j} + \dots + (-1)^n a_{nj}d_{nj}.\] 両辺を $(-1)^{j+1}$ 倍することで,
\[\begin{array}{rl}\det A &= (-1)^{2j}\det A \cr &= (-1)^{j+1} a_{1j} d_{1j} + (-1)^{j+2} a_{2j} d_{2j} + \dots + (-1)^{j+n} a_{nj} d_{nj} \cr &= a_{1j} \widetilde{a} _ {1j} + \dots + a_{nj} \widetilde{a} _ {nj} \end{array}\] となり欲しい式が得られる.

#### <u>注意</u>
実際の行列式の手計算においては, この定理よりもむしろ先の補題の方が使い勝手が良いだろう.

---

#### <u>定義 (余因子行列)</u>
$n$ 次正方行列 $A$ に対し, 第 $(i,j)$ 成分が $A$ の第 $(j,i)$ 余因子 $\widetilde{a}_{ji}$ である $n$ 次正方行列を $A$ の**余因子行列** (**adjugate matrix**) といい, $\operatorname{adj} A$ と表記する.

#### <u>注意</u>
$A$ の余因子行列は $\widetilde{A}$ と表記することも多いが, **このメモでは, 第 $(i,j)$ 成分が $A$ の第 $(i,j)$ 余因子 $\widetilde{a}_{ij}$ である行列を $\widetilde{A}$ と表すことにする**. このとき, $\operatorname{adj} A = \widetilde{A}^{\operatorname{T}}$ である.

#### <u>補題</u>
$n$ 次正方行列 $A$ に対し, 
\[A(\operatorname{adj}A) =(\operatorname{adj}A)A = (\det A)I.\] が成立する.

> 証明
> 行列 $A(\operatorname{adj}A)$ の第 $(i,j)$ 成分は
\[\displaystyle\sum_{k=1}^n a_{ik} \widetilde{a} _ {jk}\] となり, $i=j$ ならば余因子展開より $\det A$ と一致する. もしも $i\neq j$ ならば, これは $A$ の第 $j$ 行を第 $i$ 行で置き換えた行列の余因子展開と一致するが, そのような行列は第 $i$ 行と第 $j$ 行が等しいため行列式が $0$ になる. 従って $A(\operatorname{adj}A) = (\det A)I$ が得られる. $(\operatorname{adj}A)A = (\det A)I$ も同様にして証明される.

この結果と, $\det A\neq0\iff A$ が正則であることを用いると, 以下が得られる:

#### <u>定理 (クラメルの公式)</u>
正則行列 $A$ に対し,
\[A^{-1} = \dfrac{1}{\det A}\operatorname{adj} A\] が成立する.

#### <u>注意</u>
クラメルの公式は, 行列の成分に数値ではなく記号が含まれている場合などに有用である. 一方で, 具体的な数値を成分とする行列に対する逆行列の計算方法として実用的とは言い難い. 