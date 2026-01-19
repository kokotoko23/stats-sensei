---
layout: default
title: 確率論の問題 - 準1級対策
description: 条件付き確率、ベイズの定理、母関数、積率の選択式問題
permalink: /semi-1/problems/probability/
---

# 確率論の問題

条件付き確率、ベイズの定理、母関数、積率と特性値に関する問題です。

<div class="quiz-progress">
  <span class="quiz-progress-text">0 / 5 正解</span>
  <div class="quiz-progress-bar">
    <div class="quiz-progress-fill" style="width: 0%"></div>
  </div>
</div>

---

## 問題 1：条件付き確率

<div class="quiz-container" data-quiz-id="prob-1" data-correct="c">
  <div class="quiz-question">
    事象 $A$ と $B$ が独立であるとき、$P(A \cup B)$ を $P(A) = p$、$P(B) = q$ を用いて表すとどれか。
  </div>
  <div class="quiz-options">
    <div class="quiz-option" data-value="a">
      <input type="radio" name="q1" id="q1a">
      <label for="q1a">$p + q$</label>
    </div>
    <div class="quiz-option" data-value="b">
      <input type="radio" name="q1" id="q1b">
      <label for="q1b">$pq$</label>
    </div>
    <div class="quiz-option" data-value="c">
      <input type="radio" name="q1" id="q1c">
      <label for="q1c">$p + q - pq$</label>
    </div>
    <div class="quiz-option" data-value="d">
      <input type="radio" name="q1" id="q1d">
      <label for="q1d">$1 - (1-p)(1-q)$</label>
    </div>
  </div>
  <button class="quiz-btn" disabled>解答を確認</button>
  <div class="quiz-feedback">
    <span class="quiz-feedback-icon"></span>
    <strong>正解：(c)（(d)も同値）</strong>
    <div class="quiz-explanation">
      加法定理より $P(A \cup B) = P(A) + P(B) - P(A \cap B)$。

      $A$ と $B$ が独立なので $P(A \cap B) = P(A)P(B) = pq$。

      したがって $P(A \cup B) = p + q - pq$。

      なお、(d) の $1 - (1-p)(1-q) = 1 - 1 + p + q - pq = p + q - pq$ なので (c) と同値です。
    </div>
  </div>
</div>

---

## 問題 2：ベイズの定理

<div class="quiz-container" data-quiz-id="prob-2" data-correct="b">
  <div class="quiz-question">
    ある病気の有病率は1%である。検査の感度（病気の人が陽性になる確率）は95%、特異度（健康な人が陰性になる確率）は90%である。陽性と判定された人が実際に病気である確率に最も近いものはどれか。
  </div>
  <div class="quiz-options">
    <div class="quiz-option" data-value="a">
      <input type="radio" name="q2" id="q2a">
      <label for="q2a">約 5%</label>
    </div>
    <div class="quiz-option" data-value="b">
      <input type="radio" name="q2" id="q2b">
      <label for="q2b">約 9%</label>
    </div>
    <div class="quiz-option" data-value="c">
      <input type="radio" name="q2" id="q2c">
      <label for="q2c">約 50%</label>
    </div>
    <div class="quiz-option" data-value="d">
      <input type="radio" name="q2" id="q2d">
      <label for="q2d">約 95%</label>
    </div>
  </div>
  <button class="quiz-btn" disabled>解答を確認</button>
  <div class="quiz-feedback">
    <span class="quiz-feedback-icon"></span>
    <strong>正解：(b)</strong>
    <div class="quiz-explanation">
      ベイズの定理より：

      $$P(\text{病気} \mid \text{陽性}) = \frac{P(\text{陽性} \mid \text{病気}) \cdot P(\text{病気})}{P(\text{陽性})}$$

      $P(\text{陽性}) = 0.95 \times 0.01 + 0.10 \times 0.99 = 0.0095 + 0.099 = 0.1085$

      $P(\text{病気} \mid \text{陽性}) = \frac{0.95 \times 0.01}{0.1085} = \frac{0.0095}{0.1085} \approx 0.088 \approx 9\%$

      有病率が低いと、陽性でも実際に病気である確率は低くなります（偽陽性の影響）。
    </div>
  </div>
</div>

---

## 問題 3：積率母関数

<div class="quiz-container" data-quiz-id="prob-3" data-correct="a">
  <div class="quiz-question">
    確率変数 $X$ の積率母関数（MGF）が $M_X(t) = e^{3t + 2t^2}$ のとき、$E[X]$ と $\text{Var}(X)$ の値はどれか。
  </div>
  <div class="quiz-options">
    <div class="quiz-option" data-value="a">
      <input type="radio" name="q3" id="q3a">
      <label for="q3a">$E[X] = 3$、$\text{Var}(X) = 4$</label>
    </div>
    <div class="quiz-option" data-value="b">
      <input type="radio" name="q3" id="q3b">
      <label for="q3b">$E[X] = 3$、$\text{Var}(X) = 2$</label>
    </div>
    <div class="quiz-option" data-value="c">
      <input type="radio" name="q3" id="q3c">
      <label for="q3c">$E[X] = 2$、$\text{Var}(X) = 3$</label>
    </div>
    <div class="quiz-option" data-value="d">
      <input type="radio" name="q3" id="q3d">
      <label for="q3d">$E[X] = 5$、$\text{Var}(X) = 4$</label>
    </div>
  </div>
  <button class="quiz-btn" disabled>解答を確認</button>
  <div class="quiz-feedback">
    <span class="quiz-feedback-icon"></span>
    <strong>正解：(a)</strong>
    <div class="quiz-explanation">
      MGFの形 $e^{\mu t + \frac{\sigma^2 t^2}{2}}$ は正規分布 $N(\mu, \sigma^2)$ のMGFです。

      $M_X(t) = e^{3t + 2t^2} = e^{3t + \frac{4t^2}{2}}$ より、

      $\mu = 3$、$\sigma^2 = 4$。

      したがって $E[X] = 3$、$\text{Var}(X) = 4$。

      別解：$E[X] = M'_X(0) = 3$、$E[X^2] = M''_X(0) = 13$、$\text{Var}(X) = 13 - 9 = 4$。
    </div>
  </div>
</div>

---

## 問題 4：歪度と尖度

<div class="quiz-container" data-quiz-id="prob-4" data-correct="d">
  <div class="quiz-question">
    標準正規分布の歪度（skewness）と尖度（kurtosis）の値はどれか。ただし、尖度は超過尖度（excess kurtosis）とする。
  </div>
  <div class="quiz-options">
    <div class="quiz-option" data-value="a">
      <input type="radio" name="q4" id="q4a">
      <label for="q4a">歪度 = 1、尖度 = 3</label>
    </div>
    <div class="quiz-option" data-value="b">
      <input type="radio" name="q4" id="q4b">
      <label for="q4b">歪度 = 0、尖度 = 3</label>
    </div>
    <div class="quiz-option" data-value="c">
      <input type="radio" name="q4" id="q4c">
      <label for="q4c">歪度 = 1、尖度 = 0</label>
    </div>
    <div class="quiz-option" data-value="d">
      <input type="radio" name="q4" id="q4d">
      <label for="q4d">歪度 = 0、尖度 = 0</label>
    </div>
  </div>
  <button class="quiz-btn" disabled>解答を確認</button>
  <div class="quiz-feedback">
    <span class="quiz-feedback-icon"></span>
    <strong>正解：(d)</strong>
    <div class="quiz-explanation">
      正規分布は左右対称なので歪度 = 0。

      正規分布の尖度（非超過）は 3 ですが、超過尖度（excess kurtosis）は「尖度 - 3」で定義されるため 0 になります。

      超過尖度が正なら正規分布より裾が重い（leptokurtic）、負なら裾が軽い（platykurtic）ことを意味します。
    </div>
  </div>
</div>

---

## 問題 5：変数変換

<div class="quiz-container" data-quiz-id="prob-5" data-correct="c">
  <div class="quiz-question">
    $X \sim \text{Exp}(1)$（平均1の指数分布）のとき、$Y = -\log X$ の分布はどれか。
  </div>
  <div class="quiz-options">
    <div class="quiz-option" data-value="a">
      <input type="radio" name="q5" id="q5a">
      <label for="q5a">指数分布 $\text{Exp}(1)$</label>
    </div>
    <div class="quiz-option" data-value="b">
      <input type="radio" name="q5" id="q5b">
      <label for="q5b">標準正規分布 $N(0, 1)$</label>
    </div>
    <div class="quiz-option" data-value="c">
      <input type="radio" name="q5" id="q5c">
      <label for="q5c">標準ガンベル分布（極値分布）</label>
    </div>
    <div class="quiz-option" data-value="d">
      <input type="radio" name="q5" id="q5d">
      <label for="q5d">一様分布 $U(0, 1)$</label>
    </div>
  </div>
  <button class="quiz-btn" disabled>解答を確認</button>
  <div class="quiz-feedback">
    <span class="quiz-feedback-icon"></span>
    <strong>正解：(c)</strong>
    <div class="quiz-explanation">
      $X \sim \text{Exp}(1)$ のとき、$F_X(x) = 1 - e^{-x}$。

      $Y = -\log X$ より $X = e^{-Y}$。ヤコビアンは $\left\lvert\frac{dx}{dy}\right\rvert = e^{-y}$。

      $f_Y(y) = f_X(e^{-y}) \cdot e^{-y} = e^{-e^{-y}} \cdot e^{-y} = \exp(-y - e^{-y})$

      これは標準ガンベル分布（タイプI極値分布）の密度関数です。

      極値分布は最大値・最小値の漸近分布として重要です。
    </div>
  </div>
</div>

---

## 関連コンテンツ

- [理論編：確率の基礎]({{ site.baseurl }}/semi-1/1-probability/fundamentals/)
- [理論編：母関数]({{ site.baseurl }}/semi-1/1-probability/generating-functions/)
- [理論編：積率と特性値]({{ site.baseurl }}/semi-1/1-probability/moments/)
- [確率分布の問題]({{ site.baseurl }}/semi-1/problems/distributions/)

---

[問題一覧に戻る]({{ site.baseurl }}/semi-1/problems/) | [準1級トップ]({{ site.baseurl }}/semi-1/)
