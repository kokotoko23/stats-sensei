---
layout: default
title: 確率分布の問題 - 準1級対策
description: 離散分布、連続分布、極限定理の選択式問題
permalink: /semi-1/problems/distributions/
---

# 確率分布の問題

離散型分布、連続型分布、極限定理に関する問題です。

<div class="quiz-progress">
  <span class="quiz-progress-text">0 / 10 正解</span>
  <div class="quiz-progress-bar">
    <div class="quiz-progress-fill" style="width: 0%"></div>
  </div>
</div>

---

## 問題 1：ガンマ分布

<div class="quiz-container" data-quiz-id="dist-1" data-correct="b" data-difficulty="easy">
  <div class="quiz-question">
    $X_1, X_2, \ldots, X_n$ が独立に指数分布 $\text{Exp}(\lambda)$ に従うとき、$Y = \sum_{i=1}^n X_i$ の分布はどれか。
  </div>
  <div class="quiz-options">
    <div class="quiz-option" data-value="a">
      <input type="radio" name="q1" id="q1a">
      <label for="q1a">指数分布 $\text{Exp}(n\lambda)$</label>
    </div>
    <div class="quiz-option" data-value="b">
      <input type="radio" name="q1" id="q1b">
      <label for="q1b">ガンマ分布 $\text{Gamma}(n, \lambda)$</label>
    </div>
    <div class="quiz-option" data-value="c">
      <input type="radio" name="q1" id="q1c">
      <label for="q1c">カイ二乗分布 $\chi^2_n$</label>
    </div>
    <div class="quiz-option" data-value="d">
      <input type="radio" name="q1" id="q1d">
      <label for="q1d">正規分布 $N(n/\lambda, n/\lambda^2)$</label>
    </div>
  </div>
  <button class="quiz-btn" disabled>解答を確認</button>
  <div class="quiz-feedback">
    <span class="quiz-feedback-icon"></span>
    <strong>正解：(b)</strong>
    <div class="quiz-explanation">
      指数分布はガンマ分布の特殊ケース：$\text{Exp}(\lambda) = \text{Gamma}(1, \lambda)$。

      ガンマ分布の再生性より、独立なガンマ分布の和はガンマ分布に従います：

      $\text{Gamma}(\alpha_1, \lambda) + \text{Gamma}(\alpha_2, \lambda) = \text{Gamma}(\alpha_1 + \alpha_2, \lambda)$

      したがって、$Y = \sum X_i \sim \text{Gamma}(n, \lambda)$。

      これは「$n$番目の事象が起こるまでの待ち時間」の分布でもあります。
    </div>
  </div>
</div>

---

## 問題 2：ベータ分布

<div class="quiz-container" data-quiz-id="dist-2" data-correct="a" data-difficulty="medium">
  <div class="quiz-question">
    $X \sim \text{Beta}(\alpha, \beta)$ のとき、$E[X]$ はどれか。
  </div>
  <div class="quiz-options">
    <div class="quiz-option" data-value="a">
      <input type="radio" name="q2" id="q2a">
      <label for="q2a">$\displaystyle \frac{\alpha}{\alpha + \beta}$</label>
    </div>
    <div class="quiz-option" data-value="b">
      <input type="radio" name="q2" id="q2b">
      <label for="q2b">$\displaystyle \frac{\beta}{\alpha + \beta}$</label>
    </div>
    <div class="quiz-option" data-value="c">
      <input type="radio" name="q2" id="q2c">
      <label for="q2c">$\displaystyle \frac{\alpha \beta}{(\alpha + \beta)^2}$</label>
    </div>
    <div class="quiz-option" data-value="d">
      <input type="radio" name="q2" id="q2d">
      <label for="q2d">$\displaystyle \frac{1}{2}$</label>
    </div>
  </div>
  <button class="quiz-btn" disabled>解答を確認</button>
  <div class="quiz-feedback">
    <span class="quiz-feedback-icon"></span>
    <strong>正解：(a)</strong>
    <div class="quiz-explanation">
      ベータ分布 $\text{Beta}(\alpha, \beta)$ の期待値は $E[X] = \frac{\alpha}{\alpha + \beta}$。

      分散は $\text{Var}(X) = \frac{\alpha\beta}{(\alpha+\beta)^2(\alpha+\beta+1)}$。

      $\alpha = \beta$ のとき $E[X] = 1/2$ で対称、$\alpha > \beta$ なら右寄り、$\alpha < \beta$ なら左寄りの分布になります。

      ベータ分布は二項分布のベイズ推定における共役事前分布として重要です。
    </div>
  </div>
</div>

---

## 問題 3：カイ二乗分布

<div class="quiz-container" data-quiz-id="dist-3" data-correct="c" data-difficulty="medium">
  <div class="quiz-question">
    $Z_1, Z_2, \ldots, Z_n$ が独立に標準正規分布 $N(0, 1)$ に従うとき、$\sum_{i=1}^n Z_i^2$ の分布はどれか。
  </div>
  <div class="quiz-options">
    <div class="quiz-option" data-value="a">
      <input type="radio" name="q3" id="q3a">
      <label for="q3a">$F_{n, n}$ 分布</label>
    </div>
    <div class="quiz-option" data-value="b">
      <input type="radio" name="q3" id="q3b">
      <label for="q3b">$t_n$ 分布</label>
    </div>
    <div class="quiz-option" data-value="c">
      <input type="radio" name="q3" id="q3c">
      <label for="q3c">$\chi^2_n$ 分布</label>
    </div>
    <div class="quiz-option" data-value="d">
      <input type="radio" name="q3" id="q3d">
      <label for="q3d">$\text{Gamma}(n, 1)$ 分布</label>
    </div>
  </div>
  <button class="quiz-btn" disabled>解答を確認</button>
  <div class="quiz-feedback">
    <span class="quiz-feedback-icon"></span>
    <strong>正解：(c)</strong>
    <div class="quiz-explanation">
      これはカイ二乗分布の定義そのものです。

      $\chi^2_n = \sum_{i=1}^n Z_i^2$ where $Z_i \sim N(0, 1)$ i.i.d.

      なお、$\chi^2_n = \text{Gamma}(n/2, 1/2)$ なので (d) は惜しいですが、パラメータが異なります。

      カイ二乗分布の期待値は $n$、分散は $2n$ です。
    </div>
  </div>
</div>

---

## 問題 4：中心極限定理

<div class="quiz-container" data-quiz-id="dist-4" data-correct="b" data-difficulty="hard">
  <div class="quiz-question">
    $X_1, X_2, \ldots, X_n$ が独立に期待値 $\mu$、分散 $\sigma^2$ の分布に従うとき、中心極限定理により $n \to \infty$ で分布収束するものはどれか。
  </div>
  <div class="quiz-options">
    <div class="quiz-option" data-value="a">
      <input type="radio" name="q4" id="q4a">
      <label for="q4a">$\bar{X}_n \xrightarrow{d} N(\mu, \sigma^2)$</label>
    </div>
    <div class="quiz-option" data-value="b">
      <input type="radio" name="q4" id="q4b">
      <label for="q4b">$\displaystyle \frac{\sqrt{n}(\bar{X}_n - \mu)}{\sigma} \xrightarrow{d} N(0, 1)$</label>
    </div>
    <div class="quiz-option" data-value="c">
      <input type="radio" name="q4" id="q4c">
      <label for="q4c">$\displaystyle \frac{\bar{X}_n - \mu}{\sigma} \xrightarrow{d} N(0, 1)$</label>
    </div>
    <div class="quiz-option" data-value="d">
      <input type="radio" name="q4" id="q4d">
      <label for="q4d">$n(\bar{X}_n - \mu) \xrightarrow{d} N(0, \sigma^2)$</label>
    </div>
  </div>
  <button class="quiz-btn" disabled>解答を確認</button>
  <div class="quiz-feedback">
    <span class="quiz-feedback-icon"></span>
    <strong>正解：(b)</strong>
    <div class="quiz-explanation">
      中心極限定理（CLT）：

      $$\frac{\sqrt{n}(\bar{X}_n - \mu)}{\sigma} = \frac{\sum X_i - n\mu}{\sigma\sqrt{n}} \xrightarrow{d} N(0, 1)$$

      (a) は誤り：$\bar{X}_n$ の分散は $\sigma^2/n$ で、$n \to \infty$ で 0 に収束します。

      (c) は誤り：$\sqrt{n}$ の正規化がないと発散します。

      (d) は誤り：$n$ での正規化は強すぎます。
    </div>
  </div>
</div>

---

## 問題 5：デルタ法

<div class="quiz-container" data-quiz-id="dist-5" data-correct="d" data-difficulty="medium">
  <div class="quiz-question">
    $\sqrt{n}(\hat{\theta}_n - \theta) \xrightarrow{d} N(0, \sigma^2)$ のとき、連続微分可能な関数 $g$ に対してデルタ法を適用すると、$\sqrt{n}(g(\hat{\theta}_n) - g(\theta))$ の漸近分散はどれか。
  </div>
  <div class="quiz-options">
    <div class="quiz-option" data-value="a">
      <input type="radio" name="q5" id="q5a">
      <label for="q5a">$\sigma^2$</label>
    </div>
    <div class="quiz-option" data-value="b">
      <input type="radio" name="q5" id="q5b">
      <label for="q5b">$g'(\theta) \cdot \sigma^2$</label>
    </div>
    <div class="quiz-option" data-value="c">
      <input type="radio" name="q5" id="q5c">
      <label for="q5c">$g(\sigma^2)$</label>
    </div>
    <div class="quiz-option" data-value="d">
      <input type="radio" name="q5" id="q5d">
      <label for="q5d">$[g'(\theta)]^2 \cdot \sigma^2$</label>
    </div>
  </div>
  <button class="quiz-btn" disabled>解答を確認</button>
  <div class="quiz-feedback">
    <span class="quiz-feedback-icon"></span>
    <strong>正解：(d)</strong>
    <div class="quiz-explanation">
      デルタ法：$g'(\theta) \neq 0$ のとき、

      $$\sqrt{n}(g(\hat{\theta}_n) - g(\theta)) \xrightarrow{d} N(0, [g'(\theta)]^2 \sigma^2)$$

      テイラー展開 $g(\hat{\theta}) \approx g(\theta) + g'(\theta)(\hat{\theta} - \theta)$ より、

      $\sqrt{n}(g(\hat{\theta}) - g(\theta)) \approx g'(\theta) \cdot \sqrt{n}(\hat{\theta} - \theta)$

      正規分布のスカラー倍は、分散が2乗倍されます。
    </div>
  </div>
</div>

---

## 問題 6：t分布

<div class="quiz-container" data-quiz-id="dist-6" data-correct="a" data-difficulty="easy">
  <div class="quiz-question">
    $Z \sim N(0,1)$ と $V \sim \chi^2_n$ が独立のとき、$T = \frac{Z}{\sqrt{V/n}}$ の分布はどれか。
  </div>
  <div class="quiz-options">
    <div class="quiz-option" data-value="a">
      <input type="radio" name="q6" id="q6a">
      <label for="q6a">自由度 $n$ の $t$ 分布</label>
    </div>
    <div class="quiz-option" data-value="b">
      <input type="radio" name="q6" id="q6b">
      <label for="q6b">自由度 $n-1$ の $t$ 分布</label>
    </div>
    <div class="quiz-option" data-value="c">
      <input type="radio" name="q6" id="q6c">
      <label for="q6c">標準正規分布</label>
    </div>
    <div class="quiz-option" data-value="d">
      <input type="radio" name="q6" id="q6d">
      <label for="q6d">$F_{1, n}$ 分布</label>
    </div>
  </div>
  <button class="quiz-btn" disabled>解答を確認</button>
  <div class="quiz-feedback">
    <span class="quiz-feedback-icon"></span>
    <strong>正解：(a)</strong>
    <div class="quiz-explanation">
      これは $t$ 分布の定義です。

      $$T = \frac{Z}{\sqrt{V/n}} \sim t_n$$

      $t$ 分布の特徴：
      - 期待値：$n > 1$ のとき 0
      - 分散：$n > 2$ のとき $\frac{n}{n-2}$
      - $n \to \infty$ で標準正規分布に収束

      なお、$T^2 \sim F_{1, n}$ なので (d) は $T^2$ の分布です。
    </div>
  </div>
</div>

---

## 問題 7：F分布

<div class="quiz-container" data-quiz-id="dist-7" data-correct="c" data-difficulty="medium">
  <div class="quiz-question">
    $U \sim \chi^2_m$、$V \sim \chi^2_n$ が独立のとき、$F = \frac{U/m}{V/n}$ について正しいものはどれか。
  </div>
  <div class="quiz-options">
    <div class="quiz-option" data-value="a">
      <input type="radio" name="q7" id="q7a">
      <label for="q7a">$E[F] = 1$（$n > 2$ のとき）</label>
    </div>
    <div class="quiz-option" data-value="b">
      <input type="radio" name="q7" id="q7b">
      <label for="q7b">$1/F \sim F_{m, n}$</label>
    </div>
    <div class="quiz-option" data-value="c">
      <input type="radio" name="q7" id="q7c">
      <label for="q7c">$E[F] = \frac{n}{n-2}$（$n > 2$ のとき）</label>
    </div>
    <div class="quiz-option" data-value="d">
      <input type="radio" name="q7" id="q7d">
      <label for="q7d">$F$ は負の値をとりうる</label>
    </div>
  </div>
  <button class="quiz-btn" disabled>解答を確認</button>
  <div class="quiz-feedback">
    <span class="quiz-feedback-icon"></span>
    <strong>正解：(c)</strong>
    <div class="quiz-explanation">
      $F_{m, n}$ 分布の性質：

      - 期待値：$n > 2$ のとき $E[F] = \frac{n}{n-2}$（1より少し大きい）
      - $F$ は常に正（カイ二乗の比なので）
      - $1/F \sim F_{n, m}$（分子分母の自由度が入れ替わる）

      (b) は惜しいですが、自由度が $F_{n, m}$ になります。

      $F$ 分布は分散分析や回帰分析の検定統計量として重要です。
    </div>
  </div>
</div>

---

## 問題 8：負の二項分布

<div class="quiz-container" data-quiz-id="dist-8" data-correct="b" data-difficulty="hard">
  <div class="quiz-question">
    成功確率 $p$ のベルヌーイ試行を繰り返し、$r$ 回成功するまでの失敗回数 $X$ が従う分布はどれか。
  </div>
  <div class="quiz-options">
    <div class="quiz-option" data-value="a">
      <input type="radio" name="q8" id="q8a">
      <label for="q8a">幾何分布</label>
    </div>
    <div class="quiz-option" data-value="b">
      <input type="radio" name="q8" id="q8b">
      <label for="q8b">負の二項分布</label>
    </div>
    <div class="quiz-option" data-value="c">
      <input type="radio" name="q8" id="q8c">
      <label for="q8c">二項分布</label>
    </div>
    <div class="quiz-option" data-value="d">
      <input type="radio" name="q8" id="q8d">
      <label for="q8d">超幾何分布</label>
    </div>
  </div>
  <button class="quiz-btn" disabled>解答を確認</button>
  <div class="quiz-feedback">
    <span class="quiz-feedback-icon"></span>
    <strong>正解：(b)</strong>
    <div class="quiz-explanation">
      負の二項分布 $\text{NB}(r, p)$：

      $$P(X = k) = \binom{k+r-1}{k} p^r (1-p)^k, \quad k = 0, 1, 2, \ldots$$

      - 期待値：$E[X] = \frac{r(1-p)}{p}$
      - 分散：$\text{Var}(X) = \frac{r(1-p)}{p^2}$

      特殊ケース：
      - $r = 1$：幾何分布
      - 二項分布は「$n$ 回中の成功数」、負の二項分布は「$r$ 回成功までの失敗数」

      過分散（分散 > 期待値）のカウントデータのモデリングに使われます。
    </div>
  </div>
</div>

---

## 問題 9：順序統計量

<div class="quiz-container" data-quiz-id="dist-9" data-correct="d" data-difficulty="hard">
  <div class="quiz-question">
    $X_1, \ldots, X_n$ が一様分布 $U(0, 1)$ からの i.i.d. 標本のとき、最大値 $X_{(n)}$ の期待値はどれか。
  </div>
  <div class="quiz-options">
    <div class="quiz-option" data-value="a">
      <input type="radio" name="q9" id="q9a">
      <label for="q9a">$\displaystyle \frac{1}{2}$</label>
    </div>
    <div class="quiz-option" data-value="b">
      <input type="radio" name="q9" id="q9b">
      <label for="q9b">$\displaystyle \frac{1}{n}$</label>
    </div>
    <div class="quiz-option" data-value="c">
      <input type="radio" name="q9" id="q9c">
      <label for="q9c">$\displaystyle 1 - \frac{1}{n}$</label>
    </div>
    <div class="quiz-option" data-value="d">
      <input type="radio" name="q9" id="q9d">
      <label for="q9d">$\displaystyle \frac{n}{n+1}$</label>
    </div>
  </div>
  <button class="quiz-btn" disabled>解答を確認</button>
  <div class="quiz-feedback">
    <span class="quiz-feedback-icon"></span>
    <strong>正解：(d)</strong>
    <div class="quiz-explanation">
      $U(0,1)$ の順序統計量 $X_{(k)}$ は $\text{Beta}(k, n-k+1)$ に従います。

      最大値 $X_{(n)} \sim \text{Beta}(n, 1)$ なので：

      $$E[X_{(n)}] = \frac{n}{n+1}$$

      同様に、最小値 $X_{(1)} \sim \text{Beta}(1, n)$ なので：

      $$E[X_{(1)}] = \frac{1}{n+1}$$

      一般に、$k$ 番目の順序統計量 $E[X_{(k)}] = \frac{k}{n+1}$。
    </div>
  </div>
</div>

---

## 問題 10：多変量正規分布

<div class="quiz-container" data-quiz-id="dist-10" data-correct="a" data-difficulty="hard">
  <div class="quiz-question">
    $(X, Y)^\top$ が二変量正規分布に従い、$\text{Cov}(X, Y) = 0$ のとき、正しいものはどれか。
  </div>
  <div class="quiz-options">
    <div class="quiz-option" data-value="a">
      <input type="radio" name="q10" id="q10a">
      <label for="q10a">$X$ と $Y$ は独立である</label>
    </div>
    <div class="quiz-option" data-value="b">
      <input type="radio" name="q10" id="q10b">
      <label for="q10b">$X + Y$ は正規分布に従わない</label>
    </div>
    <div class="quiz-option" data-value="c">
      <input type="radio" name="q10" id="q10c">
      <label for="q10c">$X$ と $Y$ の相関係数は 1 である</label>
    </div>
    <div class="quiz-option" data-value="d">
      <input type="radio" name="q10" id="q10d">
      <label for="q10d">$X$ の周辺分布は正規分布に従わない</label>
    </div>
  </div>
  <button class="quiz-btn" disabled>解答を確認</button>
  <div class="quiz-feedback">
    <span class="quiz-feedback-icon"></span>
    <strong>正解：(a)</strong>
    <div class="quiz-explanation">
      多変量正規分布の重要な性質：

      **無相関 ⇔ 独立**（多変量正規分布の場合のみ）

      一般の分布では「無相関 ⇏ 独立」ですが、多変量正規分布では同値になります。

      その他の性質：
      - 周辺分布は正規分布
      - 線形結合も正規分布
      - 条件付き分布も正規分布

      $(X, Y) \sim N_2(\boldsymbol{\mu}, \boldsymbol{\Sigma})$ で $\boldsymbol{\Sigma}$ が対角なら独立。
    </div>
  </div>
</div>

---

## 関連コンテンツ

- [理論編：離散型分布]({{ site.baseurl }}/semi-1/2-distributions/discrete/)
- [理論編：連続型分布]({{ site.baseurl }}/semi-1/2-distributions/continuous/)
- [理論編：極限定理]({{ site.baseurl }}/semi-1/2-distributions/limit-theorems/)
- [確率論の問題]({{ site.baseurl }}/semi-1/problems/probability/)

---

[問題一覧に戻る]({{ site.baseurl }}/semi-1/problems/) | [準1級トップ]({{ site.baseurl }}/semi-1/)
