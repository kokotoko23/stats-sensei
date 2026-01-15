---
layout: default
title: 主成分分析（PCA） - 準1級対策
description: 主成分分析の理論、固有値分解、寄与率の計算方法を解説
---

# 主成分分析（PCA）

主成分分析（Principal Component Analysis）は、多変量データを少数の主成分で要約する次元削減手法です。

---

## 1. 主成分分析の目的

- **次元削減**：多数の変数を少数の主成分に要約
- **可視化**：高次元データを2〜3次元で可視化
- **多重共線性の解消**：回帰分析の前処理として使用
- **ノイズ除去**：重要な成分のみを抽出

---

## 2. 数学的定式化

### 2.1 問題設定

$n$ 個のサンプル、$p$ 個の変数を持つデータ行列 $\mathbf{X}$ $(n \times p)$ を考える。

各変数は中心化されているとする（平均0）。

### 2.2 主成分の定義

第1主成分 $z_1$ は、分散を最大化する線形結合：

$$z_1 = \mathbf{X} \mathbf{a}_1 = a_{11}x_1 + a_{21}x_2 + \cdots + a_{p1}x_p$$

制約条件：$\|\mathbf{a}_1\|^2 = \mathbf{a}_1^\top \mathbf{a}_1 = 1$

### 2.3 最適化問題

$$\max_{\mathbf{a}_1} \text{Var}(z_1) = \max_{\mathbf{a}_1} \mathbf{a}_1^\top \mathbf{S} \mathbf{a}_1$$

ここで $\mathbf{S}$ は分散共分散行列：

$$\mathbf{S} = \frac{1}{n-1} \mathbf{X}^\top \mathbf{X}$$

### 2.4 ラグランジュの未定乗数法

$$L = \mathbf{a}_1^\top \mathbf{S} \mathbf{a}_1 - \lambda(\mathbf{a}_1^\top \mathbf{a}_1 - 1)$$

微分して0とおくと：

$$\frac{\partial L}{\partial \mathbf{a}_1} = 2\mathbf{S}\mathbf{a}_1 - 2\lambda\mathbf{a}_1 = 0$$

$$\mathbf{S}\mathbf{a}_1 = \lambda\mathbf{a}_1$$

これは固有値問題！$\mathbf{a}_1$ は $\mathbf{S}$ の固有ベクトル、$\lambda$ は固有値。

---

## 3. 固有値と寄与率

### 3.1 固有値の意味

分散共分散行列 $\mathbf{S}$ の固有値 $\lambda_1 \geq \lambda_2 \geq \cdots \geq \lambda_p \geq 0$ は、各主成分の分散を表す：

$$\text{Var}(z_k) = \lambda_k$$

### 3.2 寄与率

第 $k$ 主成分の**寄与率**（contribution ratio）：

$$\text{寄与率}_k = \frac{\lambda_k}{\sum_{j=1}^{p} \lambda_j} = \frac{\lambda_k}{\text{tr}(\mathbf{S})}$$

### 3.3 累積寄与率

第 $k$ 主成分までの**累積寄与率**：

$$\text{累積寄与率}_k = \frac{\sum_{j=1}^{k} \lambda_j}{\sum_{j=1}^{p} \lambda_j}$$

**目安**：累積寄与率が80%以上になる主成分数を採用することが多い。

---

## 4. 主成分得点と主成分負荷量

### 4.1 主成分得点（Principal Component Scores）

各サンプルの主成分得点：

$$\mathbf{Z} = \mathbf{X} \mathbf{A}$$

ここで $\mathbf{A} = (\mathbf{a}_1, \mathbf{a}_2, \ldots, \mathbf{a}_p)$ は固有ベクトルを並べた行列。

### 4.2 主成分負荷量（Principal Component Loadings）

主成分負荷量は、元の変数と主成分の相関係数：

$$\text{Loading}_{jk} = \text{Cor}(x_j, z_k) = a_{jk} \sqrt{\lambda_k} / s_j$$

相関行列を使う場合：

$$\text{Loading}_{jk} = a_{jk} \sqrt{\lambda_k}$$

---

## 5. 分散共分散行列 vs 相関行列

| 基準 | 分散共分散行列 | 相関行列 |
|-----|--------------|---------|
| 使用場面 | 変数の単位が同じ | 単位が異なる |
| 標準化 | 不要 | 必要（各変数を標準化） |
| 固有値の和 | $\sum \lambda_j = \sum s_j^2$ | $\sum \lambda_j = p$ |

**注意**：実務では相関行列を使うことが多い（変数間のスケールの違いを除去）。

---

## 6. 特異値分解（SVD）との関係

中心化データ行列 $\mathbf{X}$ の特異値分解：

$$\mathbf{X} = \mathbf{U} \mathbf{D} \mathbf{V}^\top$$

- $\mathbf{U}$：左特異ベクトル（$n \times p$）
- $\mathbf{D}$：特異値の対角行列（$p \times p$）
- $\mathbf{V}$：右特異ベクトル（$p \times p$）

### SVDと主成分の関係

- **主成分係数**：$\mathbf{A} = \mathbf{V}$
- **主成分得点**：$\mathbf{Z} = \mathbf{U}\mathbf{D}$
- **固有値**：$\lambda_k = d_k^2 / (n-1)$

---

## 7. 例題

### 例題1：固有値と寄与率

3変数のデータの分散共分散行列の固有値が $\lambda_1 = 5.4$, $\lambda_2 = 2.1$, $\lambda_3 = 0.5$ のとき、第1主成分と第2主成分の累積寄与率を求めよ。

<details markdown="1">
<summary>解答を見る</summary>

### 解答

固有値の合計：

$$\sum \lambda_j = 5.4 + 2.1 + 0.5 = 8.0$$

第1主成分の寄与率：

$$\frac{5.4}{8.0} = 0.675 = 67.5\%$$

第2主成分の寄与率：

$$\frac{2.1}{8.0} = 0.2625 = 26.25\%$$

累積寄与率：

$$\frac{5.4 + 2.1}{8.0} = \frac{7.5}{8.0} = 0.9375 = 93.75\%$$

**答え：93.75%**

第1・第2主成分で全体の約94%の情報を説明できる。

</details>

---

### 例題2：主成分得点の計算

2変数 $(x_1, x_2)$ のデータがあり、相関行列の第1固有ベクトルが $\mathbf{a}_1 = (0.707, 0.707)^\top$ である。標準化後のデータ点 $(1.5, 0.5)$ の第1主成分得点を求めよ。

<details markdown="1">
<summary>解答を見る</summary>

### 解答

主成分得点は内積で計算：

$$z_1 = a_{11} x_1 + a_{21} x_2 = 0.707 \times 1.5 + 0.707 \times 0.5$$

$$= 0.707 \times 2.0 = 1.414$$

**答え：1.414**（または $\sqrt{2}$）

</details>

---

### 例題3：相関行列からの主成分分析

2変数の相関行列が以下のとき、固有値と第1主成分の固有ベクトルを求めよ。

$$\mathbf{R} = \begin{pmatrix} 1 & 0.6 \\ 0.6 & 1 \end{pmatrix}$$

<details markdown="1">
<summary>解答を見る</summary>

### 解答

固有方程式：

$$\det(\mathbf{R} - \lambda \mathbf{I}) = 0$$

$$(1-\lambda)^2 - 0.36 = 0$$

$$1 - 2\lambda + \lambda^2 - 0.36 = 0$$

$$\lambda^2 - 2\lambda + 0.64 = 0$$

解の公式より：

$$\lambda = \frac{2 \pm \sqrt{4 - 2.56}}{2} = \frac{2 \pm \sqrt{1.44}}{2} = \frac{2 \pm 1.2}{2}$$

$$\lambda_1 = 1.6, \quad \lambda_2 = 0.4$$

第1固有ベクトル（$\lambda_1 = 1.6$）：

$$(\mathbf{R} - 1.6\mathbf{I})\mathbf{a}_1 = 0$$

$$\begin{pmatrix} -0.6 & 0.6 \\ 0.6 & -0.6 \end{pmatrix} \begin{pmatrix} a_1 \\ a_2 \end{pmatrix} = 0$$

$-0.6a_1 + 0.6a_2 = 0$ より $a_1 = a_2$

正規化条件 $a_1^2 + a_2^2 = 1$ より：

$$\mathbf{a}_1 = \begin{pmatrix} 1/\sqrt{2} \\ 1/\sqrt{2} \end{pmatrix} \approx \begin{pmatrix} 0.707 \\ 0.707 \end{pmatrix}$$

**答え：**
- 固有値：$\lambda_1 = 1.6$, $\lambda_2 = 0.4$
- 第1固有ベクトル：$(0.707, 0.707)^\top$
- 第1主成分の寄与率：$1.6/2 = 80\%$

</details>

---

## 8. 重要公式まとめ

| 項目 | 公式 |
|-----|------|
| 固有値問題 | $\mathbf{S}\mathbf{a} = \lambda\mathbf{a}$ |
| 主成分得点 | $z_k = \mathbf{x}^\top \mathbf{a}_k$ |
| 第k主成分の分散 | $\text{Var}(z_k) = \lambda_k$ |
| 寄与率 | $\lambda_k / \sum_j \lambda_j$ |
| 固有値の和（分散共分散） | $\sum \lambda_j = \text{tr}(\mathbf{S})$ |
| 固有値の和（相関行列） | $\sum \lambda_j = p$ |

---

## 9. 練習問題

準備中

---

[多変量解析に戻る]({{ site.baseurl }}/semi-1/7-multivariate/) | [準1級トップ]({{ site.baseurl }}/semi-1/) | [トップページ]({{ site.baseurl }}/)
