---
layout: default
title: 離散型分布 - 準1級対策
description: 超幾何分布、負の二項分布、多項分布を解説
---

# 離散型分布

2級レベルより発展的な離散型確率分布を学びます。

---

## 1. 基本的な離散分布（復習）

| 分布 | 記号 | PMF | 期待値 | 分散 |
|-----|------|-----|--------|------|
| ベルヌーイ | $\text{Ber}(p)$ | $p^x(1-p)^{1-x}$ | $p$ | $p(1-p)$ |
| 二項 | $\text{Bin}(n,p)$ | $\binom{n}{x}p^x(1-p)^{n-x}$ | $np$ | $np(1-p)$ |
| ポアソン | $\text{Poi}(\lambda)$ | $e^{-\lambda}\frac{\lambda^x}{x!}$ | $\lambda$ | $\lambda$ |
| 幾何 | $\text{Geo}(p)$ | $(1-p)^{x-1}p$ | $1/p$ | $(1-p)/p^2$ |

---

## 2. 超幾何分布

### 2.1 設定

$N$ 個の対象中、$K$ 個が「成功」（特定の属性を持つ）。
$n$ 個を非復元抽出したとき、成功の数 $X$。

### 2.2 確率関数

$$P(X = x) = \frac{\binom{K}{x}\binom{N-K}{n-x}}{\binom{N}{n}}$$

範囲：$\max(0, n+K-N) \leq x \leq \min(n, K)$

### 2.3 期待値と分散

$$E[X] = \frac{nK}{N}$$

$$\text{Var}(X) = \frac{nK(N-K)(N-n)}{N^2(N-1)}$$

### 2.4 二項分布との関係

$N \to \infty$、$K/N \to p$ のとき：

$$\text{Hypergeometric}(N, K, n) \to \text{Bin}(n, p)$$

**有限母集団補正**：

$$\text{Var}(X)_{\text{超幾何}} = \text{Var}(X)_{\text{二項}} \times \frac{N-n}{N-1}$$

---

## 3. 負の二項分布

### 3.1 定義

成功確率 $p$ の独立試行で、$r$ 回目の成功までに要する試行回数 $X$。

### 3.2 確率関数

$$P(X = x) = \binom{x-1}{r-1} p^r (1-p)^{x-r}, \quad x = r, r+1, \ldots$$

または、失敗回数 $Y = X - r$ で表すと：

$$P(Y = y) = \binom{r+y-1}{y} p^r (1-p)^y, \quad y = 0, 1, 2, \ldots$$

### 3.3 期待値と分散

$$E[X] = \frac{r}{p}, \quad \text{Var}(X) = \frac{r(1-p)}{p^2}$$

失敗回数 $Y$ の場合：

$$E[Y] = \frac{r(1-p)}{p}, \quad \text{Var}(Y) = \frac{r(1-p)}{p^2}$$

### 3.4 幾何分布との関係

$r = 1$ のとき幾何分布。

### 3.5 モーメント母関数

$$M_Y(t) = \left(\frac{p}{1 - (1-p)e^t}\right)^r$$

### 3.6 ポアソンとの関係

$r \to \infty$、$(1-p)/p \to \lambda/r$ のとき：

$$\text{NB}(r, p) \to \text{Poi}(\lambda)$$

---

## 4. 多項分布

### 4.1 定義

$k$ 個のカテゴリへの分類。各カテゴリの確率 $p_1, \ldots, p_k$（$\sum p_i = 1$）。
$n$ 回の独立試行で各カテゴリの度数 $(X_1, \ldots, X_k)$。

### 4.2 確率関数

$$P(X_1 = x_1, \ldots, X_k = x_k) = \frac{n!}{x_1! \cdots x_k!} p_1^{x_1} \cdots p_k^{x_k}$$

条件：$\sum x_i = n$

### 4.3 周辺分布

$$X_i \sim \text{Bin}(n, p_i)$$

### 4.4 期待値・分散・共分散

$$E[X_i] = np_i$$

$$\text{Var}(X_i) = np_i(1-p_i)$$

$$\text{Cov}(X_i, X_j) = -np_i p_j \quad (i \neq j)$$

### 4.5 条件付き分布

$X_1 = x_1$ が与えられたとき、$(X_2, \ldots, X_k)$ は：

$$\text{Multinomial}\left(n - x_1; \frac{p_2}{1-p_1}, \ldots, \frac{p_k}{1-p_1}\right)$$

---

## 5. ポアソン分布の応用

### 5.1 ポアソン過程との関係

単位時間あたりの発生率 $\lambda$ のポアソン過程で、時間 $t$ 内の発生回数：

$$N(t) \sim \text{Poi}(\lambda t)$$

### 5.2 ポアソン近似（少数の法則）

$n$ が大きく、$p$ が小さく、$np = \lambda$ のとき：

$$\text{Bin}(n, p) \approx \text{Poi}(\lambda)$$

### 5.3 条件付きポアソン

$X \sim \text{Poi}(\lambda_1)$, $Y \sim \text{Poi}(\lambda_2)$ が独立のとき：

$$X | X + Y = n \sim \text{Bin}\left(n, \frac{\lambda_1}{\lambda_1 + \lambda_2}\right)$$

### 5.4 ポアソンの加法性

$$\text{Poi}(\lambda_1) + \text{Poi}(\lambda_2) \sim \text{Poi}(\lambda_1 + \lambda_2)$$

---

## 6. その他の離散分布

### 6.1 離散一様分布

$$P(X = x) = \frac{1}{n}, \quad x = 1, 2, \ldots, n$$

$$E[X] = \frac{n+1}{2}, \quad \text{Var}(X) = \frac{n^2 - 1}{12}$$

### 6.2 ベータ二項分布

$$P(X = x) = \binom{n}{x} \frac{B(x + \alpha, n - x + \beta)}{B(\alpha, \beta)}$$

二項分布のパラメータ $p$ がベータ分布に従うとき。

### 6.3 ポアソン・ガンマ（負の二項）

ポアソン分布のパラメータ $\lambda$ がガンマ分布に従うとき、周辺分布は負の二項分布。

---

## 7. 例題

### 例題1：超幾何分布

10個の製品中3個が不良品。4個を非復元抽出したとき、不良品が1個だけ含まれる確率を求めよ。

<details markdown="1">
<summary>解答を見る</summary>

### 解答

$N = 10$, $K = 3$（不良品）, $n = 4$

$$P(X = 1) = \frac{\binom{3}{1}\binom{7}{3}}{\binom{10}{4}}$$

$$= \frac{3 \times 35}{210} = \frac{105}{210} = \frac{1}{2}$$

**答え：1/2（50%）**

</details>

---

### 例題2：負の二項分布

成功確率0.3で、3回成功するまでに平均何回の試行が必要か。また、その分散を求めよ。

<details markdown="1">
<summary>解答を見る</summary>

### 解答

$r = 3$, $p = 0.3$

$$E[X] = \frac{r}{p} = \frac{3}{0.3} = 10$$

$$\text{Var}(X) = \frac{r(1-p)}{p^2} = \frac{3 \times 0.7}{0.09} = \frac{2.1}{0.09} = \frac{70}{3} \approx 23.33$$

**答え：期待値 10回、分散 70/3 ≈ 23.33**

</details>

---

### 例題3：多項分布の共分散

サイコロを60回投げる。1の目の回数を $X_1$、2の目の回数を $X_2$ とするとき、$\text{Cov}(X_1, X_2)$ を求めよ。

<details markdown="1">
<summary>解答を見る</summary>

### 解答

$n = 60$, $p_1 = p_2 = 1/6$

$$\text{Cov}(X_1, X_2) = -np_1 p_2 = -60 \times \frac{1}{6} \times \frac{1}{6}$$

$$= -\frac{60}{36} = -\frac{5}{3} \approx -1.67$$

**答え：$-5/3 \approx -1.67$**

（負の共分散：一方が増えれば他方が減る傾向）

</details>

---

## 8. 重要公式まとめ

| 分布 | 期待値 | 分散 |
|-----|--------|------|
| 超幾何 $H(N, K, n)$ | $nK/N$ | $nK(N-K)(N-n)/(N^2(N-1))$ |
| 負の二項 $\text{NB}(r, p)$ | $r/p$ | $r(1-p)/p^2$ |
| 多項 $X_i$ | $np_i$ | $np_i(1-p_i)$ |
| 多項共分散 | — | $\text{Cov}(X_i, X_j) = -np_ip_j$ |

---

[確率分布に戻る]({{ site.baseurl }}/semi-1/2-distributions/) | [準1級トップ]({{ site.baseurl }}/semi-1/) | [トップページ]({{ site.baseurl }}/)
