---
layout: default
title: 確率論の問題 - 準1級対策
description: 条件付き確率、ベイズの定理、母関数、積率の選択式問題
permalink: /semi-1/problems/probability/
---

# 確率論の問題

条件付き確率、ベイズの定理、母関数、積率と特性値に関する問題です。

<div class="quiz-progress">
  <span class="quiz-progress-text">0 / 10 正解</span>
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

## 問題 6：チェビシェフの不等式

<div class="quiz-container" data-quiz-id="prob-6" data-correct="b">
  <div class="quiz-question">
    確率変数 $X$ の平均が $\mu$、分散が $\sigma^2$ のとき、チェビシェフの不等式 $P(|X - \mu| \geq k\sigma) \leq ?$ の右辺はどれか。
  </div>
  <div class="quiz-options">
    <div class="quiz-option" data-value="a">
      <input type="radio" name="q6" id="q6a">
      <label for="q6a">$k$</label>
    </div>
    <div class="quiz-option" data-value="b">
      <input type="radio" name="q6" id="q6b">
      <label for="q6b">$\displaystyle \frac{1}{k^2}$</label>
    </div>
    <div class="quiz-option" data-value="c">
      <input type="radio" name="q6" id="q6c">
      <label for="q6c">$\displaystyle \frac{1}{k}$</label>
    </div>
    <div class="quiz-option" data-value="d">
      <input type="radio" name="q6" id="q6d">
      <label for="q6d">$\displaystyle \frac{\sigma^2}{k^2}$</label>
    </div>
  </div>
  <button class="quiz-btn" disabled>解答を確認</button>
  <div class="quiz-feedback">
    <span class="quiz-feedback-icon"></span>
    <strong>正解：(b)</strong>
    <div class="quiz-explanation">
      チェビシェフの不等式：任意の $k > 0$ に対して

      $$P(|X - \mu| \geq k\sigma) \leq \frac{1}{k^2}$$

      例えば $k = 2$ のとき、平均から2標準偏差以上離れる確率は最大でも 25%。

      この不等式は分布の形を仮定せずに成り立ち、大数の法則の証明にも使われます。

      関連：マルコフの不等式 $P(X \geq a) \leq \frac{E[X]}{a}$（$X \geq 0$、$a > 0$）
    </div>
  </div>
</div>

---

## 問題 7：条件付き期待値

<div class="quiz-container" data-quiz-id="prob-7" data-correct="a">
  <div class="quiz-question">
    確率変数 $X$, $Y$ に対して、全期待値の法則（law of total expectation）の正しい表現はどれか。
  </div>
  <div class="quiz-options">
    <div class="quiz-option" data-value="a">
      <input type="radio" name="q7" id="q7a">
      <label for="q7a">$E[X] = E[E[X \mid Y]]$</label>
    </div>
    <div class="quiz-option" data-value="b">
      <input type="radio" name="q7" id="q7b">
      <label for="q7b">$E[X] = E[X \mid E[Y]]$</label>
    </div>
    <div class="quiz-option" data-value="c">
      <input type="radio" name="q7" id="q7c">
      <label for="q7c">$E[X \mid Y] = E[X] \cdot E[Y]$</label>
    </div>
    <div class="quiz-option" data-value="d">
      <input type="radio" name="q7" id="q7d">
      <label for="q7d">$E[X] = E[Y \mid X]$</label>
    </div>
  </div>
  <button class="quiz-btn" disabled>解答を確認</button>
  <div class="quiz-feedback">
    <span class="quiz-feedback-icon"></span>
    <strong>正解：(a)</strong>
    <div class="quiz-explanation">
      全期待値の法則（繰り返し期待値の法則）：

      $$E[X] = E[E[X \mid Y]] = E_Y[E[X \mid Y]]$$

      つまり「$Y$ で条件付けた $X$ の期待値」の期待値は、$X$ の（無条件の）期待値に等しい。

      離散の場合：$E[X] = \sum_y E[X \mid Y = y] \cdot P(Y = y)$

      全分散の法則も重要：$\text{Var}(X) = E[\text{Var}(X \mid Y)] + \text{Var}(E[X \mid Y])$
    </div>
  </div>
</div>

---

## 問題 8：共分散と相関係数

<div class="quiz-container" data-quiz-id="prob-8" data-correct="c">
  <div class="quiz-question">
    $X$ と $Y$ の共分散 $\text{Cov}(X, Y) = 0$ のとき、必ず成り立つものはどれか。
  </div>
  <div class="quiz-options">
    <div class="quiz-option" data-value="a">
      <input type="radio" name="q8" id="q8a">
      <label for="q8a">$X$ と $Y$ は独立である</label>
    </div>
    <div class="quiz-option" data-value="b">
      <input type="radio" name="q8" id="q8b">
      <label for="q8b">$P(X = Y) = 0$</label>
    </div>
    <div class="quiz-option" data-value="c">
      <input type="radio" name="q8" id="q8c">
      <label for="q8c">$\text{Var}(X + Y) = \text{Var}(X) + \text{Var}(Y)$</label>
    </div>
    <div class="quiz-option" data-value="d">
      <input type="radio" name="q8" id="q8d">
      <label for="q8d">$E[XY] = 0$</label>
    </div>
  </div>
  <button class="quiz-btn" disabled>解答を確認</button>
  <div class="quiz-feedback">
    <span class="quiz-feedback-icon"></span>
    <strong>正解：(c)</strong>
    <div class="quiz-explanation">
      分散の加法性：

      $$\text{Var}(X + Y) = \text{Var}(X) + \text{Var}(Y) + 2\text{Cov}(X, Y)$$

      $\text{Cov}(X, Y) = 0$（無相関）のとき、分散は単純に足し算できます。

      注意：
      - 無相関 ⇏ 独立（反例：$X \sim N(0,1)$、$Y = X^2$ は無相関だが従属）
      - 独立 ⇒ 無相関（逆は一般に成り立たない）
      - $E[XY] = E[X]E[Y] + \text{Cov}(X, Y)$ なので、(d) は $E[X]E[Y] = 0$ のときのみ成立
    </div>
  </div>
</div>

---

## 問題 9：イェンセンの不等式

<div class="quiz-container" data-quiz-id="prob-9" data-correct="d">
  <div class="quiz-question">
    凸関数 $g$ と確率変数 $X$ に対するイェンセンの不等式として正しいものはどれか。
  </div>
  <div class="quiz-options">
    <div class="quiz-option" data-value="a">
      <input type="radio" name="q9" id="q9a">
      <label for="q9a">$g(E[X]) \geq E[g(X)]$</label>
    </div>
    <div class="quiz-option" data-value="b">
      <input type="radio" name="q9" id="q9b">
      <label for="q9b">$E[g(X)] = g(E[X])$</label>
    </div>
    <div class="quiz-option" data-value="c">
      <input type="radio" name="q9" id="q9c">
      <label for="q9c">$\text{Var}(g(X)) \leq g(\text{Var}(X))$</label>
    </div>
    <div class="quiz-option" data-value="d">
      <input type="radio" name="q9" id="q9d">
      <label for="q9d">$E[g(X)] \geq g(E[X])$</label>
    </div>
  </div>
  <button class="quiz-btn" disabled>解答を確認</button>
  <div class="quiz-feedback">
    <span class="quiz-feedback-icon"></span>
    <strong>正解：(d)</strong>
    <div class="quiz-explanation">
      イェンセンの不等式：$g$ が凸関数のとき

      $$E[g(X)] \geq g(E[X])$$

      凹関数の場合は不等号が逆転します。

      応用例：
      - $g(x) = x^2$（凸）：$E[X^2] \geq (E[X])^2$ → $\text{Var}(X) \geq 0$
      - $g(x) = -\log x$（凸）：$E[-\log X] \geq -\log E[X]$
      - $g(x) = e^x$（凸）：$E[e^X] \geq e^{E[X]}$

      KLダイバージェンスの非負性の証明などに使われます。
    </div>
  </div>
</div>

---

## 問題 10：確率母関数

<div class="quiz-container" data-quiz-id="prob-10" data-correct="b">
  <div class="quiz-question">
    非負整数値をとる確率変数 $X$ の確率母関数（PGF）$G_X(s) = E[s^X]$ について、$X \sim \text{Poisson}(\lambda)$ のとき $G_X(s)$ はどれか。
  </div>
  <div class="quiz-options">
    <div class="quiz-option" data-value="a">
      <input type="radio" name="q10" id="q10a">
      <label for="q10a">$\displaystyle \frac{\lambda}{1 - s}$</label>
    </div>
    <div class="quiz-option" data-value="b">
      <input type="radio" name="q10" id="q10b">
      <label for="q10b">$e^{\lambda(s-1)}$</label>
    </div>
    <div class="quiz-option" data-value="c">
      <input type="radio" name="q10" id="q10c">
      <label for="q10c">$(1 - p + ps)^n$</label>
    </div>
    <div class="quiz-option" data-value="d">
      <input type="radio" name="q10" id="q10d">
      <label for="q10d">$\displaystyle \frac{p}{1 - (1-p)s}$</label>
    </div>
  </div>
  <button class="quiz-btn" disabled>解答を確認</button>
  <div class="quiz-feedback">
    <span class="quiz-feedback-icon"></span>
    <strong>正解：(b)</strong>
    <div class="quiz-explanation">
      ポアソン分布の PGF：

      $$G_X(s) = E[s^X] = \sum_{k=0}^{\infty} s^k \frac{\lambda^k e^{-\lambda}}{k!} = e^{-\lambda} \sum_{k=0}^{\infty} \frac{(\lambda s)^k}{k!} = e^{-\lambda} e^{\lambda s} = e^{\lambda(s-1)}$$

      各選択肢の PGF：
      - (a)：これは有効な PGF ではない
      - (c)：二項分布 $\text{Bin}(n, p)$
      - (d)：幾何分布 $\text{Geom}(p)$

      PGF の性質：$G'_X(1) = E[X]$、$G''_X(1) = E[X(X-1)]$
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
