---
layout: default
title: その他の多変量解析手法 - 準1級対策
description: 多次元尺度法、正準相関分析、対応分析を解説
---

# その他の多変量解析手法

主成分分析、判別分析、クラスター分析、因子分析以外の重要な多変量解析手法を学びます。

---

## 1. 多次元尺度法（MDS）

### 1.1 概要

**多次元尺度法**（Multidimensional Scaling）は、対象間の非類似度（距離）データから低次元空間での配置を求める手法。

**目的**：対象間の距離関係を保存しながら可視化

### 1.2 計量MDS

距離行列 $\mathbf{D} = (d_{ij})$ から座標 $\mathbf{X}$ を求める。

**手順**：
1. 距離行列から内積行列（グラム行列）$\mathbf{B}$ を計算
2. $\mathbf{B}$ を固有値分解
3. 上位 $k$ 個の固有値・固有ベクトルから座標を構成

内積行列の計算：

$$b_{ij} = -\frac{1}{2}\left( d_{ij}^2 - \frac{1}{n}\sum_k d_{ik}^2 - \frac{1}{n}\sum_k d_{kj}^2 + \frac{1}{n^2}\sum_k\sum_l d_{kl}^2 \right)$$

座標：

$$\mathbf{X} = \mathbf{V}_k \mathbf{\Lambda}_k^{1/2}$$

ここで $\mathbf{V}_k$ は上位 $k$ 個の固有ベクトル、$\mathbf{\Lambda}_k$ は対応する固有値の対角行列。

### 1.3 非計量MDS

順序尺度の非類似度に対応。距離の順序関係のみを保存。

**ストレス関数**を最小化：

$$\text{Stress} = \sqrt{\frac{\sum_{i<j}(d_{ij} - \hat{d}_{ij})^2}{\sum_{i<j} d_{ij}^2}}$$

$\hat{d}_{ij}$：推定された配置からの距離

---

## 2. 正準相関分析

### 2.1 概要

**正準相関分析**（Canonical Correlation Analysis）は、2組の変数群間の関係を分析する手法。

- 変数群1：$\mathbf{x} = (x_1, \ldots, x_p)^\top$
- 変数群2：$\mathbf{y} = (y_1, \ldots, y_q)^\top$

### 2.2 正準変量

線形結合を構成：

$$u = \mathbf{a}^\top \mathbf{x}, \quad v = \mathbf{b}^\top \mathbf{y}$$

**目的**：$\text{Cor}(u, v)$ を最大化する $\mathbf{a}$, $\mathbf{b}$ を求める。

### 2.3 数学的定式化

分散共分散行列を分割：

$$\mathbf{\Sigma} = \begin{pmatrix} \mathbf{\Sigma}_{xx} & \mathbf{\Sigma}_{xy} \\ \mathbf{\Sigma}_{yx} & \mathbf{\Sigma}_{yy} \end{pmatrix}$$

正準相関：

$$\rho = \frac{\mathbf{a}^\top \mathbf{\Sigma}_{xy} \mathbf{b}}{\sqrt{\mathbf{a}^\top \mathbf{\Sigma}_{xx} \mathbf{a}} \sqrt{\mathbf{b}^\top \mathbf{\Sigma}_{yy} \mathbf{b}}}$$

### 2.4 解法

固有値問題に帰着：

$$\mathbf{\Sigma}_{xx}^{-1} \mathbf{\Sigma}_{xy} \mathbf{\Sigma}_{yy}^{-1} \mathbf{\Sigma}_{yx} \mathbf{a} = \rho^2 \mathbf{a}$$

- $\rho_1 \geq \rho_2 \geq \cdots$：正準相関係数
- 最大 $\min(p, q)$ 組の正準変量が得られる

### 2.5 正準相関の検定

**ウィルクスのΛ**（Wilks' Lambda）：

$$\Lambda = \prod_{k=1}^{s} (1 - \rho_k^2)$$

帰無仮説「すべての正準相関が0」の検定に使用。

---

## 3. 対応分析

### 3.1 概要

**対応分析**（Correspondence Analysis）は、分割表（クロス表）のカテゴリ間の関係を可視化する手法。

- 行カテゴリと列カテゴリを同一の低次元空間にプロット
- カイ二乗距離に基づく

### 3.2 分割表の分析

$r \times c$ の分割表 $\mathbf{N} = (n_{ij})$ に対し：

- 周辺確率：$p_{i\cdot} = \sum_j n_{ij}/n$, $p_{\cdot j} = \sum_i n_{ij}/n$
- 相対頻度：$p_{ij} = n_{ij}/n$

### 3.3 カイ二乗距離

行プロファイル間のカイ二乗距離：

$$d^2(i, i') = \sum_{j=1}^{c} \frac{1}{p_{\cdot j}} \left( \frac{p_{ij}}{p_{i\cdot}} - \frac{p_{i'j}}{p_{i'\cdot}} \right)^2$$

### 3.4 慣性（Inertia）

全体の慣性：

$$I = \sum_{i,j} \frac{(p_{ij} - p_{i\cdot}p_{\cdot j})^2}{p_{i\cdot}p_{\cdot j}} = \frac{\chi^2}{n}$$

- カイ二乗統計量を標本サイズで割ったもの
- 行と列の関連の強さを表す

### 3.5 特異値分解による解法

標準化残差行列を特異値分解：

$$\mathbf{S} = \mathbf{D}_r^{-1/2}(\mathbf{P} - \mathbf{r}\mathbf{c}^\top)\mathbf{D}_c^{-1/2} = \mathbf{U}\mathbf{\Lambda}\mathbf{V}^\top$$

行座標と列座標を求め、同一空間にプロット。

---

## 4. 数量化法

日本で開発されたカテゴリカルデータの分析手法。

| 手法 | 対応する手法 | 目的 |
|-----|------------|------|
| 数量化I類 | 重回帰分析 | 質的説明変数→量的目的変数 |
| 数量化II類 | 判別分析 | 質的説明変数→質的目的変数 |
| 数量化III類 | 対応分析 | 質的変数間の関係 |
| 数量化IV類 | MDS | 類似度データの可視化 |

---

## 5. 例題

### 例題1：正準相関分析

2組の変数 $\mathbf{x} = (x_1, x_2)^\top$ と $\mathbf{y} = (y_1, y_2)^\top$ の正準相関係数が $\rho_1 = 0.8$, $\rho_2 = 0.3$ のとき、ウィルクスのΛを求めよ。

<details markdown="1">
<summary>解答を見る</summary>

### 解答

$$\Lambda = \prod_{k=1}^{2} (1 - \rho_k^2) = (1 - 0.8^2)(1 - 0.3^2)$$

$$= (1 - 0.64)(1 - 0.09) = 0.36 \times 0.91 = 0.3276$$

**答え：0.3276**

$\Lambda$ が小さいほど、2組の変数群間に強い関係がある。

</details>

---

### 例題2：対応分析の慣性

3×3の分割表でカイ二乗統計量が $\chi^2 = 45$、サンプルサイズが $n = 150$ のとき、全体の慣性を求めよ。

<details markdown="1">
<summary>解答を見る</summary>

### 解答

$$I = \frac{\chi^2}{n} = \frac{45}{150} = 0.3$$

**答え：0.3**

慣性は0から1の範囲（理論上は上限なし）で、値が大きいほど行と列の関連が強い。

</details>

---

### 例題3：MDSのストレス

5つの対象のMDS分析で、元の距離と推定距離が以下のとき、ストレスを計算せよ。

| ペア | 元の距離 $d$ | 推定距離 $\hat{d}$ |
|-----|------------|------------------|
| 1-2 | 2.0 | 2.2 |
| 1-3 | 3.0 | 2.8 |
| 2-3 | 1.5 | 1.6 |

<details markdown="1">
<summary>解答を見る</summary>

### 解答

分子：

$$(2.0-2.2)^2 + (3.0-2.8)^2 + (1.5-1.6)^2 = 0.04 + 0.04 + 0.01 = 0.09$$

分母：

$$2.0^2 + 3.0^2 + 1.5^2 = 4 + 9 + 2.25 = 15.25$$

ストレス：

$$\text{Stress} = \sqrt{\frac{0.09}{15.25}} = \sqrt{0.0059} \approx 0.077$$

**答え：約0.077（7.7%）**

ストレス < 0.1 は良好な適合。

</details>

---

## 6. 重要公式まとめ

| 手法 | 主要な公式 |
|-----|----------|
| 計量MDS | $\mathbf{X} = \mathbf{V}_k \mathbf{\Lambda}_k^{1/2}$ |
| 非計量MDS | ストレス = $\sqrt{\sum(d-\hat{d})^2/\sum d^2}$ |
| 正準相関 | $\mathbf{\Sigma}_{xx}^{-1}\mathbf{\Sigma}_{xy}\mathbf{\Sigma}_{yy}^{-1}\mathbf{\Sigma}_{yx}\mathbf{a} = \rho^2\mathbf{a}$ |
| ウィルクスのΛ | $\Lambda = \prod_k (1-\rho_k^2)$ |
| 対応分析の慣性 | $I = \chi^2/n$ |

---

[多変量解析に戻る]({{ site.baseurl }}/semi-1/7-multivariate/) | [準1級トップ]({{ site.baseurl }}/semi-1/) | [トップページ]({{ site.baseurl }}/)
