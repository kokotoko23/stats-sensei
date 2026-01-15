---
layout: default
title: 重回帰と正則化 - 準1級対策
description: リッジ回帰、LASSO、Elastic Netによる正則化手法を解説
---

# 重回帰と正則化

正則化（Regularization）は、過学習を防ぎ、多重共線性に対処するための手法です。

---

## 1. 正則化の必要性

### 1.1 過学習の問題

- 訓練データに過度に適合
- 新しいデータへの予測精度が低下
- パラメータ数が多い、サンプルサイズが小さい場合に発生

### 1.2 多重共線性の問題

- 説明変数間に強い相関
- 係数の推定が不安定
- 分散が大きくなる

### 1.3 バイアス・バリアンストレードオフ

$$\text{MSE} = \text{Bias}^2 + \text{Variance}$$

正則化により：
- バイアスは増加
- バリアンスは減少
- 総合的な予測精度が向上することがある

---

## 2. リッジ回帰（L2正則化）

### 2.1 目的関数

$$\min_{\boldsymbol{\beta}} \left\{ \sum_{i=1}^{n}(y_i - \mathbf{x}_i^\top\boldsymbol{\beta})^2 + \lambda \sum_{j=1}^{p}\beta_j^2 \right\}$$

または同等の制約付き最適化：

$$\min_{\boldsymbol{\beta}} \text{RSS} \quad \text{s.t.} \quad \sum_{j=1}^{p}\beta_j^2 \leq t$$

### 2.2 解の閉形式

$$\hat{\boldsymbol{\beta}}_{\text{ridge}} = (\mathbf{X}^\top\mathbf{X} + \lambda\mathbf{I})^{-1}\mathbf{X}^\top\mathbf{y}$$

### 2.3 特徴

- 係数を0に近づけるが、**完全に0にはならない**
- すべての変数がモデルに残る
- 多重共線性に強い

### 2.4 スケーリングの重要性

変数のスケールが異なると、ペナルティの影響が不均等になる。

→ **標準化**してからリッジ回帰を適用

---

## 3. LASSO（L1正則化）

### 3.1 目的関数

$$\min_{\boldsymbol{\beta}} \left\{ \sum_{i=1}^{n}(y_i - \mathbf{x}_i^\top\boldsymbol{\beta})^2 + \lambda \sum_{j=1}^{p}|\beta_j| \right\}$$

### 3.2 特徴

- 一部の係数を**完全に0**にする（スパース解）
- **変数選択**の機能を持つ
- 閉形式の解がない（数値最適化が必要）

### 3.3 ソフト閾値関数

単変量の場合、LASSO解は：

$$\hat{\beta} = \text{sign}(\hat{\beta}_{\text{OLS}}) \cdot \max(|\hat{\beta}_{\text{OLS}}| - \lambda, 0)$$

---

## 4. Elastic Net

### 4.1 目的関数

L1とL2を組み合わせ：

$$\min_{\boldsymbol{\beta}} \left\{ \text{RSS} + \lambda_1 \sum_{j}|\beta_j| + \lambda_2 \sum_{j}\beta_j^2 \right\}$$

または混合比 $\alpha$ を使って：

$$\min_{\boldsymbol{\beta}} \left\{ \text{RSS} + \lambda \left( \alpha \sum_{j}|\beta_j| + \frac{1-\alpha}{2}\sum_{j}\beta_j^2 \right) \right\}$$

### 4.2 特徴

- $\alpha = 1$：LASSO
- $\alpha = 0$：リッジ
- LASSOの変数選択能力 + リッジの安定性

---

## 5. 正則化パラメータの選択

### 5.1 交差検証（Cross-Validation）

1. データを $K$ 分割
2. 各 $\lambda$ に対し、K-fold CVで予測誤差を計算
3. 予測誤差が最小の $\lambda$ を選択

### 5.2 情報量規準

- AIC
- BIC（より強いペナルティ）

### 5.3 1標準誤差ルール

CV誤差が最小値から1標準誤差以内の、最も単純なモデル（最大の $\lambda$）を選択。

---

## 6. リッジ vs LASSO の比較

| 特徴 | リッジ | LASSO |
|-----|-------|-------|
| ペナルティ | L2（二乗和） | L1（絶対値和） |
| 係数 | 0に縮小 | 0になる（スパース） |
| 変数選択 | なし | あり |
| 多重共線性 | 強い | やや弱い |
| 解の一意性 | 常に一意 | 必ずしも一意でない |
| 計算 | 閉形式解 | 反復最適化 |

---

## 7. 例題

### 例題1：リッジ回帰の計算

単純なケース：$\mathbf{X}^\top\mathbf{X} = \begin{pmatrix} 1 & 0 \\ 0 & 1 \end{pmatrix}$, $\mathbf{X}^\top\mathbf{y} = \begin{pmatrix} 2 \\ 3 \end{pmatrix}$, $\lambda = 0.5$ のとき、リッジ推定量を求めよ。

<details markdown="1">
<summary>解答を見る</summary>

### 解答

$$\hat{\boldsymbol{\beta}}_{\text{ridge}} = (\mathbf{X}^\top\mathbf{X} + \lambda\mathbf{I})^{-1}\mathbf{X}^\top\mathbf{y}$$

$$= \begin{pmatrix} 1.5 & 0 \\ 0 & 1.5 \end{pmatrix}^{-1} \begin{pmatrix} 2 \\ 3 \end{pmatrix}$$

$$= \begin{pmatrix} 1/1.5 & 0 \\ 0 & 1/1.5 \end{pmatrix} \begin{pmatrix} 2 \\ 3 \end{pmatrix} = \begin{pmatrix} 4/3 \\ 2 \end{pmatrix} \approx \begin{pmatrix} 1.33 \\ 2.0 \end{pmatrix}$$

**答え：** $\hat{\beta}_1 \approx 1.33$, $\hat{\beta}_2 = 2.0$

OLS推定値 $(2, 3)$ より縮小されている。

</details>

---

### 例題2：縮小の程度

OLS推定値が $\hat{\beta}_{\text{OLS}} = 5$ のとき、リッジとLASSOでそれぞれどの程度縮小されるか概念的に説明せよ。

<details markdown="1">
<summary>解答を見る</summary>

### 解答

**リッジ回帰**（単変量、$\mathbf{X}^\top\mathbf{X} = 1$ の場合）：

$$\hat{\beta}_{\text{ridge}} = \frac{1}{1+\lambda} \hat{\beta}_{\text{OLS}} = \frac{5}{1+\lambda}$$

$\lambda = 1$ なら $\hat{\beta}_{\text{ridge}} = 2.5$

**LASSO**：

$$\hat{\beta}_{\text{LASSO}} = \text{sign}(5) \cdot \max(5 - \lambda, 0) = \max(5 - \lambda, 0)$$

$\lambda = 3$ なら $\hat{\beta}_{\text{LASSO}} = 2$
$\lambda = 6$ なら $\hat{\beta}_{\text{LASSO}} = 0$（変数が除外）

**違い**：リッジは比例的に縮小、LASSOは一定量を引く

</details>

---

### 例題3：交差検証

5-fold CVで以下の結果が得られた。最適な $\lambda$ は？

| $\lambda$ | CV誤差 | 標準誤差 |
|----------|--------|---------|
| 0.01 | 2.50 | 0.15 |
| 0.1 | 2.35 | 0.12 |
| 1.0 | 2.40 | 0.10 |
| 10 | 3.20 | 0.20 |

<details markdown="1">
<summary>解答を見る</summary>

### 解答

**最小CV誤差**：$\lambda = 0.1$ で 2.35

**1標準誤差ルール**：
- 最小値 + 1SE = 2.35 + 0.12 = 2.47
- この範囲内で最大の $\lambda$ は 1.0（CV誤差 2.40 < 2.47）

**答え**：
- 最小CV誤差なら $\lambda = 0.1$
- 1標準誤差ルールなら $\lambda = 1.0$（よりスパースなモデル）

</details>

---

## 8. 重要公式まとめ

| 項目 | 公式 |
|-----|------|
| リッジ推定量 | $(\mathbf{X}^\top\mathbf{X}+\lambda\mathbf{I})^{-1}\mathbf{X}^\top\mathbf{y}$ |
| リッジ目的関数 | $\text{RSS} + \lambda\sum\beta_j^2$ |
| LASSO目的関数 | $\text{RSS} + \lambda\sum|\beta_j|$ |
| Elastic Net | $\text{RSS} + \lambda(\alpha\sum|\beta_j| + \frac{1-\alpha}{2}\sum\beta_j^2)$ |
| ソフト閾値 | $\text{sign}(\beta)\max(|\beta|-\lambda, 0)$ |

---

[回帰分析に戻る]({{ site.baseurl }}/semi-1/5-regression/) | [準1級トップ]({{ site.baseurl }}/semi-1/) | [トップページ]({{ site.baseurl }}/)
