---
layout: default
title: 確率過程の問題 - 準1級対策
description: マルコフ連鎖、ポアソン過程の選択式問題
permalink: /semi-1/problems/stochastic/
---

# 確率過程の問題

マルコフ連鎖、ポアソン過程、ブラウン運動に関する問題です。

<div class="quiz-progress">
  <span class="quiz-progress-text">0 / 10 正解</span>
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

## 問題 6：ランダムウォーク

<div class="quiz-container" data-quiz-id="stoch-6" data-correct="b">
  <div class="quiz-question">
    1次元の単純ランダムウォークで、各ステップで確率 $p$ で右に1、確率 $q = 1-p$ で左に1移動する。原点からスタートして $n$ ステップ後の位置 $S_n$ の期待値 $E[S_n]$ はどれか。
  </div>
  <div class="quiz-options">
    <div class="quiz-option" data-value="a">
      <input type="radio" name="q6" id="q6a">
      <label for="q6a">$0$</label>
    </div>
    <div class="quiz-option" data-value="b">
      <input type="radio" name="q6" id="q6b">
      <label for="q6b">$n(p - q) = n(2p - 1)$</label>
    </div>
    <div class="quiz-option" data-value="c">
      <input type="radio" name="q6" id="q6c">
      <label for="q6c">$\sqrt{n}$</label>
    </div>
    <div class="quiz-option" data-value="d">
      <input type="radio" name="q6" id="q6d">
      <label for="q6d">$np$</label>
    </div>
  </div>
  <button class="quiz-btn" disabled>解答を確認</button>
  <div class="quiz-feedback">
    <span class="quiz-feedback-icon"></span>
    <strong>正解：(b)</strong>
    <div class="quiz-explanation">
      各ステップ $X_i$ は $+1$（確率 $p$）または $-1$（確率 $q$）をとります。

      $E[X_i] = (+1) \cdot p + (-1) \cdot q = p - q = 2p - 1$

      $S_n = \sum_{i=1}^n X_i$ より：

      $$E[S_n] = n(p - q) = n(2p - 1)$$

      $p = q = 0.5$ のとき $E[S_n] = 0$（対称ランダムウォーク）。

      分散は $\text{Var}(S_n) = 4npq$ です。
    </div>
  </div>
</div>

---

## 問題 7：初到達時間

<div class="quiz-container" data-quiz-id="stoch-7" data-correct="a">
  <div class="quiz-question">
    マルコフ連鎖において、状態 $i$ から状態 $j$ への初到達時間（first passage time）$T_{ij} = \min\{n \geq 1 : X_n = j \mid X_0 = i\}$ の期待値 $m_{ij} = E[T_{ij}]$ について正しいものはどれか。
  </div>
  <div class="quiz-options">
    <div class="quiz-option" data-value="a">
      <input type="radio" name="q7" id="q7a">
      <label for="q7a">定常分布 $\pi_j$ に対して、$m_{jj} = 1/\pi_j$ が成り立つ</label>
    </div>
    <div class="quiz-option" data-value="b">
      <input type="radio" name="q7" id="q7b">
      <label for="q7b">$m_{ij} = m_{ji}$ が常に成り立つ</label>
    </div>
    <div class="quiz-option" data-value="c">
      <input type="radio" name="q7" id="q7c">
      <label for="q7c">$m_{ii} = 0$ が常に成り立つ</label>
    </div>
    <div class="quiz-option" data-value="d">
      <input type="radio" name="q7" id="q7d">
      <label for="q7d">$m_{ij}$ は常に有限である</label>
    </div>
  </div>
  <button class="quiz-btn" disabled>解答を確認</button>
  <div class="quiz-feedback">
    <span class="quiz-feedback-icon"></span>
    <strong>正解：(a)</strong>
    <div class="quiz-explanation">
      エルゴード的マルコフ連鎖では、平均回帰時間（mean recurrence time）と定常分布の間に：

      $$m_{jj} = E[T_{jj}] = \frac{1}{\pi_j}$$

      の関係があります。定常分布の確率が小さい状態ほど、そこに戻るまでの時間が長くなります。

      (b) は対称でない限り成り立たない。
      (c) は $T_{ii} \geq 1$ の定義より成り立たない。
      (d) は一時的（transient）な状態では $m_{ij} = \infty$ になりうる。
    </div>
  </div>
</div>

---

## 問題 8：出生死亡過程

<div class="quiz-container" data-quiz-id="stoch-8" data-correct="c">
  <div class="quiz-question">
    連続時間マルコフ連鎖である出生死亡過程（birth-death process）について正しいものはどれか。
  </div>
  <div class="quiz-options">
    <div class="quiz-option" data-value="a">
      <input type="radio" name="q8" id="q8a">
      <label for="q8a">状態は任意の実数値をとりうる</label>
    </div>
    <div class="quiz-option" data-value="b">
      <input type="radio" name="q8" id="q8b">
      <label for="q8b">状態 $n$ から状態 $n+2$ への直接遷移が可能</label>
    </div>
    <div class="quiz-option" data-value="c">
      <input type="radio" name="q8" id="q8c">
      <label for="q8c">状態 $n$ からは $n+1$（出生）または $n-1$（死亡）への遷移のみ可能</label>
    </div>
    <div class="quiz-option" data-value="d">
      <input type="radio" name="q8" id="q8d">
      <label for="q8d">待ち時間は正規分布に従う</label>
    </div>
  </div>
  <button class="quiz-btn" disabled>解答を確認</button>
  <div class="quiz-feedback">
    <span class="quiz-feedback-icon"></span>
    <strong>正解：(c)</strong>
    <div class="quiz-explanation">
      出生死亡過程の特徴：

      - 状態空間：非負整数 $\{0, 1, 2, \ldots\}$
      - 遷移：$n \to n+1$（出生率 $\lambda_n$）または $n \to n-1$（死亡率 $\mu_n$）のみ
      - 待ち時間：指数分布（連続時間マルコフ連鎖の性質）

      例：
      - M/M/1待ち行列（$\lambda_n = \lambda$, $\mu_n = \mu$）
      - 単純出生過程（$\mu_n = 0$）
    </div>
  </div>
</div>

---

## 問題 9：ブラウン運動

<div class="quiz-container" data-quiz-id="stoch-9" data-correct="d">
  <div class="quiz-question">
    標準ブラウン運動（ウィーナー過程）$\{W(t), t \geq 0\}$ の性質として<strong>正しくないもの</strong>はどれか。
  </div>
  <div class="quiz-options">
    <div class="quiz-option" data-value="a">
      <input type="radio" name="q9" id="q9a">
      <label for="q9a">$W(0) = 0$ である</label>
    </div>
    <div class="quiz-option" data-value="b">
      <input type="radio" name="q9" id="q9b">
      <label for="q9b">$W(t) - W(s) \sim N(0, t-s)$（$s < t$）</label>
    </div>
    <div class="quiz-option" data-value="c">
      <input type="radio" name="q9" id="q9c">
      <label for="q9c">標本路は連続だが、ほとんど至る所で微分不可能</label>
    </div>
    <div class="quiz-option" data-value="d">
      <input type="radio" name="q9" id="q9d">
      <label for="q9d">標本路は有界変動である</label>
    </div>
  </div>
  <button class="quiz-btn" disabled>解答を確認</button>
  <div class="quiz-feedback">
    <span class="quiz-feedback-icon"></span>
    <strong>正解：(d)</strong>
    <div class="quiz-explanation">
      標準ブラウン運動の性質：

      1. $W(0) = 0$
      2. 独立増分：重なりのない区間の増分は独立
      3. 定常増分：$W(t) - W(s) \sim N(0, t-s)$
      4. 標本路は確率1で連続
      5. 標本路は確率1で**至る所微分不可能**
      6. 標本路は**非有界変動**（2次変分は $t$ に等しい）

      (d) は誤り。ブラウン運動の2次変分は有限ですが、1次変分（通常の変動）は無限大になります。
    </div>
  </div>
</div>

---

## 問題 10：マルチンゲール

<div class="quiz-container" data-quiz-id="stoch-10" data-correct="b">
  <div class="quiz-question">
    確率過程 $\{M_n\}$ がマルチンゲールであるための条件はどれか。
  </div>
  <div class="quiz-options">
    <div class="quiz-option" data-value="a">
      <input type="radio" name="q10" id="q10a">
      <label for="q10a">$E[M_{n+1} \mid M_0, \ldots, M_n] = M_0$</label>
    </div>
    <div class="quiz-option" data-value="b">
      <input type="radio" name="q10" id="q10b">
      <label for="q10b">$E[M_{n+1} \mid M_0, \ldots, M_n] = M_n$</label>
    </div>
    <div class="quiz-option" data-value="c">
      <input type="radio" name="q10" id="q10c">
      <label for="q10c">$E[M_{n+1} \mid M_0, \ldots, M_n] > M_n$</label>
    </div>
    <div class="quiz-option" data-value="d">
      <input type="radio" name="q10" id="q10d">
      <label for="q10d">$E[M_{n+1}] = E[M_n] + 1$</label>
    </div>
  </div>
  <button class="quiz-btn" disabled>解答を確認</button>
  <div class="quiz-feedback">
    <span class="quiz-feedback-icon"></span>
    <strong>正解：(b)</strong>
    <div class="quiz-explanation">
      マルチンゲールの定義：

      $$E[M_{n+1} \mid \mathcal{F}_n] = M_n$$

      つまり「将来の期待値は現在の値に等しい」（公平なゲーム）。

      関連概念：
      - **劣マルチンゲール**：$E[M_{n+1} \mid \mathcal{F}_n] \geq M_n$（平均的に増加）
      - **優マルチンゲール**：$E[M_{n+1} \mid \mathcal{F}_n] \leq M_n$（平均的に減少）

      例：累積和 $S_n = \sum_{i=1}^n X_i$（$E[X_i] = 0$ のとき）、ブラウン運動
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
