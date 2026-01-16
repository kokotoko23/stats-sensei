---
layout: default
title: 極限定理 - 準1級対策
description: 大数の法則、中心極限定理、デルタ法、漸近理論を解説
---

# 極限定理と漸近理論

大標本理論の基盤となる重要な定理を学びます。

---

## 極限定理はなぜ重要か

極限定理は「標本サイズが大きくなると何が起こるか」を教えてくれます。実際の統計分析で使う多くの手法は、極限定理に基づいた近似です。

```
極限定理の主要な応用

大数の法則 → 標本平均は母平均に近づく（推定の正当化）
中心極限定理 → 標本平均は正規分布に近づく（検定・信頼区間の基礎）
デルタ法 → 変換後の統計量の分散が計算できる
```

**重要な略語**：
- **LLN** = **L**aw of **L**arge **N**umbers（大数の法則）
- **CLT** = **C**entral **L**imit **T**heorem（中心極限定理）
- **a.s.** = **a**lmost **s**urely（概収束、ほとんど確実に）
- **iid** = **i**ndependent and **i**dentically **d**istributed（独立同分布）

---

## 1. 収束の種類

### 収束の直感的理解

確率変数列 $X_n$ が「$X$ に収束する」とは何を意味するのか？3つの異なる概念があります。

```
収束の概念比較

概収束（a.s.）：
  「ほぼ全ての系列で、いずれ X に限りなく近づく」
  例：サイコロを無限回投げると、平均はほぼ確実に 3.5 に収束

確率収束（p）：
  「X から離れている確率がゼロに近づく」
  例：n が大きくなると、標本平均が母平均から遠い確率は小さくなる

分布収束（d）：
  「分布の形が X の分布に近づく」
  例：二項分布が正規分布に近づく（形が似てくる）
```

### 1.1 概収束（ほとんど確実な収束）

$$X_n \xrightarrow{a.s.} X \quad \Leftrightarrow \quad P\left(\lim_{n \to \infty} X_n = X\right) = 1$$

### 1.2 確率収束

$$X_n \xrightarrow{p} X \quad \Leftrightarrow \quad \forall \epsilon > 0, \lim_{n \to \infty} P(\lvert X_n - X \rvert > \epsilon) = 0$$

### 1.3 分布収束（法則収束）

$$X_n \xrightarrow{d} X \quad \Leftrightarrow \quad \lim_{n \to \infty} F_{X_n}(x) = F_X(x) \text{ （連続点で）}$$

### 1.4 収束の強さ

$$\text{概収束} \Rightarrow \text{確率収束} \Rightarrow \text{分布収束}$$

（逆は一般に成り立たない）

---

## 2. 大数の法則

### 2.1 大数の弱法則（Weak Law）

$X_1, X_2, \ldots$ が独立同分布で $E[X_i] = \mu$, $\text{Var}(X_i) = \sigma^2 < \infty$ のとき：

$$\bar{X}_n = \frac{1}{n}\sum_{i=1}^n X_i \xrightarrow{p} \mu$$

### 2.2 大数の強法則（Strong Law）

$E[\lvert X_i \rvert] < \infty$ のとき：

$$\bar{X}_n \xrightarrow{a.s.} \mu$$

### 2.3 チェビシェフの証明（弱法則）

$$P(\lvert \bar{X}_n - \mu \rvert > \epsilon) \leq \frac{\text{Var}(\bar{X}_n)}{\epsilon^2} = \frac{\sigma^2}{n\epsilon^2} \to 0$$

---

## 3. 中心極限定理（CLT）

### CLT の驚くべき点

中心極限定理の最も驚くべき点は、**元の分布が何であっても**標本平均は正規分布に近づくことです。

```
CLT のイメージ（元の分布 → 標本平均の分布）

元の分布（例：一様分布）     n=2          n=10         n=30
    ┌─────┐               ╱╲           ╱╲           ╱╲
    │     │              ╱  ╲         ╱  ╲         ╱  ╲
    │     │             ╱    ╲       ╱    ╲       ╱    ╲
    └─────┘            └──────┘     └──────┘     └──────┘
                        三角形に      ほぼ山型に    ほぼ正規に！

どんな形の分布でも、平均をとり続けると正規分布に近づく
```

### 3.1 古典的CLT（リンデベルグ・レヴィ）

$X_1, X_2, \ldots$ が iid（独立同分布）で $E[X_i] = \mu$, $\text{Var}(X_i) = \sigma^2$ のとき：

$$\frac{\bar{X}_n - \mu}{\sigma/\sqrt{n}} = \frac{\sum X_i - n\mu}{\sigma\sqrt{n}} \xrightarrow{d} N(0, 1)$$

または：

$$\sqrt{n}(\bar{X}_n - \mu) \xrightarrow{d} N(0, \sigma^2)$$

### 3.2 実用的な表現

大きな $n$ で：

$$\bar{X}_n \approx N\left(\mu, \frac{\sigma^2}{n}\right)$$

$$\sum_{i=1}^n X_i \approx N(n\mu, n\sigma^2)$$

### 3.3 リンデベルグ・フェラーの定理

独立だが同分布でない場合への一般化。

**リンデベルグ条件**を満たせば CLT が成り立つ。

### 3.4 ベリー・エッセーン定理

CLT の収束速度の評価：

$$\sup_x \lvert F_n(x) - \Phi(x) \rvert \leq \frac{C \cdot E[\lvert X - \mu \rvert^3]}{\sigma^3 \sqrt{n}}$$

$C \approx 0.4748$（ベリー・エッセーン定数）

---

## 4. デルタ法

### デルタ法の直感的理解

統計量 $X_n$ の漸近分布がわかっているとき、$g(X_n)$（例えば $\log X_n$ や $X_n^2$）の漸近分布はどうなるか？デルタ法はこれに答えます。

```
デルタ法のイメージ

X_n が θ の周りで「ばらつき σ」を持つとき、
g(X_n) は g(θ) の周りでどれくらいばらつくか？

g(x)
  │        ／
  │       ／ ← 傾き g'(θ)
  │      ╱
  │     ╱
  │────╱──────
       θ

X_n のばらつき σ が、g の傾き g'(θ) で「引き伸ばされる」

g(X_n) のばらつき ≈ |g'(θ)| × σ
```

### 4.1 定理

$\sqrt{n}(X_n - \theta) \xrightarrow{d} N(0, \sigma^2)$ のとき、$g$ が $\theta$ で微分可能なら：

$$\sqrt{n}(g(X_n) - g(\theta)) \xrightarrow{d} N(0, \sigma^2 [g'(\theta)]^2)$$

### 4.2 漸近分散

$$\text{Avar}(g(X_n)) \approx \frac{\sigma^2 [g'(\theta)]^2}{n}$$

**注**：$\text{Avar}$ は **A**symptotic **Var**iance（漸近分散）の略。標本サイズ $n$ が大きいときの分散を表す。

### 4.3 多変数への拡張

$\sqrt{n}(\mathbf{X}_n - \boldsymbol{\theta}) \xrightarrow{d} N(\mathbf{0}, \boldsymbol{\Sigma})$ のとき：

$$\sqrt{n}(g(\mathbf{X}_n) - g(\boldsymbol{\theta})) \xrightarrow{d} N(0, \nabla g(\boldsymbol{\theta})^\top \boldsymbol{\Sigma} \nabla g(\boldsymbol{\theta}))$$

### 4.4 二次のデルタ法

$g'(\theta) = 0$ のとき（一次が退化）：

$$n(g(X_n) - g(\theta)) \xrightarrow{d} \frac{\sigma^2 g''(\theta)}{2} \chi^2_1$$

### 4.5 デルタ法の導出

```
導出のアイデア：テイラー展開と分布収束の性質を使う

Step 1: テイラー展開
  g(Xₙ) を θ の周りで1次まで展開：
  g(Xₙ) ≈ g(θ) + g'(θ)(Xₙ - θ)

Step 2: 変形
  g(Xₙ) - g(θ) ≈ g'(θ)(Xₙ - θ)

  両辺に √n をかける：
  √n(g(Xₙ) - g(θ)) ≈ g'(θ) · √n(Xₙ - θ)

Step 3: 分布収束
  仮定より √n(Xₙ - θ) →ᵈ N(0, σ²)

  定数倍の分布収束：
  g'(θ) · √n(Xₙ - θ) →ᵈ g'(θ) · N(0, σ²)
                      = N(0, σ²[g'(θ)]²)

Step 4: 結論
  √n(g(Xₙ) - g(θ)) →ᵈ N(0, σ²[g'(θ)]²)

  漸近分散 = σ²[g'(θ)]²/n

例：g(x) = log(x), θ = μ のとき
  g'(μ) = 1/μ
  Avar(log X̄) = σ²/μ² · 1/n = σ²/(nμ²)
```

---

## 5. スラツキーの定理

### 5.1 定理

$X_n \xrightarrow{d} X$ かつ $Y_n \xrightarrow{p} c$（定数）のとき：

- $X_n + Y_n \xrightarrow{d} X + c$
- $X_n Y_n \xrightarrow{d} cX$
- $X_n / Y_n \xrightarrow{d} X/c$ （$c \neq 0$）

### 5.2 応用例

$$\frac{\bar{X}_n - \mu}{S_n/\sqrt{n}} \xrightarrow{d} N(0, 1)$$

$S_n \xrightarrow{p} \sigma$ より成り立つ。

---

## 6. 連続写像定理

### 6.1 定理

$g$ が連続のとき：

$$X_n \xrightarrow{d} X \Rightarrow g(X_n) \xrightarrow{d} g(X)$$

$$X_n \xrightarrow{p} X \Rightarrow g(X_n) \xrightarrow{p} g(X)$$

### 6.2 応用

$$X_n \xrightarrow{d} N(0, 1) \Rightarrow X_n^2 \xrightarrow{d} \chi^2_1$$

---

## 7. 漸近展開

### 7.1 エッジワース展開

標準化統計量の分布関数の展開：

$$F_n(x) \approx \Phi(x) - \frac{\gamma_1}{6\sqrt{n}}(x^2 - 1)\phi(x) + O(n^{-1})$$

$\gamma_1$：歪度、$\phi$：標準正規密度

### 7.2 コーニッシュ・フィッシャー展開

分位点の展開：

$$x_\alpha \approx z_\alpha + \frac{\gamma_1}{6}(z_\alpha^2 - 1)/\sqrt{n} + O(n^{-1})$$

---

## 8. 例題

### 例題1：中心極限定理の応用

$X_i \sim \text{Exp}(1)$（$E[X]=1$, $\text{Var}(X)=1$）が100個あるとき、$\sum X_i > 110$ となる確率を正規近似で求めよ。

<details markdown="1">
<summary>解答を見る</summary>

### 解答

CLT より：

$$\sum_{i=1}^{100} X_i \approx N(100, 100)$$

標準化：

$$Z = \frac{110 - 100}{\sqrt{100}} = \frac{10}{10} = 1$$

$$P\left(\sum X_i > 110\right) = P(Z > 1) = 1 - \Phi(1) \approx 1 - 0.8413 = 0.1587$$

**答え：約15.9%**

</details>

---

### 例題2：デルタ法

$X_1, \ldots, X_n$ が $E[X] = \mu$, $\text{Var}(X) = \sigma^2$ の独立同分布からの標本のとき、$\log \bar{X}$ の漸近分散を求めよ。

<details markdown="1">
<summary>解答を見る</summary>

### 解答

$g(x) = \log x$ より $g'(x) = 1/x$

デルタ法より：

$$\text{Avar}(\log \bar{X}) = \frac{\sigma^2 [g'(\mu)]^2}{n} = \frac{\sigma^2}{n\mu^2}$$

**答え：$\sigma^2/(n\mu^2)$**

</details>

---

### 例題3：スラツキーの定理

$\bar{X}_n \xrightarrow{p} \mu$, $S_n^2 \xrightarrow{p} \sigma^2$ のとき、$\bar{X}_n / S_n$ の確率収束先を求めよ。

<details markdown="1">
<summary>解答を見る</summary>

### 解答

連続写像定理より $S_n = \sqrt{S_n^2} \xrightarrow{p} \sigma$

スラツキーの定理より：

$$\frac{\bar{X}_n}{S_n} \xrightarrow{p} \frac{\mu}{\sigma}$$

**答え：$\mu/\sigma$**

</details>

---

## 9. よくある誤解

### 誤解1：CLT と大数の法則の混同

```
✗ 誤り：「CLT は標本平均が母平均に収束することを示す」

✓ 正しい：
  大数の法則 → 標本平均は母平均に「収束する」（値が近づく）
  CLT → 標本平均の「分布の形」が正規分布に近づく

大数の法則：X̄ₙ → μ（点として）
CLT：√n(X̄ₙ - μ) の分布 → N(0, σ²)（形として）
```

### 誤解2：CLT の適用条件

```
✗ 誤り：「どんな分布でも n ≥ 30 なら正規近似できる」

✓ 正しい：n ≥ 30 は目安であり、分布の形状による
  ・対称分布 → 比較的小さい n でOK
  ・強い歪み → より大きな n が必要
  ・裾が重い → 収束が遅い

実用的には分布の歪度・尖度を確認すべき
```

### 誤解3：分布収束と確率収束

```
✗ 誤り：「分布収束すれば確率収束する」

✓ 正しい：逆！
  確率収束 → 分布収束（常に成り立つ）
  分布収束 → 確率収束（一般には成り立たない）

ただし、収束先が定数 c のとき：
  Xₙ →ᵈ c ⟺ Xₙ →ᵖ c
```

---

## 10. 概念のつながり

```
極限定理と漸近理論の体系

                  収束の種類
         ┌──────────┼──────────┐
         ↓          ↓          ↓
       概収束    確率収束    分布収束
       (a.s.)     (p)        (d)
         │          │          │
         └────→─────┴────←─────┘
           強い ←────────→ 弱い

         大数の法則（LLN）
              ↓
         X̄ₙ →ᵖ μ（点推定の正当化）
              │
              ↓
         中心極限定理（CLT）
              ↓
         √n(X̄ₙ-μ) →ᵈ N(0,σ²)
              │
    ┌─────────┼─────────┐
    ↓         ↓         ↓
 t検定    信頼区間   漸近検定
    │
    ↓
 デルタ法（変換後の分布）
    │
    ↓
 g(X̄ₙ)の漸近分布
    │
    ↓
 スラツキー・連続写像
 （複合的な統計量の扱い）
```

---

## 11. 重要公式まとめ

| 定理 | 内容 |
|-----|------|
| 大数の法則 | $\bar{X}_n \xrightarrow{p} \mu$ |
| CLT | $\sqrt{n}(\bar{X}_n - \mu) \xrightarrow{d} N(0, \sigma^2)$ |
| デルタ法 | $\text{Avar}(g(X_n)) = \sigma^2[g'(\theta)]^2/n$ |
| スラツキー | $X_n \xrightarrow{d} X$, $Y_n \xrightarrow{p} c$ $\Rightarrow$ $X_nY_n \xrightarrow{d} cX$ |
| 連続写像 | $X_n \xrightarrow{d} X$ $\Rightarrow$ $g(X_n) \xrightarrow{d} g(X)$ |

---

[確率分布に戻る]({{ site.baseurl }}/semi-1/2-distributions/) | [準1級トップ]({{ site.baseurl }}/semi-1/) | [トップページ]({{ site.baseurl }}/)
