---
layout: default
title: 推定の基礎 - 準1級対策
description: 最尤推定、十分統計量、フィッシャー情報量、クラメル・ラオの不等式を解説
---

# 推定の基礎

パラメータの点推定に関する理論的基盤を学びます。

---

## 1. 最尤推定法

### 1.1 最尤推定量（MLE）の定義

データ $\mathbf{x} = (x_1, \ldots, x_n)$ が与えられたとき、尤度関数を最大化するパラメータ値：

$$\hat{\theta}_{\text{MLE}} = \arg\max_\theta L(\theta; \mathbf{x})$$

尤度関数：

$$L(\theta; \mathbf{x}) = \prod_{i=1}^{n} f(x_i; \theta)$$

### 1.2 対数尤度関数

計算の便宜上、対数尤度を最大化：

$$\ell(\theta) = \log L(\theta) = \sum_{i=1}^{n} \log f(x_i; \theta)$$

**スコア関数**（対数尤度の微分）：

$$U(\theta) = \frac{\partial \ell(\theta)}{\partial \theta}$$

スコア関数の期待値は0：

$$E[U(\theta)] = 0$$

### 1.3 MLEの性質

| 性質 | 説明 |
|-----|------|
| 一致性 | $\hat{\theta}_n \xrightarrow{p} \theta$ （$n \to \infty$） |
| 漸近正規性 | $\sqrt{n}(\hat{\theta}_n - \theta) \xrightarrow{d} N(0, I(\theta)^{-1})$ |
| 漸近有効性 | クラメル・ラオ下界を漸近的に達成 |
| 不変性 | $g(\theta)$ のMLEは $g(\hat{\theta})$ |

---

## 2. 十分統計量

### 2.1 定義

統計量 $T(\mathbf{X})$ が $\theta$ に対して**十分統計量**であるとは、$T$ が与えられたときの $\mathbf{X}$ の条件付き分布が $\theta$ に依存しないこと：

$$P(\mathbf{X} = \mathbf{x} | T(\mathbf{X}) = t)$$ が $\theta$ によらない

### 2.2 分解定理（ネイマン・フィッシャーの分解定理）

$T(\mathbf{x})$ が十分統計量 $\Leftrightarrow$ 尤度関数が以下のように分解できる：

$$L(\theta; \mathbf{x}) = g(T(\mathbf{x}), \theta) \cdot h(\mathbf{x})$$

- $g$：$T$ と $\theta$ のみの関数
- $h$：$\theta$ に依存しない関数

### 2.3 最小十分統計量

他のすべての十分統計量から導出できる最も簡約な十分統計量。

**判定法**：

$$\frac{L(\theta; \mathbf{x})}{L(\theta; \mathbf{y})}$$ が $\theta$ によらない $\Leftrightarrow T(\mathbf{x}) = T(\mathbf{y})$

### 2.4 指数型分布族

$$f(x; \theta) = h(x) \exp\left(\eta(\theta) T(x) - A(\theta)\right)$$

この形の分布では $T(x)$ が十分統計量。

| 分布 | 十分統計量 |
|-----|-----------|
| 正規 $N(\mu, \sigma^2)$ | $(\sum x_i, \sum x_i^2)$ |
| ポアソン $\text{Poi}(\lambda)$ | $\sum x_i$ |
| 指数 $\text{Exp}(\lambda)$ | $\sum x_i$ |
| 二項 $\text{Bin}(n, p)$ | $\sum x_i$ |

---

## 3. フィッシャー情報量

### 3.1 定義

スコア関数の分散：

$$I(\theta) = E\left[\left(\frac{\partial \log f(X; \theta)}{\partial \theta}\right)^2\right]$$

または、対数尤度の2階微分の期待値（符号反転）：

$$I(\theta) = -E\left[\frac{\partial^2 \log f(X; \theta)}{\partial \theta^2}\right]$$

### 3.2 $n$ 個の独立標本の情報量

$$I_n(\theta) = n \cdot I(\theta)$$

### 3.3 多次元パラメータの場合

フィッシャー情報行列：

$$[I(\boldsymbol{\theta})]_{jk} = E\left[\frac{\partial \log f}{\partial \theta_j} \cdot \frac{\partial \log f}{\partial \theta_k}\right]$$

### 3.4 代表的な分布の情報量

| 分布 | パラメータ | フィッシャー情報量 |
|-----|-----------|------------------|
| $N(\mu, \sigma^2)$ | $\mu$（$\sigma^2$既知） | $1/\sigma^2$ |
| $N(\mu, \sigma^2)$ | $\sigma^2$（$\mu$既知） | $1/(2\sigma^4)$ |
| $\text{Ber}(p)$ | $p$ | $1/(p(1-p))$ |
| $\text{Poi}(\lambda)$ | $\lambda$ | $1/\lambda$ |
| $\text{Exp}(\lambda)$ | $\lambda$ | $1/\lambda^2$ |

---

## 4. クラメル・ラオの不等式

### 4.1 定理

$T$ を $\theta$ の不偏推定量とすると：

$$\text{Var}(T) \geq \frac{1}{I_n(\theta)} = \frac{1}{n \cdot I(\theta)}$$

右辺を**クラメル・ラオ下界**（CRLB）という。

### 4.2 有効推定量

クラメル・ラオ下界を達成する不偏推定量を**有効推定量**という。

有効推定量が存在する条件：

$$\frac{\partial \log L(\theta)}{\partial \theta} = a(\theta)(T - \theta)$$

（スコア関数が推定量の線形関数）

### 4.3 有効性（効率）

推定量 $T$ の効率：

$$e(T) = \frac{\text{CRLB}}{\text{Var}(T)} \leq 1$$

---

## 5. ラオ・ブラックウェルの定理

### 5.1 定理

$T$ を $\theta$ の不偏推定量、$S$ を十分統計量とする。

$$T^* = E[T | S]$$ とおくと、$T^*$ も不偏推定量であり：

$$\text{Var}(T^*) \leq \text{Var}(T)$$

### 5.2 完備十分統計量

十分統計量 $T$ が**完備**であるとは：

任意の関数 $g$ に対し $E[g(T)] = 0$ （すべての $\theta$ で） $\Rightarrow P(g(T) = 0) = 1$

### 5.3 レーマン・シェッフェの定理

完備十分統計量の関数で不偏推定量があれば、それが**一様最小分散不偏推定量（UMVUE）**。

---

## 6. 例題

### 例題1：MLEの導出

$X_1, \ldots, X_n$ が独立に指数分布 $\text{Exp}(\lambda)$ に従うとき、$\lambda$ のMLEを求めよ。

<details markdown="1">
<summary>解答を見る</summary>

### 解答

尤度関数：

$$L(\lambda) = \prod_{i=1}^{n} \lambda e^{-\lambda x_i} = \lambda^n \exp\left(-\lambda \sum_{i=1}^{n} x_i\right)$$

対数尤度：

$$\ell(\lambda) = n \log \lambda - \lambda \sum_{i=1}^{n} x_i$$

微分して0とおく：

$$\frac{d\ell}{d\lambda} = \frac{n}{\lambda} - \sum_{i=1}^{n} x_i = 0$$

$$\hat{\lambda}_{\text{MLE}} = \frac{n}{\sum_{i=1}^{n} x_i} = \frac{1}{\bar{x}}$$

**答え：$\hat{\lambda} = 1/\bar{x}$**

</details>

---

### 例題2：フィッシャー情報量の計算

ベルヌーイ分布 $\text{Ber}(p)$ のフィッシャー情報量を求めよ。

<details markdown="1">
<summary>解答を見る</summary>

### 解答

確率関数：

$$f(x; p) = p^x (1-p)^{1-x}, \quad x \in \{0, 1\}$$

対数尤度：

$$\log f(x; p) = x \log p + (1-x) \log(1-p)$$

スコア関数：

$$\frac{\partial \log f}{\partial p} = \frac{x}{p} - \frac{1-x}{1-p} = \frac{x - p}{p(1-p)}$$

2階微分：

$$\frac{\partial^2 \log f}{\partial p^2} = -\frac{x}{p^2} - \frac{1-x}{(1-p)^2}$$

期待値：

$$I(p) = -E\left[\frac{\partial^2 \log f}{\partial p^2}\right] = \frac{p}{p^2} + \frac{1-p}{(1-p)^2} = \frac{1}{p} + \frac{1}{1-p} = \frac{1}{p(1-p)}$$

**答え：$I(p) = \frac{1}{p(1-p)}$**

</details>

---

### 例題3：十分統計量と分解定理

$X_1, \ldots, X_n$ が独立に $N(\mu, 1)$ に従うとき、$\bar{X}$ が $\mu$ に対する十分統計量であることを示せ。

<details markdown="1">
<summary>解答を見る</summary>

### 解答

尤度関数：

$$L(\mu) = \prod_{i=1}^{n} \frac{1}{\sqrt{2\pi}} \exp\left(-\frac{(x_i - \mu)^2}{2}\right)$$

$$= (2\pi)^{-n/2} \exp\left(-\frac{1}{2}\sum_{i=1}^{n}(x_i - \mu)^2\right)$$

指数部分を展開：

$$\sum_{i=1}^{n}(x_i - \mu)^2 = \sum_{i=1}^{n}x_i^2 - 2\mu\sum_{i=1}^{n}x_i + n\mu^2$$

$$= \sum_{i=1}^{n}x_i^2 - 2n\mu\bar{x} + n\mu^2$$

よって：

$$L(\mu) = \underbrace{(2\pi)^{-n/2} \exp\left(-\frac{1}{2}\sum_{i=1}^{n}x_i^2\right)}_{h(\mathbf{x})} \cdot \underbrace{\exp\left(n\mu\bar{x} - \frac{n\mu^2}{2}\right)}_{g(\bar{x}, \mu)}$$

分解定理より、$\bar{X}$ は十分統計量。

**答え：分解定理により証明完了**

</details>

---

## 7. 重要公式まとめ

| 項目 | 公式 |
|-----|------|
| 最尤推定量 | $\hat{\theta} = \arg\max_\theta \sum_i \log f(x_i; \theta)$ |
| 分解定理 | $L(\theta; \mathbf{x}) = g(T(\mathbf{x}), \theta) h(\mathbf{x})$ |
| フィッシャー情報量 | $I(\theta) = E[(U(\theta))^2] = -E[\ell''(\theta)]$ |
| クラメル・ラオ下界 | $\text{Var}(T) \geq 1/(nI(\theta))$ |
| MLEの漸近分散 | $\sqrt{n}(\hat{\theta} - \theta) \xrightarrow{d} N(0, I(\theta)^{-1})$ |

---

[統計的推測に戻る]({{ site.baseurl }}/semi-1/3-inference/) | [準1級トップ]({{ site.baseurl }}/semi-1/) | [トップページ]({{ site.baseurl }}/)
