---
layout: default
title: 確率の基礎演習
description: 確率計算の基本練習問題
category: basic
difficulty: 1
order: 10
---

# 確率の基礎演習

確率計算の基本を身につける練習問題です。

---

## 問題1：古典的確率

サイコロを1回振るとき、偶数が出る確率は？

<details markdown="1">
<summary>解答を見る</summary>

### 解答

偶数：2, 4, 6の3通り
全事象：1, 2, 3, 4, 5, 6の6通り

$$P(偶数) = \frac{3}{6} = \frac{1}{2}$$

**答え：1/2（50%）**

</details>

---

## 問題2：余事象

サイコロを1回振るとき、1以外が出る確率は？

<details markdown="1">
<summary>解答を見る</summary>

### 解答

余事象を使う：

$$P(1以外) = 1 - P(1) = 1 - \frac{1}{6} = \frac{5}{6}$$

**答え：5/6**

</details>

---

## 問題3：和事象

トランプから1枚引くとき、ハートまたはキングを引く確率は？

<details markdown="1">
<summary>解答を見る</summary>

### 解答

$$P(ハート \cup キング) = P(ハート) + P(キング) - P(ハートのキング)$$

$$= \frac{13}{52} + \frac{4}{52} - \frac{1}{52} = \frac{16}{52} = \frac{4}{13}$$

**答え：4/13**

</details>

---

## 問題4：独立事象

コインを2回投げるとき、2回とも表が出る確率は？

<details markdown="1">
<summary>解答を見る</summary>

### 解答

独立事象なので：

$$P(表 \cap 表) = P(表) \times P(表) = \frac{1}{2} \times \frac{1}{2} = \frac{1}{4}$$

**答え：1/4（25%）**

</details>

---

## 問題5：くじ引き

10本のくじから当たり3本があります。2本引くとき、少なくとも1本当たる確率は？

<details markdown="1">
<summary>解答を見る</summary>

### 解答

余事象を使う：

$$P(少なくとも1本当たり) = 1 - P(2本ともハズレ)$$

$$P(2本ともハズレ) = \frac{7}{10} \times \frac{6}{9} = \frac{42}{90} = \frac{7}{15}$$

$$P(少なくとも1本当たり) = 1 - \frac{7}{15} = \frac{8}{15}$$

**答え：8/15**

</details>

---

## 問題6：条件付き確率

袋に赤玉5個、白玉3個があります。1個取り出して赤だったとき、次に白を取り出す確率は？

<details markdown="1">
<summary>解答を見る</summary>

### 解答

1個目に赤を取り出した後：
- 残り：赤4個、白3個（計7個）

$$P(2個目が白 | 1個目が赤) = \frac{3}{7}$$

**答え：3/7**

</details>

---

## 問題7：乗法定理

問題6で、1個目が赤、2個目が白となる確率は？

<details markdown="1">
<summary>解答を見る</summary>

### 解答

$$P(1個目赤 \cap 2個目白) = P(1個目赤) \times P(2個目白 | 1個目赤)$$

$$= \frac{5}{8} \times \frac{3}{7} = \frac{15}{56}$$

**答え：15/56**

</details>

---

## 問題8：反復試行

成功率60%のゲームを3回行うとき、2回成功する確率は？

<details markdown="1">
<summary>解答を見る</summary>

### 解答

二項分布：

$$P(X=2) = \binom{3}{2} (0.6)^2 (0.4)^1 = 3 \times 0.36 \times 0.4 = 0.432$$

**答え：0.432（43.2%）**

</details>

---

## 問題9：確率の加法（排反事象）

サイコロを振って、1または6が出る確率は？

<details markdown="1">
<summary>解答を見る</summary>

### 解答

1と6は同時に出ないので排反事象：

$$P(1 \cup 6) = P(1) + P(6) = \frac{1}{6} + \frac{1}{6} = \frac{2}{6} = \frac{1}{3}$$

**答え：1/3**

</details>

---

## 問題10：確率の性質

P(A) = 0.4、P(B) = 0.5、P(A∩B) = 0.2 のとき、P(A∪B) は？

<details markdown="1">
<summary>解答を見る</summary>

### 解答

$$P(A \cup B) = P(A) + P(B) - P(A \cap B)$$

$$= 0.4 + 0.5 - 0.2 = 0.7$$

**答え：0.7（70%）**

</details>

---

## 問題11：条件付き確率の計算

P(A) = 0.6、P(B|A) = 0.5 のとき、P(A∩B) は？

<details markdown="1">
<summary>解答を見る</summary>

### 解答

$$P(A \cap B) = P(A) \times P(B|A) = 0.6 \times 0.5 = 0.3$$

**答え：0.3（30%）**

</details>

---

## 関連コンテンツ

- [理論編：確率の基礎]({{ site.baseurl }}/theory/probability/)
- [確率の基本計算問題]({{ site.baseurl }}/problems/probability-basics-problems/)

---

[問題編一覧に戻る]({{ site.baseurl }}/problems/) | [トップページに戻る]({{ site.baseurl }}/)
