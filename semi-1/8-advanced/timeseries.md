---
layout: default
title: 時系列解析 - 準1級対策
description: AR、MA、ARIMA、定常性を解説
---

# 時系列解析

時間の経過とともに変化するデータの分析手法を学びます。

---

## 1. 基本概念

### 1.1 時系列データ

$$\{Y_t\}_{t=1}^T = Y_1, Y_2, \ldots, Y_T$$

時点 $t$ における観測値の系列。

### 1.2 定常性

**弱定常（共分散定常）**：
1. $E[Y_t] = \mu$（一定）
2. $\text{Var}(Y_t) = \sigma^2$（一定）
3. $\text{Cov}(Y_t, Y_{t+h}) = \gamma(h)$（$t$ に依存しない）

**強定常**：同時分布が時間シフトで不変。

### 1.3 自己共分散関数

$$\gamma(h) = \text{Cov}(Y_t, Y_{t+h})$$

### 1.4 自己相関関数（ACF）

$$\rho(h) = \frac{\gamma(h)}{\gamma(0)} = \text{Cor}(Y_t, Y_{t+h})$$

---

## 2. AR（自己回帰）モデル

### 2.1 AR(1)モデル

$$Y_t = \phi Y_{t-1} + \epsilon_t$$

$\epsilon_t \sim \text{WN}(0, \sigma^2)$（ホワイトノイズ）

**定常条件**：$|\phi| < 1$

### 2.2 AR(1)の性質

$$E[Y_t] = 0$$

$$\text{Var}(Y_t) = \frac{\sigma^2}{1 - \phi^2}$$

$$\rho(h) = \phi^h$$（指数減衰）

### 2.3 AR(p)モデル

$$Y_t = \phi_1 Y_{t-1} + \phi_2 Y_{t-2} + \cdots + \phi_p Y_{t-p} + \epsilon_t$$

**特性方程式**：

$$1 - \phi_1 z - \phi_2 z^2 - \cdots - \phi_p z^p = 0$$

すべての根が単位円の外 $\Leftrightarrow$ 定常

### 2.4 偏自己相関関数（PACF）

$$\phi_{hh} = \text{Cor}(Y_t, Y_{t+h} | Y_{t+1}, \ldots, Y_{t+h-1})$$

AR(p)では：$\phi_{hh} = 0$ （$h > p$）

---

## 3. MA（移動平均）モデル

### 3.1 MA(1)モデル

$$Y_t = \epsilon_t + \theta \epsilon_{t-1}$$

常に定常。

### 3.2 MA(1)の性質

$$E[Y_t] = 0$$

$$\text{Var}(Y_t) = (1 + \theta^2)\sigma^2$$

$$\rho(1) = \frac{\theta}{1 + \theta^2}, \quad \rho(h) = 0 \text{ for } h > 1$$

### 3.3 MA(q)モデル

$$Y_t = \epsilon_t + \theta_1 \epsilon_{t-1} + \cdots + \theta_q \epsilon_{t-q}$$

ACFは $h > q$ で0（カットオフ）。

### 3.4 反転可能性

MA(1)が反転可能：$|\theta| < 1$

反転可能なら無限次のARで表現可能。

---

## 4. ARMA・ARIMAモデル

### 4.1 ARMA(p, q)モデル

$$Y_t = \phi_1 Y_{t-1} + \cdots + \phi_p Y_{t-p} + \epsilon_t + \theta_1 \epsilon_{t-1} + \cdots + \theta_q \epsilon_{t-q}$$

### 4.2 後退オペレータ

$B Y_t = Y_{t-1}$

AR(p)：$(1 - \phi_1 B - \cdots - \phi_p B^p) Y_t = \epsilon_t$

MA(q)：$Y_t = (1 + \theta_1 B + \cdots + \theta_q B^q) \epsilon_t$

### 4.3 差分

$$\Delta Y_t = Y_t - Y_{t-1} = (1 - B) Y_t$$

### 4.4 ARIMA(p, d, q)モデル

$$\Delta^d Y_t$$ が ARMA(p, q) に従う。

- $d$：差分の次数（単位根の数）
- 非定常時系列への対応

### 4.5 モデル同定

| モデル | ACF | PACF |
|-------|-----|------|
| AR(p) | 徐々に減衰 | $p$ でカットオフ |
| MA(q) | $q$ でカットオフ | 徐々に減衰 |
| ARMA(p,q) | 徐々に減衰 | 徐々に減衰 |

---

## 5. 予測

### 5.1 最小二乗予測

$$\hat{Y}_{T+h} = E[Y_{T+h} | Y_1, \ldots, Y_T]$$

### 5.2 予測誤差分散

AR(1)の場合：

$$\text{Var}(Y_{T+h} - \hat{Y}_{T+h}) = \sigma^2 \frac{1 - \phi^{2h}}{1 - \phi^2}$$

$h \to \infty$ で $\gamma(0)$ に収束。

---

## 6. 例題

### 例題1：AR(1)の自己相関

$Y_t = 0.6 Y_{t-1} + \epsilon_t$ のとき、$\rho(2)$ を求めよ。

<details markdown="1">
<summary>解答を見る</summary>

### 解答

AR(1)では $\rho(h) = \phi^h$

$$\rho(2) = 0.6^2 = 0.36$$

**答え：0.36**

</details>

---

### 例題2：MA(1)の分散

$Y_t = \epsilon_t + 0.5\epsilon_{t-1}$（$\sigma^2 = 4$）のとき、$\text{Var}(Y_t)$ を求めよ。

<details markdown="1">
<summary>解答を見る</summary>

### 解答

$$\text{Var}(Y_t) = (1 + \theta^2)\sigma^2 = (1 + 0.25) \times 4 = 5$$

**答え：5**

</details>

---

### 例題3：モデル同定

ACFが1次で急激に減少し、PACFが徐々に減衰する場合、適切なモデルは何か。

<details markdown="1">
<summary>解答を見る</summary>

### 解答

- ACFが急激に減少（カットオフ）→ MA成分
- PACFが徐々に減衰 → MA成分（ARならカットオフ）

ACFが1次でカットオフ → MA(1)

**答え：MA(1)**

</details>

---

## 7. 重要公式まとめ

| 項目 | 公式 |
|-----|------|
| AR(1) ACF | $\rho(h) = \phi^h$ |
| AR(1) 分散 | $\text{Var}(Y_t) = \sigma^2/(1-\phi^2)$ |
| MA(1) ACF | $\rho(1) = \theta/(1+\theta^2)$, $\rho(h)=0$ ($h>1$) |
| MA(1) 分散 | $\text{Var}(Y_t) = (1+\theta^2)\sigma^2$ |
| 差分 | $\Delta Y_t = Y_t - Y_{t-1}$ |

---

[発展的手法に戻る]({{ site.baseurl }}/semi-1/8-advanced/) | [準1級トップ]({{ site.baseurl }}/semi-1/) | [トップページ]({{ site.baseurl }}/)
