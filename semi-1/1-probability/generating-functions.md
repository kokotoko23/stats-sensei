---
layout: default
title: 母関数 - 準1級対策
description: モーメント母関数、確率母関数、特性関数を解説
---

# 母関数

分布の性質を調べるための強力なツール「母関数」を学びます。

---

## 母関数とは？

### なぜ母関数を使うのか

確率分布を扱う際、以下のような問題に直面します：

- 独立な確率変数の**和の分布**は？
- この分布の**平均・分散・高次積率**は？
- 2つの分布が**同じ**かどうか判定したい

母関数を使うと、これらが**代数的な計算**で解けます。

```
母関数の威力：

【畳み込み問題】             【母関数を使うと】
X + Y の分布は？              M_{X+Y}(t) = M_X(t) · M_Y(t)
→ 畳み込み積分が必要         → 掛け算だけ！
  （計算が大変）
```

### 3種類の母関数

| 母関数 | 正式名称 | 記号 | 主な用途 |
|-------|---------|------|---------|
| **MGF** | Moment Generating Function（積率母関数） | $M_X(t)$ | 積率の計算、和の分布 |
| **PGF** | Probability Generating Function（確率母関数） | $G_X(s)$ | 離散分布、カウントデータ |
| **CF** | Characteristic Function（特性関数） | $\varphi_X(t)$ | 理論的証明（常に存在） |

---

## 1. モーメント母関数（MGF: Moment Generating Function）

### 1.1 定義

$$M_X(t) = E[e^{tX}]$$

- 離散：$M_X(t) = \sum_x e^{tx} P(X=x)$
- 連続：$M_X(t) = \int_{-\infty}^{\infty} e^{tx} f(x) dx$

**名前の由来**：この関数から積率（モーメント）を「生成」できるから。

### 1.2 積率の導出

$e^{tX}$ をテイラー展開すると：

$$e^{tX} = 1 + tX + \frac{(tX)^2}{2!} + \frac{(tX)^3}{3!} + \cdots$$

期待値をとると：

$$M_X(t) = 1 + tE[X] + \frac{t^2 E[X^2]}{2!} + \frac{t^3 E[X^3]}{3!} + \cdots$$

したがって、**$t=0$ で微分**すれば積率が出てくる：

$$E[X^n] = M_X^{(n)}(0) = \left.\frac{d^n M_X(t)}{dt^n}\right|_{t=0}$$

```
例：E[X] と E[X²] の求め方

M_X(t) を t で微分して t=0 を代入：

M'_X(0)  = E[X]      ← 平均
M''_X(0) = E[X²]     ← 分散の計算に使う

Var(X) = E[X²] - (E[X])² = M''_X(0) - (M'_X(0))²
```

### 1.3 最重要性質：独立な和

**独立な確率変数の和のMGFは、MGFの積になる**：

$$M_{X+Y}(t) = M_X(t) \cdot M_Y(t)$$

**証明**：
$$M_{X+Y}(t) = E[e^{t(X+Y)}] = E[e^{tX} e^{tY}] = E[e^{tX}] E[e^{tY}]$$
（独立性より期待値の積に分解）

### 1.4 一意性定理

MGFが存在して一致すれば、分布も一致：

$$M_X(t) = M_Y(t) \text{ (ある区間で)} \Rightarrow X \overset{d}{=} Y$$

**応用**：和のMGFを計算して、既知の分布のMGFと比較すれば分布が特定できる。

### 1.5 線形変換

$Y = aX + b$ のとき：

$$M_Y(t) = E[e^{t(aX+b)}] = e^{bt} E[e^{(at)X}] = e^{bt} M_X(at)$$

### 1.6 代表的な分布のMGF

| 分布 | MGF | 存在範囲 |
|-----|-----|---------|
| $N(\mu, \sigma^2)$ | $\exp(\mu t + \sigma^2 t^2/2)$ | $t \in \mathbb{R}$ |
| $\text{Exp}(\lambda)$ | $\lambda/(\lambda - t)$ | $t < \lambda$ |
| $\text{Poi}(\lambda)$ | $\exp(\lambda(e^t - 1))$ | $t \in \mathbb{R}$ |
| $\text{Bin}(n, p)$ | $(1-p+pe^t)^n$ | $t \in \mathbb{R}$ |
| $\Gamma(\alpha, \beta)$ | $(1 - t/\beta)^{-\alpha}$ | $t < \beta$ |
| $\chi^2_k$ | $(1 - 2t)^{-k/2}$ | $t < 1/2$ |

### 1.7 注意：MGFが存在しない場合

**すべての分布でMGFが存在するわけではない**。

- コーシー分布：MGFが存在しない（裾が重すぎる）
- 対数正規分布：すべての $t > 0$ でMGFが発散

→ このような場合は**特性関数**を使う

---

## 2. 確率母関数（PGF: Probability Generating Function）

### なぜPGFを使うのか

**非負整数値**をとる確率変数（カウントデータ）に特化した母関数。

- ポアソン分布、二項分布、幾何分布など
- 分岐過程、待ち行列理論で活躍

### 2.1 定義

$$G_X(s) = E[s^X] = \sum_{k=0}^{\infty} P(X=k) \cdot s^k$$

$s$ のべき級数として展開すると、係数が確率になる。

### 2.2 確率と積率の導出

**確率の取り出し**：

$$P(X=k) = \frac{G_X^{(k)}(0)}{k!}$$

**期待値**：

$$E[X] = G_X'(1)$$

**分散**：

$$\text{Var}(X) = G_X''(1) + G_X'(1) - (G_X'(1))^2$$

### 2.3 代表的な分布のPGF

| 分布 | PGF | $E[X]$ の計算 |
|-----|-----|--------------|
| $\text{Ber}(p)$ | $1 - p + ps$ | $G'(1) = p$ |
| $\text{Bin}(n, p)$ | $(1 - p + ps)^n$ | $G'(1) = np$ |
| $\text{Poi}(\lambda)$ | $\exp(\lambda(s-1))$ | $G'(1) = \lambda$ |
| $\text{Geo}(p)$ | $ps/(1-(1-p)s)$ | $G'(1) = 1/p$ |
| $\text{NB}(r, p)$ | $(ps/(1-(1-p)s))^r$ | $G'(1) = r/p$ |

### 2.4 MGFとPGFの関係

$$G_X(s) = M_X(\log s)$$
$$M_X(t) = G_X(e^t)$$

---

## 3. 特性関数（CF: Characteristic Function）

### なぜ特性関数を使うのか

MGFには「存在しない場合がある」という弱点がありました。特性関数は**常に存在**します。

### 3.1 定義

$$\varphi_X(t) = E[e^{itX}]$$

ここで $i = \sqrt{-1}$（虚数単位）。オイラーの公式より：

$$e^{itX} = \cos(tX) + i\sin(tX)$$

なので：

$$\varphi_X(t) = E[\cos(tX)] + i \cdot E[\sin(tX)]$$

### 3.2 なぜ常に存在するか

$$\lvert e^{itX} \rvert = \lvert \cos(tX) + i\sin(tX) \rvert = 1$$

絶対値が常に1なので、期待値が必ず有限になる。

### 3.3 積率の導出

$$E[X^n] = \frac{1}{i^n} \varphi_X^{(n)}(0)$$

### 3.4 代表的な分布の特性関数

| 分布 | 特性関数 |
|-----|---------|
| $N(\mu, \sigma^2)$ | $\exp(i\mu t - \sigma^2 t^2/2)$ |
| $\text{Exp}(\lambda)$ | $\lambda/(\lambda - it)$ |
| $\text{Poi}(\lambda)$ | $\exp(\lambda(e^{it} - 1))$ |
| コーシー分布 | $\exp(-\lvert t \rvert)$ |

### 3.5 連続性定理（レヴィの定理）

$$\varphi_{X_n}(t) \to \varphi_X(t) \quad \Rightarrow \quad X_n \xrightarrow{d} X$$

**中心極限定理（CLT: Central Limit Theorem）の証明**に使われる重要定理。

---

## 4. キュムラント母関数

### 4.1 定義

MGFの対数をとったもの：

$$K_X(t) = \log M_X(t)$$

### 4.2 キュムラント

$K_X(t)$ を $t=0$ で微分して得られる値を**キュムラント**と呼ぶ：

$$\kappa_n = K_X^{(n)}(0)$$

| キュムラント | 意味 |
|------------|------|
| $\kappa_1$ | 平均 $\mu$ |
| $\kappa_2$ | 分散 $\sigma^2$ |
| $\kappa_3$ | 3次中心積率 $\mu_3$ |
| $\kappa_4$ | $\mu_4 - 3\sigma^4$（超過尖度に関連） |

### 4.3 加法性

**独立な和のキュムラントは、キュムラントの和**：

$$K_{X+Y}(t) = K_X(t) + K_Y(t)$$

$$\kappa_n(X+Y) = \kappa_n(X) + \kappa_n(Y)$$

積率は加法的でないが、キュムラントは加法的（この性質が便利）。

### 4.4 正規分布の特殊性

$X \sim N(\mu, \sigma^2)$ のとき：

$$K_X(t) = \mu t + \frac{\sigma^2 t^2}{2}$$

- $\kappa_1 = \mu$, $\kappa_2 = \sigma^2$
- **$\kappa_3 = \kappa_4 = \cdots = 0$**（3次以上のキュムラントがすべて0）

正規分布は「キュムラントが2次で打ち切られる」唯一の分布。

---

## 5. 母関数の応用

### 5.1 独立な和の分布

$X_1, \ldots, X_n$ が独立で同分布（iid: independent and identically distributed）のとき：

$$M_{S_n}(t) = [M_X(t)]^n$$

```
例：指数分布の和

X₁, X₂, X₃ ~ Exp(λ) が独立

M_X(t) = λ/(λ-t)

M_{X₁+X₂+X₃}(t) = [λ/(λ-t)]³ = λ³/(λ-t)³

→ これは Γ(3, λ) のMGF！
→ 指数分布の和はガンマ分布に従う
```

### 5.2 ランダム和（複合分布）

$N$ を確率変数、$X_i$ を iid として：

$$S = \sum_{i=1}^{N} X_i$$

このとき：

$$M_S(t) = G_N(M_X(t))$$

**Nが離散なのでPGFを使い、その引数にMGFを代入する**。

### 5.3 分布の特定

MGFの一意性を利用して分布を特定する典型的な流れ：

```
Step 1: 問題設定から和のMGFを計算
Step 2: 整理して既知の形に変形
Step 3: 表と照合して分布を同定
```

---

## 6. 母関数の比較

| 特性 | MGF | PGF | 特性関数 |
|-----|-----|-----|---------|
| 定義 | $E[e^{tX}]$ | $E[s^X]$ | $E[e^{itX}]$ |
| 存在 | 常にではない | 非負整数値なら常に | **常に存在** |
| 用途 | 積率計算、和の分布 | 離散分布 | 理論的証明 |
| 独立和 | 積になる | 積になる | 積になる |
| 一意性 | あり | あり | あり |

---

## 7. 例題

### 例題1：MGFから期待値と分散

$X \sim \text{Poi}(\lambda)$ のMGF $M_X(t) = \exp(\lambda(e^t - 1))$ から $E[X]$ と $\text{Var}(X)$ を求めよ。

<details markdown="1">
<summary>解答を見る</summary>

### 解答

**Step 1：1階微分**

$$M_X'(t) = \exp(\lambda(e^t - 1)) \cdot \lambda e^t = M_X(t) \cdot \lambda e^t$$

$$M_X'(0) = 1 \cdot \lambda \cdot 1 = \lambda$$

$$E[X] = \lambda$$

**Step 2：2階微分**

積の微分より：

$$M_X''(t) = M_X'(t) \cdot \lambda e^t + M_X(t) \cdot \lambda e^t$$

$$M_X''(0) = \lambda \cdot \lambda + 1 \cdot \lambda = \lambda^2 + \lambda$$

$$E[X^2] = \lambda^2 + \lambda$$

**Step 3：分散**

$$\text{Var}(X) = E[X^2] - (E[X])^2 = \lambda^2 + \lambda - \lambda^2 = \lambda$$

**答え：$E[X] = \lambda$, $\text{Var}(X) = \lambda$**

ポアソン分布は平均と分散が等しい。

</details>

---

### 例題2：和の分布の特定

$X_1, X_2, X_3$ が独立に $\text{Exp}(1)$ に従うとき、$S = X_1 + X_2 + X_3$ の分布を求めよ。

<details markdown="1">
<summary>解答を見る</summary>

### 解答

**Step 1：個別のMGF**

$\text{Exp}(1)$ のMGF：$M_X(t) = \frac{1}{1-t}$ （$t < 1$）

**Step 2：和のMGF**

独立なので：

$$M_S(t) = [M_X(t)]^3 = \left(\frac{1}{1-t}\right)^3 = (1-t)^{-3}$$

**Step 3：分布の特定**

$\Gamma(\alpha, \beta)$ のMGFは $(1 - t/\beta)^{-\alpha}$

$M_S(t) = (1-t)^{-3}$ と比較すると $\alpha = 3$, $\beta = 1$

**答え：$S \sim \Gamma(3, 1)$**

一般に、iid な $\text{Exp}(\lambda)$ を $n$ 個足すと $\Gamma(n, \lambda)$ になる。

</details>

---

### 例題3：ランダム和

$N \sim \text{Poi}(\mu)$, $X_i \sim \text{Exp}(\lambda)$ が独立のとき、$S = \sum_{i=1}^{N} X_i$ のMGFを求めよ。

<details markdown="1">
<summary>解答を見る</summary>

### 解答

**Step 1：各母関数**

- $N$ のPGF：$G_N(s) = \exp(\mu(s-1))$
- $X$ のMGF：$M_X(t) = \frac{\lambda}{\lambda - t}$

**Step 2：ランダム和の公式**

$$M_S(t) = G_N(M_X(t))$$

$$= \exp\left(\mu\left(\frac{\lambda}{\lambda - t} - 1\right)\right)$$

**Step 3：整理**

$$= \exp\left(\mu \cdot \frac{\lambda - (\lambda - t)}{\lambda - t}\right) = \exp\left(\frac{\mu t}{\lambda - t}\right)$$

**答え：$M_S(t) = \exp\left(\dfrac{\mu t}{\lambda - t}\right)$**

</details>

---

## 8. 重要公式まとめ

### 定義

| 母関数 | 定義 |
|-------|------|
| MGF（積率母関数） | $M_X(t) = E[e^{tX}]$ |
| PGF（確率母関数） | $G_X(s) = E[s^X]$ |
| CF（特性関数） | $\varphi_X(t) = E[e^{itX}]$ |
| キュムラント母関数 | $K_X(t) = \log M_X(t)$ |

### 主要公式

| 公式 | 内容 |
|-----|------|
| 積率の導出 | $E[X^n] = M_X^{(n)}(0)$ |
| 独立な和 | $M_{X+Y}(t) = M_X(t) \cdot M_Y(t)$ |
| 線形変換 | $M_{aX+b}(t) = e^{bt} M_X(at)$ |
| ランダム和 | $M_S(t) = G_N(M_X(t))$ |
| キュムラントの加法性 | $\kappa_n(X+Y) = \kappa_n(X) + \kappa_n(Y)$ |

---

[確率論に戻る]({{ site.baseurl }}/semi-1/1-probability/) | [準1級トップ]({{ site.baseurl }}/semi-1/) | [トップページ]({{ site.baseurl }}/)
