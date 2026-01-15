---
layout: default
title: 母関数 - 準1級対策
description: モーメント母関数、確率母関数、特性関数を解説
---

# 母関数

分布の性質を調べるための強力なツールを学びます。

---

## 1. モーメント母関数（MGF）

### 1.1 定義

確率変数 $X$ のモーメント母関数：

$$M_X(t) = E[e^{tX}]$$

- 離散：$M_X(t) = \sum_x e^{tx} P(X=x)$
- 連続：$M_X(t) = \int_{-\infty}^{\infty} e^{tx} f(x) dx$

### 1.2 積率の導出

$$E[X^n] = M_X^{(n)}(0) = \left.\frac{d^n M_X(t)}{dt^n}\right|_{t=0}$$

特に：
- $E[X] = M_X'(0)$
- $E[X^2] = M_X''(0)$

### 1.3 基本性質

| 性質 | 公式 |
|-----|------|
| $Y = aX + b$ | $M_Y(t) = e^{bt} M_X(at)$ |
| 独立な和 | $M_{X+Y}(t) = M_X(t) M_Y(t)$ |
| 一意性 | $M_X(t) = M_Y(t) \Rightarrow X \overset{d}{=} Y$ |

### 1.4 代表的な分布のMGF

| 分布 | MGF | 存在範囲 |
|-----|-----|---------|
| $N(\mu, \sigma^2)$ | $\exp(\mu t + \sigma^2 t^2/2)$ | $t \in \mathbb{R}$ |
| $\text{Exp}(\lambda)$ | $\lambda/(\lambda - t)$ | $t < \lambda$ |
| $\text{Poi}(\lambda)$ | $\exp(\lambda(e^t - 1))$ | $t \in \mathbb{R}$ |
| $\text{Bin}(n, p)$ | $(1-p+pe^t)^n$ | $t \in \mathbb{R}$ |
| $\Gamma(\alpha, \beta)$ | $(1 - t/\beta)^{-\alpha}$ | $t < \beta$ |

---

## 2. 確率母関数（PGF）

### 2.1 定義

非負整数値をとる確率変数 $X$ の確率母関数：

$$G_X(s) = E[s^X] = \sum_{k=0}^{\infty} P(X=k) s^k$$

### 2.2 確率の導出

$$P(X=k) = \frac{G_X^{(k)}(0)}{k!}$$

### 2.3 積率の導出

$$E[X] = G_X'(1)$$

$$E[X(X-1)] = G_X''(1)$$

$$\text{Var}(X) = G_X''(1) + G_X'(1) - (G_X'(1))^2$$

### 2.4 代表的な分布のPGF

| 分布 | PGF |
|-----|-----|
| $\text{Ber}(p)$ | $1 - p + ps$ |
| $\text{Bin}(n, p)$ | $(1 - p + ps)^n$ |
| $\text{Poi}(\lambda)$ | $\exp(\lambda(s-1))$ |
| $\text{Geo}(p)$ | $ps/(1-(1-p)s)$ |
| $\text{NB}(r, p)$ | $(ps/(1-(1-p)s))^r$ |

---

## 3. 特性関数

### 3.1 定義

$$\varphi_X(t) = E[e^{itX}] = E[\cos(tX)] + i E[\sin(tX)]$$

$i = \sqrt{-1}$（虚数単位）

### 3.2 特徴

- **常に存在する**（MGFと異なり）
- 一意性定理が成り立つ
- フーリエ変換との関係

### 3.3 積率の導出

$$E[X^n] = \frac{1}{i^n} \varphi_X^{(n)}(0)$$

### 3.4 代表的な分布の特性関数

| 分布 | 特性関数 |
|-----|---------|
| $N(\mu, \sigma^2)$ | $\exp(i\mu t - \sigma^2 t^2/2)$ |
| $\text{Exp}(\lambda)$ | $\lambda/(\lambda - it)$ |
| $\text{Poi}(\lambda)$ | $\exp(\lambda(e^{it} - 1))$ |
| Cauchy | $\exp(-\|t\|)$ |

### 3.5 連続性定理（レヴィの定理）

$$\varphi_{X_n}(t) \to \varphi_X(t) \quad \Rightarrow \quad X_n \xrightarrow{d} X$$

中心極限定理の証明に使用される。

---

## 4. キュムラント母関数

### 4.1 定義

$$K_X(t) = \log M_X(t)$$

### 4.2 キュムラント

$$\kappa_n = K_X^{(n)}(0)$$

- $\kappa_1 = E[X]$（平均）
- $\kappa_2 = \text{Var}(X)$（分散）
- $\kappa_3 = E[(X-\mu)^3]$（3次中心積率）
- $\kappa_4 = E[(X-\mu)^4] - 3\sigma^4$（過剰尖度に関連）

### 4.3 加法性

$X, Y$ が独立のとき：

$$K_{X+Y}(t) = K_X(t) + K_Y(t)$$

キュムラントも加法的：$\kappa_n(X+Y) = \kappa_n(X) + \kappa_n(Y)$

### 4.4 正規分布のキュムラント

$X \sim N(\mu, \sigma^2)$ のとき：

$$K_X(t) = \mu t + \frac{\sigma^2 t^2}{2}$$

$\kappa_1 = \mu$, $\kappa_2 = \sigma^2$, $\kappa_n = 0$ ($n \geq 3$)

---

## 5. 母関数の応用

### 5.1 和の分布

$X_1, \ldots, X_n$ が独立で同分布のとき：

$$M_{S_n}(t) = [M_X(t)]^n$$

### 5.2 ランダム和（複合分布）

$S = \sum_{i=1}^{N} X_i$（$N$ はランダム、$X_i$ と独立）

$$G_S(s) = G_N(G_X(s))$$

$$M_S(t) = G_N(M_X(t))$$

### 5.3 分布の特定

MGFが一致すれば分布も一致（一意性定理）。

例：$X + Y$ のMGFが特定の形なら、分布を同定できる。

---

## 6. 例題

### 例題1：MGFから期待値と分散

$X \sim \text{Poi}(\lambda)$ のMGF $M_X(t) = \exp(\lambda(e^t - 1))$ から $E[X]$ と $\text{Var}(X)$ を求めよ。

<details markdown="1">
<summary>解答を見る</summary>

### 解答

$$M_X'(t) = \exp(\lambda(e^t - 1)) \cdot \lambda e^t$$

$$M_X'(0) = \exp(0) \cdot \lambda \cdot 1 = \lambda$$

$$E[X] = \lambda$$

$$M_X''(t) = \lambda e^t \cdot \exp(\lambda(e^t - 1)) \cdot \lambda e^t + \exp(\lambda(e^t - 1)) \cdot \lambda e^t$$

$$= \exp(\lambda(e^t - 1)) \cdot \lambda e^t (\lambda e^t + 1)$$

$$M_X''(0) = 1 \cdot \lambda \cdot (\lambda + 1) = \lambda^2 + \lambda$$

$$\text{Var}(X) = E[X^2] - (E[X])^2 = \lambda^2 + \lambda - \lambda^2 = \lambda$$

**答え：$E[X] = \lambda$, $\text{Var}(X) = \lambda$**

</details>

---

### 例題2：和の分布

$X_1, X_2, X_3$ が独立に $\text{Exp}(1)$ に従うとき、$S = X_1 + X_2 + X_3$ の分布を求めよ。

<details markdown="1">
<summary>解答を見る</summary>

### 解答

$\text{Exp}(1)$ のMGF：

$$M_X(t) = \frac{1}{1-t} \quad (t < 1)$$

$S$ のMGF：

$$M_S(t) = [M_X(t)]^3 = \left(\frac{1}{1-t}\right)^3 = (1-t)^{-3}$$

これは $\Gamma(3, 1)$（形状パラメータ3、レートパラメータ1）のMGF。

**答え：$S \sim \Gamma(3, 1)$（ガンマ分布）**

</details>

---

### 例題3：ランダム和

$N \sim \text{Poi}(\mu)$, $X_i \sim \text{Exp}(\lambda)$ が独立のとき、$S = \sum_{i=1}^{N} X_i$ のMGFを求めよ。

<details markdown="1">
<summary>解答を見る</summary>

### 解答

$G_N(s) = \exp(\mu(s-1))$

$M_X(t) = \frac{\lambda}{\lambda - t}$

$$M_S(t) = G_N(M_X(t)) = \exp\left(\mu\left(\frac{\lambda}{\lambda - t} - 1\right)\right)$$

$$= \exp\left(\mu \cdot \frac{\lambda - (\lambda - t)}{\lambda - t}\right) = \exp\left(\frac{\mu t}{\lambda - t}\right)$$

**答え：$M_S(t) = \exp\left(\frac{\mu t}{\lambda - t}\right)$**

</details>

---

## 7. 重要公式まとめ

| 項目 | 公式 |
|-----|------|
| MGF | $M_X(t) = E[e^{tX}]$ |
| PGF | $G_X(s) = E[s^X]$ |
| 特性関数 | $\varphi_X(t) = E[e^{itX}]$ |
| 積率の導出 | $E[X^n] = M_X^{(n)}(0)$ |
| 独立な和 | $M_{X+Y}(t) = M_X(t) M_Y(t)$ |
| キュムラント | $K_X(t) = \log M_X(t)$ |
| ランダム和 | $M_S(t) = G_N(M_X(t))$ |

---

[確率論に戻る]({{ site.baseurl }}/semi-1/1-probability/) | [準1級トップ]({{ site.baseurl }}/semi-1/) | [トップページ]({{ site.baseurl }}/)
