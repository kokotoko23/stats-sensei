---
layout: default
title: 因子分析 - 準1級対策
description: 因子分析の理論、因子負荷量、回転法、構造方程式モデルを解説
---

# 因子分析

因子分析（Factor Analysis）は、観測変数の背後にある潜在的な因子（共通因子）を見つける手法です。

---

## 1. 因子分析の目的

- **データの次元削減**：多数の変数を少数の因子で説明
- **潜在構造の発見**：観測できない概念（知能、満足度など）を抽出
- **尺度構成**：心理学やマーケティングでの質問項目の妥当性検証

### 主成分分析との違い

| 項目 | 主成分分析 | 因子分析 |
|-----|----------|---------|
| 目的 | データの要約 | 潜在因子の発見 |
| モデル | $z = \mathbf{a}^\top \mathbf{x}$ | $\mathbf{x} = \mathbf{\Lambda} \mathbf{f} + \mathbf{e}$ |
| 誤差 | 考慮しない | 独自因子として考慮 |

---

## 2. 因子分析モデル

### 2.1 1因子モデル

$p$ 個の観測変数 $x_1, \ldots, x_p$ に対し、1つの共通因子 $f$ を仮定：

$$x_j = \lambda_j f + e_j \quad (j = 1, \ldots, p)$$

- $\lambda_j$：因子負荷量（factor loading）
- $f$：共通因子（common factor）、$E[f]=0$, $\text{Var}(f)=1$
- $e_j$：独自因子（unique factor）、$E[e_j]=0$, $\text{Var}(e_j)=\psi_j$

### 2.2 多因子モデル

$m$ 個の共通因子を持つ一般的なモデル：

$$\mathbf{x} = \mathbf{\Lambda} \mathbf{f} + \mathbf{e}$$

$$\begin{pmatrix} x_1 \\ x_2 \\ \vdots \\ x_p \end{pmatrix} = \begin{pmatrix} \lambda_{11} & \lambda_{12} & \cdots & \lambda_{1m} \\ \lambda_{21} & \lambda_{22} & \cdots & \lambda_{2m} \\ \vdots & \vdots & \ddots & \vdots \\ \lambda_{p1} & \lambda_{p2} & \cdots & \lambda_{pm} \end{pmatrix} \begin{pmatrix} f_1 \\ f_2 \\ \vdots \\ f_m \end{pmatrix} + \begin{pmatrix} e_1 \\ e_2 \\ \vdots \\ e_p \end{pmatrix}$$

### 2.3 仮定

- $E[\mathbf{f}] = \mathbf{0}$, $\text{Cov}(\mathbf{f}) = \mathbf{I}_m$（因子は無相関、分散1）
- $E[\mathbf{e}] = \mathbf{0}$, $\text{Cov}(\mathbf{e}) = \mathbf{\Psi} = \text{diag}(\psi_1, \ldots, \psi_p)$
- $\text{Cov}(\mathbf{f}, \mathbf{e}) = \mathbf{O}$（因子と独自因子は無相関）

---

## 3. 分散共分散行列の分解

観測変数の分散共分散行列：

$$\mathbf{\Sigma} = \mathbf{\Lambda} \mathbf{\Lambda}^\top + \mathbf{\Psi}$$

### 3.1 共通性と独自性

変数 $x_j$ の分散の分解：

$$\sigma_j^2 = \sum_{k=1}^{m} \lambda_{jk}^2 + \psi_j = h_j^2 + \psi_j$$

- **共通性**（communality）：$h_j^2 = \sum_{k=1}^{m} \lambda_{jk}^2$（共通因子で説明される分散）
- **独自性**（uniqueness）：$\psi_j$（独自因子による分散）

---

## 4. 因子の推定法

### 4.1 主因子法

1. 相関行列 $\mathbf{R}$ の対角成分を共通性の推定値で置き換え
2. 固有値分解
3. 反復して共通性を更新

### 4.2 最尤法

対数尤度関数を最大化：

$$\ell(\mathbf{\Lambda}, \mathbf{\Psi}) = -\frac{n}{2}\left\{ \log|\mathbf{\Sigma}| + \text{tr}(\mathbf{S}\mathbf{\Sigma}^{-1}) \right\}$$

ここで $\mathbf{\Sigma} = \mathbf{\Lambda}\mathbf{\Lambda}^\top + \mathbf{\Psi}$

**利点**：統計的検定が可能、信頼区間が計算できる

---

## 5. 因子の回転

### 5.1 回転の必要性

因子負荷行列 $\mathbf{\Lambda}$ は一意に定まらない。直交行列 $\mathbf{T}$ に対し：

$$\mathbf{\Lambda}^* = \mathbf{\Lambda}\mathbf{T}$$

も同じ分散共分散行列を再現する。**解釈しやすい**因子構造を得るために回転を行う。

### 5.2 直交回転

因子間の無相関を保つ回転。

**バリマックス回転（Varimax）**：

各因子について、因子負荷量の2乗の分散を最大化：

$$V = \frac{1}{p}\sum_{k=1}^{m}\left\{ \sum_{j=1}^{p} \tilde{\lambda}_{jk}^4 - \frac{1}{p}\left(\sum_{j=1}^{p} \tilde{\lambda}_{jk}^2\right)^2 \right\}$$

**結果**：各因子に対し、高い負荷量と低い負荷量が明確に分かれる（単純構造）

### 5.3 斜交回転

因子間の相関を許す回転。

**プロマックス回転（Promax）**：
1. バリマックス回転を実行
2. 負荷量のべき乗を取って単純構造を強調
3. 最小二乗法で回転行列を求める

---

## 6. 因子数の決定

| 方法 | 基準 |
|-----|------|
| カイザー基準 | 固有値 > 1 の因子を採用 |
| スクリープロット | 固有値の減少が緩やかになる点 |
| 累積寄与率 | 累積寄与率が70-80%以上 |
| 適合度検定 | カイ二乗検定でモデルの適合度を評価 |
| 平行分析 | ランダムデータの固有値と比較 |

---

## 7. 構造方程式モデル（SEM）

### 7.1 概要

因子分析を拡張し、**因子間の因果関係**もモデル化。

- **測定モデル**：観測変数と潜在変数の関係（因子分析）
- **構造モデル**：潜在変数間の関係（回帰分析）

### 7.2 パス図

- 四角：観測変数
- 楕円：潜在変数
- 矢印：因果関係または相関

### 7.3 適合度指標

| 指標 | 基準 |
|-----|------|
| CFI | > 0.95 で良好 |
| RMSEA | < 0.05 で良好、< 0.08 で許容 |
| SRMR | < 0.08 で良好 |

---

## 8. 例題

### 例題1：因子負荷量と共通性

2因子モデルで、変数 $x_1$ の因子負荷量が $\lambda_{11} = 0.8$, $\lambda_{12} = 0.3$ のとき、共通性を求めよ。

<details markdown="1">
<summary>解答を見る</summary>

### 解答

共通性：

$$h_1^2 = \lambda_{11}^2 + \lambda_{12}^2 = 0.8^2 + 0.3^2 = 0.64 + 0.09 = 0.73$$

**答え：0.73**

変数 $x_1$ の分散の73%が共通因子で説明される。

</details>

---

### 例題2：分散共分散行列の再現

1因子モデルで因子負荷量が $\lambda_1 = 0.9$, $\lambda_2 = 0.6$、独自分散が $\psi_1 = 0.19$, $\psi_2 = 0.64$ のとき、変数間の相関係数を求めよ。

<details markdown="1">
<summary>解答を見る</summary>

### 解答

1因子モデルでは：

$$\sigma_{12} = \lambda_1 \lambda_2 = 0.9 \times 0.6 = 0.54$$

各変数の分散：

$$\sigma_1^2 = \lambda_1^2 + \psi_1 = 0.81 + 0.19 = 1.0$$

$$\sigma_2^2 = \lambda_2^2 + \psi_2 = 0.36 + 0.64 = 1.0$$

相関係数：

$$r_{12} = \frac{\sigma_{12}}{\sigma_1 \sigma_2} = \frac{0.54}{1.0 \times 1.0} = 0.54$$

**答え：0.54**

</details>

---

### 例題3：バリマックス回転

回転前の因子負荷行列が以下のとき、バリマックス回転の効果を説明せよ。

$$\mathbf{\Lambda} = \begin{pmatrix} 0.7 & 0.5 \\ 0.6 & 0.6 \\ 0.5 & 0.7 \end{pmatrix}$$

<details markdown="1">
<summary>解答を見る</summary>

### 解答

回転前：各変数が両方の因子に中程度の負荷量を持ち、解釈が困難。

バリマックス回転後（概念的に）：

$$\mathbf{\Lambda}^* \approx \begin{pmatrix} 0.85 & 0.1 \\ 0.6 & 0.6 \\ 0.1 & 0.85 \end{pmatrix}$$

**効果**：
- 変数1は第1因子に高い負荷
- 変数3は第2因子に高い負荷
- 変数2は両方に中程度の負荷

→ 因子の解釈が容易になる（単純構造）

</details>

---

## 9. 重要公式まとめ

| 項目 | 公式 |
|-----|------|
| 因子モデル | $\mathbf{x} = \mathbf{\Lambda}\mathbf{f} + \mathbf{e}$ |
| 分散共分散 | $\mathbf{\Sigma} = \mathbf{\Lambda}\mathbf{\Lambda}^\top + \mathbf{\Psi}$ |
| 共通性 | $h_j^2 = \sum_k \lambda_{jk}^2$ |
| 独自性 | $\psi_j = \sigma_j^2 - h_j^2$ |
| 変数間の共分散 | $\sigma_{ij} = \sum_k \lambda_{ik}\lambda_{jk}$（$i \neq j$） |

---

[多変量解析に戻る]({{ site.baseurl }}/semi-1/7-multivariate/) | [準1級トップ]({{ site.baseurl }}/semi-1/) | [トップページ]({{ site.baseurl }}/)
