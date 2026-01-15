---
layout: default
title: 期待値と分散の計算
description: 期待値と分散の様々な計算問題
category: standard
difficulty: 2
order: 35
---

# 期待値と分散の計算

期待値と分散の計算スキルを養う問題です。

---

## 問題1：離散分布の期待値

サイコロを1回振るとき、出る目の期待値は？

<details markdown="1">
<summary>解答を見る</summary>

### 解答

$$E[X] = \sum x \cdot P(X=x)$$

$$= 1 \times \frac{1}{6} + 2 \times \frac{1}{6} + 3 \times \frac{1}{6} + 4 \times \frac{1}{6} + 5 \times \frac{1}{6} + 6 \times \frac{1}{6}$$

$$= \frac{1+2+3+4+5+6}{6} = \frac{21}{6} = 3.5$$

**答え：3.5**

</details>

---

## 問題2：分散の計算

前問のサイコロの目の分散を計算してください。

<details markdown="1">
<summary>解答を見る</summary>

### 解答

**E[X²]の計算：**
$$E[X^2] = \frac{1^2+2^2+3^2+4^2+5^2+6^2}{6} = \frac{91}{6}$$

**分散：**
$$Var(X) = E[X^2] - (E[X])^2 = \frac{91}{6} - \left(\frac{7}{2}\right)^2$$

$$= \frac{91}{6} - \frac{49}{4} = \frac{182-147}{12} = \frac{35}{12} \approx 2.92$$

**答え：35/12 ≈ 2.92**

</details>

---

## 問題3：線形変換

X の期待値が10、分散が4のとき、Y = 3X + 5 の期待値と分散は？

<details markdown="1">
<summary>解答を見る</summary>

### 解答

**期待値の線形性：**
$$E[Y] = E[3X + 5] = 3E[X] + 5 = 3 \times 10 + 5 = 35$$

**分散の性質：**
$$Var(Y) = Var(3X + 5) = 3^2 \times Var(X) = 9 \times 4 = 36$$

**答え：E[Y] = 35, Var(Y) = 36**

定数を足しても分散は変わらない。係数の2乗が分散にかかる。

</details>

---

## 問題4：和の期待値

2つの独立な確率変数 X, Y があり、E[X]=3, E[Y]=5。E[X+Y]は？

<details markdown="1">
<summary>解答を見る</summary>

### 解答

**期待値の加法性：**
$$E[X+Y] = E[X] + E[Y] = 3 + 5 = 8$$

**答え：8**

**注意：**
期待値の加法性は独立でなくても成り立つ。

</details>

---

## 問題5：和の分散

前問で、Var(X)=2, Var(Y)=3 のとき、Var(X+Y)は？

<details markdown="1">
<summary>解答を見る</summary>

### 解答

**独立な確率変数の和の分散：**
$$Var(X+Y) = Var(X) + Var(Y) = 2 + 3 = 5$$

**答え：5**

**注意：**
独立でない場合は共分散を考慮：
$$Var(X+Y) = Var(X) + Var(Y) + 2Cov(X,Y)$$

</details>

---

## 問題6：宝くじの期待値

1000円で買う宝くじ：
- 1等（100万円）：確率0.00001
- 2等（1万円）：確率0.001
- 3等（100円）：確率0.1
- ハズレ：残り

この宝くじの期待値（期待収益）は？

<details markdown="1">
<summary>解答を見る</summary>

### 解答

$$E[賞金] = 1000000 \times 0.00001 + 10000 \times 0.001 + 100 \times 0.1 + 0 \times 残り$$

$$= 10 + 10 + 10 = 30円$$

**期待収益 = 期待賞金 - 購入費 = 30 - 1000 = -970円**

**答え：期待収益は-970円（平均的に970円の損）**

</details>

---

## 問題7：共分散

X, Y の同時確率分布：

| | Y=0 | Y=1 |
|---|---|---|
| X=0 | 0.2 | 0.3 |
| X=1 | 0.4 | 0.1 |

Cov(X,Y)を求めてください。

<details markdown="1">
<summary>解答を見る</summary>

### 解答

**周辺確率：**
- P(X=0) = 0.5, P(X=1) = 0.5
- P(Y=0) = 0.6, P(Y=1) = 0.4

**期待値：**
- E[X] = 0×0.5 + 1×0.5 = 0.5
- E[Y] = 0×0.6 + 1×0.4 = 0.4

**E[XY]：**
$$E[XY] = 0 \times 0.2 + 0 \times 0.3 + 0 \times 0.4 + 1 \times 0.1 = 0.1$$

**共分散：**
$$Cov(X,Y) = E[XY] - E[X]E[Y] = 0.1 - 0.5 \times 0.4 = 0.1 - 0.2 = -0.1$$

**答え：Cov(X,Y) = -0.1（負の相関）**

</details>

---

## 問題8：条件付き期待値

サイコロを振り、偶数が出たときの目の期待値は？

<details markdown="1">
<summary>解答を見る</summary>

### 解答

偶数：2, 4, 6（各確率1/3）

$$E[X|偶数] = 2 \times \frac{1}{3} + 4 \times \frac{1}{3} + 6 \times \frac{1}{3}$$

$$= \frac{2+4+6}{3} = 4$$

**答え：4**

</details>

---

## 問題9：最大値の期待値

2つの独立なサイコロの目の最大値の期待値は？

<details markdown="1">
<summary>解答を見る</summary>

### 解答

M = max(X₁, X₂) の分布を求める。

P(M ≤ k) = P(X₁ ≤ k)P(X₂ ≤ k) = (k/6)²

P(M = k) = P(M ≤ k) - P(M ≤ k-1)

| k | P(M ≤ k) | P(M = k) |
|---|---|---|
| 1 | 1/36 | 1/36 |
| 2 | 4/36 | 3/36 |
| 3 | 9/36 | 5/36 |
| 4 | 16/36 | 7/36 |
| 5 | 25/36 | 9/36 |
| 6 | 36/36 | 11/36 |

$$E[M] = \frac{1 \times 1 + 2 \times 3 + 3 \times 5 + 4 \times 7 + 5 \times 9 + 6 \times 11}{36}$$

$$= \frac{1+6+15+28+45+66}{36} = \frac{161}{36} \approx 4.47$$

**答え：161/36 ≈ 4.47**

</details>

---

## 問題10：反復試行の期待値

コインを10回投げるとき、表が出る回数の期待値は？

<details markdown="1">
<summary>解答を見る</summary>

### 解答

X ~ Bin(10, 0.5)（二項分布）

**二項分布の期待値：**
$$E[X] = np = 10 \times 0.5 = 5$$

**答え：5回**

</details>

---

## 問題11：幾何分布の期待値

表が出るまでコインを投げ続けるとき、投げる回数の期待値は？

<details markdown="1">
<summary>解答を見る</summary>

### 解答

X ~ Geom(0.5)（幾何分布）

**幾何分布の期待値：**
$$E[X] = \frac{1}{p} = \frac{1}{0.5} = 2$$

**答え：2回**

</details>

---

## 問題12：複合的な期待値

ギャンブルゲーム：サイコロを振り、出た目×100円もらえる。参加費はいくらが公平か？

<details markdown="1">
<summary>解答を見る</summary>

### 解答

賞金 Y = 100X（Xはサイコロの目）

$$E[Y] = 100 \times E[X] = 100 \times 3.5 = 350円$$

**答え：参加費350円が公平**

これより高いと胴元有利、低いとプレイヤー有利。

</details>

---

## 問題13：分散の加法性

独立でないX, Yについて、Var(X)=4, Var(Y)=9, Cov(X,Y)=2 のとき、Var(X+Y)は？

<details markdown="1">
<summary>解答を見る</summary>

### 解答

$$Var(X+Y) = Var(X) + Var(Y) + 2Cov(X,Y)$$

$$= 4 + 9 + 2 \times 2 = 17$$

**答え：17**

正の共分散があると、和の分散は個々の分散の和より大きくなる。

</details>

---

## 関連コンテンツ

- [理論編：確率の基礎]({{ site.baseurl }}/theory/probability/)
- [確率と期待値の問題]({{ site.baseurl }}/problems/probability-04/)

---

[問題編一覧に戻る]({{ site.baseurl }}/problems/) | [トップページに戻る]({{ site.baseurl }}/)
