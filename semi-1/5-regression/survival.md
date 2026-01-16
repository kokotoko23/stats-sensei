---
layout: default
title: 生存時間分析 - 準1級対策
description: 生存関数、ハザード関数、カプラン・マイヤー、Cox回帰を解説
---

# 生存時間分析

生存時間分析（Survival Analysis）は、イベント（死亡、故障、離脱など）が発生するまでの時間を分析する手法です。

---

## 1. 基本概念

### 1.1 生存時間データの特徴

- **打ち切り（Censoring）**：観察終了時にイベント未発生
  - 右打ち切り：最も一般的
  - 左打ち切り：イベント発生時刻が観察開始前
  - 区間打ち切り：特定の区間内で発生

### 1.2 生存関数（Survival Function）

時刻 $t$ まで生存する確率：

$$S(t) = P(T > t) = 1 - F(t)$$

- $T$：生存時間（確率変数）
- $F(t) = P(T \leq t)$：累積分布関数

**性質**：
- $S(0) = 1$
- $\lim_{t \to \infty} S(t) = 0$
- 単調非増加

### 1.3 ハザード関数（Hazard Function）

時刻 $t$ まで生存した条件で、直後にイベントが起こる瞬間的な確率（率）：

$$h(t) = \lim_{\Delta t \to 0} \frac{P(t \leq T < t + \Delta t \mid T \geq t)}{\Delta t}$$

$$h(t) = \frac{f(t)}{S(t)} = -\frac{d}{dt}\log S(t)$$

### 1.4 累積ハザード関数

$$H(t) = \int_0^t h(u) du = -\log S(t)$$

$$S(t) = \exp(-H(t))$$

---

## 2. 代表的な生存時間分布

| 分布 | ハザード関数 | 特徴 |
|-----|------------|------|
| 指数分布 | $h(t) = \lambda$（定数） | 無記憶性 |
| ワイブル分布 | $h(t) = \lambda \gamma t^{\gamma-1}$ | 柔軟なハザード形状 |
| 対数正規分布 | 単峰型 | 初期増加後減少 |

### 指数分布の場合

$$S(t) = e^{-\lambda t}, \quad H(t) = \lambda t$$

---

## 3. カプラン・マイヤー推定量

### 3.1 定義

ノンパラメトリックな生存関数の推定量：

$$\hat{S}(t) = \prod_{t_i \leq t} \left(1 - \frac{d_i}{n_i}\right)$$

- $t_1 < t_2 < \cdots$：イベント発生時刻（順序統計量）
- $d_i$：時刻 $t_i$ でのイベント数
- $n_i$：時刻 $t_i$ 直前のリスク集合のサイズ（打ち切りを除く）

### 3.2 標準誤差（Greenwood の公式）

$$\text{SE}(\hat{S}(t)) = \hat{S}(t) \sqrt{\sum_{t_i \leq t} \frac{d_i}{n_i(n_i - d_i)}}$$

### 3.3 信頼区間

対数変換を使った信頼区間：

$$\hat{S}(t)^{\exp(\pm z_{\alpha/2} \cdot \text{SE}(\log\hat{S}(t)))}$$

---

## 4. ログランク検定

### 4.1 目的

2群以上の生存曲線を比較。

帰無仮説：$H_0: S_1(t) = S_2(t)$ （全ての $t$ で）

### 4.2 検定統計量

$$\chi^2 = \frac{(O_1 - E_1)^2}{E_1} + \frac{(O_2 - E_2)^2}{E_2}$$

- $O_k$：群 $k$ の観測イベント数
- $E_k$：帰無仮説のもとでの期待イベント数

漸近的に $\chi^2_1$ 分布に従う。

---

## 5. Cox比例ハザードモデル

### 5.1 モデル

$$h(t | \mathbf{x}) = h_0(t) \exp(\mathbf{x}^\top \boldsymbol{\beta})$$

- $h_0(t)$：ベースラインハザード（未知）
- $\exp(\mathbf{x}^\top \boldsymbol{\beta})$：共変量の効果

### 5.2 比例ハザード仮定

任意の2つの個体のハザード比が時間に依存しない：

$$\frac{h(t | \mathbf{x}_1)}{h(t | \mathbf{x}_2)} = \exp((\mathbf{x}_1 - \mathbf{x}_2)^\top \boldsymbol{\beta})$$

### 5.3 ハザード比の解釈

$x_j$ が1単位増加したときのハザード比：

$$\text{HR}_j = e^{\beta_j}$$

- HR > 1：リスク増加
- HR < 1：リスク減少
- HR = 1：効果なし

### 5.4 部分尤度（Partial Likelihood）

ベースラインハザードを推定せずに $\boldsymbol{\beta}$ を推定：

$$L(\boldsymbol{\beta}) = \prod_{i: \delta_i = 1} \frac{\exp(\mathbf{x}_i^\top \boldsymbol{\beta})}{\sum_{j \in R_i} \exp(\mathbf{x}_j^\top \boldsymbol{\beta})}$$

- $\delta_i$：イベント指示変数（1=イベント、0=打ち切り）
- $R_i$：時刻 $t_i$ でのリスク集合

---

## 6. 例題

### 例題1：カプラン・マイヤー推定

イベント時刻と打ち切りデータ：2(E), 3(C), 5(E), 5(E), 7(C), 8(E)
（E=イベント、C=打ち切り）

$t = 5$ での生存率を求めよ。

<details markdown="1">
<summary>解答を見る</summary>

### 解答

| 時刻 $t$ | $n_i$ | $d_i$ | $1 - d_i/n_i$ |
|---------|-------|-------|---------------|
| 2 | 6 | 1 | 5/6 |
| 5 | 4 | 2 | 2/4 = 1/2 |

（$t=3$ は打ち切りなのでイベントとしてカウントしない）

$$\hat{S}(5) = \frac{5}{6} \times \frac{1}{2} = \frac{5}{12} \approx 0.417$$

**答え：約41.7%**

</details>

---

### 例題2：ハザード比の解釈

Coxモデルで「喫煙」の係数が $\beta = 0.5$ のとき、ハザード比を求め解釈せよ。

<details markdown="1">
<summary>解答を見る</summary>

### 解答

$$\text{HR} = e^{0.5} \approx 1.65$$

**解釈**：喫煙者は非喫煙者に比べて、イベント（例：死亡）のハザードが約1.65倍高い。

**答え：HR ≈ 1.65**

</details>

---

### 例題3：指数分布の生存関数

ハザード率 $\lambda = 0.1$（/年）のとき、5年生存率を求めよ。

<details markdown="1">
<summary>解答を見る</summary>

### 解答

指数分布の生存関数：

$$S(t) = e^{-\lambda t} = e^{-0.1 \times 5} = e^{-0.5} \approx 0.607$$

**答え：約60.7%**

</details>

---

## 7. 重要公式まとめ

| 項目 | 公式 |
|-----|------|
| ハザード関数 | $h(t) = f(t)/S(t) = -\frac{d}{dt}\log S(t)$ |
| 生存関数とハザード | $S(t) = \exp(-\int_0^t h(u)du)$ |
| 指数分布 | $S(t) = e^{-\lambda t}$, $h(t) = \lambda$ |
| カプラン・マイヤー | $\hat{S}(t) = \prod_{t_i \leq t}(1-d_i/n_i)$ |
| Coxモデル | $h(t|\mathbf{x}) = h_0(t)\exp(\mathbf{x}^\top\boldsymbol{\beta})$ |
| ハザード比 | $\text{HR} = e^{\beta}$ |

---

[回帰分析に戻る]({{ site.baseurl }}/semi-1/5-regression/) | [準1級トップ]({{ site.baseurl }}/semi-1/) | [トップページ]({{ site.baseurl }}/)
