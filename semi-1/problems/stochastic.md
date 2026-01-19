---
layout: default
title: 確率過程の問題 - 準1級対策
description: マルコフ連鎖、ポアソン過程の選択式問題
permalink: /semi-1/problems/stochastic/
---

# 確率過程の問題

マルコフ連鎖、ポアソン過程、ブラウン運動に関する問題です。

<div class="quiz-progress">
  <span class="quiz-progress-text">0 / 5 正解</span>
  <div class="quiz-progress-bar">
    <div class="quiz-progress-fill" style="width: 0%"></div>
  </div>
</div>

---

## 問題 1：マルコフ連鎖の定義

<div class="quiz-container" data-quiz-id="stoch-1" data-correct="c">
  <div class="quiz-question">
    マルコフ連鎖の「マルコフ性」を正しく表しているものはどれか。
  </div>
  <div class="quiz-options">
    <div class="quiz-option" data-value="a">
      <input type="radio" name="q1" id="q1a">
      <label for="q1a">$P(X_{n+1} = j) = P(X_n = j)$</label>
    </div>
    <div class="quiz-option" data-value="b">
      <input type="radio" name="q1" id="q1b">
      <label for="q1b">$P(X_{n+1} = j \mid X_0, \ldots, X_n) = P(X_{n+1} = j)$</label>
    </div>
    <div class="quiz-option" data-value="c">
      <input type="radio" name="q1" id="q1c">
      <label for="q1c">$P(X_{n+1} = j \mid X_0, \ldots, X_n) = P(X_{n+1} = j \mid X_n)$</label>
    </div>
    <div class="quiz-option" data-value="d">
      <input type="radio" name="q1" id="q1d">
      <label for="q1d">$P(X_{n+1} = j \mid X_n = i) = P(X_1 = j \mid X_0 = i)$</label>
    </div>
  </div>
  <button class="quiz-btn" disabled>解答を確認</button>
  <div class="quiz-feedback">
    <span class="quiz-feedback-icon"></span>
    <strong>正解：(c)</strong>
    <div class="quiz-explanation">
      マルコフ性（無記憶性）：「未来は現在のみに依存し、過去には依存しない」

      $P(X_{n+1} = j \mid X_0, X_1, \ldots, X_n) = P(X_{n+1} = j \mid X_n)$

      (d) は時間的定常性（time-homogeneity）を表しており、マルコフ性とは異なります。
    </div>
  </div>
</div>

---

## 問題 2：推移確率行列

<div class="quiz-container" data-quiz-id="stoch-2" data-correct="a">
  <div class="quiz-question">
    2状態のマルコフ連鎖で、推移確率行列が $P = \begin{pmatrix} 0.7 & 0.3 \\ 0.4 & 0.6 \end{pmatrix}$ のとき、定常分布 $\boldsymbol{\pi} = (\pi_1, \pi_2)$ はどれか。
  </div>
  <div class="quiz-options">
    <div class="quiz-option" data-value="a">
      <input type="radio" name="q2" id="q2a">
      <label for="q2a">$\displaystyle \left(\frac{4}{7}, \frac{3}{7}\right)$</label>
    </div>
    <div class="quiz-option" data-value="b">
      <input type="radio" name="q2" id="q2b">
      <label for="q2b">$\displaystyle \left(\frac{3}{7}, \frac{4}{7}\right)$</label>
    </div>
    <div class="quiz-option" data-value="c">
      <input type="radio" name="q2" id="q2c">
      <label for="q2c">$\displaystyle \left(\frac{1}{2}, \frac{1}{2}\right)$</label>
    </div>
    <div class="quiz-option" data-value="d">
      <input type="radio" name="q2" id="q2d">
      <label for="q2d">$\displaystyle \left(\frac{7}{10}, \frac{3}{10}\right)$</label>
    </div>
  </div>
  <button class="quiz-btn" disabled>解答を確認</button>
  <div class="quiz-feedback">
    <span class="quiz-feedback-icon"></span>
    <strong>正解：(a)</strong>
    <div class="quiz-explanation">
      定常分布は $\boldsymbol{\pi} P = \boldsymbol{\pi}$、$\pi_1 + \pi_2 = 1$ を満たします。

      $\pi_1 = 0.7\pi_1 + 0.4\pi_2$
      $\pi_2 = 0.3\pi_1 + 0.6\pi_2$

      第1式より：$0.3\pi_1 = 0.4\pi_2$、つまり $\pi_1 = \frac{4}{3}\pi_2$

      $\pi_1 + \pi_2 = 1$ と合わせて：$\frac{4}{3}\pi_2 + \pi_2 = 1$

      $\pi_2 = \frac{3}{7}$、$\pi_1 = \frac{4}{7}$
    </div>
  </div>
</div>

---

## 問題 3：ポアソン過程

<div class="quiz-container" data-quiz-id="stoch-3" data-correct="b">
  <div class="quiz-question">
    強度 $\lambda$ のポアソン過程 $\{N(t)\}$ において、$N(t)$ の分布と $N(s+t) - N(s)$（時刻 $s$ から $s+t$ までの事象数）の分布について正しいものはどれか。
  </div>
  <div class="quiz-options">
    <div class="quiz-option" data-value="a">
      <input type="radio" name="q3" id="q3a">
      <label for="q3a">$N(t) \sim \text{Poi}(\lambda)$、$N(s+t) - N(s) \sim \text{Poi}(\lambda)$</label>
    </div>
    <div class="quiz-option" data-value="b">
      <input type="radio" name="q3" id="q3b">
      <label for="q3b">$N(t) \sim \text{Poi}(\lambda t)$、$N(s+t) - N(s) \sim \text{Poi}(\lambda t)$</label>
    </div>
    <div class="quiz-option" data-value="c">
      <input type="radio" name="q3" id="q3c">
      <label for="q3c">$N(t) \sim \text{Poi}(\lambda t)$、$N(s+t) - N(s) \sim \text{Poi}(\lambda s)$</label>
    </div>
    <div class="quiz-option" data-value="d">
      <input type="radio" name="q3" id="q3d">
      <label for="q3d">$N(t) \sim \text{Exp}(\lambda t)$、$N(s+t) - N(s) \sim \text{Exp}(\lambda t)$</label>
    </div>
  </div>
  <button class="quiz-btn" disabled>解答を確認</button>
  <div class="quiz-feedback">
    <span class="quiz-feedback-icon"></span>
    <strong>正解：(b)</strong>
    <div class="quiz-explanation">
      ポアソン過程の性質：

      1. $N(t) \sim \text{Poi}(\lambda t)$（時刻 $t$ までの事象数）

      2. 独立増分性：$N(s+t) - N(s)$ は $N(s)$ と独立

      3. 定常増分性：$N(s+t) - N(s) \sim \text{Poi}(\lambda t)$（長さ $t$ の区間での事象数は開始時刻 $s$ によらない）

      パラメータは「期間の長さ」に比例します。
    </div>
  </div>
</div>

---

## 問題 4：到着間隔

<div class="quiz-container" data-quiz-id="stoch-4" data-correct="d">
  <div class="quiz-question">
    強度 $\lambda$ のポアソン過程において、連続する事象間の時間間隔（到着間隔）$T$ の分布はどれか。
  </div>
  <div class="quiz-options">
    <div class="quiz-option" data-value="a">
      <input type="radio" name="q4" id="q4a">
      <label for="q4a">ポアソン分布 $\text{Poi}(\lambda)$</label>
    </div>
    <div class="quiz-option" data-value="b">
      <input type="radio" name="q4" id="q4b">
      <label for="q4b">ガンマ分布 $\text{Gamma}(2, \lambda)$</label>
    </div>
    <div class="quiz-option" data-value="c">
      <input type="radio" name="q4" id="q4c">
      <label for="q4c">一様分布 $U(0, 1/\lambda)$</label>
    </div>
    <div class="quiz-option" data-value="d">
      <input type="radio" name="q4" id="q4d">
      <label for="q4d">指数分布 $\text{Exp}(\lambda)$</label>
    </div>
  </div>
  <button class="quiz-btn" disabled>解答を確認</button>
  <div class="quiz-feedback">
    <span class="quiz-feedback-icon"></span>
    <strong>正解：(d)</strong>
    <div class="quiz-explanation">
      ポアソン過程と指数分布の関係：

      - 到着間隔 $T_i \sim \text{Exp}(\lambda)$（独立同分布）
      - $n$ 番目の事象までの待ち時間 $S_n = \sum_{i=1}^n T_i \sim \text{Gamma}(n, \lambda)$

      指数分布の無記憶性：$P(T > s + t \mid T > s) = P(T > t)$

      これがポアソン過程のマルコフ性の基礎になっています。
    </div>
  </div>
</div>

---

## 問題 5：エルゴード性

<div class="quiz-container" data-quiz-id="stoch-5" data-correct="c">
  <div class="quiz-question">
    有限状態のマルコフ連鎖がエルゴード的（ergodic）であるための条件として<strong>正しいもの</strong>はどれか。
  </div>
  <div class="quiz-options">
    <div class="quiz-option" data-value="a">
      <input type="radio" name="q5" id="q5a">
      <label for="q5a">すべての推移確率が正である</label>
    </div>
    <div class="quiz-option" data-value="b">
      <input type="radio" name="q5" id="q5b">
      <label for="q5b">可約（reducible）である</label>
    </div>
    <div class="quiz-option" data-value="c">
      <input type="radio" name="q5" id="q5c">
      <label for="q5c">既約（irreducible）かつ非周期的（aperiodic）である</label>
    </div>
    <div class="quiz-option" data-value="d">
      <input type="radio" name="q5" id="q5d">
      <label for="q5d">周期的（periodic）である</label>
    </div>
  </div>
  <button class="quiz-btn" disabled>解答を確認</button>
  <div class="quiz-feedback">
    <span class="quiz-feedback-icon"></span>
    <strong>正解：(c)</strong>
    <div class="quiz-explanation">
      有限状態マルコフ連鎖がエルゴード的であるための条件：

      1. **既約（irreducible）**：任意の状態から任意の状態へ到達可能
      2. **非周期的（aperiodic）**：周期が1（自己ループがあるか、奇数・偶数のサイクルが混在）

      エルゴード的なら、初期分布によらず定常分布に収束し、時間平均と空間平均が一致します。

      (a) は十分条件ですが、必要条件ではありません。
    </div>
  </div>
</div>

---

## 関連コンテンツ

- [理論編：マルコフ連鎖]({{ site.baseurl }}/semi-1/4-stochastic/markov/)
- [理論編：確率過程の基礎]({{ site.baseurl }}/semi-1/4-stochastic/processes/)
- [確率分布の問題]({{ site.baseurl }}/semi-1/problems/distributions/)

---

[問題一覧に戻る]({{ site.baseurl }}/semi-1/problems/) | [準1級トップ]({{ site.baseurl }}/semi-1/)
