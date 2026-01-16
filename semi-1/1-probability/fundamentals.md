---
layout: default
title: 確率の基礎 - 準1級対策
description: 条件付き確率、独立性、ベイズの定理を解説
---

# 確率の基礎

確率論の公理的基盤から条件付き確率、ベイズの定理まで学びます。

---

## 1. 確率の公理

### 1.1 コルモゴロフの公理

標本空間 $\Omega$ 上の確率測度 $P$ は以下を満たす：

1. **非負性**：$P(A) \geq 0$（任意の事象 $A$）
2. **正規性**：$P(\Omega) = 1$
3. **可算加法性**：互いに排反な事象 $A_1, A_2, \ldots$ に対し

$$P\left(\bigcup_{i=1}^{\infty} A_i\right) = \sum_{i=1}^{\infty} P(A_i)$$

### 1.2 確率の性質

| 性質 | 式 |
|-----|-----|
| 補集合 | $P(A^c) = 1 - P(A)$ |
| 単調性 | $A \subseteq B \Rightarrow P(A) \leq P(B)$ |
| 加法定理 | $P(A \cup B) = P(A) + P(B) - P(A \cap B)$ |
| ボンフェローニ | $P(A \cap B) \geq P(A) + P(B) - 1$ |

### 1.3 包除原理

$$P\left(\bigcup_{i=1}^{n} A_i\right) = \sum_{i} P(A_i) - \sum_{i<j} P(A_i \cap A_j) + \cdots + (-1)^{n+1} P\left(\bigcap_{i=1}^{n} A_i\right)$$

---

## 2. 条件付き確率

### 2.1 定義

$P(B) > 0$ のとき、$B$ が起こったという条件のもとでの $A$ の確率：

$$P(A \mid B) = \frac{P(A \cap B)}{P(B)}$$

### 2.2 乗法定理

$$P(A \cap B) = P(A \mid B) P(B) = P(B \mid A) P(A)$$

一般化（連鎖律）：

$$P(A_1 \cap A_2 \cap \cdots \cap A_n) = P(A_1) P(A_2 \mid A_1) P(A_3 \mid A_1 \cap A_2) \cdots$$

### 2.3 条件付き確率の性質

条件付き確率 $P(\cdot \mid B)$ も確率の公理を満たす：

- $P(A \mid B) \geq 0$
- $P(\Omega \mid B) = 1$
- 可算加法性を満たす

---

## 3. 独立性

### 3.1 2事象の独立

$A$ と $B$ が**独立**：

$$P(A \cap B) = P(A) P(B)$$

同値条件：
- $P(A \mid B) = P(A)$（$P(B) > 0$ のとき）
- $P(B \mid A) = P(B)$（$P(A) > 0$ のとき）

### 3.2 相互独立と対独立

$n$ 個の事象 $A_1, \ldots, A_n$ について：

**対独立**：任意の2つが独立
$$P(A_i \cap A_j) = P(A_i) P(A_j) \quad (i \neq j)$$

**相互独立**：任意の部分集合について
$$P\left(\bigcap_{i \in S} A_i\right) = \prod_{i \in S} P(A_i) \quad (\text{任意の } S \subseteq \{1, \ldots, n\})$$

**注意**：対独立は相互独立を意味しない。

### 3.3 確率変数の独立

$X$ と $Y$ が独立：

$$P(X \leq x, Y \leq y) = P(X \leq x) P(Y \leq y)$$

同時分布が周辺分布の積：

$$f_{X,Y}(x, y) = f_X(x) f_Y(y)$$

---

## 4. 全確率の公式

### 4.1 分割

$B_1, B_2, \ldots, B_n$ が $\Omega$ の**分割**：
- $B_i \cap B_j = \emptyset$ （$i \neq j$）
- $\bigcup_{i=1}^{n} B_i = \Omega$
- $P(B_i) > 0$ （すべての $i$）

### 4.2 全確率の公式

$$P(A) = \sum_{i=1}^{n} P(A \mid B_i) P(B_i)$$

---

## 5. ベイズの定理

### 5.1 基本形

$$P(B_j \mid A) = \frac{P(A \mid B_j) P(B_j)}{\sum_{i=1}^{n} P(A \mid B_i) P(B_i)}$$

### 5.2 用語

| 用語 | 意味 |
|-----|------|
| 事前確率 | $P(B_j)$：データ観測前の確率 |
| 尤度 | $P(A \mid B_j)$：$B_j$ のもとでのデータの確率 |
| 事後確率 | $P(B_j \mid A)$：データ観測後の確率 |
| 周辺尤度 | $\sum_i P(A \mid B_i) P(B_i)$：正規化定数 |

### 5.3 連続版

$$f_{\Theta \mid X}(\theta \mid x) = \frac{f_{X \mid \Theta}(x \mid \theta) f_\Theta(\theta)}{\int f_{X \mid \Theta}(x \mid \theta') f_\Theta(\theta') d\theta'}$$

### 5.4 オッズ形式

$$\frac{P(B_1 \mid A)}{P(B_2 \mid A)} = \frac{P(A \mid B_1)}{P(A \mid B_2)} \cdot \frac{P(B_1)}{P(B_2)}$$

事後オッズ = 尤度比 × 事前オッズ

---

## 6. 条件付き期待値

### 6.1 定義

$$E[X \mid Y=y] = \sum_x x \cdot P(X=x \mid Y=y)$$ （離散）

$$E[X \mid Y=y] = \int x \cdot f_{X \mid Y}(x \mid y) dx$$ （連続）

### 6.2 全期待値の公式（繰り返し期待値の法則）

$$E[X] = E[E[X \mid Y]]$$

### 6.3 条件付き分散

$$\text{Var}(X \mid Y) = E[X^2 \mid Y] - (E[X \mid Y])^2$$

### 6.4 全分散の公式

$$\text{Var}(X) = E[\text{Var}(X \mid Y)] + \text{Var}(E[X \mid Y])$$

---

## 7. 例題

### 例題1：ベイズの定理

ある病気の有病率は1%。検査の感度（病気のとき陽性）は95%、特異度（健康のとき陰性）は90%。検査が陽性のとき、実際に病気である確率を求めよ。

<details markdown="1">
<summary>解答を見る</summary>

### 解答

- $D$：病気、$D^c$：健康
- $+$：陽性

ベイズの定理：

$$P(D \mid +) = \frac{P(+ \mid D) P(D)}{P(+ \mid D) P(D) + P(+ \mid D^c) P(D^c)}$$

$$= \frac{0.95 \times 0.01}{0.95 \times 0.01 + 0.10 \times 0.99}$$

$$= \frac{0.0095}{0.0095 + 0.099} = \frac{0.0095}{0.1085} \approx 0.0875$$

**答え：約8.75%**

有病率が低いため、陽性でも病気である確率は低い。

</details>

---

### 例題2：全確率の公式

箱Aには赤玉3個、白玉2個。箱Bには赤玉1個、白玉4個。サイコロを振り、1, 2が出たら箱A、それ以外なら箱Bから玉を1個取り出す。赤玉が出る確率を求めよ。

<details markdown="1">
<summary>解答を見る</summary>

### 解答

- $P(A) = 2/6 = 1/3$, $P(B) = 4/6 = 2/3$
- $P(\text{赤} \mid A) = 3/5$, $P(\text{赤} \mid B) = 1/5$

全確率の公式：

$$P(\text{赤}) = P(\text{赤} \mid A) P(A) + P(\text{赤} \mid B) P(B)$$

$$= \frac{3}{5} \times \frac{1}{3} + \frac{1}{5} \times \frac{2}{3}$$

$$= \frac{3}{15} + \frac{2}{15} = \frac{5}{15} = \frac{1}{3}$$

**答え：1/3**

</details>

---

### 例題3：条件付き期待値

$(X, Y)$ の同時分布が $P(X=i, Y=j) = c(i+j)$（$i, j \in \{1, 2\}$）のとき、$E[X \mid Y=1]$ を求めよ。

<details markdown="1">
<summary>解答を見る</summary>

### 解答

まず正規化定数 $c$ を求める：

$$\sum_{i,j} c(i+j) = c[(1+1)+(1+2)+(2+1)+(2+2)] = c(2+3+3+4) = 12c = 1$$

$c = 1/12$

$Y=1$ の周辺確率：

$$P(Y=1) = P(X=1, Y=1) + P(X=2, Y=1) = \frac{2}{12} + \frac{3}{12} = \frac{5}{12}$$

条件付き期待値：

$$E[X \mid Y=1] = 1 \times P(X=1 \mid Y=1) + 2 \times P(X=2 \mid Y=1)$$

$$= 1 \times \frac{2/12}{5/12} + 2 \times \frac{3/12}{5/12} = \frac{2}{5} + \frac{6}{5} = \frac{8}{5}$$

**答え：8/5 = 1.6**

</details>

---

## 8. 重要公式まとめ

| 項目 | 公式 |
|-----|------|
| 条件付き確率 | $P(A \mid B) = P(A \cap B)/P(B)$ |
| 乗法定理 | $P(A \cap B) = P(A \mid B)P(B)$ |
| 独立 | $P(A \cap B) = P(A)P(B)$ |
| 全確率の公式 | $P(A) = \sum_i P(A \mid B_i)P(B_i)$ |
| ベイズの定理 | $P(B_j \mid A) = P(A \mid B_j)P(B_j)/P(A)$ |
| 全期待値の公式 | $E[X] = E[E[X \mid Y]]$ |
| 全分散の公式 | $\text{Var}(X) = E[\text{Var}(X \mid Y)] + \text{Var}(E[X \mid Y])$ |

---

[確率論に戻る]({{ site.baseurl }}/semi-1/1-probability/) | [準1級トップ]({{ site.baseurl }}/semi-1/) | [トップページ]({{ site.baseurl }}/)
