---
layout: default
title: 二項分布の問題
description: 二項分布の確率計算問題
category: intermediate
difficulty: 2
order: 10
---

# 二項分布の問題

二項分布に関する問題です。[理論編：二項分布]({{ site.baseurl }}/theory/binomial/)を学んでから取り組みましょう。

---

## 問題1：基本的な確率計算

コインを5回投げるとき、ちょうど3回表が出る確率を求めてください。

<details markdown="1">
<summary>解答を見る</summary>

### 解答

$n=5$, $k=3$, $p=0.5$

$$P(X=3) = \binom{5}{3}(0.5)^3(0.5)^2 = 10 \times 0.125 \times 0.25 = 0.3125$$

**答え：0.3125（31.25%）**

</details>

---

## 問題2：成功確率が異なる場合

ある製品の不良率は10%です。5個の製品を検査するとき、ちょうど1個が不良品である確率を求めてください。

<details markdown="1">
<summary>解答を見る</summary>

### 解答

$n=5$, $k=1$, $p=0.1$

$$P(X=1) = \binom{5}{1}(0.1)^1(0.9)^4 = 5 \times 0.1 \times 0.6561 = 0.328$$

**答え：約32.8%**

</details>

---

## 問題3：累積確率（以下）

サイコロを4回振るとき、1が出る回数が2回以下である確率を求めてください。

<details markdown="1">
<summary>解答を見る</summary>

### 解答

1が出る確率 $p = \frac{1}{6}$、$n=4$

$$P(X \leq 2) = P(X=0) + P(X=1) + P(X=2)$$

$$P(X=0) = \binom{4}{0}\left(\frac{1}{6}\right)^0\left(\frac{5}{6}\right)^4 = 1 \times 1 \times 0.482 = 0.482$$

$$P(X=1) = \binom{4}{1}\left(\frac{1}{6}\right)^1\left(\frac{5}{6}\right)^3 = 4 \times 0.167 \times 0.579 = 0.386$$

$$P(X=2) = \binom{4}{2}\left(\frac{1}{6}\right)^2\left(\frac{5}{6}\right)^2 = 6 \times 0.028 \times 0.694 = 0.116$$

$$P(X \leq 2) = 0.482 + 0.386 + 0.116 = 0.984$$

**答え：約98.4%**

</details>

---

## 問題4：累積確率（以上）

打率3割の打者が10打席に立つとき、3本以上ヒットを打つ確率を求めてください。

<details markdown="1">
<summary>解答を見る</summary>

### 解答

$n=10$, $p=0.3$

$$P(X \geq 3) = 1 - P(X \leq 2) = 1 - [P(X=0) + P(X=1) + P(X=2)]$$

$$P(X=0) = \binom{10}{0}(0.3)^0(0.7)^{10} = 0.028$$

$$P(X=1) = \binom{10}{1}(0.3)^1(0.7)^9 = 10 \times 0.3 \times 0.040 = 0.121$$

$$P(X=2) = \binom{10}{2}(0.3)^2(0.7)^8 = 45 \times 0.09 \times 0.058 = 0.233$$

$$P(X \geq 3) = 1 - (0.028 + 0.121 + 0.233) = 1 - 0.382 = 0.618$$

**答え：約61.8%**

</details>

---

## 問題5：期待値と分散

ある試験の合格率は60%です。10人が受験するとき：

(1) 合格者数の期待値
(2) 合格者数の分散
(3) 合格者数の標準偏差

<details markdown="1">
<summary>解答を見る</summary>

### 解答

$n=10$, $p=0.6$

**(1) 期待値**
$$E[X] = np = 10 \times 0.6 = 6$$

**答え：6人**

**(2) 分散**
$$Var(X) = np(1-p) = 10 \times 0.6 \times 0.4 = 2.4$$

**答え：2.4**

**(3) 標準偏差**
$$\sigma = \sqrt{2.4} \approx 1.55$$

**答え：約1.55人**

</details>

---

## 問題6：逆問題（nを求める）

成功確率20%の試行を何回行えば、少なくとも1回成功する確率が95%以上になりますか？

<details markdown="1">
<summary>解答を見る</summary>

### 解答

$P(X \geq 1) \geq 0.95$

余事象を使う：
$$1 - P(X=0) \geq 0.95$$
$$P(X=0) \leq 0.05$$
$$(0.8)^n \leq 0.05$$

両辺の対数をとる：
$$n \log(0.8) \leq \log(0.05)$$
$$n \times (-0.097) \leq -1.301$$
$$n \geq \frac{-1.301}{-0.097} = 13.4$$

**答え：14回以上**

</details>

---

## 問題7：最頻値

$n=10$, $p=0.3$ の二項分布で、最も起こりやすい成功回数（最頻値）は何回ですか？

<details markdown="1">
<summary>解答を見る</summary>

### 解答

最頻値の公式：$(n+1)p - 1 \leq$ 最頻値 $\leq (n+1)p$

$$(10+1) \times 0.3 - 1 = 2.3$$
$$(10+1) \times 0.3 = 3.3$$

最頻値は整数なので、2.3〜3.3の間にある整数 = **3**

確認：$P(X=3) = \binom{10}{3}(0.3)^3(0.7)^7 = 120 \times 0.027 \times 0.082 = 0.267$

**答え：3回**

</details>

---

## 問題8：品質管理への応用

ある工場の製品の不良率は5%です。100個の製品を抜き取り検査したとき：

(1) 不良品が3個以下である確率（正規近似を使用）
(2) 不良品の数の95%信頼区間

<details markdown="1">
<summary>解答を見る</summary>

### 解答

$n=100$, $p=0.05$

期待値：$\mu = np = 5$
標準偏差：$\sigma = \sqrt{np(1-p)} = \sqrt{100 \times 0.05 \times 0.95} = \sqrt{4.75} \approx 2.18$

**(1) P(X ≤ 3) の正規近似**

連続性補正：$P(X \leq 3.5)$

$$z = \frac{3.5 - 5}{2.18} = \frac{-1.5}{2.18} \approx -0.69$$

標準正規分布表より：$P(Z \leq -0.69) \approx 0.245$

**答え：約24.5%**

**(2) 95%信頼区間**

$$\mu \pm 1.96\sigma = 5 \pm 1.96 \times 2.18 = 5 \pm 4.27$$

**答え：約0.7個〜9.3個（整数で1〜9個）**

</details>

---

## 関連コンテンツ

- [理論編：二項分布]({{ site.baseurl }}/theory/binomial/)
- [理論編：正規分布]({{ site.baseurl }}/theory/normal-distribution/)
- [正規分布の問題]({{ site.baseurl }}/problems/normal-distribution-problems/)

---

[問題編一覧に戻る]({{ site.baseurl }}/problems/) | [トップページに戻る]({{ site.baseurl }}/)
