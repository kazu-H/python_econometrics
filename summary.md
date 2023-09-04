# [Pythonで学ぶ入門計量経済学](https://py4etrics.github.io/index.html)

## はじめに
 本稿は掲題の教材をまとめることを目的としている。バージョン管理の観点から、Dockerを用いて環境設定しており、VSCodeによる開発を念頭においている。なお、バージョン管理はgitで行っており、ページは[ここ](https://github.com/kazu-H/python_econometrics)。環境整備にあたって導入過程は[ここ](https://hackmd.io/G6B0bkqQQIexhxWxCJyvEQ)にまとめている。
 
 ## 本稿の使い方
 wooldridgeのテキストをベースにしていることもあり、概ね既知の内容となっている。このため、不明瞭であった点などを断片的にまとめていくこととする。
 
:::info
参考：Latexの数式レイアウト
- [【LaTeX】数式環境まとめ【amsmath】](https://mathlandscape.com/latex-eq/)
- [【LaTeX】アクセント記号【ö,æ,ç】](https://takataninote.com/tex/accent.html)
:::
 
### panel
- 固定効果モデルの仮定
$Cov(a_{i}x_{it} ≠ 0, \  t=1,2,..,T)$

- ランダム効果モデルの仮定
$Cov(a_{i}x_{it} = 0, \  t=1,2,..,T)$

  * ランダム効果モデルの仮定の下では、
$$\begin{align}
y_{it} &= \beta_0+\beta_1x_{it} + a_i +u_{it} \\
&= \beta_0+\beta_1x_{it} +e_{it},
&\ where\ e_{it} = a_i +u_{it} 
\end{align}$$
が成り立ち、この時、$Corr(e_{it},e_{is})≠0,\ when\ t≠s$となる。パネルデータで回帰するときは、異時点間で自己相関が生じるため推定量の効率性が悪くなる。また、階差をとったり固定効果モデルを回すと効率性が悪くなる。

  * solution
  $$\dot{y} = \beta_0(1-\theta)+\beta_1\dot{x}_{it}+\dot{e}_{it}$$

    $$\begin{gather}
where,\\
\dot{y} = y_{it} - \theta \bar{y}_i\\
\dot{x} = x_{it} - \theta \bar{x}_i\\
\dot{e} = e_{it} - \theta \bar{e}_i\\
\theta = 1 - \sqrt{\frac{\sigma^2_{u}}{\sigma^2_{u}+T\sigma^2_{a}}}
\end{gather}$$
    というモデルを考える。ここでは、$\sigma^2_{a}$が個体の個別項のばらつきを意味し、これが0に近づくほど異質性が小さくなり、1に近づくほど異質性は大きくなる。$\sigma^2_{a}\to\infty$なら、$\theta\to1$となり、固定効果モデルの変形と完全に一致する。

### 相関ランダム効果モデル
- wooldridgeのテキストくらいでしか見ないやや発展的な分析。固定効果モデルとランダム効果モデルの中間的な位置にあり，両方を包含している。
- 先ほどの式において、$a_i = \alpha+\gamma\bar{x}_{i}+r_i$と表現できるとする。ただし、$\gamma$は$\alpha$と$\bar{x}_{i}$の相関関係をとらえており、$r_i$は$\bar{x}_{i}$と相関しないと仮定する。この式を用いて、パネルデータを分析する式を、$$\begin{align}
y_{it} &= \beta_0+\beta_1x_{it} + a_i +u_{it} \\
&= \alpha+\beta x_{it}+\gamma\bar{x}_{i} +v_{it}
\end{align}$$と変形する。具体的な推定は、まず$\bar{x}_{i}$を計算し、それを項に加えた回帰を行う。
- $\gamma$の係数が0であればランダム効果モデルを、0でなければ固定効果モデルを用いるのと同じなので、Hausman検定をやっているようなもの。
- まだ完全には理解していないものの、階差をとることもないので時間に対して不変な変数も加えたうえで、固定効果モデルと同様の推計結果を得られる。
