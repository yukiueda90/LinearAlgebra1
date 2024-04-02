# 1. 行列
## 1.1 行列の定義
##### <u>定義</u> (行列)
縦に$m$個, 横に$n$個の数を長方形状に並べたものを$m\times n$ 型の**行列** (**matrix**) という.

##### <u>例</u> 
$$A = \begin{pmatrix}a_{11}&a_{12}\\a_{21}&a_{22}\end{pmatrix},\qquad B=\begin{pmatrix}b_{11}&b_{12}&b_{13}\\b_{21}&b_{22}&b_{32}\end{pmatrix}.$$

* 行列を構成する$mn$個の数を行列の**成分** (**element**) という
* 行列を構成する要素たちを横に並べた部分を**行** (**row**), 縦に並べた部分を**列** (**column**)という
* 上から $i$ 番目の行を**第 $i$ 行**, 左から $j$ 番目の列を**第 $j$ 列**という.
* 第 $i$ 行, 第 $j$ 列にある成分を **$(i,j)$ 成分**という.
    * 以降, 断りの無い限り, 行列 $A$ の $(i,j)$ 成分を $a_{ij}$ と表す. 
    * また, $(i,j)$ 成分が $a_{ij}$ である行列を $(a_{ij})$ と表す.

##### <u>例</u>
$$A = \begin{pmatrix}a_{11}&a_{12}\\a_{21}&a_{22}\end{pmatrix} = (a_{ij}).$$
    * この行列 $A$ の第 $1$ 行は $(a_{11},a_{12})$.
    * この行列 $A$ の第 $2$ 列は $\begin{pmatrix}a_{12}\\a_{22}\end{pmatrix}$.
    * この行列 $A$ の $(1,2)$ 成分は $a_{12}$.

* 全ての成分が実数である行列を**実行列** (**real matrix**)という.
    * 行列 $A$ が $m\times n$ 型の実行列であるとき, $A\in \mathbb{R}^{m\times n}$ と表記する.
* 全ての成分が複素数である行列を**複素行列** (**real matrix**)という.
    * 行列 $A$ が $m\times n$ 型の複素行列であるとき, $A\in \mathbb{C}^{m\times n}$ と表記する.
* $1\times n$ 型の行列を**行ベクトル** (**row vector**)という.
* $m\times 1$ 型の行列を**列ベクトル** (**column vector**)という.

##### <u>例</u>
$$A = \begin{pmatrix}a_{11}&a_{12}\\a_{21}&a_{22}\end{pmatrix} \in \mathbb{R}^{2\times 2}.$$
    $$\bm{x} = (x_1,x_2,x_3), \qquad \bm{x}\text{は行ベクトル}.$$
    $$\bm{v} = \begin{pmatrix}v_1\\v_2\\v_3\end{pmatrix},\qquad \bm{v}\text{は列ベクトル}.$$

## 1.2 行列の演算
##### <u>定義</u>
$2$つの行列 $A=(a_{ij})$, $B=(b_{ij})$ について, $A$ と $B$ が同じ型であって, 全ての $i,j$ に対して $$a_{ij} = b_{ij}$$ となるとき, $A$ と $B$ は等しいといい, $$A=B$$ と表記する. $A=B$ でない場合は, $A\neq B$ と表記する.

##### <u>例</u>
$$A=\begin{pmatrix}1&2\\3&4\end{pmatrix},\quad B=\begin{pmatrix}1&2\\3&4\end{pmatrix},\quad C=\begin{pmatrix}1&2\\3&0\end{pmatrix},\quad D=\begin{pmatrix}1&2\\3&4\\0&0\end{pmatrix}.$$
* 行列の型が同じで, 全ての成分が等しいため $A=B$.
* $(2,2)$ 成分が異なるため $A\neq C$. 
* 行列の型が異なるため $A\neq D$.

##### <u>定義</u> (行列の和)
同じ型の$2$つの行列 $A=(a_{ij})$, $B=(b_{ij})$ について, $(i,j)$ 成分が $a_{ij}+b_{ij}$ である行列を $A$ と $B$ の和といい, $A+B$ と表記する.
##### <u>例</u>
$$A=\begin{pmatrix}1&2\\3&4\end{pmatrix},\quad B=\begin{pmatrix}1&2\\3&4\end{pmatrix},\quad C=\begin{pmatrix}1&2\\3&0\end{pmatrix},\quad D=\begin{pmatrix}1&2\\3&4\\0&0\end{pmatrix}.$$
* $A+B = \begin{pmatrix}1&2\\3&4\end{pmatrix}+\begin{pmatrix}1&2\\3&4\end{pmatrix} = \begin{pmatrix}2&4\\6&8\end{pmatrix}$ 
* $A+C = \begin{pmatrix}1&2\\3&4\end{pmatrix} + \begin{pmatrix}1&2\\3&0\end{pmatrix} = \begin{pmatrix}2&4\\6&4\end{pmatrix}$
* 行列の型が異なるため, $A+D$ は定義されていない. 

##### <u>定義</u> (行列のスカラー倍)
行列 $A=(a_{ij})$ と複素数 $\lambda$ に対し, $(i,j)$ 成分が $\lambda a_{ij}$ である行列を $\lambda A$ と表記する.
##### <u>例</u>
$$A=\begin{pmatrix}1&2\\3&4\end{pmatrix}$$
* $2A = 2\begin{pmatrix}1&2\\3&4\end{pmatrix} = \begin{pmatrix}2&4\\6&8\end{pmatrix} = A+A$

##### <u>定義</u> (行列の積)
