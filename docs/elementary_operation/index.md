<a id="section2"></a>

# 2: 行列の基本変形とその応用

<a id="section2-1"></a>
## 2.1: 導入
例として, 以下の連立$1$次方程式を考える:
\[\left\{\begin{array}{rll}
    x+2y &= 20, &\qquad (1)\\
    3x+4y &= 46. &\qquad (2)
\end{array}\right.\] これは行列を用いて以下のように書き直すことができる:
\[
    \begin{pmatrix}1&2\cr 3&4\end{pmatrix}\begin{pmatrix}x\cr y\end{pmatrix} = \begin{pmatrix}20\cr 46\end{pmatrix}.
\] ここで, 左辺にある行列 $A = \begin{pmatrix}1&2\cr 3&4\end{pmatrix}$ の逆行列は 
\[
    A^{-1}=\begin{pmatrix}-2&1\cr 3/2&-1/2\end{pmatrix}
\] であることを用いると, 
\[
    \begin{pmatrix}x\cr y\end{pmatrix} = A^{-1}\begin{pmatrix}20\cr 46\end{pmatrix} = \begin{pmatrix}6\cr 7\end{pmatrix}
\] と計算することで, 連立$1$次方程式を解くことができる. すなわち, 連立 $1$ 次方程式を解くことと逆行列を求めることとを同一視することができる.

一方で, この連立$1$次方程式は, 例えば $(2)$ 式から $(1)$ 式を $2$ 倍したものを引くことで $(1)$ 式から $y$ の項を消去する, といった操作を用いて解くこともできる. ここで例に挙げた操作を実際に適用すると,
\[\left\{\begin{array}{rll}
    x+2y &= 20, &\qquad (1)\\
    x &= 6. &\qquad (2)'
\end{array}\right.\] と変形することができるが, これは『行列 $A$ と右辺の列ベクトル の第 $2$ 行から第 $1$ 行の $2$ 倍を引く』という操作と同値である:
\[
    \begin{pmatrix}1&2\cr 1&0\end{pmatrix}\begin{pmatrix}x\cr y\end{pmatrix} = \begin{pmatrix}20\cr 6\end{pmatrix}.
\] 連立 $1$ 次方程式を解く際に用いられるこのような操作は, 行列に対しても, その性質を保ちつつ簡単な形に変形する操作としてしばしば用いられるものである. 

この章では, 行列の**基本変形**と呼ばれる特定の変形, 及びそこから得られる行列の性質について解説し, またそれらの応用として連立 $1$ 次方程式を解く, すなわち逆行列を計算する手順について紹介する.

<a id="section2-2"></a>
## 2.2: 基本変形
##### <u>定義</u> (基本変形)
行列に対する基本的な操作として, 以下の $3$ つを**行基本変形** (**elementary row operations**) という:
* 第 $i$ 行と第 $j$ 行を入れ替える.
* 第 $i$ 行に $0$ でない数を掛ける.
* 第 $i$ 行に第 $j$ 行のスカラー倍を加える.

また, 以下の $3$ つを**列基本変形** (**elementary column operations**) という:
* 第 $i$ 列と第 $j$ 列を入れ替える.
* 第 $i$ 列に $0$ でない数を掛ける.
* 第 $i$ 列に第 $j$ 列のスカラー倍を加える.

ただし, $i\neq j$ とする.

---

行列に対する基本変形は, 以下に挙げる行列を掛けることにより表現することができる.
##### <u>定義</u> (基本行列)
以下の $3$ つの正方行列を**基本行列** (**elementary matrix**) という:
* $P_{i,j}$: 単位行列 $I$ の 第 $i$ 行と第 $j$ 行を入れ替えたもの.
* $Q_{i,\lambda}$: 単位行列 $I$ の $(i,i)$ 成分を $\lambda\neq0$ に置き換えたもの.
* $R_{i,j,\lambda}$: 単位行列 $I$ の $(i,j)$ 成分を $\lambda$ に置き換えたもの.

\[
    P_{i,j} = \begin{pmatrix}1&&&&&&\cr &\ddots&&&&&\cr &&0&&1&&\cr&&&\ddots&&&\cr&&1&&0&&\cr&&&&&\ddots&\cr&&&&&&1\end{pmatrix},
\]
\[
    Q_{i,\lambda} = \begin{pmatrix}1&&&&&&\cr &\ddots&&&&&\cr &&1&&&&\cr&&&\lambda&&&\cr&&&&1&&\cr&&&&&\ddots&\cr&&&&&&1\end{pmatrix},
\]
\[
    R_{i,j,\lambda} = \begin{pmatrix}1&&&&&&\cr &\ddots&&&&&\cr &&1&&\lambda&&\cr&&&\ddots&&&\cr&&&&1&&\cr&&&&&\ddots&\cr&&&&&&1\end{pmatrix}.
\]

* 行列 $A$ に対する行基本変形は, $A$ に基本行列を**左から**掛けることで表現できる.
* 行列 $A$ に対する列基本変形は, $A$ に基本行列を**右から**掛けることで表現できる.

##### <u>例</u>
\[
    A = \begin{pmatrix}1&2\cr 3&4\end{pmatrix}.
\]
* 行列 $A$ の第 $2$ 行に第 $1$ 行の $-2$ 倍を加える行基本変形は,
\[
    R_{2,1,-2}A = \begin{pmatrix}1&0\cr -2&1\end{pmatrix}A = \begin{pmatrix}1&2\cr 1&0\end{pmatrix}
\] により表現することができる.

##### <u>性質</u>
基本変形行列は全て正則であり,
\[
    P_{ij}^{-1}=P_{ij},\quad Q_{i,\lambda}^{-1} = Q_{i,\lambda^{-1}},\quad R_{i,j,\lambda}^{-1} = R_{i,j,\lambda^{-1}}
\] となる. 実際, 行 (および列) 基本変形を考えると,
* $P_{ij}P_{ij}A = A$, &emsp; $AP_{ij}P_{ij}=A$
* $Q_{i,\lambda^{-1}}Q_{i,\lambda}A = A$, &emsp; $AQ_{i,\lambda}Q_{i,\lambda^{-1}}=A$
* $R_{i,j,\lambda^{-1}}R_{i,j,\lambda}A = A$, &emsp; $AR_{i,j,\lambda}R_{i,j,\lambda^{-1}} = A$

となることは容易に想像できるし, 計算して確かめることもできる.

