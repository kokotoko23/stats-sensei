---
layout: default
title: 確率分布の問題 - 準1級対策
description: 離散分布、連続分布、極限定理の選択式問題
permalink: /semi-1/problems/distributions/
---

# 確率分布の問題

離散型分布、連続型分布、極限定理に関する問題です。

<div class="quiz-progress">
  <span class="quiz-progress-text">0 / 5 正解</span>
  <div class="quiz-progress-bar">
    <div class="quiz-progress-fill" style="width: 0%"></div>
  </div>
</div>

---

## 問題 1：ガンマ分布

<div class="quiz-container" data-quiz-id="dist-1" data-correct="b">
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

<div class="quiz-container" data-quiz-id="dist-2" data-correct="a">
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

<div class="quiz-container" data-quiz-id="dist-3" data-correct="c">
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

<div class="quiz-container" data-quiz-id="dist-4" data-correct="b">
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

<div class="quiz-container" data-quiz-id="dist-5" data-correct="d">
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

## 関連コンテンツ

- [理論編：離散型分布]({{ site.baseurl }}/semi-1/2-distributions/discrete/)
- [理論編：連続型分布]({{ site.baseurl }}/semi-1/2-distributions/continuous/)
- [理論編：極限定理]({{ site.baseurl }}/semi-1/2-distributions/limit-theorems/)
- [確率論の問題]({{ site.baseurl }}/semi-1/problems/probability/)

---

[問題一覧に戻る]({{ site.baseurl }}/semi-1/problems/) | [準1級トップ]({{ site.baseurl }}/semi-1/)
