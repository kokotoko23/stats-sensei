---
layout: default
title: 推定の基礎 - 準1級対策
description: 最尤推定、十分統計量、フィッシャー情報量、クラメル・ラオの不等式を解説
---

# 推定の基礎

パラメータの点推定に関する理論的基盤を学びます。

---

## 推定理論の全体像

推定理論は「データからパラメータをどう推測するか」という問題に答えます。

```
推定の主要な問い

Q1: どうやって推定するか？ → 最尤推定法（MLE）、モーメント法
Q2: データの何を使えば十分？ → 十分統計量
Q3: 推定はどれくらい不確実？ → フィッシャー情報量
Q4: 推定の精度には限界がある？ → クラメル・ラオの不等式
Q5: 最良の推定量は何？ → UMVUE（一様最小分散不偏推定量）
```

**重要な略語**：
- **MLE** = **M**aximum **L**ikelihood **E**stimator（最尤推定量）
- **CRLB** = **C**ramér-**R**ao **L**ower **B**ound（クラメル・ラオ下界）
- **UMVUE** = **U**niformly **M**inimum **V**ariance **U**nbiased **E**stimator（一様最小分散不偏推定量）

---

## 1. 最尤推定法

### 最尤推定の考え方

「今観測されたデータが最も起こりやすくなるパラメータ値を選ぶ」という直感的なアイデアです。

```
最尤推定のイメージ

データ: x₁=3, x₂=5, x₃=4 が観測された

θ=2 のとき、このデータが出る確率 = 0.01（低い）
θ=4 のとき、このデータが出る確率 = 0.15（高い！）
θ=6 のとき、このデータが出る確率 = 0.05（中程度）

→ θ=4 を選ぶ（データが最も「尤もらしい」値）

          尤度
           │      ●
           │    ╱  ╲
           │   ╱    ╲
           │  ╱      ╲
           └──────────── θ
              2  4  6
                 ↑
              MLE
```

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

### 1.4 MLEの漸近正規性の導出

```
Step 1: スコア関数のテイラー展開
  MLE の定義より：U(θ̂) = ∂ℓ(θ̂)/∂θ = 0

  真のパラメータ θ₀ のまわりでテイラー展開：
  U(θ̂) ≈ U(θ₀) + (θ̂ - θ₀)·U'(θ₀)

  0 = U(θ₀) + (θ̂ - θ₀)·U'(θ₀)

Step 2: 変形
  θ̂ - θ₀ = -U(θ₀)/U'(θ₀)

  √n(θ̂ - θ₀) = -√n·U(θ₀)/U'(θ₀)
             = -(1/√n)·U(θ₀) / (U'(θ₀)/n)

Step 3: 各項の収束
  (a) (1/√n)·U(θ₀) = (1/√n)·Σᵢ uᵢ(θ₀)

      中心極限定理より：
      (1/√n)·Σ uᵢ →ᵈ N(0, I(θ₀))

      ∵ E[uᵢ] = 0, Var(uᵢ) = I(θ₀)

  (b) U'(θ₀)/n = (1/n)·Σᵢ u'ᵢ(θ₀)

      大数の法則より：
      (1/n)·Σ u'ᵢ →ᵖ E[u'ᵢ] = -I(θ₀)

Step 4: スラツキーの定理
  √n(θ̂ - θ₀) = -N(0, I(θ₀)) / (-I(θ₀))
             →ᵈ N(0, 1/I(θ₀))
```

**ポイント**：中心極限定理、大数の法則、スラツキーの定理の組み合わせ

---

## 2. 十分統計量

### 十分統計量の直感的理解

「十分統計量」とは、パラメータ推定に必要な情報をすべて含む要約統計量です。元データを捨てても、十分統計量だけあれば推定精度は変わりません。

```
十分統計量のイメージ

元データ: x₁=3, x₂=7, x₃=5, x₄=9, x₅=6 （正規分布からの標本）

平均 μ の推定に必要な情報は？
  → 標本平均 x̄ = 6 だけで十分！
  → 個々のデータの順序や配置は μ の推定に無関係

つまり：
  データ (3,7,5,9,6) と (9,6,7,3,5) は、
  x̄ が同じなら、μ の推定には等価

十分統計量 = 「パラメータについて知りたいことは全部詰まった要約」
```

### 2.1 定義

統計量 $T(\mathbf{X})$ が $\theta$ に対して**十分統計量**であるとは、$T$ が与えられたときの $\mathbf{X}$ の条件付き分布が $\theta$ に依存しないこと：

$$P(\mathbf{X} = \mathbf{x} \mid T(\mathbf{X}) = t)$$ が $\theta$ によらない

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

### フィッシャー情報量の直感的理解

フィッシャー情報量は「データがパラメータについてどれだけの情報を持っているか」を測ります。

```
フィッシャー情報量のイメージ

情報量が大きい場合（尤度関数が尖っている）：
    尤度
      │    │
      │   ╱╲      ← 峰が鋭い
      │  ╱  ╲
      └──────── θ
      θの推定が正確

情報量が小さい場合（尤度関数がなだらか）：
    尤度
      │  ╱──╲     ← 峰がなだらか
      │ ╱    ╲
      │╱      ╲
      └──────── θ
      θの推定が不正確

I(θ) = 尤度関数の「尖り具合」
     = 対数尤度の曲率（2階微分の符号反転）
```

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

### 4.4 クラメル・ラオ下界の導出

```
導出のアイデア：コーシー・シュワルツの不等式を使う

Step 1: 不偏推定量の性質
  T が θ の不偏推定量なら：E[T] = θ
  両辺を θ で微分：∂/∂θ E[T] = 1

  ∫ T·f(x;θ)dx の θ 微分を考えると：
  ∫ T · ∂f/∂θ dx = 1

Step 2: スコア関数の利用
  ∂logf/∂θ = (1/f)·(∂f/∂θ)
  より
  ∂f/∂θ = f · (∂logf/∂θ) = f · U(θ)

  したがって：
  ∫ T · f · U dx = E[T·U] = 1

Step 3: コーシー・シュワルツの不等式
  E[T·U] ≤ √(E[T²]) · √(E[U²])

  T を T-θ に置き換え（期待値は同じ1）：
  1 = E[(T-θ)·U] ≤ √(Var(T)) · √(I(θ))

  ※ E[U] = 0 なので E[U²] = Var(U) = I(θ)

Step 4: 結論
  1 ≤ √(Var(T)) · √(I(θ))

  両辺を2乗して整理：
  Var(T) ≥ 1/I(θ)  ← クラメル・ラオ下界
```

**ポイント**：
- スコア関数 $U(\theta)$ の期待値が0であること
- コーシー・シュワルツの等号成立条件 → 有効推定量の存在条件

---

## 5. ラオ・ブラックウェルの定理

### 5.1 定理

$T$ を $\theta$ の不偏推定量、$S$ を十分統計量とする。

$$T^* = E[T \mid S]$$ とおくと、$T^*$ も不偏推定量であり：

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

## 7. よくある誤解

### 誤解1：MLE は常に不偏

```
✗ 誤り：最尤推定量は常に不偏推定量である

✓ 正しい：MLE は一般に偏りを持つことがある
  例：正規分布の分散のMLE = (1/n)Σ(xᵢ - x̄)²
      これは不偏ではない（係数は 1/(n-1) で不偏）

  MLE は漸近的に不偏（n → ∞ で偏りが消える）
```

### 誤解2：クラメル・ラオ下界と有効推定量

```
✗ 誤り：「すべての分布で有効推定量（CRLB達成）が存在する」

✓ 正しい：有効推定量が存在するのは限定的な場合のみ
  ・指数型分布族では多くの場合存在
  ・一様分布 U(0, θ) では有効推定量は存在しない

CRLB は「下限」であり、必ずしも達成可能とは限らない
```

### 誤解3：十分統計量と推定量

```
✗ 誤り：「十分統計量がそのまま良い推定量」

✓ 正しい：十分統計量は推定量ではなく「要約」
  例：正規分布の十分統計量 = (Σxᵢ, Σxᵢ²)
      これは μ の推定量ではない

  十分統計量の「関数」として推定量を構成する
  （Σxᵢ から x̄ = Σxᵢ/n を作る）
```

---

## 8. 概念のつながり

```
推定理論の全体構造

データ x₁, ..., xₙ
    │
    ↓ 十分統計量
T(x) に要約（情報の損失なし）
    │
    ├─→ フィッシャー情報量 I(θ)
    │        │
    │        ↓
    │   クラメル・ラオ下界 1/(nI(θ))
    │        │
    │        ↓
    │   「これ以上精度は上がらない」という限界
    │
    ├─→ 最尤推定量（MLE）
    │        │
    │        ↓
    │   漸近的にCRLBを達成（漸近有効）
    │
    └─→ ラオ・ブラックウェル化
             │
             ↓
        UMVUE（有限標本で最良の不偏推定量）
```

---

## 9. 重要公式まとめ

| 項目 | 公式 |
|-----|------|
| 最尤推定量 | $\hat{\theta} = \arg\max_\theta \sum_i \log f(x_i; \theta)$ |
| 分解定理 | $L(\theta; \mathbf{x}) = g(T(\mathbf{x}), \theta) h(\mathbf{x})$ |
| フィッシャー情報量 | $I(\theta) = E[(U(\theta))^2] = -E[\ell''(\theta)]$ |
| クラメル・ラオ下界 | $\text{Var}(T) \geq 1/(nI(\theta))$ |
| MLEの漸近分散 | $\sqrt{n}(\hat{\theta} - \theta) \xrightarrow{d} N(0, I(\theta)^{-1})$ |

---

[統計的推測に戻る]({{ site.baseurl }}/semi-1/3-inference/) | [準1級トップ]({{ site.baseurl }}/semi-1/) | [トップページ]({{ site.baseurl }}/)
