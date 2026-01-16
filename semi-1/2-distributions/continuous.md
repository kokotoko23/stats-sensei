---
layout: default
title: 連続型分布 - 準1級対策
description: ガンマ、ベータ、非心分布、分布間の関係を解説
---

# 連続型分布

統計学で重要な連続型確率分布とその関係を学びます。

---

## 連続分布の全体像

連続型分布は測定データ（時間、長さ、割合など）をモデル化します。各分布には固有の「得意分野」があります。

```
連続分布の使い分け

データの特徴                    → 適切な分布
──────────────────────────────────────────────
正（+）の値、待ち時間           → 指数分布、ガンマ分布
0〜1 の範囲（割合、確率）       → ベータ分布
正の値、右裾が長い             → 対数正規分布
寿命・故障時間                  → ワイブル分布
正規分布からの導出              → カイ二乗、t、F 分布
検出力計算                      → 非心分布
```

**PDF** = **P**robability **D**ensity **F**unction（確率密度関数）

---

## 1. ガンマ分布

### ガンマ分布の直感的理解

ガンマ分布は「待ち時間の分布」を一般化したものです。指数分布は「1回のイベントまでの待ち時間」、ガンマ分布は「$\alpha$ 回のイベントまでの待ち時間」と解釈できます。

```
ガンマ分布のイメージ（α = 形状パラメータ）

α = 1（指数分布）      α = 2                α = 5
    │                    │  ╱╲                │    ╱──╲
    │╲                   │ ╱  ╲               │   ╱    ╲
    │ ╲                  │╱    ╲              │  ╱      ╲
    │  ╲                 │      ╲             │ ╱        ╲
    └───────            └───────             └───────────

・α が大きいほど「山」の形になる
・α が大きいほど正規分布に近づく
```

### 1.1 定義

$$f(x; \alpha, \beta) = \frac{\beta^\alpha}{\Gamma(\alpha)} x^{\alpha-1} e^{-\beta x}, \quad x > 0$$

- $\alpha > 0$：形状パラメータ（shape）
- $\beta > 0$：レートパラメータ（rate）

**注意**：スケールパラメータ $\theta = 1/\beta$ で定義する流儀もある。

### 1.2 期待値と分散

$$E[X] = \frac{\alpha}{\beta}, \quad \text{Var}(X) = \frac{\alpha}{\beta^2}$$

### 1.3 モーメント母関数

$$M_X(t) = \left(\frac{\beta}{\beta - t}\right)^\alpha, \quad t < \beta$$

### 1.4 特殊ケース

| 条件 | 分布 |
|-----|------|
| $\alpha = 1$ | 指数分布 $\text{Exp}(\beta)$ |
| $\alpha = n/2$, $\beta = 1/2$ | カイ二乗分布 $\chi^2_n$ |
| $\alpha = n$ | アーラン分布 |

### 1.5 加法性

$X_1 \sim \Gamma(\alpha_1, \beta)$, $X_2 \sim \Gamma(\alpha_2, \beta)$ が独立のとき：

$$X_1 + X_2 \sim \Gamma(\alpha_1 + \alpha_2, \beta)$$

---

## 2. ベータ分布

### ベータ分布の直感的理解

ベータ分布は「0から1の間の値」（確率、割合）をモデル化するのに最適です。パラメータ $\alpha$, $\beta$ で様々な形状を表現できます。

```
ベータ分布の形状（α, β の効果）

α=1, β=1（一様）    α=2, β=2（山型）     α=5, β=1（右寄り）
    ┌─────┐           ╱╲                      ╱│
    │     │          ╱  ╲                    ╱ │
    │     │         ╱    ╲                  ╱  │
    │     │        ╱      ╲                ╱   │
    └─────┘       └────────┘             └────┘
    0     1       0        1              0    1

・α > β → 右（1に近い方）に偏る
・α < β → 左（0に近い方）に偏る
・α = β → 対称
・α, β が大きい → より尖った形に
```

**ベイズ統計での重要性**：二項分布の成功確率 $p$ の事前分布として頻用されます。

### 2.1 定義

$$f(x; \alpha, \beta) = \frac{1}{B(\alpha, \beta)} x^{\alpha-1} (1-x)^{\beta-1}, \quad 0 < x < 1$$

ベータ関数：

$$B(\alpha, \beta) = \frac{\Gamma(\alpha)\Gamma(\beta)}{\Gamma(\alpha + \beta)} = \int_0^1 t^{\alpha-1}(1-t)^{\beta-1} dt$$

### 2.2 期待値と分散

$$E[X] = \frac{\alpha}{\alpha + \beta}$$

$$\text{Var}(X) = \frac{\alpha\beta}{(\alpha + \beta)^2(\alpha + \beta + 1)}$$

### 2.3 特殊ケース

| 条件 | 分布 |
|-----|------|
| $\alpha = \beta = 1$ | 一様分布 $\text{Uniform}(0, 1)$ |
| $\alpha = 1$ or $\beta = 1$ | べき乗分布 |

### 2.4 ガンマ分布との関係

$X \sim \Gamma(\alpha, 1)$, $Y \sim \Gamma(\beta, 1)$ が独立のとき：

$$\frac{X}{X + Y} \sim \text{Beta}(\alpha, \beta)$$

### 2.5 順序統計量との関係

$U_1, \ldots, U_n \sim \text{Uniform}(0, 1)$ のとき：

$$U_{(k)} \sim \text{Beta}(k, n - k + 1)$$

---

## 3. 対数正規分布

### 3.1 定義

$Y = \log X \sim N(\mu, \sigma^2)$ のとき、$X$ は対数正規分布。

$$f(x) = \frac{1}{x\sigma\sqrt{2\pi}} \exp\left(-\frac{(\log x - \mu)^2}{2\sigma^2}\right), \quad x > 0$$

### 3.2 期待値と分散

$$E[X] = \exp\left(\mu + \frac{\sigma^2}{2}\right)$$

$$\text{Var}(X) = \exp(2\mu + \sigma^2)(e^{\sigma^2} - 1)$$

### 3.3 特徴

- 右に裾が長い（正の歪み）
- 所得分布、粒子径分布などのモデルに使用
- 乗法的な変動のモデル

---

## 4. ワイブル分布

### 4.1 定義

$$f(x; k, \lambda) = \frac{k}{\lambda}\left(\frac{x}{\lambda}\right)^{k-1} \exp\left(-\left(\frac{x}{\lambda}\right)^k\right), \quad x > 0$$

- $k > 0$：形状パラメータ
- $\lambda > 0$：尺度パラメータ

### 4.2 期待値と分散

$$E[X] = \lambda \Gamma\left(1 + \frac{1}{k}\right)$$

$$\text{Var}(X) = \lambda^2 \left[\Gamma\left(1 + \frac{2}{k}\right) - \left(\Gamma\left(1 + \frac{1}{k}\right)\right)^2\right]$$

### 4.3 ハザード関数

$$h(x) = \frac{k}{\lambda}\left(\frac{x}{\lambda}\right)^{k-1}$$

| $k$ | ハザード |
|-----|---------|
| $k < 1$ | 減少 |
| $k = 1$ | 一定（指数分布） |
| $k > 1$ | 増加 |

### 4.4 生存時間分析での利用

信頼性工学、生存時間分析で頻用。

---

## 5. 非心分布

### 非心分布とは

「中心」分布（通常のカイ二乗、t、F分布）は、正規分布の平均が0のときに導かれます。平均が0でない場合に導かれるのが「非心」分布です。

```
中心分布 vs 非心分布

中心カイ二乗：Z₁² + Z₂² + ... + Zₙ²   （Zᵢ ~ N(0,1)）
非心カイ二乗：X₁² + X₂² + ... + Xₙ²   （Xᵢ ~ N(μᵢ,1)）
                                        ↑
                                   平均が0でない！

非心度 δ = Σμᵢ² は「0からのずれ」の総量を表す

δ = 0 のとき、非心分布 = 中心分布
```

### 5.1 非心カイ二乗分布

$X_i \sim N(\mu_i, 1)$ が独立のとき：

$$\sum_{i=1}^n X_i^2 \sim \chi^2_n(\delta)$$

非心度パラメータ：$\delta = \sum \mu_i^2$

**期待値**：$E[\chi^2_n(\delta)] = n + \delta$

**分散**：$\text{Var}(\chi^2_n(\delta)) = 2(n + 2\delta)$

### 5.2 非心t分布

$$T = \frac{Z + \delta}{\sqrt{V/n}}$$

- $Z \sim N(0, 1)$
- $V \sim \chi^2_n$
- $Z$ と $V$ は独立

$T$ は自由度 $n$、非心度 $\delta$ の非心t分布。

### 5.3 非心F分布

$$F = \frac{U/m}{V/n}$$

- $U \sim \chi^2_m(\delta)$（非心カイ二乗）
- $V \sim \chi^2_n$（中心カイ二乗）
- $U$ と $V$ は独立

$F$ は自由度 $(m, n)$、非心度 $\delta$ の非心F分布。

### 5.4 検出力計算での利用

非心分布は検定の検出力計算に重要：

- 対立仮説のもとでの検定統計量の分布
- サンプルサイズの設計

---

## 6. 分布間の関係

### 6.1 正規分布からの導出

$$Z \sim N(0, 1) \Rightarrow Z^2 \sim \chi^2_1$$

$$\sum_{i=1}^n Z_i^2 \sim \chi^2_n$$

$$\frac{Z}{\sqrt{\chi^2_n/n}} \sim t_n$$

$$\frac{\chi^2_m/m}{\chi^2_n/n} \sim F_{m,n}$$

### 6.2 ガンマ・ベータの関係

$$\Gamma(\alpha, \beta), \Gamma(\gamma, \beta) \text{ 独立} \Rightarrow \frac{X}{X+Y} \sim \text{Beta}(\alpha, \gamma)$$

### 6.3 極限関係

| 元の分布 | 極限 | 結果 |
|---------|------|------|
| $\text{Bin}(n, p)$ | $n \to \infty$, $np \to \lambda$ | $\text{Poi}(\lambda)$ |
| $\text{Poi}(\lambda)$ | $\lambda \to \infty$ | $N(\lambda, \lambda)$ |
| $t_n$ | $n \to \infty$ | $N(0, 1)$ |
| $\chi^2_n$ | $n \to \infty$ | $N(n, 2n)$ |
| $F_{m,n}$ | $n \to \infty$ | $\chi^2_m/m$ |

### 6.4 分布の関係図

```
連続分布の関係（正規分布を中心に）

                        正規分布 N(0,1)
                             │
              ┌──────────────┼──────────────┐
              ↓              ↓              ↓
           Z²の和         Z/√(V/n)       V₁/V₂
              ↓              ↓              ↓
        カイ二乗 χ²ₙ      t 分布 tₙ      F 分布 Fₘ,ₙ
              │                              │
              └──────────────────────────────┘
                    （χ²ₘ/m）/（χ²ₙ/n）

また：
・ガンマ分布の商 → ベータ分布
・一様分布の順序統計量 → ベータ分布
・指数分布の和 → ガンマ分布
```

---

## 7. 例題

### 例題1：ガンマ分布の加法性

$X \sim \Gamma(2, 1)$, $Y \sim \Gamma(3, 1)$ が独立のとき、$X + Y$ の分布を求めよ。

<details markdown="1">
<summary>解答を見る</summary>

### 解答

ガンマ分布の加法性より：

$$X + Y \sim \Gamma(2 + 3, 1) = \Gamma(5, 1)$$

**答え：$\Gamma(5, 1)$**

これはアーラン分布であり、5つの独立な指数分布の和に等しい。

</details>

---

### 例題2：ベータ分布の期待値

$X \sim \text{Beta}(3, 2)$ のとき、$E[X]$ と $\text{Var}(X)$ を求めよ。

<details markdown="1">
<summary>解答を見る</summary>

### 解答

$$E[X] = \frac{\alpha}{\alpha + \beta} = \frac{3}{3 + 2} = \frac{3}{5} = 0.6$$

$$\text{Var}(X) = \frac{\alpha\beta}{(\alpha + \beta)^2(\alpha + \beta + 1)}$$

$$= \frac{3 \times 2}{5^2 \times 6} = \frac{6}{150} = \frac{1}{25} = 0.04$$

**答え：$E[X] = 0.6$, $\text{Var}(X) = 0.04$**

</details>

---

### 例題3：非心カイ二乗分布

$X_1 \sim N(1, 1)$, $X_2 \sim N(2, 1)$ が独立のとき、$X_1^2 + X_2^2$ の期待値を求めよ。

<details markdown="1">
<summary>解答を見る</summary>

### 解答

非心度：$\delta = 1^2 + 2^2 = 1 + 4 = 5$

$X_1^2 + X_2^2 \sim \chi^2_2(5)$（非心カイ二乗、自由度2、非心度5）

期待値：

$$E[\chi^2_n(\delta)] = n + \delta = 2 + 5 = 7$$

**答え：7**

</details>

---

## 8. よくある誤解

### 誤解1：ガンマ分布のパラメータ

```
✗ 誤り：ガンマ分布のパラメータは統一されている

✓ 正しい：2つの流儀がある

流儀1：Γ(α, β) で β = rate（レート）
       E[X] = α/β

流儀2：Γ(α, θ) で θ = scale（スケール）= 1/β
       E[X] = αθ

問題文でどちらを使っているか確認が必要！
```

### 誤解2：対数正規分布のパラメータ

```
✗ 誤り：μ, σ² は対数正規分布の期待値と分散

✓ 正しい：μ, σ² は log X の期待値と分散
         X 自体の期待値は exp(μ + σ²/2) ≠ μ
```

### 誤解3：非心度パラメータ

```
✗ 誤り：非心度 δ は平均の和 Σμᵢ

✓ 正しい：非心度 δ は平均の二乗和 Σμᵢ²
         （だから常に δ ≥ 0）
```

---

## 9. 重要公式まとめ

| 分布 | 期待値 | 分散 |
|-----|--------|------|
| $\Gamma(\alpha, \beta)$ | $\alpha/\beta$ | $\alpha/\beta^2$ |
| $\text{Beta}(\alpha, \beta)$ | $\alpha/(\alpha+\beta)$ | $\alpha\beta/((\alpha+\beta)^2(\alpha+\beta+1))$ |
| 対数正規 | $e^{\mu + \sigma^2/2}$ | $e^{2\mu+\sigma^2}(e^{\sigma^2}-1)$ |
| $\chi^2_n(\delta)$ | $n + \delta$ | $2(n + 2\delta)$ |

---

[確率分布に戻る]({{ site.baseurl }}/semi-1/2-distributions/) | [準1級トップ]({{ site.baseurl }}/semi-1/) | [トップページ]({{ site.baseurl }}/)
