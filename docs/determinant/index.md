<a id="section3"></a>

# 3: 行列式

<a id="section3-1"></a>
## 3.1: 逆行列の存在

ここでは, 行列 $A$ として常に正方行列を考えることにする. この行列 $A$ の逆行列について, ここまでの内容を以下にいくつか再掲する:

##### <u>定義</u> (正則行列と逆行列)
正方行列 $A$ に対して, 同じ型の正方行列 $B$ であって 
\[
    AB = BA = I
\] を満たすものが存在するならば, $B$ を $A$ の**逆行列** (**inverse matrix**) といい, $A^{-1}$ と表記する. 正方行列 $A$ の逆行列が存在するならば, $A$ を**正則行列** (**regular matrix**) もしくは**可逆行列** (**invertible matrix**) という.

##### <u>命題</u> 
逆行列について以下が成立する:
* $A^{-1}$, $B^{-1}$ が存在するならば $(AB)^{-1} = B^{-1}A^{-1}$  
* $A^{-1}$ が存在するならば, $(A^{-1})^{-1} = A$.
* $A^{-1}$ は存在するならばただ$1$つに定まる.

##### <u>注意</u> 
* 正則行列たちの積は正則行列になる.
* 正方行列 $A$ に対し $AB=I$ を満たす $B$ が存在すれば, そのような $B$ は $BA=I$ も満たす (つまり $B=A^{-1}$ となる).
* 同様に, $BA=I$ なる $B$ は, $B=A^{-1}$ となる.

##### <u>定理</u>
$A$ を $n$ 次正方行列とする. このとき, 以下が成立する:
\[
    \operatorname{rank}A = n \iff A \text{ は正則}.
\]

##### <u>系</u>
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
* 実正方行列の行列式は実数である.
* $n$ 次正方行列
\[
    F(r) =\begin{pmatrix}I_r&O\cr O&O\end{pmatrix} = \begin{pmatrix}1\cr&1\cr&&\ddots\cr&&&1\cr&&&&0\cr&&&&&\ddots\end{pmatrix}   
\] に対して, 
\[
    \det F(r) = \cases{\begin{array}{rl}
    1&\text{if } r = n,\\
    0&\text{if } r < n
    \end{array}}
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
##### <u>定理</u>
$A$ を $n$ 次正方行列とする. このとき, 以下が成立する:
\[
    \det A\neq 0\iff \operatorname{rank}A = n \iff A \text{ は正則}.
\]
> 証明
正方行列 $A$ は, 基本行列の積により表される行列 $P$, $Q$ を用いて $A = PF(r)Q$ と表されるのだった. これと行列式の性質より, 
\[
    \det A\neq 0 \iff \det F(r)\neq 0 \iff \operatorname{rank} A=n
\] が得られる.

すなわち, 正方行列 $A$ の逆行列が存在するか否か判定するには, $A$ の行列式を計算すれば良いことになる.

---

<a id="section3-2"></a>
## 3.2: 行列式の定義

ここでは, 行列式の定義を述べる. 行列式を上で述べた性質が満たされるよう構成するために, (唐突に感じるかもしれないが) まずは**置換**という概念を導入する:

##### <u>定義 (置換)</u>
$n$ 個の元からなる集合を考える (ここでは, $\{1, 2, \dots, n\}$ のみを考えることにする). これを並び替える操作を**置換** (**permutation**) という. いま, $\{1, 2, \dots n\} を \{\sigma(1), \sigma(2), \dots, \sigma(n)\}$ に並び替える置換を
\[
    \sigma = \begin{bmatrix}1& 2& \dots & n\cr \sigma(1) & \sigma(2) & \dots & \sigma(n)\end{bmatrix}
\]
と表記する. $n$ 個に対する置換全体を $S_n$ と表記し, $\sigma$ が $n$ 個に対する置換であるとき $\sigma\in S_n$ と表記する.

##### <u>例</u>
$\{1,2,3\}$ に対し, $1$ 番目と $2$ 番目を入れ替えると $\{2,1,3\}$ という順序になるが, この並び替えは
\[
    \begin{bmatrix}1&2&3\cr 2&1&3\end{bmatrix}\in S_3
\] と表記される.

##### <u>例</u>
$\{1,2,3\}$ に対し, $1$ 番目を $2$ 番目に, $2$ 番目を $3$ 番目に, $3$ 番目を $1$ 番目に取り替えると $\{2,3,1\}$ という順序になるが, この並び替えは 
\[
    \begin{bmatrix}1&2&3\cr 2&3&1\end{bmatrix} \in S_3
\] と表記される.

##### <u>例</u>
$\{1,2,3\}$ の置換 $S_n$ は以下の $6$ つからなる:
\[
    \begin{bmatrix}1& 2& 3\cr 1 & 2 & 3\end{bmatrix},\quad \begin{bmatrix}1& 2& 3\cr 2 & 1 & 3\end{bmatrix},\quad \begin{bmatrix}1& 2& 3\cr 1 & 3 & 2\end{bmatrix},
\] \[
    \begin{bmatrix}1& 2& 3\cr 3 & 2 & 1\end{bmatrix},\quad \begin{bmatrix}1& 2& 3\cr 2 & 3 & 1\end{bmatrix},\quad \begin{bmatrix}1& 2& 3\cr 3 & 1 & 2\end{bmatrix}.
\]

##### <u>定義 (置換の積)</u>
$2$ つの置換 $\sigma$, $\tau$ を合成したもの (つまり $\sigma$ により並び替えたものを $\tau$ によりさらに並び替えたもの) を置換の**積**といい, $\tau\sigma$ と表記する.

##### <u>例</u>
\[
    \sigma = \begin{bmatrix}1& 2& 3\cr 2 & 1 & 3\end{bmatrix}, \quad \tau = \begin{bmatrix}1& 2& 3\cr 1 & 3 & 2\end{bmatrix}.
\]
* $\{1,2,3\}$ を $\sigma$ により並び替えると $\{2,1,3\}$ となる.
* これをさらに $\tau$ により並び替える: つまり $\{2,1,3\}$ の $2$ 番目と $3$ 番目を入れ替えると $\{2,3,1\}$ となる.
* つまり $\sigma$ と $\tau$ の合成は $\{1,2,3\}$ を $\{2,3,1\}$ に並び替える置換になる.
* 従って $\tau\sigma = \begin{bmatrix}1&2&3\cr 2&3&1\end{bmatrix}$ となる.

##### <u>注意</u>
* 置換の積は右側から先に適用する. 先の例では, $\sigma$ により並び替えたものを $\tau$ で並び替える操作は $\tau\sigma$ と表記される.
* 一般には $\tau\sigma \neq \sigma\tau$ に注意. 上の例では, $\sigma\tau$ は $\{1,2,3\}$ を $\{3,1,2\}$ に並び替える操作であり,
\[
    \sigma\tau = \begin{bmatrix}1&2&3\cr 3&1&2\end{bmatrix} \neq \tau\sigma.
\] である.

##### <u>定義 (恒等置換と逆置換)</u>
* $\{1,2,\dots, n\}$ を並び替えない操作を**恒等置換**といい, 
\[
    1_n = \begin{bmatrix}1&2&\dots &n\cr 1&2&\dots & n\end{bmatrix}
\] と表記する.
* 置換 $\sigma$ に対し, $\sigma\tau = \tau\sigma = 1_n$ を満たす置換 $\tau$ を $\sigma$ の**逆置換** といい, $\tau=\sigma^{-1}$ と表記する.

##### <u>定義 (互換)</u>
置換であって, $2$ つの入れ替えとして表現されるものを**互換** (**transposition**) という.

##### <u>例</u>
置換 $\begin{bmatrix}1&2&3\cr 2&1&3\end{bmatrix}$ は, $\{1,2,3\}$ の $1$ 番目と $2$ 番目を入れ替えたものとみなせるので互換である.

##### <u>例</u>
置換 $\begin{bmatrix}1&2&3\cr 2&3&1\end{bmatrix}$ は, $\{1,2,3\}$ の $2$ つのみ入れ替えたものとして表現できないため互換ではない.


##### <u>命題</u>
全ての置換は互換の積として表される.
証明略

##### <u>定義 (偶置換と奇置換)</u>
* 置換 $\sigma$ が恒等置換であるか, 偶数個の互換の積として表現されるならば, $\sigma$ を**偶置換** (**even permutation**)という.
* 置換 $\sigma$ が奇数個の互換の積として表現されるならば, $\sigma$ を**奇置換** (**odd permutation**)という.

##### <u>定義 (置換の符号)</u>
置換 $\sigma$ に対して,
\[
    \operatorname{sgn}\sigma = \cases{\begin{array}{rl}
    1&\text{if }\sigma \text{ が偶置換},\\
    -1&\text{if }\sigma \text{ が奇置換}
    \end{array}}
\] を置換 $\sigma$ の**符号**という.

##### <u>命題</u>
* $\operatorname{sgn} \sigma^{-1} = \operatorname{sgn}\sigma$.
* $\operatorname{sgn}(\tau\sigma) = (\operatorname{sgn}\sigma)(\operatorname{sgn}\tau)$.

証明略

---

置換の符号を用いることで, 正方行列に対する行列式の定義を記述することができる.

##### <u>定義 (行列式)</u>
$n$ 次正方行列 $A=(a_{ij})$ に対して,
\[
    \sum_{\sigma\in S_n}(\operatorname{sgn}\sigma) a_{1\sigma(1)} a_{2\sigma(2)}\dots a_{n\sigma(n)}
\] を $A$ の行列式といい, $\det A$ (もしくは $|A|$) と表記する.

##### <u>例</u>
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
        \det A &= \operatorname{sgn}\sigma_1 a_{1\sigma_1(1)} a_{2\sigma_1(2)} + \operatorname{sgn}\sigma_2 a_{1\sigma_2(1)} a_{2\sigma_2(2)} \\
        &= a_{11}a_{22} - a_{12}a_{21}\\
        &= ad-bc
    \end{array}
\] となる. 計算中に行列 $A$ の $i\sigma_k(i)$ 成分を用いているが, $i$ と $\sigma_k(i)$ のペアは置換 $\sigma_k$ を行列とみなしたときの第 $i$ 列に一致することに注意.

##### <u>例</u>
$3$ 次正方行列 $A = (a_{ij}) = \begin{pmatrix}a&b&c\cr d&e&f\cr g&h&i\end{pmatrix}$ を考える. いま $S_3$ は先の例に挙げた 
\[
    \begin{bmatrix}1& 2& 3\cr 1 & 2 & 3\end{bmatrix},\quad \begin{bmatrix}1& 2& 3\cr 2 & 1 & 3\end{bmatrix},\quad \begin{bmatrix}1& 2& 3\cr 1 & 3 & 2\end{bmatrix},
\] \[
    \begin{bmatrix}1& 2& 3\cr 3 & 2 & 1\end{bmatrix},\quad \begin{bmatrix}1& 2& 3\cr 2 & 3 & 1\end{bmatrix},\quad \begin{bmatrix}1& 2& 3\cr 3 & 1 & 2\end{bmatrix}.
\] の$6$ つであり, それらを用いて計算すると
\[
    \begin{array}{rl}
        \det A &= a_{11} a_{22} a_{33} - a_{12} a_{21} a_{33} - a_{11} a_{23} a_{32} \\
        &\qquad - a_{13} a_{22} a_{31} + a_{12} a_{23} a_{31} + a_{13} a_{21} a_{32}  \\
        &= aei + bfg + cdh - ceg - bdi - afh
    \end{array}
\] となる.

##### <u>注意</u>
$4$ 次以上の正方行列に対しても上と同様にして行列式を計算することは可能だが, 実用上は (いくつかの特殊な場合を除いて) $2$ 次と $3$ 次の場合の行列式を公式として暗記すれば十分だろう:
\[
    A = \begin{pmatrix}a&b\cr c&d\end{pmatrix},\quad \det A = ad-bc.
\] \[
    A = \begin{pmatrix}a&b&c\cr d&e&f\cr g&h&i\end{pmatrix},\quad \det A =  aei + bfg + cdh - ceg - bdi - afh.
\]
