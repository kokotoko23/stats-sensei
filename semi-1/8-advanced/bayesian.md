---
layout: default
title: ベイズ法 - 準1級対策
description: 事前分布、事後分布、MCMCを解説
---

# ベイズ法

事前情報を活用した統計的推論を学びます。

---

## 1. ベイズ推論の基本

### 1.1 ベイズの定理（パラメータ推定版）

$$p(\theta | \mathbf{x}) = \frac{p(\mathbf{x} | \theta) p(\theta)}{p(\mathbf{x})} \propto p(\mathbf{x} | \theta) p(\theta)$$

| 用語 | 記号 | 意味 |
|-----|------|------|
| 事前分布 | $p(\theta)$ | データ観測前の信念 |
| 尤度 | $p(\mathbf{x} \| \theta)$ | データが観測される確率 |
| 事後分布 | $p(\theta \| \mathbf{x})$ | データ観測後の信念 |
| 周辺尤度 | $p(\mathbf{x})$ | 正規化定数 |

### 1.2 事後分布 ∝ 尤度 × 事前分布

$$\text{posterior} \propto \text{likelihood} \times \text{prior}$$

---

## 2. 共役事前分布

### 2.1 定義

尤度と同じ分布族の事後分布を与える事前分布。

### 2.2 主な共役事前分布

| 尤度 | 事前分布 | 事後分布 |
|-----|---------|---------|
| 二項 $\text{Bin}(n, p)$ | $\text{Beta}(\alpha, \beta)$ | $\text{Beta}(\alpha + x, \beta + n - x)$ |
| ポアソン $\text{Poi}(\lambda)$ | $\Gamma(\alpha, \beta)$ | $\Gamma(\alpha + x, \beta + 1)$ |
| 正規（$\sigma^2$ 既知） | $N(\mu_0, \tau_0^2)$ | $N(\mu_n, \tau_n^2)$ |
| 正規（$\mu$ 既知） | $\Gamma^{-1}(\alpha, \beta)$ | $\Gamma^{-1}(\alpha + n/2, \beta + SS/2)$ |

### 2.3 二項分布×ベータ分布

観測：$x$ 回成功、$n - x$ 回失敗

事前：$p \sim \text{Beta}(\alpha, \beta)$

事後：$p | x \sim \text{Beta}(\alpha + x, \beta + n - x)$

**事後期待値**：

$$E[p | x] = \frac{\alpha + x}{\alpha + \beta + n}$$

### 2.4 正規分布×正規分布

観測：$\bar{x}$（$n$ 個の平均）

事前：$\mu \sim N(\mu_0, \tau_0^2)$

事後：$\mu | \bar{x} \sim N(\mu_n, \tau_n^2)$

$$\mu_n = \frac{\frac{\mu_0}{\tau_0^2} + \frac{n\bar{x}}{\sigma^2}}{\frac{1}{\tau_0^2} + \frac{n}{\sigma^2}}$$

$$\frac{1}{\tau_n^2} = \frac{1}{\tau_0^2} + \frac{n}{\sigma^2}$$

---

## 3. ベイズ推定

### 3.1 点推定

| 推定量 | 定義 | 損失関数 |
|-------|------|---------|
| 事後平均 | $E[\theta \| \mathbf{x}]$ | 二乗損失 |
| 事後中央値 | $\text{median}(\theta \| \mathbf{x})$ | 絶対損失 |
| 事後最頻値（MAP） | $\arg\max p(\theta \| \mathbf{x})$ | 0-1損失 |

### 3.2 信用区間（Credible Interval）

確率 $1 - \alpha$ で $\theta$ が含まれる区間：

$$P(\theta \in [L, U] | \mathbf{x}) = 1 - \alpha$$

**最高事後密度（HPD）区間**：最も短い信用区間。

### 3.3 頻度論的信頼区間との違い

| | ベイズ（信用区間） | 頻度論（信頼区間） |
|---|-----------------|-----------------|
| 解釈 | $\theta$ がこの区間に入る確率 | 繰り返しのうちの割合 |
| $\theta$ | 確率変数 | 固定（未知） |

---

## 4. マルコフ連鎖モンテカルロ法（MCMC）

### 4.1 必要性

事後分布が解析的に求まらないとき、シミュレーションで近似。

### 4.2 メトロポリス・ヘイスティングス法

1. 提案分布 $q(\theta^* | \theta^{(t)})$ から候補 $\theta^*$ を生成
2. 採択確率を計算：

$$\alpha = \min\left(1, \frac{p(\theta^* | \mathbf{x}) q(\theta^{(t)} | \theta^*)}{p(\theta^{(t)} | \mathbf{x}) q(\theta^* | \theta^{(t)})}\right)$$

3. 確率 $\alpha$ で $\theta^{(t+1)} = \theta^*$、それ以外は $\theta^{(t+1)} = \theta^{(t)}$

### 4.3 ギブスサンプリング

多次元パラメータ $\boldsymbol{\theta} = (\theta_1, \ldots, \theta_k)$ の各成分を条件付き分布からサンプリング：

1. $\theta_1^{(t+1)} \sim p(\theta_1 | \theta_2^{(t)}, \ldots, \theta_k^{(t)}, \mathbf{x})$
2. $\theta_2^{(t+1)} \sim p(\theta_2 | \theta_1^{(t+1)}, \theta_3^{(t)}, \ldots, \theta_k^{(t)}, \mathbf{x})$
3. ...

### 4.4 収束診断

- **トレースプロット**：パラメータの軌跡
- **自己相関**：連続サンプル間の相関
- **バーンイン**：初期サンプルの除去
- **$\hat{R}$統計量**：複数チェーンの比較

---

## 5. ベイズ因子とモデル選択

### 5.1 ベイズ因子

2つのモデル $M_1$, $M_2$ の比較：

$$BF_{12} = \frac{p(\mathbf{x} | M_1)}{p(\mathbf{x} | M_2)}$$

### 5.2 周辺尤度

$$p(\mathbf{x} | M) = \int p(\mathbf{x} | \theta, M) p(\theta | M) d\theta$$

### 5.3 解釈

| $BF_{12}$ | $M_1$ への証拠 |
|-----------|---------------|
| 1-3 | ほとんどなし |
| 3-20 | 正（positive） |
| 20-150 | 強い |
| > 150 | 非常に強い |

---

## 6. 例題

### 例題1：共役事前分布

10回のコイン投げで7回表が出た。事前分布を $\text{Beta}(1, 1)$ としたとき、表が出る確率 $p$ の事後分布と事後期待値を求めよ。

<details markdown="1">
<summary>解答を見る</summary>

### 解答

$\text{Beta}(1, 1) = \text{Uniform}(0, 1)$（無情報事前分布）

事後分布：

$$p | x \sim \text{Beta}(1 + 7, 1 + 3) = \text{Beta}(8, 4)$$

事後期待値：

$$E[p | x] = \frac{8}{8 + 4} = \frac{8}{12} = \frac{2}{3} \approx 0.667$$

**答え：事後分布は $\text{Beta}(8, 4)$、期待値は 2/3**

</details>

---

### 例題2：事後分散

上記の例で、事後分散を求めよ。

<details markdown="1">
<summary>解答を見る</summary>

### 解答

$\text{Beta}(\alpha, \beta)$ の分散：

$$\text{Var} = \frac{\alpha\beta}{(\alpha+\beta)^2(\alpha+\beta+1)}$$

$$= \frac{8 \times 4}{12^2 \times 13} = \frac{32}{144 \times 13} = \frac{32}{1872} \approx 0.0171$$

**答え：約 0.017**

</details>

---

### 例題3：MHアルゴリズム

対称な提案分布（$q(\theta^* | \theta) = q(\theta | \theta^*)$）のとき、採択確率の式を簡略化せよ。

<details markdown="1">
<summary>解答を見る</summary>

### 解答

対称な提案分布では $q(\theta^* | \theta) = q(\theta | \theta^*)$ なので：

$$\alpha = \min\left(1, \frac{p(\theta^* | \mathbf{x})}{p(\theta | \mathbf{x})}\right)$$

事後分布の比のみで採択確率が決まる。

**答え：$\alpha = \min(1, p(\theta^* | \mathbf{x})/p(\theta | \mathbf{x}))$**

（メトロポリスアルゴリズム）

</details>

---

## 7. 重要公式まとめ

| 項目 | 公式 |
|-----|------|
| ベイズの定理 | $p(\theta \| \mathbf{x}) \propto p(\mathbf{x} \| \theta) p(\theta)$ |
| 二項×ベータ | 事後 $\text{Beta}(\alpha+x, \beta+n-x)$ |
| MH採択確率 | $\alpha = \min(1, \frac{p(\theta^*\|\mathbf{x})q(\theta\|\theta^*)}{p(\theta\|\mathbf{x})q(\theta^*\|\theta)})$ |
| ベイズ因子 | $BF_{12} = p(\mathbf{x}\|M_1)/p(\mathbf{x}\|M_2)$ |

---

[発展的手法に戻る]({{ site.baseurl }}/semi-1/8-advanced/) | [準1級トップ]({{ site.baseurl }}/semi-1/) | [トップページ]({{ site.baseurl }}/)
