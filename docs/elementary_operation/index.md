<a id="section2"></a>

# 2: 行列の基本変形とその応用

<a id="section2-1"></a>

## 2.1: 導入
例として, 以下の連立$1$次方程式を考える:

\[\left\lbrace
\begin{array}{rll}
    x+2y &= 20, &(1) \cr
    3x+4y &= 46. &(2)
\end{array}
\right.\] これは行列を用いると以下のように書き直すことができる:
\[
    \begin{pmatrix}1&2\cr 3&4\end{pmatrix}\begin{pmatrix}x\cr y\end{pmatrix} = \begin{pmatrix}20\cr 46\end{pmatrix}.
\] このように, 連立 $1$ 次方程式を, 行列と列ベクトルの行列積により表現することは, 行列の基本的な応用の $1$ つである (以降, 上のようにして連立 $1$ 次方程式と同一視することができる $A\mathbf{x} = \mathbf{b}$ という形の方程式のことも連立 $1$ 次方程式と呼ぶことがある).

ここで, 左辺にある行列 $A = \begin{pmatrix}1&2\cr 3&4\end{pmatrix}$ の逆行列が
\[
    A^{-1}=\begin{pmatrix}-2&1\cr 3/2&-1/2\end{pmatrix}
\] であることを用いると, 
\[
    \begin{pmatrix}x\cr y\end{pmatrix} = A^{-1}\begin{pmatrix}20\cr 46\end{pmatrix} = \begin{pmatrix}6\cr 7\end{pmatrix}
\] と計算することで, 連立$1$次方程式を解くことができる. すなわち, 連立 $1$ 次方程式を解くことと逆行列を求めることとを同一視することができる.

一方で, この連立$1$次方程式は, 例えば $(2)$ 式から $(1)$ 式を $2$ 倍したものを引くことで $(1)$ 式から $y$ の項を消去する, といった操作を用いて解くこともできる. ここで例に挙げた操作を実際に適用すると,
\[\left\lbrace
    \begin{array}{rll}
    x+2y &= 20, &(1)\cr
    x &= 6. &(2)^\prime
    \end{array}\right.
\] と変形することができるが, これは『行列 $A$ と右辺の列ベクトル の第 $2$ 行から第 $1$ 行の $2$ 倍を引く』という操作と同値である:
\[
    \begin{pmatrix}1&2\cr 1&0\end{pmatrix}\begin{pmatrix}x\cr y\end{pmatrix} = \begin{pmatrix}20\cr 6\end{pmatrix}.
\] 連立 $1$ 次方程式を解く際に用いられるこのような操作は, 行列に対しても, その性質を保ちつつ簡単な形に変形する操作としてしばしば用いられるものである. 

この章では, 行列の**基本変形**と呼ばれる特定の変形, 及びそこから得られる行列の性質について解説し, またそれらの応用として連立 $1$ 次方程式を解く, すなわち逆行列を計算する手順について紹介する.

<a id="section2-2"></a>

## 2.2: 基本変形

#### <u>定義</u> (基本変形)
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
#### <u>定義</u> (基本行列)
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

#### <u>例</u>
\[
    A = \begin{pmatrix}1&2\cr 3&4\end{pmatrix}.
\]
* 行列 $A$ の第 $2$ 行に第 $1$ 行の $-2$ 倍を加える行基本変形は,
\[
    R_{2,1,-2}A = \begin{pmatrix}1&0\cr -2&1\end{pmatrix}A = \begin{pmatrix}1&2\cr 1&0\end{pmatrix}
\] と表現することができる.

#### <u>性質</u>
基本行列は全て正則であり,
\[
    P_{i,j}^{-1}=P_{i,j},\quad Q_{i,\lambda}^{-1} = Q_{i,\lambda^{-1}},\quad R_{i,j,\lambda}^{-1} = R_{i,j,\lambda^{-1}}
\] となる, すなわち, 基本行列の逆行列は基本変形行列で表現できる. 実際, 行 (および列) 基本変形を考えると,
* $P_{i,j}P_{i,j}A = A$, &emsp; $AP_{i,j}P_{i,j}=A$
* $Q_{i,\lambda^{-1}}Q_{i,\lambda}A = A$, &emsp; $AQ_{i,\lambda}Q_{i,\lambda^{-1}}=A$
* $R_{i,j,\lambda^{-1}}R_{i,j,\lambda}A = A$, &emsp; $AR_{i,j,\lambda}R_{i,j,\lambda^{-1}} = A$

となることは容易に想像できるし, 計算して確かめることもできる.

#### <u>注意</u>
我々は基本行列がどのような形であるかに興味があるというよりも, 単に行列に対してどのような基本変形を行なったかを簡単に記述するために用いたい. 例えば, 行列 $A$ に対して『第 $2$ 行に第 $1$ 行の $-2$ 倍を加える』という基本変形は, 『$A$ を $R_{2,1,-2}A$ に置き換える』ということと同じことを意味しているため, 記述を簡単にしたい場合に後者の表現を用いることがある. 

---

<a id="section2-3"></a>

## 2.3: 階数と正則性

基本行列を用いて, 実数の因数分解に相当するものを考えてみる: つまり, 与えられた行列 $A$ を, 基本行列と簡単な形をした行列たちの積によって表現する. 
* 例えば, $6552 = 2^3\times 3^2\times 7\times 13$.
* 行列の場合, $A = (\text{基本行列たちの積})\widetilde{A}(\text{基本行列たちの積})$ と表現できないかを考える.

基本変形の性質を用いることで, 以下が成立する:

#### <u>補題 (掃き出し)</u>
行列 $A=(a_{ij})$ の $(p,q)$ 成分が $0$ でないなら, 基本変形により第 $p$ 行 及び第 $q$ 列の成分を, $(p,q)$ 成分のみ $1$, それ以外を全て $0$ にすることができる (これを第 $p$ 行および第 $q$ 列を**掃き出す**という).

> 証明: 
> * まず, 第 $p$ 行を $a_{pq}$ で割ることで, $(p,q)$ 成分を $1$ にすることができる. 
> * 次に, $p$ 以外の全ての $i$ に対し, 第 $p$ 行の $(i,q)$ 成分倍を引くことで, 第 $q$ 列は $(p,q)$ 成分を除いて全て $0$ になる.
> * 最後に, 第 $q$ 列に対して同様の操作を行うことで, 第 $q$ 列は $(p,q)$ 成分を除いて全て $0$ になる. 

#### <u>例</u>
\[
    A = \begin{pmatrix}2&4&6\cr2&3&4\cr1&3&5\end{pmatrix}.
\]
* この行列の 第 $1$ 行, 第 $1$ 列について, $(1,1)$ 成分のみ $1$, それ以外は $0$ とする基本変形を求めてみよう.
* まず, 第 $1$ 行を $a_{11}=2$ で割ることで $(1,1)$ 成分を $1$ にする:
\[
    Q_{1,1/2}A = \begin{pmatrix}1&2&3\cr 2&3&4\cr1&3&5\end{pmatrix}.
\]
* 次に, 第 $2$ 行に第 $1$ 行の $-2$ 倍, 第 $3$ 行に第 $1$ 行の $-1$ 倍を加える:
\[
    R_{3,1,-1}R_{2,1,-2}Q_{1,1/2}A = \begin{pmatrix}1&2&3\cr0&-1&-2\cr0&1&2\end{pmatrix}.
\]
* 最後に, 第 $2$ 列に第 $1$ 列の $-2$ 倍, 第 $3$ 列に第 $1$ 列の $-3$ 倍を加える:
\[
    R_{3,2,-3}R_{1,2,-2}Q_{2,1/2}AR_{2,1,-2}R_{3,1,-3} = \begin{pmatrix}1&0&0\cr0&-1&-2\cr0&1&2\end{pmatrix}.
\]

この結果を繰り返し適用することで, 第 $2$ 行, 第 $2$ 列以降も同様に変形することができる.

#### <u>注意</u>
掃き出しによる結果は, どのような順序で基本変形を行うかに依存しない. しかしながら, 上で計算しているように, 第 $(i,j)$ 成分に注目して
1. 第 $(i,j)$ 成分を $1$ にする.
2. 第 $i$ 行の定数倍を加えることで, 他の行の第 $j$ 列を全て $0$ にする.
3. 第 $j$ 列の定数倍を加えることで, 他の列の第 $i$ 行を全て $0$ にする.

という手順で計算することを推奨する.

#### <u>定理 (階数)</u>
任意の行列 $m\times n$ 型行列 $A$ は, 基本行列の積により表される行列 $P$, $Q$, および $m\times n$ 型行列
\[
    F(r) =\begin{pmatrix}I_r&O\cr O&O\end{pmatrix} = \begin{pmatrix}1\cr&1\cr&&\ddots\cr&&&1\cr&&&&0\cr&&&&&\ddots\end{pmatrix}   
\] を用いて, $A=PF(r)Q$ と表される, ここで $I_r$ は $r\times r$ 型の単位行列である (この $r$ を行列 $A$ の**階数**(**rank**)という).

> 証明:
> * $A=O$ ならば, $A=F(0)$ なので成立.
> * $A\neq O$ ならば, $0$ でない成分があるため, 基本変形 (行及び列の入れ替え) によりその成分を 第 $1$ 行, 第 $1$ 列 に移動させる.
> * 上の補題より, 第 $1$ 行及び第 $1$ 列を, $(1,1)$ 成分のみ $1$ に, それ以外を $0$ にするような基本変形が存在する:
\[
    P^\prime AQ^\prime = \left(\begin{array}{cc}1&O\cr O&A^\prime\end{array}\right)
\] 
> * $A^\prime=O$ なら $P^\prime AQ^\prime = F(1)$, そうでなければ $0$ でない成分を第 $2$ 行, 第 $2$ 列に移動させ, 同様の操作により
\[
    P^{\prime\prime} A Q^{\prime\prime} = \left(\begin{array}{cc}I_2&O\cr O&A^{\prime\prime}\end{array}\right)
\] が得られる.
> * この手順を繰り返すことにより, 最終的に
\[
    \widetilde{P} A \widetilde{Q} = F(r)
\] という形が得られる, ただし $\widetilde{P}$, $\widetilde{Q}$ は基本行列の積で表される.
> * 基本行列は正則かつ逆行列も基本行列で表されるので, $P=\widetilde{P}^{-1}$, $Q=\widetilde{Q}^{-1}$ とすれば, $P$, $Q$ は基本行列の積で表され,
\[
    A = PF(r)Q
\] が成立する.

#### <u>注意</u>
* この $r$ を行列 $A$ の**階数**(**rank**)といい, $\operatorname{rank} A = r$ と表記する. 
* 行列 $F(r)$ を, 行列 $A$ の標準形と呼ぶことがある.
* 本当は, このような $r$ が一意に定まることも示す必要があるが, ここでは証明は省略する.

#### <u>例</u>
(ここでのみ) 行及び列基本変形を $\longrightarrow$ により表すことにする. 例として, 
\[\begin{pmatrix}0&2&4&6\cr 1&2&3&4\cr -2&-1&0&1\end{pmatrix}\] という行列の階数を計算してみる:
\[\begin{array}{rll}\begin{pmatrix}0&2&4&6\cr 1&2&3&4\cr -2&-1&0&1\end{pmatrix} &\longrightarrow \begin{pmatrix}1&2&3&4\cr 0&2&4&6\cr -2&-1&0&1\end{pmatrix}\quad&\text{($1$ 行目と $2$ 行目を交換)} \cr
&\longrightarrow \begin{pmatrix}1&2&3&4\cr 0&2&4&6\cr 0&3&6&9\end{pmatrix} &\text{($1$ 行目の $2$ 倍を $3$ 行目に加えた)} \cr
&\longrightarrow \begin{pmatrix}1&0&0&0\cr 0&2&4&6\cr 0&3&6&9\end{pmatrix} &\text{($1$ 列目のスカラー倍を $2$, $3$, $4$ 列目に加えた)} \cr
&\longrightarrow \begin{pmatrix}1&0&0&0\cr 0&1&2&3\cr 0&1&2&3\end{pmatrix} &\text{($2$ 行目と $3$ 行目をスカラー倍)} \cr
&\longrightarrow \begin{pmatrix}1&0&0&0\cr 0&1&2&3\cr 0&0&0&0\end{pmatrix} &\text{($3$ 行目に $2$ 行目の $-1$ 倍を加えた)} \cr
&\longrightarrow \begin{pmatrix}1&0&0&0\cr 0&1&0&0\cr 0&0&0&0\end{pmatrix} &\text{($2$ 列目のスカラー倍を $3$, $4$ 列目に加えた)}.
\end{array}\] このことから $\operatorname{rank}A = 2$ であることがわかる.

#### <u>注意</u>
階数を求める上の計算も, やはりどのような順序で基本変形を行うかに依存しない. しかしながら, $i = 1, 2, \dots, n$ の順に, 
1. 第 $(i,i)$ 成分を $1$ にする.
2. 第 $i$ 行の定数倍を加えることで, 他の行の第 $i$ 列を全て $0$ にする.
3. 第 $i$ 列の定数倍を加えることで, 他の列の第 $i$ 行を全て $0$ にする.

という手順で計算することを推奨する.

---

実は正方行列の階数と正則性 (すなわち逆行列の存在) とは密接に関連している.

#### <u>定理</u>
$A$ を $n$ 次正方行列とする. このとき, 以下が成立する:
\[
    \operatorname{rank}A = n \iff A \text{ は正則}.
\]
> 証明
> * 上の定理より, $A=PF(r)Q$ と表すことができるのであった, ただし $P$, $Q$ は基本行列の積で表される行列であり, $r=\operatorname{rank}A$に対し $F(r)\in\mathbb{R}^{n\times n}$ は
\[
    F(r) = \begin{pmatrix}I_r&O\cr O&O\end{pmatrix}
\] という形の行列である. $P$, $Q$ は正則なので,
\[A \text{ が正則} \iff F(r)\text{ が正則}\] が得られる. 従って, \[\operatorname{rank} A=n \iff F(r) \text{ が正則}\] を示せば良い:
> * $(\implies)$ &emsp; $\operatorname{rank}A=n$ ならば, $F(r)$ は $n$ 次の単位行列となるため特に正則である. 
> * $(\impliedby)$ &emsp; 対偶を示す: &emsp; $r<n$ のとき, $F(r)$ が正則でないことを示せば良い. 
>> (背理法) &emsp; $F(r)$ が正則であると仮定する, このとき $F(r)^{-1}$ が存在し $F(r)F(r)^{-1}=I$ となる. いま, $r < n$ なので, $F(r)$ の 第 $r+1$ 行から第 $n$ 行の成分は全て $0$ である. 
従って, $F(r)F(r)^{-1}$ の第 $r+1$ 行から第 $n$ 行の成分も全て $0$ となるため, $F(r)F(r)^{-1}\neq I$ となり矛盾する.
>
> 以上より \[\operatorname{rank} A=n \iff F(r) \text{ が正則}\] が証明される.

#### <u>注意</u>
* $n$ 次正方行列 $A$ について, $\operatorname{rank}A=n$ のとき, $A$ は**フルランク** (**full rank**) であるということがある:
\[A \text{ がフルランク}\iff A \text{ が正則}\]
* 正方行列 $A$ がフルランクならば, 対応する標準形 $F(r)$ は単位行列になる.

この定理より, 以下の結論が直ちに得られる:

#### <u>系</u>
$A$ を $n$ 次正方行列とする. このとき, 以下が成立する:
\[
    A\text{ が正則}\iff A\text{ は基本行列の積で表現される}.
\]

これは以下のように言い換えることもできる:

#### <u>系</u>
$A$ を $n$ 次正方行列とする. このとき, 以下が成立する:
\[
    A\text{ が正則} \iff A \text{ は行 (もしくは列) 基本変形だけで単位行列に変形できる}
\]

#### <u>注意</u>
以降は, 特に行基本変形のみを考えることにする.

#### <u>例</u>
\[A = \begin{pmatrix}1&2\cr 3&4\end{pmatrix},\quad B= \begin{pmatrix}-2&1\cr 3/2&-1/2\end{pmatrix}\] とすると, $A^{-1}=B$ を確かめることができるので $A$ は正則である. この行列 $A$ が行基本変形のみで単位行列に変形できることを確かめてみる. 以降, 行基本変形を矢印 ($\longrightarrow$) で表すことにする:
\[\begin{array}{rll}A &= \begin{pmatrix}1&2\cr 3&4\end{pmatrix}\cr
&\longrightarrow\begin{pmatrix}1&2\cr 0&-2\end{pmatrix} \quad &\text{(第 $2$ 行に第 $1$ 行の $-3$ 倍を加えた)}\cr
&\longrightarrow\begin{pmatrix}1&0\cr 0&-2\end{pmatrix} \quad &\text{(第 $1$ 行に第 $2$ 行の $1$ 倍を加えた)}\cr
&\longrightarrow\begin{pmatrix}1&0\cr 0&1\end{pmatrix} \quad &\text{(第 $2$ 行を $-1/2$ 倍した)}
\end{array}\]

これは $Q_{2,-1/2}R_{1,2,1}R_{2,1,-3}A = I$ と同じことを意味している.

---

一方で, 正則でない行列に対して行基本変形を行なっても単位行列にすることはできない.

#### <u>例</u>
\[C = \begin{pmatrix}1&2\cr 2&4\end{pmatrix}\] は逆行列を持たない. この行列に行基本変形を行うと,
\[\begin{array}{rll}
    C &= \begin{pmatrix}1&2\cr 2&4\end{pmatrix}\quad&\cr
    &\longrightarrow \begin{pmatrix}1&2\cr 0&0\end{pmatrix} \quad &\text{(第 $2$ 行に第 $1$ 行の $-2$ 倍を加えた)}
\end{array}\] などとなり, 単位行列にすることはできない. 

正則でない行列 (正方行列でない行列も含む) に対して行基本変形のみを施した場合は, 以下の性質を持つ行列に変形することができる (が, それ以上単位行列に"近づける"ことはできない) ことが知られている:
* 全ての成分が $0$ となる行が, 行列の最下部に配置される.
* 各行の**主成分** (行の最も左にある $0$ でない要素, **leading coefficient**) が, その行の上にある他の行の主成分よりも右側にある.

このような性質を満たす行列を**行階段形** (**row echelon from**) であるという. 特に, 全ての主成分が $1$ である行階段形を**行簡約階段形** (**reduced row echelon form**) という. 単位行列は行簡約階段形である行列の一種である.

#### <u>例</u>
例えば,
\[
    \begin{pmatrix}2&2a&2b&2c+3\cr 1&a&b&c+4\cr 4&4a&4b&4c+5\end{pmatrix}    
\] という行列に行基本変形を行うことで得られる
\[\begin{pmatrix}1&a&b&c\cr 0&0&0&1\cr 0&0&0&0\end{pmatrix}\] という行列は行簡約階段形である.

---

<a id="section2-4"></a>

## 2.4: 掃き出し法 (ガウスの消去法)

上述のように, 行列に対して行基本変形を行うことで, 行階段簡約形 (単位行列を含む) に変形することができる. このような計算手順 (アルゴリズム) を**掃き出し法** (**row reduction**) もしくは **ガウスの消去法** (**Gaussian elimination**) という. 掃き出し法は, 先ほども紹介したように, 行列の階数を求めるテクニックとして応用できるが, 他にも連立 $1$ 次方程式の解法, もしくは逆行列を計算する方法としても応用することができる. これらを説明するため, まず**拡大行列**という概念を導入する.

#### <u>定義</u> (拡大行列)
行の数が等しい $2$ つの行列 $A$, $B$ に対して, それらを横に連結して得られる行列 $\left(\begin{array}{c:c}A&B\end{array}\right)$ を**拡大行列** (**augmented matrix**) という.

拡大行列は, $2$ つの行列に同じ行基本変形を行う際に, 記述を簡単にするために用いられる.

#### <u>例</u>
\[A = \begin{pmatrix}1&2&3\cr 2&3&4\cr 1&3&5\end{pmatrix},\quad I = \begin{pmatrix}1&0&0\cr 0&1&0\cr 0&0&1\end{pmatrix},\quad \mathbf{b} = \begin{pmatrix}4\cr 7\cr 5\end{pmatrix}.\] このとき, 
\[\left(\begin{array}{c:c}A&I\end{array}\right) = \left(\begin{array}{ccc:ccc}1&2&3&1&0&0\cr 2&3&4&0&1&0\cr 1&3&5&0&0&1\end{array}\right),\quad \left(\begin{array}{c:c}A&\mathbf{b}\end{array}\right) = \left(\begin{array}{ccc:c}1&2&3&4\cr 2&3&4&7\cr 1&3&5&5\end{array}\right).\]

---

まず, 掃き出し法による逆行列の計算方法を紹介する. 

例えば
\[\begin{array}{rll}A &= \begin{pmatrix}1&2\cr 3&4\end{pmatrix}\cr
&\longrightarrow\begin{pmatrix}1&2\cr 0&-2\end{pmatrix} \quad &\text{(第 $2$ 行に第 $1$ 行の $-3$ 倍を加えた)}\cr
&\longrightarrow\begin{pmatrix}1&0\cr 0&-2\end{pmatrix} \quad &\text{(第 $1$ 行に第 $2$ 行の $1$ 倍を加えた)}\cr
&\longrightarrow\begin{pmatrix}1&0\cr 0&1\end{pmatrix} \quad &\text{(第 $2$ 行を $-1/2$ 倍した)}
\end{array}\] という行基本変形は, 
\[Q_{2,-1/2}R_{1,2,1}R_{2,1,-3}A = I\] と同じことを意味しているのだった. これは
\[A^{-1} = Q_{2,-1/2}R_{1,2,1}R_{2,1,-3} = Q_{2,-1/2}R_{1,2,1}R_{2,1,-3}I\] ということに他ならない. 言い換えると, 次が成立する: 

#### <u>命題 (掃き出し法による逆行列の計算)</u>
行列 $A$ を行基本変形で単位行列に変形することができるならば, 同じ行基本変形を単位行列に対して行うことで $A^{-1}$ を得ることができる. 

#### <u>例</u>
これによる逆行列の計算を, 拡大行列を用いて記述してみよう:
\[\begin{array}{rll}\left(\begin{array}{c:c}A&I\end{array}\right) &= \left(\begin{array}{cc:cc}1&2&1&0\cr 3&4&0&1\end{array}\right)\cr
&\longrightarrow\left(\begin{array}{cc:cc}1&2&1&0\cr 0&-2&-3&1\end{array}\right) \quad &\text{(第 $2$ 行に第 $1$ 行の $-3$ 倍を加えた)}\cr
&\longrightarrow\left(\begin{array}{cc:cc}1&0&-2&1\cr 0&-2&-3&1\end{array}\right) \quad &\text{(第 $1$ 行に第 $2$ 行の $1$ 倍を加えた)}\cr
&\longrightarrow\left(\begin{array}{cc:cc}1&0&-2&1\cr 0&1&3/2&-1/2\end{array}\right) \quad &\text{(第 $2$ 行を $-1/2$ 倍した)}.
\end{array}\] このように, 拡大行列 $\left(\begin{array}{c:c}A&I\end{array}\right)$ に対する行基本変形により, 左側を単位行列に変形することができたならば, 右側が $A^{-1}$ となる.

#### <u>注意</u>
この計算の結果も, (階数を求める上の計算などと同様に) 行基本変形の順序に依存しない. しかしながら, $i = 1, 2, \dots, n$ の順に, 
1. 第 $(i,i)$ 成分を $1$ にする.
2. 第 $i$ 行の定数倍を加えることで他の行の第 $i$ 列を全て $0$ にする.

という手順で計算することを推奨する.

#### <u>注意</u>
この計算は, 基本行列たちの積 $P$ であって
\[
    PA = I \quad (\text{つまり } P=A^{-1})
\] を満たすものは, 同時に
\[
    PI = \begin{pmatrix}-2&1\cr 3/2&-1/2\end{pmatrix}
\] を満たす, ということを意味する筆算である. 上のような変形により $P=A^{-1}$ が得られるのは, (繰り返すが) 以下の $2$ つが同じ計算を意味しているからである:

> \[\begin{array}{rll}\left(\begin{array}{c:c}A&I\end{array}\right) =& \left(\begin{array}{cc:cc}1&2&1&0\cr 3&4&0&1\end{array}\right)\cr
\longrightarrow & \left(\begin{array}{cc:cc}1&2&1&0\cr 0&-2&-3&1\end{array}\right) \quad &\text{(第 $2$ 行に第 $1$ 行の $-3$ 倍を加えた)}\cr
\longrightarrow & \left(\begin{array}{cc:cc}1&0&-2&1\cr 0&-2&-3&1\end{array}\right) \quad &\text{(第 $1$ 行に第 $2$ 行の $1$ 倍を加えた)}\cr
\longrightarrow & \left(\begin{array}{cc:cc}1&0&-2&1\cr 0&1&3/2&-1/2\end{array}\right) \quad &\text{(第 $2$ 行を $-1/2$ 倍した)}.
\end{array}\]

> \[\begin{array}{rll} & A = \begin{pmatrix}1&2\cr 3&4\end{pmatrix},\quad I = \begin{pmatrix}1&0\cr 0&1\end{pmatrix}\cr 
\iff & R_{2,1,-3}A = \begin{pmatrix}1&2\cr 0&-2\end{pmatrix},\qquad R_{2,1,-3}I = \begin{pmatrix}1&0\cr -3&1\end{pmatrix}\cr
\iff & R_{1,2,1}R_{2,1,-3}A = \begin{pmatrix}1&0\cr 0&-2\end{pmatrix},\qquad R_{1,2,1}R_{2,1,-3}I = \begin{pmatrix}-2&1\cr -3&1\end{pmatrix}\cr
\iff & Q_{2,-1/2}R_{1,2,1}R_{2,1,-3}A = \begin{pmatrix}1&0\cr 0&1\end{pmatrix},\qquad Q_{2,-1/2}R_{1,2,1}R_{2,1,-3}I = \begin{pmatrix}-2&1\cr 3/2&-1/2\end{pmatrix}\
\end{array}\]


#### <u>注意</u>
もしも $A$ が正則行列でなかったならば, 拡大行列 $\left(\begin{array}{c:c}A&I\end{array}\right)$ に対する行基本変形により左側を単位行列に変形することはできない. このことを利用すれば, $A$ が正則であるかどうかの判定も行うことができる.

---

掃き出し法を用いて連立 $1$ 次方程式を解く方法を紹介する. 

**2.1: 導入** において挙げたものと同じ例を用いる:
\[\left\lbrace\begin{array}{rll}
    x+2y &= 20, &(1)\cr
    3x+4y &= 46. &(2)
    \end{array}\right.
\] まず, この連立 $1$ 次方程式をそのまま解いてみる, 例えば以下のような式変形を考えよう:
\[
    \longrightarrow\left\lbrace\begin{array}{rll}
    x+2y &= 20, &(1)\cr
    -2y &= -14. &(2)^{\prime} = (2) - 3\times(1)
    \end{array}\right.
\] \[
    \longrightarrow\left\lbrace\begin{array}{rll}
    x &= 6, &(1)^{\prime} = (1) + (2)^{\prime}\cr
    -2y &= -14. &(2)^{\prime}
    \end{array}\right.
\] \[
    \longrightarrow\left\lbrace\begin{array}{rll}
    x &= 6, &(1)'\cr
    y &= 7. &(2)^{\prime \prime} = -1/2\times (2)^{\prime}
    \end{array}\right.
\] このような式変形により, 解 $x=6$, $y=7$ が得られる.

次に, この連立 $1$ 次方程式を $A\mathbf{x} = \mathbf{b}$ と同一視してみる, ここで
\[
    A = \begin{pmatrix}1&2\cr 3&4\end{pmatrix}, \quad \mathbf{x}=\begin{pmatrix}x\cr y\end{pmatrix}, \quad \mathbf{b} = \begin{pmatrix}20\cr 46\end{pmatrix}.
\] もしも $A$ が正則行列であるならば, $\mathbf{x} = A^{-1}A\mathbf{x} = A^{-1}\mathbf{b}$ を計算することで連立 $1$ 次方程式の解 $x$, $y$ を得ることができるが, 先ほども見たように $A^{-1}$ は (存在するならば) 行基本変形により表現できる. (この例に対しては, 上の連立 $1$ 次方程式を解く際に用いた変形は
\[Q_{2,-1/2}R_{1,2,1}R_{2,1,-3}A = I\] と同一視でき, これを用いると
\[
    \mathbf{x} = A^{-1}\mathbf{b} = Q_{2,-1/2}R_{1,2,1}R_{2,1,-3}\mathbf{b}
\] となる). 言い換えれば, 次が成立する:

#### <u>命題 (掃き出し法による連立 $1$ 次方程式の解法)</u>
行列 $A$ を行基本変形で単位行列に変形することができるならば, 同じ行基本変形を列ベクトル$\mathbf{b}$に対して行うことで $A^{-1}\mathbf{b}$ を得ることができる. 

#### <u>例</u>
上に例として挙げた連立 $1$ 次方程式の解法と同じ計算を, 拡大行列に対する掃き出し法を用いて記述してみる:
\[\begin{array}{rll}\left(\begin{array}{c:c}A&\mathbf{b}\end{array}\right) &= \left(\begin{array}{cc:c}1&2&20\cr 3&4&46\end{array}\right)\cr
&\longrightarrow\left(\begin{array}{cc:c}1&2&20\cr 0&-2&-14\end{array}\right) \quad &\text{(第 $2$ 行に第 $1$ 行の $-3$ 倍を加えた)}\cr
&\longrightarrow\left(\begin{array}{cc:c}1&0&6\cr 0&-2&-14\end{array}\right) \quad &\text{(第 $1$ 行に第 $2$ 行の $1$ 倍を加えた)}\cr
&\longrightarrow\left(\begin{array}{cc:c}1&0&6\cr 0&1&7\end{array}\right) \quad &\text{(第 $2$ 行を $-1/2$ 倍した)}.
\end{array}\] ここで用いた行基本変形は, 連立 $1$ 次方程式に対する各操作と確かに同一視できる (例えば上の連立 $1$ 次方程式の解法において, $(1)^\prime = (1) - 3\times (2)$ という式変形を用いたが, これは第 $2$ 行に第 $1$ 行の $-3$ 倍を加える行基本変形と同値である).

このように, 拡大行列 $\left(\begin{array}{c:c}A&\mathbf{b}\end{array}\right)$ に対する行基本変形により, 左側を単位行列に変形することができたならば, 右側が $A^{-1}\mathbf{b}$ となる.

#### <u>注意</u>
何度も同じことを書くが, この計算は基本行列たちの積 $P$ であって
\[
    PA = I \quad (\text{つまり } P=A^{-1})
\] を満たすものは, 同時に
\[
    P\mathbf{b} = \begin{pmatrix}6\cr 7\end{pmatrix}
\] を満たす, ということを意味する筆算であり, また以下の $3$ つは全て同じ計算を意味している:

> \[\begin{array}{rl}
    & \left\lbrace\begin{array}{rll}
    x+2y &= 20, &(1)\cr
    3x+4y &= 46. &(2)
    \end{array}\right.\cr
    \longrightarrow & \left\lbrace\begin{array}{rll}
    x+2y &= 20, &(1)\cr
    -2y &= -14. &(2)^{\prime} = (2) - 3\times(1)
    \end{array}\right.\cr
    \longrightarrow & \left\lbrace\begin{array}{rll}
    x &= 6, &(1)^{\prime} = (1) + (2)^{\prime}\cr
    -2y &= -14. &(2)^{\prime}
    \end{array}\right.\cr
    \longrightarrow & \left\lbrace\begin{array}{rll}
    x &= 6, &(1)'\cr
    y &= 7. &(2)^{\prime \prime} = -1/2\times (2)^{\prime}
    \end{array}\right.
    \end{array}
\]

> \[\begin{array}{rll}\left(\begin{array}{c:c}A&\mathbf{b}\end{array}\right) =& \left(\begin{array}{cc:c}1&2&20\cr 3&4&46\end{array}\right)\cr
\longrightarrow & \left(\begin{array}{cc:c}1&2&20\cr 0&-2&-14\end{array}\right) \quad &\text{(第 $2$ 行に第 $1$ 行の $-3$ 倍を加えた)}\cr
\longrightarrow & \left(\begin{array}{cc:c}1&0&6\cr 0&-2&-14\end{array}\right) \quad &\text{(第 $1$ 行に第 $2$ 行の $1$ 倍を加えた)}\cr
\longrightarrow & \left(\begin{array}{cc:c}1&0&6\cr 0&1&7\end{array}\right) \quad &\text{(第 $2$ 行を $-1/2$ 倍した)}.
\end{array}\]

> \[\begin{array}{rl}
&A = \begin{pmatrix}1&2\cr 3&4\end{pmatrix},\qquad \mathbf{b} = \begin{pmatrix}20\cr 40\end{pmatrix}\cr
\iff & R_{2,1,-3}A = \begin{pmatrix}1&2\cr 0&-2\end{pmatrix},\qquad R_{2,1,-3}\mathbf{b} = \begin{pmatrix}20\cr -14\end{pmatrix}\cr
\iff & R_{1,2,1}R_{2,1,-3}A = \begin{pmatrix}1&0\cr 0&-2\end{pmatrix},\qquad R_{1,2,1}R_{2,1,-3}\mathbf{b} = \begin{pmatrix}6\cr -14\end{pmatrix}\cr
\iff & Q_{2,-1/2}R_{1,2,1}R_{2,1,-3}A = \begin{pmatrix}1&0\cr 0&1\end{pmatrix},\qquad Q_{2,-1/2}R_{1,2,1}R_{2,1,-3}\mathbf{b} = \begin{pmatrix}6\cr 7\end{pmatrix}
\end{array}\]


#### <u>注意</u>
もしも $A$ が正則行列でなかったならば (正方行列でない場合も含む), 拡大行列 $\left(\begin{array}{c:c}A&\mathbf{b}\end{array}\right)$ に対する行基本変形により左側を単位行列に変形することはできない. これは, 連立 $1$ 次方程式の解が存在しない, もしくは一意に定まらないことを意味する.

#### <u>例</u>
\[\left\lbrace\begin{array}{rll}
    x+2y &= a, &(1)\cr
    2x+4y &= b. &(2)
    \end{array}\right.
\] という連立 $1$ 次方程式, もしくはこれと同値な問題
\[\begin{pmatrix}1&2\cr 2&4\end{pmatrix} \begin{pmatrix}x\cr y\end{pmatrix} = \begin{pmatrix}a\cr b\end{pmatrix}\] を考える. 拡大係数行列に対する掃き出し法により
\[
    \left(\begin{array}{cc:c}1&2&a\cr 2&4&b
    \end{array}\right)\longrightarrow \left(\begin{array}{cc:c}1&2&a\cr 0&0&b-2a
    \end{array}\right)
\] という行階段形 ($b-2a\neq0$ ならば第 $2$ 行を $b-2a$ で割ることで行簡約階段形) が得られるが, この左側はこれ以上単位行列に"近づける"ことはできない. この行階段形は,
\[
    \left\lbrace\begin{array}{rll}
        x+2y &= a, &(1)\cr
        0 &= b-2a. &(2)^{\prime}
    \end{array}\right.
\] と同値であるが, この問題は $2a=b$ ならば $x+2y=a$ を満たす全ての $x$, $y$ が解となり, 一方で $2a\neq b$ ならば 解は存在しない. 

---
