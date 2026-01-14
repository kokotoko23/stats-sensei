---
layout: default
title: 統計用語集
description: 統計学の重要用語をカテゴリ別に解説
permalink: /glossary/
---

# 統計用語集

統計学で使われる重要な用語をカテゴリ別にまとめました。

<div class="glossary-nav">
  <a href="#descriptive">記述統計</a>
  <a href="#probability">確率</a>
  <a href="#distribution">確率分布</a>
  <a href="#inference">推測統計</a>
  <a href="#regression">回帰分析</a>
</div>

---

<h2 id="descriptive">記述統計</h2>

<div class="glossary-section">

<dl class="glossary-term">
<dt>平均（Mean / Average）</dt>
<dd>データの合計をデータ数で割った値。データの「中心」を表す代表的な指標。記号は $\bar{x}$（標本平均）または $\mu$（母平均）。
<div class="related-link">関連: <a href="{{ site.baseurl }}/theory/mean-median-mode/">平均・中央値・最頻値</a></div>
</dd>
</dl>

<dl class="glossary-term">
<dt>中央値（Median）</dt>
<dd>データを小さい順に並べたときの真ん中の値。外れ値の影響を受けにくい。
<div class="related-link">関連: <a href="{{ site.baseurl }}/theory/mean-median-mode/">平均・中央値・最頻値</a></div>
</dd>
</dl>

<dl class="glossary-term">
<dt>最頻値（Mode）</dt>
<dd>データの中で最も頻繁に出現する値。カテゴリデータにも使える。
<div class="related-link">関連: <a href="{{ site.baseurl }}/theory/mean-median-mode/">平均・中央値・最頻値</a></div>
</dd>
</dl>

<dl class="glossary-term">
<dt>分散（Variance）</dt>
<dd>データのばらつきを表す指標。各データと平均の差（偏差）の2乗の平均。記号は $s^2$（標本分散）または $\sigma^2$（母分散）。
<div class="related-link">関連: <a href="{{ site.baseurl }}/theory/variance-std/">分散と標準偏差</a></div>
</dd>
</dl>

<dl class="glossary-term">
<dt>標準偏差（Standard Deviation）</dt>
<dd>分散の平方根。元のデータと同じ単位でばらつきを表現できる。記号は $s$（標本標準偏差）または $\sigma$（母標準偏差）。
<div class="related-link">関連: <a href="{{ site.baseurl }}/theory/variance-std/">分散と標準偏差</a></div>
</dd>
</dl>

<dl class="glossary-term">
<dt>偏差（Deviation）</dt>
<dd>各データと平均との差。偏差の合計は常に0になる。
<div class="related-link">関連: <a href="{{ site.baseurl }}/theory/variance-std/">分散と標準偏差</a></div>
</dd>
</dl>

<dl class="glossary-term">
<dt>ヒストグラム（Histogram）</dt>
<dd>データの分布を視覚化するグラフ。横軸に階級、縦軸に度数をとる。
<div class="related-link">関連: <a href="{{ site.baseurl }}/theory/histogram/">ヒストグラムと度数分布</a></div>
</dd>
</dl>

<dl class="glossary-term">
<dt>度数分布（Frequency Distribution）</dt>
<dd>データを階級（範囲）に分け、各階級に含まれるデータの個数（度数）をまとめたもの。
<div class="related-link">関連: <a href="{{ site.baseurl }}/theory/histogram/">ヒストグラムと度数分布</a></div>
</dd>
</dl>

</div>

---

<h2 id="probability">確率</h2>

<div class="glossary-section">

<dl class="glossary-term">
<dt>確率（Probability）</dt>
<dd>ある事象が起こる可能性を0から1（または0%から100%）の数値で表したもの。
<div class="related-link">関連: <a href="{{ site.baseurl }}/theory/probability-basics/">確率の基本概念</a></div>
</dd>
</dl>

<dl class="glossary-term">
<dt>標本空間（Sample Space）</dt>
<dd>起こりうる全ての結果の集合。記号は $\Omega$ または $S$。
<div class="related-link">関連: <a href="{{ site.baseurl }}/theory/probability-basics/">確率の基本概念</a></div>
</dd>
</dl>

<dl class="glossary-term">
<dt>事象（Event）</dt>
<dd>標本空間の部分集合。「サイコロで偶数が出る」などの結果の集まり。
<div class="related-link">関連: <a href="{{ site.baseurl }}/theory/probability-basics/">確率の基本概念</a></div>
</dd>
</dl>

<dl class="glossary-term">
<dt>余事象（Complement）</dt>
<dd>ある事象が起こらない場合の事象。事象Aの余事象は $\bar{A}$ と書き、$P(\bar{A}) = 1 - P(A)$。
<div class="related-link">関連: <a href="{{ site.baseurl }}/theory/probability-basics/">確率の基本概念</a></div>
</dd>
</dl>

<dl class="glossary-term">
<dt>条件付き確率（Conditional Probability）</dt>
<dd>ある事象Bが起きたという条件のもとで、事象Aが起きる確率。$P(A|B) = \frac{P(A \cap B)}{P(B)}$
<div class="related-link">関連: <a href="{{ site.baseurl }}/theory/conditional-probability/">条件付き確率</a></div>
</dd>
</dl>

<dl class="glossary-term">
<dt>独立（Independence）</dt>
<dd>2つの事象が互いに影響しないこと。$P(A \cap B) = P(A) \times P(B)$ が成り立つ。
<div class="related-link">関連: <a href="{{ site.baseurl }}/theory/conditional-probability/">条件付き確率</a></div>
</dd>
</dl>

<dl class="glossary-term">
<dt>期待値（Expected Value）</dt>
<dd>確率変数の「平均的な値」。各値にその確率を掛けた総和。記号は $E[X]$ または $\mu$。
<div class="related-link">関連: <a href="{{ site.baseurl }}/theory/expected-value/">期待値</a></div>
</dd>
</dl>

<dl class="glossary-term">
<dt>ベイズの定理（Bayes' Theorem）</dt>
<dd>条件付き確率を逆転させる公式。$P(A|B) = \frac{P(B|A) \times P(A)}{P(B)}$
<div class="related-link">関連: <a href="{{ site.baseurl }}/theory/conditional-probability/">条件付き確率</a></div>
</dd>
</dl>

</div>

---

<h2 id="distribution">確率分布</h2>

<div class="glossary-section">

<dl class="glossary-term">
<dt>確率分布（Probability Distribution）</dt>
<dd>確率変数がとる値とその確率の対応関係。離散型と連続型がある。
<div class="related-link">関連: <a href="{{ site.baseurl }}/theory/normal-distribution/">正規分布</a></div>
</dd>
</dl>

<dl class="glossary-term">
<dt>正規分布（Normal Distribution）</dt>
<dd>釣鐘型の左右対称な分布。自然界・社会現象で最もよく見られる分布。$N(\mu, \sigma^2)$と表記。
<div class="related-link">関連: <a href="{{ site.baseurl }}/theory/normal-distribution/">正規分布</a></div>
</dd>
</dl>

<dl class="glossary-term">
<dt>標準正規分布（Standard Normal Distribution）</dt>
<dd>平均0、標準偏差1の正規分布。$N(0, 1)$。z値の分布。
<div class="related-link">関連: <a href="{{ site.baseurl }}/theory/normal-distribution/">正規分布</a></div>
</dd>
</dl>

<dl class="glossary-term">
<dt>二項分布（Binomial Distribution）</dt>
<dd>成功確率pの試行をn回行ったときの成功回数の分布。$B(n, p)$と表記。
<div class="related-link">関連: <a href="{{ site.baseurl }}/theory/binomial/">二項分布</a></div>
</dd>
</dl>

<dl class="glossary-term">
<dt>ポアソン分布（Poisson Distribution）</dt>
<dd>一定期間に起こる稀な事象の回数の分布。パラメータは $\lambda$（平均発生回数）。
<div class="related-link">関連: <a href="{{ site.baseurl }}/theory/poisson/">ポアソン分布</a></div>
</dd>
</dl>

<dl class="glossary-term">
<dt>t分布（t-distribution）</dt>
<dd>標本サイズが小さいときに使う分布。正規分布より裾が厚い。自由度で形が決まる。
<div class="related-link">関連: <a href="{{ site.baseurl }}/theory/t-test/">t検定</a></div>
</dd>
</dl>

<dl class="glossary-term">
<dt>z値（z-score）</dt>
<dd>データを標準化した値。$z = \frac{x - \mu}{\sigma}$。平均からのずれを標準偏差の何倍かで表す。
<div class="related-link">関連: <a href="{{ site.baseurl }}/theory/normal-distribution/">正規分布</a></div>
</dd>
</dl>

</div>

---

<h2 id="inference">推測統計</h2>

<div class="glossary-section">

<dl class="glossary-term">
<dt>母集団（Population）</dt>
<dd>調査対象となる集団全体。通常は全数調査が困難なため、標本を使って推測する。
<div class="related-link">関連: <a href="{{ site.baseurl }}/theory/interval-estimation/">区間推定</a></div>
</dd>
</dl>

<dl class="glossary-term">
<dt>標本（Sample）</dt>
<dd>母集団から抽出したデータの一部。標本から母集団の特性を推測する。
<div class="related-link">関連: <a href="{{ site.baseurl }}/theory/interval-estimation/">区間推定</a></div>
</dd>
</dl>

<dl class="glossary-term">
<dt>標準誤差（Standard Error）</dt>
<dd>標本平均のばらつき。$SE = \frac{\sigma}{\sqrt{n}}$。標本サイズが大きいほど小さくなる。
<div class="related-link">関連: <a href="{{ site.baseurl }}/theory/interval-estimation/">区間推定</a></div>
</dd>
</dl>

<dl class="glossary-term">
<dt>信頼区間（Confidence Interval）</dt>
<dd>母数が含まれると推定される範囲。95%信頼区間が一般的。
<div class="related-link">関連: <a href="{{ site.baseurl }}/theory/interval-estimation/">区間推定</a></div>
</dd>
</dl>

<dl class="glossary-term">
<dt>帰無仮説（Null Hypothesis）</dt>
<dd>「差がない」「効果がない」という仮説。記号は $H_0$。検定で棄却されるかどうかを判断する。
<div class="related-link">関連: <a href="{{ site.baseurl }}/theory/hypothesis-testing/">仮説検定の基礎</a></div>
</dd>
</dl>

<dl class="glossary-term">
<dt>対立仮説（Alternative Hypothesis）</dt>
<dd>帰無仮説と対立する仮説。「差がある」「効果がある」など。記号は $H_1$ または $H_a$。
<div class="related-link">関連: <a href="{{ site.baseurl }}/theory/hypothesis-testing/">仮説検定の基礎</a></div>
</dd>
</dl>

<dl class="glossary-term">
<dt>有意水準（Significance Level）</dt>
<dd>帰無仮説を誤って棄却する確率の上限。通常は5%（$\alpha = 0.05$）を使用。
<div class="related-link">関連: <a href="{{ site.baseurl }}/theory/hypothesis-testing/">仮説検定の基礎</a></div>
</dd>
</dl>

<dl class="glossary-term">
<dt>p値（p-value）</dt>
<dd>帰無仮説が正しいと仮定したとき、観測データ以上に極端な結果が得られる確率。
<div class="related-link">関連: <a href="{{ site.baseurl }}/theory/hypothesis-testing/">仮説検定の基礎</a></div>
</dd>
</dl>

<dl class="glossary-term">
<dt>第1種の誤り（Type I Error）</dt>
<dd>帰無仮説が正しいのに棄却してしまう誤り。確率は有意水準 $\alpha$ と等しい。
<div class="related-link">関連: <a href="{{ site.baseurl }}/theory/hypothesis-testing/">仮説検定の基礎</a></div>
</dd>
</dl>

<dl class="glossary-term">
<dt>第2種の誤り（Type II Error）</dt>
<dd>帰無仮説が間違っているのに棄却しない誤り。確率は $\beta$ で表す。
<div class="related-link">関連: <a href="{{ site.baseurl }}/theory/hypothesis-testing/">仮説検定の基礎</a></div>
</dd>
</dl>

<dl class="glossary-term">
<dt>検出力（Power）</dt>
<dd>対立仮説が正しいときに正しく帰無仮説を棄却できる確率。$1 - \beta$。
<div class="related-link">関連: <a href="{{ site.baseurl }}/theory/hypothesis-testing/">仮説検定の基礎</a></div>
</dd>
</dl>

</div>

---

<h2 id="regression">回帰分析</h2>

<div class="glossary-section">

<dl class="glossary-term">
<dt>相関係数（Correlation Coefficient）</dt>
<dd>2変数間の線形関係の強さと方向を表す指標。-1から1の範囲。記号は $r$。
<div class="related-link">関連: <a href="{{ site.baseurl }}/theory/correlation/">相関分析</a></div>
</dd>
</dl>

<dl class="glossary-term">
<dt>散布図（Scatter Plot）</dt>
<dd>2変数のデータを平面上の点で表したグラフ。相関の視覚化に使う。
<div class="related-link">関連: <a href="{{ site.baseurl }}/theory/correlation/">相関分析</a></div>
</dd>
</dl>

<dl class="glossary-term">
<dt>回帰直線（Regression Line）</dt>
<dd>散布図上のデータ点に最もフィットする直線。$\hat{y} = a + bx$ の形。
<div class="related-link">関連: <a href="{{ site.baseurl }}/theory/regression/">単回帰分析</a></div>
</dd>
</dl>

<dl class="glossary-term">
<dt>最小二乗法（Least Squares Method）</dt>
<dd>残差の2乗和を最小にするように回帰係数を求める方法。
<div class="related-link">関連: <a href="{{ site.baseurl }}/theory/regression/">単回帰分析</a></div>
</dd>
</dl>

<dl class="glossary-term">
<dt>決定係数（Coefficient of Determination）</dt>
<dd>回帰式がデータをどれだけ説明できるかを表す指標。$R^2 = r^2$。0から1の範囲。
<div class="related-link">関連: <a href="{{ site.baseurl }}/theory/regression/">単回帰分析</a></div>
</dd>
</dl>

<dl class="glossary-term">
<dt>残差（Residual）</dt>
<dd>実測値と予測値の差。$e_i = y_i - \hat{y}_i$
<div class="related-link">関連: <a href="{{ site.baseurl }}/theory/regression/">単回帰分析</a></div>
</dd>
</dl>

<dl class="glossary-term">
<dt>重回帰分析（Multiple Regression）</dt>
<dd>複数の説明変数を使って目的変数を予測する分析手法。
<div class="related-link">関連: <a href="{{ site.baseurl }}/theory/multiple-regression/">重回帰分析</a></div>
</dd>
</dl>

<dl class="glossary-term">
<dt>多重共線性（Multicollinearity）</dt>
<dd>説明変数間に強い相関がある状態。回帰係数の推定が不安定になる。
<div class="related-link">関連: <a href="{{ site.baseurl }}/theory/multiple-regression/">重回帰分析</a></div>
</dd>
</dl>

</div>

---

[トップページに戻る]({{ site.baseurl }}/)
