---
layout: default
title: 積率と特性値 - 準1級対策
description: 期待値、分散、歪度、尖度、各種不等式を解説
---

# 積率と分布の特性値

分布の形状を特徴づける量と重要な不等式を学びます。

---

## 1. 積率（モーメント）

### 1.1 原点まわりの積率

$$\mu'_n = E[X^n]$$

- $\mu'_1 = E[X]$（平均）
- $\mu'_2 = E[X^2]$

### 1.2 平均まわりの積率（中心積率）

$$\mu_n = E[(X - \mu)^n]$$

- $\mu_1 = 0$
- $\mu_2 = \text{Var}(X) = \sigma^2$（分散）
- $\mu_3$：3次中心積率（歪度に関連）
- $\mu_4$：4次中心積率（尖度に関連）

### 1.3 原点積率と中心積率の関係

$$\mu_2 = \mu'_2 - (\mu'_1)^2$$

$$\mu_3 = \mu'_3 - 3\mu'_1\mu'_2 + 2(\mu'_1)^3$$

$$\mu_4 = \mu'_4 - 4\mu'_1\mu'_3 + 6(\mu'_1)^2\mu'_2 - 3(\mu'_1)^4$$

---

## 2. 歪度（Skewness）

### 2.1 定義

分布の非対称性を測る：

$$\gamma_1 = \frac{\mu_3}{\sigma^3} = \frac{E[(X-\mu)^3]}{(E[(X-\mu)^2])^{3/2}}$$

### 2.2 解釈

| 値 | 意味 |
|---|------|
| $\gamma_1 > 0$ | 右に裾が長い（正の歪み） |
| $\gamma_1 = 0$ | 対称分布 |
| $\gamma_1 < 0$ | 左に裾が長い（負の歪み） |

### 2.3 代表的な分布の歪度

| 分布 | 歪度 |
|-----|------|
| 正規分布 | 0 |
| 指数分布 | 2 |
| ポアソン分布 $\text{Poi}(\lambda)$ | $1/\sqrt{\lambda}$ |
| カイ二乗分布 $\chi^2_k$ | $\sqrt{8/k}$ |

---

## 3. 尖度（Kurtosis）

### 3.1 定義

分布の尖り具合（裾の重さ）を測る：

$$\gamma_2 = \frac{\mu_4}{\sigma^4} = \frac{E[(X-\mu)^4]}{(E[(X-\mu)^2])^2}$$

### 3.2 超過尖度（Excess Kurtosis）

正規分布を基準（尖度=3）として：

$$\text{超過尖度} = \gamma_2 - 3$$

### 3.3 解釈

| 値 | 意味 |
|---|------|
| $\gamma_2 > 3$ | 正規分布より尖っている（尖峰） |
| $\gamma_2 = 3$ | 正規分布と同じ |
| $\gamma_2 < 3$ | 正規分布より平坦（扁峰） |

### 3.4 代表的な分布の尖度

| 分布 | 尖度 | 超過尖度 |
|-----|-----|---------|
| 正規分布 | 3 | 0 |
| 一様分布 | 1.8 | -1.2 |
| 指数分布 | 9 | 6 |
| t分布 $t_\nu$ ($\nu > 4$) | $3 + 6/(\nu-4)$ | $6/(\nu-4)$ |

---

## 4. 共分散と相関

### 4.1 共分散

$$\text{Cov}(X, Y) = E[(X-\mu_X)(Y-\mu_Y)] = E[XY] - E[X]E[Y]$$

### 4.2 相関係数

$$\rho_{XY} = \frac{\text{Cov}(X, Y)}{\sigma_X \sigma_Y}$$

- $-1 \leq \rho \leq 1$
- $|\rho| = 1$ $\Leftrightarrow$ 完全な線形関係

### 4.3 分散の公式

$$\text{Var}(X + Y) = \text{Var}(X) + \text{Var}(Y) + 2\text{Cov}(X, Y)$$

独立なら：$\text{Var}(X + Y) = \text{Var}(X) + \text{Var}(Y)$

---

## 5. マルコフの不等式

### 5.1 定理

$X \geq 0$ かつ $a > 0$ のとき：

$$P(X \geq a) \leq \frac{E[X]}{a}$$

### 5.2 証明の概略

$$E[X] = E[X \cdot \mathbf{1}_{X \geq a}] + E[X \cdot \mathbf{1}_{X < a}] \geq a \cdot P(X \geq a)$$

---

## 6. チェビシェフの不等式

### 6.1 定理

任意の確率変数 $X$（$\text{Var}(X) < \infty$）に対し：

$$P(|X - \mu| \geq k\sigma) \leq \frac{1}{k^2}$$

または：

$$P(|X - \mu| \geq c) \leq \frac{\sigma^2}{c^2}$$

### 6.2 証明

マルコフの不等式を $(X - \mu)^2$ に適用：

$$P(|X - \mu| \geq c) = P((X - \mu)^2 \geq c^2) \leq \frac{E[(X-\mu)^2]}{c^2} = \frac{\sigma^2}{c^2}$$

### 6.3 応用例

| $k$ | $P(\|X-\mu\| \geq k\sigma)$ の上界 |
|-----|--------------------------------|
| 2 | 25% |
| 3 | 11.1% |
| 4 | 6.25% |

---

## 7. イェンセンの不等式

### 7.1 凸関数

$g$ が**凸関数**：任意の $x, y$, $0 \leq \lambda \leq 1$ に対し

$$g(\lambda x + (1-\lambda)y) \leq \lambda g(x) + (1-\lambda) g(y)$$

### 7.2 定理

$g$ が凸関数のとき：

$$g(E[X]) \leq E[g(X)]$$

$g$ が凹関数のとき：

$$g(E[X]) \geq E[g(X)]$$

### 7.3 応用例

- $g(x) = x^2$（凸）：$(E[X])^2 \leq E[X^2]$
- $g(x) = \log x$（凹）：$\log E[X] \geq E[\log X]$
- $g(x) = e^x$（凸）：$e^{E[X]} \leq E[e^X]$

---

## 8. ヘルダーの不等式・ミンコフスキーの不等式

### 8.1 ヘルダーの不等式

$1/p + 1/q = 1$（$p, q > 1$）のとき：

$$E[|XY|] \leq (E[|X|^p])^{1/p} (E[|Y|^q])^{1/q}$$

$p = q = 2$ のとき**コーシー・シュワルツの不等式**：

$$|E[XY]|^2 \leq E[X^2] E[Y^2]$$

### 8.2 ミンコフスキーの不等式

$p \geq 1$ のとき：

$$(E[|X+Y|^p])^{1/p} \leq (E[|X|^p])^{1/p} + (E[|Y|^p])^{1/p}$$

---

## 9. 例題

### 例題1：歪度の計算

$X \sim \text{Exp}(\lambda)$ の歪度を求めよ。

<details markdown="1">
<summary>解答を見る</summary>

### 解答

指数分布の積率：
- $E[X] = 1/\lambda$
- $E[X^2] = 2/\lambda^2$
- $E[X^3] = 6/\lambda^3$

分散：
$$\sigma^2 = E[X^2] - (E[X])^2 = \frac{2}{\lambda^2} - \frac{1}{\lambda^2} = \frac{1}{\lambda^2}$$

$$\sigma = \frac{1}{\lambda}$$

3次中心積率：
$$\mu_3 = E[X^3] - 3E[X]E[X^2] + 2(E[X])^3$$

$$= \frac{6}{\lambda^3} - 3 \cdot \frac{1}{\lambda} \cdot \frac{2}{\lambda^2} + 2 \cdot \frac{1}{\lambda^3}$$

$$= \frac{6}{\lambda^3} - \frac{6}{\lambda^3} + \frac{2}{\lambda^3} = \frac{2}{\lambda^3}$$

歪度：
$$\gamma_1 = \frac{\mu_3}{\sigma^3} = \frac{2/\lambda^3}{1/\lambda^3} = 2$$

**答え：$\gamma_1 = 2$**

</details>

---

### 例題2：チェビシェフの不等式

$E[X] = 100$, $\text{Var}(X) = 25$ のとき、$P(|X - 100| \geq 15)$ の上界を求めよ。

<details markdown="1">
<summary>解答を見る</summary>

### 解答

$\sigma = \sqrt{25} = 5$

$k\sigma = 15$ より $k = 3$

チェビシェフの不等式：

$$P(|X - 100| \geq 15) \leq \frac{1}{k^2} = \frac{1}{9} \approx 0.111$$

**答え：$\leq 1/9 \approx 11.1\%$**

</details>

---

### 例題3：イェンセンの不等式

$X > 0$ のとき、$E[\sqrt{X}]$ と $\sqrt{E[X]}$ の大小関係を示せ。

<details markdown="1">
<summary>解答を見る</summary>

### 解答

$g(x) = \sqrt{x}$ は凹関数（$g''(x) = -\frac{1}{4}x^{-3/2} < 0$）

イェンセンの不等式（凹関数版）より：

$$g(E[X]) \geq E[g(X)]$$

$$\sqrt{E[X]} \geq E[\sqrt{X}]$$

**答え：$\sqrt{E[X]} \geq E[\sqrt{X}]$**

（等号は $X$ が定数のときのみ）

</details>

---

## 10. 重要公式まとめ

| 項目 | 公式 |
|-----|------|
| 分散 | $\text{Var}(X) = E[X^2] - (E[X])^2$ |
| 歪度 | $\gamma_1 = E[(X-\mu)^3]/\sigma^3$ |
| 尖度 | $\gamma_2 = E[(X-\mu)^4]/\sigma^4$ |
| マルコフの不等式 | $P(X \geq a) \leq E[X]/a$ |
| チェビシェフの不等式 | $P(\|X-\mu\| \geq k\sigma) \leq 1/k^2$ |
| イェンセン（凸） | $g(E[X]) \leq E[g(X)]$ |
| コーシー・シュワルツ | $\|E[XY]\|^2 \leq E[X^2]E[Y^2]$ |

---

[確率論に戻る]({{ site.baseurl }}/semi-1/1-probability/) | [準1級トップ]({{ site.baseurl }}/semi-1/) | [トップページ]({{ site.baseurl }}/)
