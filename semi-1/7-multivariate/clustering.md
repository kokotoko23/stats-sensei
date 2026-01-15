---
layout: default
title: クラスター分析 - 準1級対策
description: 階層的クラスタリング、k-means、EMアルゴリズムを解説
---

# クラスター分析

クラスター分析（Cluster Analysis）は、データを類似したグループ（クラスター）に分ける手法です。判別分析と異なり、**事前のグループ情報なし**でグループを発見します。

---

## 1. クラスター分析の種類

| 種類 | 手法 | 特徴 |
|-----|------|------|
| 階層的手法 | 凝集法、分割法 | デンドログラムで可視化 |
| 非階層的手法 | k-means | クラスター数を事前に指定 |
| モデルベース | EMアルゴリズム | 混合分布を仮定 |

---

## 2. 距離の定義

### 2.1 点間の距離

| 距離 | 定義 |
|-----|------|
| ユークリッド距離 | $d(\mathbf{x}, \mathbf{y}) = \sqrt{\sum_i (x_i - y_i)^2}$ |
| マンハッタン距離 | $d(\mathbf{x}, \mathbf{y}) = \sum_i \|x_i - y_i\|$ |
| マハラノビス距離 | $d(\mathbf{x}, \mathbf{y}) = \sqrt{(\mathbf{x}-\mathbf{y})^\top \mathbf{S}^{-1} (\mathbf{x}-\mathbf{y})}$ |
| ミンコフスキー距離 | $d(\mathbf{x}, \mathbf{y}) = \left(\sum_i \|x_i - y_i\|^p\right)^{1/p}$ |

### 2.2 クラスター間の距離（連結法）

| 連結法 | 定義 | 特徴 |
|-------|------|------|
| 最短距離法（単連結法） | $\min_{i \in A, j \in B} d(i, j)$ | 鎖状になりやすい |
| 最長距離法（完全連結法） | $\max_{i \in A, j \in B} d(i, j)$ | コンパクトなクラスター |
| 群平均法 | $\frac{1}{n_A n_B}\sum_{i \in A}\sum_{j \in B} d(i, j)$ | バランスが良い |
| ウォード法 | クラスター併合時の分散増加を最小化 | 等サイズのクラスター |

---

## 3. 階層的クラスタリング

### 3.1 凝集法（Agglomerative）のアルゴリズム

1. 各データ点を1つのクラスターとする
2. 最も近い2つのクラスターを併合
3. クラスター数が1になるまで繰り返し

### 3.2 デンドログラム（樹形図）

- 縦軸：併合時の距離（非類似度）
- 横軸：各データ点
- 適切な高さで切断してクラスター数を決定

### 3.3 ウォード法の詳細

クラスターA, Bを併合したときの**群内平方和の増分**を最小化：

$$\Delta(A, B) = \frac{n_A n_B}{n_A + n_B} \|\bar{\mathbf{x}}_A - \bar{\mathbf{x}}_B\|^2$$

---

## 4. k-means法

### 4.1 アルゴリズム

1. **初期化**：$k$ 個のクラスター中心をランダムに選択
2. **割り当て**：各点を最も近い中心のクラスターに割り当て
3. **更新**：各クラスターの重心を新しい中心とする
4. 収束するまで2-3を繰り返し

### 4.2 目的関数

群内平方和（WCSS: Within-Cluster Sum of Squares）を最小化：

$$J = \sum_{k=1}^{K} \sum_{\mathbf{x}_i \in C_k} \|\mathbf{x}_i - \boldsymbol{\mu}_k\|^2$$

### 4.3 k-means法の特徴

| 長所 | 短所 |
|-----|------|
| 計算が高速 | クラスター数$k$を事前に指定 |
| 大規模データに適用可能 | 初期値に依存 |
| 実装が簡単 | 球状のクラスターを仮定 |

### 4.4 クラスター数の決定

- **エルボー法**：WCSSの減少が緩やかになる点
- **シルエット係数**：クラスターの妥当性を評価
- **ギャップ統計量**

---

## 5. シルエット係数

### 5.1 定義

データ点 $i$ のシルエット係数：

$$s(i) = \frac{b(i) - a(i)}{\max(a(i), b(i))}$$

- $a(i)$：同じクラスター内の他の点との平均距離（凝集度）
- $b(i)$：最も近い他クラスターの点との平均距離（分離度）

### 5.2 解釈

- $s(i) \approx 1$：良いクラスタリング
- $s(i) \approx 0$：境界上にある
- $s(i) < 0$：誤ったクラスターに割り当てられている可能性

---

## 6. EMアルゴリズムによるクラスタリング

### 6.1 混合正規分布モデル

データが $K$ 個の正規分布の混合から生成されると仮定：

$$p(\mathbf{x}) = \sum_{k=1}^{K} \pi_k \mathcal{N}(\mathbf{x} | \boldsymbol{\mu}_k, \boldsymbol{\Sigma}_k)$$

- $\pi_k$：混合比率（$\sum_k \pi_k = 1$）
- $\boldsymbol{\mu}_k$：第$k$成分の平均
- $\boldsymbol{\Sigma}_k$：第$k$成分の分散共分散行列

### 6.2 EMアルゴリズム

**E-step（期待値ステップ）**：

各点 $\mathbf{x}_i$ が第$k$クラスターに属する事後確率（負担率）を計算：

$$\gamma_{ik} = \frac{\pi_k \mathcal{N}(\mathbf{x}_i | \boldsymbol{\mu}_k, \boldsymbol{\Sigma}_k)}{\sum_{j=1}^{K} \pi_j \mathcal{N}(\mathbf{x}_i | \boldsymbol{\mu}_j, \boldsymbol{\Sigma}_j)}$$

**M-step（最大化ステップ）**：

パラメータを更新：

$$N_k = \sum_{i=1}^{n} \gamma_{ik}$$

$$\boldsymbol{\mu}_k^{\text{new}} = \frac{1}{N_k} \sum_{i=1}^{n} \gamma_{ik} \mathbf{x}_i$$

$$\boldsymbol{\Sigma}_k^{\text{new}} = \frac{1}{N_k} \sum_{i=1}^{n} \gamma_{ik} (\mathbf{x}_i - \boldsymbol{\mu}_k^{\text{new}})(\mathbf{x}_i - \boldsymbol{\mu}_k^{\text{new}})^\top$$

$$\pi_k^{\text{new}} = \frac{N_k}{n}$$

---

## 7. 例題

### 例題1：距離の計算

点A(1, 2)と点B(4, 6)のユークリッド距離とマンハッタン距離を求めよ。

<details markdown="1">
<summary>解答を見る</summary>

### 解答

**ユークリッド距離**：

$$d_E = \sqrt{(4-1)^2 + (6-2)^2} = \sqrt{9 + 16} = \sqrt{25} = 5$$

**マンハッタン距離**：

$$d_M = |4-1| + |6-2| = 3 + 4 = 7$$

**答え：** ユークリッド距離 5、マンハッタン距離 7

</details>

---

### 例題2：ウォード法の距離

クラスターA（3点、重心(2, 3)）とクラスターB（2点、重心(6, 5)）をウォード法で併合するときの距離増分を求めよ。

<details markdown="1">
<summary>解答を見る</summary>

### 解答

ウォード法の距離増分：

$$\Delta(A, B) = \frac{n_A n_B}{n_A + n_B} \|\bar{\mathbf{x}}_A - \bar{\mathbf{x}}_B\|^2$$

$$= \frac{3 \times 2}{3 + 2} \times \{(2-6)^2 + (3-5)^2\}$$

$$= \frac{6}{5} \times (16 + 4) = \frac{6}{5} \times 20 = 24$$

**答え：** 24

</details>

---

### 例題3：k-meansの更新

2次元データ点(1,1), (2,1), (4,3), (5,4)があり、現在の中心が$\mu_1=(1,1)$, $\mu_2=(5,4)$のとき、各点をクラスターに割り当て、新しい中心を計算せよ。

<details markdown="1">
<summary>解答を見る</summary>

### 解答

**割り当てステップ**：

各点から各中心への距離を計算：

| 点 | $\mu_1$への距離 | $\mu_2$への距離 | 割り当て |
|---|---------------|---------------|---------|
| (1,1) | 0 | $\sqrt{16+9}=5$ | C1 |
| (2,1) | 1 | $\sqrt{9+9}=\sqrt{18}\approx4.2$ | C1 |
| (4,3) | $\sqrt{9+4}=\sqrt{13}\approx3.6$ | $\sqrt{1+1}=\sqrt{2}\approx1.4$ | C2 |
| (5,4) | $\sqrt{16+9}=5$ | 0 | C2 |

**更新ステップ**：

クラスター1：点(1,1), (2,1)

$$\mu_1^{\text{new}} = \left(\frac{1+2}{2}, \frac{1+1}{2}\right) = (1.5, 1)$$

クラスター2：点(4,3), (5,4)

$$\mu_2^{\text{new}} = \left(\frac{4+5}{2}, \frac{3+4}{2}\right) = (4.5, 3.5)$$

**答え：** 新しい中心は $\mu_1=(1.5, 1)$, $\mu_2=(4.5, 3.5)$

</details>

---

## 8. 重要公式まとめ

| 項目 | 公式 |
|-----|------|
| ユークリッド距離 | $\sqrt{\sum_i (x_i - y_i)^2}$ |
| ウォード法の増分 | $\frac{n_A n_B}{n_A + n_B}\|\bar{\mathbf{x}}_A - \bar{\mathbf{x}}_B\|^2$ |
| k-means目的関数 | $\sum_k \sum_{i \in C_k}\|\mathbf{x}_i - \boldsymbol{\mu}_k\|^2$ |
| シルエット係数 | $(b(i) - a(i))/\max(a(i), b(i))$ |
| EM負担率 | $\gamma_{ik} = \pi_k \mathcal{N}_k / \sum_j \pi_j \mathcal{N}_j$ |

---

[多変量解析に戻る]({{ site.baseurl }}/semi-1/7-multivariate/) | [準1級トップ]({{ site.baseurl }}/semi-1/) | [トップページ]({{ site.baseurl }}/)
