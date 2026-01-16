---
layout: default
title: 変数変換 - 準1級対策
description: ヤコビアン、畳み込み、順序統計量の分布を解説
---

# 変数変換

確率変数の関数の分布を求める手法を学びます。

---

## 変数変換とは何か？

### なぜ変数変換が必要か

確率変数 $X$ の分布がわかっているとき、$Y = g(X)$ という別の変数の分布を知りたい場面は非常に多くあります。

**実用例**：
- 収益 $X$ から対数収益率 $Y = \log X$ を計算
- 距離 $R$ から面積 $Y = \pi R^2$ を計算
- 2つの独立な確率変数の和 $Z = X + Y$ の分布

### 変換の基本的な考え方

```
確率は保存される！

X の範囲 [a, b] が Y の範囲 [g(a), g(b)] に対応するとき、
その範囲に入る確率は変わらない。

      確率の保存
         ↓
P(a ≤ X ≤ b) = P(g(a) ≤ Y ≤ g(b))

ただし、密度関数は「伸び縮み」を補正する必要がある
```

### 変換による密度の変化（直感的理解）

```
Y = 2X の変換を考える（X を2倍に引き伸ばす）

X の分布:     Y の分布:
  ████            ██
  ████   →→→      ██
  ████            ██
  ████            ██
 [0, 1]        [0, 2]

同じ確率を2倍の幅に分散させるので、
密度（高さ）は 1/2 になる！

一般に：f_Y(y) = f_X(x) × |変換の縮み率|
             = f_X(g⁻¹(y)) × |d/dy g⁻¹(y)|
```

---

## 1. 1変数の変換

### 1.1 離散の場合

$Y = g(X)$ のとき：

$$P(Y = y) = \sum_{x: g(x) = y} P(X = x)$$

### 1.2 連続の場合（単調変換）

$Y = g(X)$ で $g$ が単調増加のとき：

$$f_Y(y) = f_X(g^{-1}(y)) \cdot \left\lvert\frac{d}{dy}g^{-1}(y)\right\rvert$$

$g$ が単調減少でも同様（絶対値をとる）。

**ポイント**：$\left\lvert\frac{d}{dy}g^{-1}(y)\right\rvert$ は「$y$ の小さな変化が $x$ のどれだけの変化に対応するか」を表す。これが変換による「引き伸ばし/圧縮」を補正する因子。

### 1.3 一般の変換

$g$ が単調でない場合：

$$f_Y(y) = \sum_{i: g(x_i) = y} \frac{f_X(x_i)}{\lvert g'(x_i) \rvert}$$

---

## 2. 多変数の変換（ヤコビアン）

### ヤコビアンの直感的理解

**Jacobian（ヤコビアン）**は、多変数における「変換による面積（体積）の伸び縮み率」を表します。

```
2次元での変換のイメージ

(x, y) 空間           (u, v) 空間
    ┌──┐                 ╱╲
    │  │    変換 →→→    ╱  ╲
    │  │               ╱    ╲
    └──┘              ╱──────╲

小さな正方形が → 平行四辺形に変形

|ヤコビアン| = 平行四辺形の面積 / 正方形の面積
            = 面積の拡大率

確率密度 × 面積 = 確率（一定）なので、
面積が n倍 になれば、密度は 1/n倍 に補正する必要がある
```

### 2.1 ヤコビ行列

$(X, Y) \to (U, V)$ の変換 $u = g_1(x, y)$, $v = g_2(x, y)$ に対し：

$$\mathbf{J} = \begin{pmatrix} \frac{\partial u}{\partial x} & \frac{\partial u}{\partial y} \\ \frac{\partial v}{\partial x} & \frac{\partial v}{\partial y} \end{pmatrix}$$

### 2.2 ヤコビアン

$$\lvert J \rvert = \left\lvert\frac{\partial(u, v)}{\partial(x, y)}\right\rvert = \lvert\det(\mathbf{J})\rvert$$

### 2.3 変換公式

$(U, V)$ の同時密度関数：

$$f_{U,V}(u, v) = f_{X,Y}(x(u,v), y(u,v)) \cdot \lvert J^{-1} \rvert$$

$$= f_{X,Y}(x(u,v), y(u,v)) \cdot \left\lvert\frac{\partial(x, y)}{\partial(u, v)}\right\rvert$$

### 2.4 ヤコビアンの性質

$$\left\lvert\frac{\partial(x, y)}{\partial(u, v)}\right\rvert = \left\lvert\frac{\partial(u, v)}{\partial(x, y)}\right\rvert^{-1}$$

---

## 3. 代表的な変換

### 3.1 線形変換

$Y = aX + b$ のとき：

$$f_Y(y) = \frac{1}{\lvert a \rvert} f_X\left(\frac{y-b}{a}\right)$$

### 3.2 対数変換

$Y = \log X$（$X > 0$）のとき：

$$f_Y(y) = f_X(e^y) \cdot e^y$$

### 3.3 逆数変換

$Y = 1/X$ のとき：

$$f_Y(y) = f_X(1/y) \cdot \frac{1}{y^2}$$

### 3.4 二乗変換

$Y = X^2$ のとき（$X$ が対称分布）：

$$f_Y(y) = \frac{1}{2\sqrt{y}}[f_X(\sqrt{y}) + f_X(-\sqrt{y})]$$

---

## 4. 極座標変換

極座標変換は2次元正規分布の解析で特に重要です。

### 4.1 2次元

$(X, Y) \to (R, \Theta)$：

$$x = r\cos\theta, \quad y = r\sin\theta$$

```
デカルト座標 → 極座標

    y                     θ
    │   *(x,y)           │   *(r,θ)
    │  /                 │  /
    │ / r                │ /
    │/θ                  │/
    └───── x             └───── r

(x, y) = (r cos θ, r sin θ)
```

ヤコビアン：

$$\left\lvert\frac{\partial(x, y)}{\partial(r, \theta)}\right\rvert = \begin{vmatrix} \cos\theta & -r\sin\theta \\ \sin\theta & r\cos\theta \end{vmatrix} = r\cos^2\theta + r\sin^2\theta = r$$

**直感的理解**：半径 $r$ が大きいほど、角度の変化に対応する弧の長さが大きくなるため、面積要素が $r$ に比例して大きくなる。

### 4.2 標準正規分布への応用

$X, Y \sim N(0, 1)$ が独立のとき：

$$f_{R, \Theta}(r, \theta) = \frac{1}{2\pi} r e^{-r^2/2}$$

- $\Theta \sim \text{Uniform}(0, 2\pi)$
- $R^2 \sim \chi^2_2$（$R^2 = X^2 + Y^2$）

---

## 5. 和と差の分布

独立な確率変数の和の分布を求める方法を学びます。

### 5.1 畳み込み（Convolution）

$X, Y$ が独立で $Z = X + Y$ のとき：

$$f_Z(z) = \int_{-\infty}^{\infty} f_X(x) f_Y(z-x) dx = (f_X * f_Y)(z)$$

**畳み込みの意味**：

```
Z = X + Y の値が z になる方法は無限にある

X = 0,   Y = z     →  X + Y = z
X = 1,   Y = z-1   →  X + Y = z
X = x,   Y = z-x   →  X + Y = z

すべての可能な組み合わせの確率を足し合わせる！

f_Z(z) = ∫ P(X = x) × P(Y = z-x) dx
       = ∫ f_X(x) × f_Y(z-x) dx
```

### 5.2 代表的な和の分布

| $X$ | $Y$ | $X + Y$ |
|-----|-----|---------|
| $N(\mu_1, \sigma_1^2)$ | $N(\mu_2, \sigma_2^2)$ | $N(\mu_1+\mu_2, \sigma_1^2+\sigma_2^2)$ |
| $\text{Poi}(\lambda_1)$ | $\text{Poi}(\lambda_2)$ | $\text{Poi}(\lambda_1+\lambda_2)$ |
| $\Gamma(\alpha_1, \beta)$ | $\Gamma(\alpha_2, \beta)$ | $\Gamma(\alpha_1+\alpha_2, \beta)$ |
| $\chi^2_{n_1}$ | $\chi^2_{n_2}$ | $\chi^2_{n_1+n_2}$ |
| $\text{Bin}(n_1, p)$ | $\text{Bin}(n_2, p)$ | $\text{Bin}(n_1+n_2, p)$ |

### 5.3 差の分布

$Z = X - Y$ のとき：

$$f_Z(z) = \int_{-\infty}^{\infty} f_X(x) f_Y(x-z) dx$$

---

## 6. 商と積の分布

### 6.1 積の分布

$Z = XY$（$X, Y > 0$）のとき：

$$f_Z(z) = \int_0^{\infty} \frac{1}{x} f_X(x) f_Y(z/x) dx$$

### 6.2 商の分布

$Z = X/Y$ のとき：

$$f_Z(z) = \int_0^{\infty} \lvert y \rvert f_X(zy) f_Y(y) dy$$

### 6.3 F分布の導出

$U \sim \chi^2_m$, $V \sim \chi^2_n$ が独立のとき：

$$F = \frac{U/m}{V/n} \sim F_{m, n}$$

---

## 7. 順序統計量

### 順序統計量とは

標本を小さい順に並べ替えたものが順序統計量（Order Statistics）です。中央値、最小値、最大値、分位点など、実用的な統計量の基盤となります。

### 7.1 定義

$X_1, \ldots, X_n$ を小さい順に並べ替えた：

$$X_{(1)} \leq X_{(2)} \leq \cdots \leq X_{(n)}$$

```
例：n = 5 のサンプル

元のデータ:    X₁=3, X₂=7, X₃=1, X₄=9, X₅=4

並べ替え後:    X₍₁₎=1, X₍₂₎=3, X₍₃₎=4, X₍₄₎=7, X₍₅₎=9
               最小値                          最大値
                        ↑
                      中央値
```

- $X_{(1)}$：最小値
- $X_{(n)}$：最大値
- $X_{(\lceil n/2 \rceil)}$：中央値（$n$ が奇数のとき）

### 7.2 最小値・最大値の分布

**最大値の直感的理解**：

```
最大値 X₍ₙ₎ ≤ x となる確率は？

「すべての Xi が x 以下」という事象

P(X₍ₙ₎ ≤ x) = P(X₁ ≤ x かつ X₂ ≤ x かつ ... かつ Xₙ ≤ x)
            = P(X₁ ≤ x) × P(X₂ ≤ x) × ... × P(Xₙ ≤ x)  [独立性]
            = [F(x)]ⁿ
```

$$F_{X_{(n)}}(x) = [F_X(x)]^n$$

**最小値の直感的理解**：

```
最小値 X₍₁₎ > x となる確率は？

「すべての Xi が x より大きい」という事象

P(X₍₁₎ > x) = [1 - F(x)]ⁿ

よって P(X₍₁₎ ≤ x) = 1 - [1 - F(x)]ⁿ
```

$$F_{X_{(1)}}(x) = 1 - [1 - F_X(x)]^n$$

密度関数：

$$f_{X_{(1)}}(x) = n[1-F_X(x)]^{n-1} f_X(x)$$

$$f_{X_{(n)}}(x) = n[F_X(x)]^{n-1} f_X(x)$$

### 7.3 $k$ 番目の順序統計量

**直感的理解**：

```
X₍ₖ₎ が x 付近にある確率を考える

・k-1 個は x より小さい     → [F(x)]^(k-1)
・1個（X₍ₖ₎）は x 付近     → f(x) dx
・n-k 個は x より大きい    → [1-F(x)]^(n-k)

さらに、どの k-1 個が小さいかの組み合わせ → n!/(k-1)!(n-k)!
```

$$f_{X_{(k)}}(x) = \frac{n!}{(k-1)!(n-k)!} [F_X(x)]^{k-1} [1-F_X(x)]^{n-k} f_X(x)$$

### 7.4 一様分布の順序統計量

$X_i \sim \text{Uniform}(0, 1)$ のとき：

$$X_{(k)} \sim \text{Beta}(k, n-k+1)$$

$$E[X_{(k)}] = \frac{k}{n+1}$$

### 7.5 範囲（Range）

$$R = X_{(n)} - X_{(1)}$$

---

## 8. 例題

### 例題1：ヤコビアンを用いた変換

$X, Y$ が独立に $\text{Exp}(1)$ に従うとき、$U = X + Y$, $V = X/(X+Y)$ の同時分布を求めよ。

<details markdown="1">
<summary>解答を見る</summary>

### 解答

逆変換：$x = uv$, $y = u(1-v)$

ヤコビアン：

$$\frac{\partial(x, y)}{\partial(u, v)} = \begin{vmatrix} v & u \\ 1-v & -u \end{vmatrix} = -uv - u(1-v) = -u$$

$$\left\lvert\frac{\partial(x, y)}{\partial(u, v)}\right\rvert = u$$

元の同時密度：

$$f_{X,Y}(x, y) = e^{-x} e^{-y} = e^{-(x+y)}$$

変換後：

$$f_{U,V}(u, v) = e^{-u} \cdot u \quad (u > 0, 0 < v < 1)$$

$$= u e^{-u} \cdot 1$$

$U \sim \Gamma(2, 1)$ と $V \sim \text{Uniform}(0, 1)$ が独立。

**答え：$f_{U,V}(u, v) = u e^{-u}$（$U$ と $V$ は独立）**

</details>

---

### 例題2：順序統計量

$X_1, \ldots, X_5$ が $\text{Uniform}(0, 1)$ から独立に得られるとき、中央値 $X_{(3)}$ の期待値と分散を求めよ。

<details markdown="1">
<summary>解答を見る</summary>

### 解答

$X_{(3)} \sim \text{Beta}(3, 3)$

ベータ分布 $\text{Beta}(\alpha, \beta)$ の期待値と分散：

$$E[X] = \frac{\alpha}{\alpha + \beta} = \frac{3}{6} = \frac{1}{2}$$

$$\text{Var}(X) = \frac{\alpha \beta}{(\alpha+\beta)^2(\alpha+\beta+1)} = \frac{3 \times 3}{36 \times 7} = \frac{9}{252} = \frac{1}{28}$$

**答え：$E[X_{(3)}] = 1/2$, $\text{Var}(X_{(3)}) = 1/28$**

</details>

---

### 例題3：畳み込み

$X \sim \text{Uniform}(0, 1)$, $Y \sim \text{Uniform}(0, 1)$ が独立のとき、$Z = X + Y$ の密度関数を求めよ。

<details markdown="1">
<summary>解答を見る</summary>

### 解答

畳み込み：

$$f_Z(z) = \int_0^1 f_X(x) f_Y(z-x) dx$$

$0 < z < 1$ のとき：

$$f_Z(z) = \int_0^z 1 \cdot 1 \, dx = z$$

$1 < z < 2$ のとき：

$$f_Z(z) = \int_{z-1}^1 1 \cdot 1 \, dx = 2 - z$$

$$f_Z(z) = \begin{cases} z & (0 < z < 1) \\ 2 - z & (1 \leq z < 2) \\ 0 & (\text{otherwise}) \end{cases}$$

**答え：三角分布（イルヴィン・ホール分布 $n=2$）**

</details>

---

## 9. よくある誤解

### 誤解1：ヤコビアンの向き

```
✗ 誤り：f_{U,V}(u,v) = f_{X,Y}(x,y) × |∂(u,v)/∂(x,y)|

✓ 正しい：f_{U,V}(u,v) = f_{X,Y}(x,y) × |∂(x,y)/∂(u,v)|

ポイント：新しい変数 (u,v) の密度を求めるには、
         (u,v) で微分した逆ヤコビアンを使う！

覚え方：「新しい方で微分」または「逆変換のヤコビアン」
```

### 誤解2：畳み込みの積分範囲

```
✗ 誤り：常に -∞ から ∞ まで積分

✓ 正しい：f_X と f_Y がゼロでない範囲のみ考慮

例：X, Y ~ Uniform(0,1) で Z = X + Y のとき
   0 < z < 1 と 1 < z < 2 で積分範囲が異なる
```

### 誤解3：順序統計量の分布

```
✗ 誤り：「最大値の期待値」は「期待値の最大値」ではない

   n個の iid サンプル X₁,...,Xₙ ~ Uniform(0,1) のとき
   E[X_i] = 1/2 だが E[X₍ₙ₎] = n/(n+1) ≠ 1/2

✗ 誤り：順序統計量どうしは独立

✓ 正しい：X₍₁₎, X₍₂₎, ... は互いに従属
         （当然：X₍₁₎ ≤ X₍₂₎ という関係がある）
```

**注**：**iid** = **i**ndependent and **i**dentically **d**istributed（独立同分布）

---

## 10. 概念のつながり

```
変数変換の全体像

確率分布の理論
     ↓
┌────────────────────────────────────────┐
│            変数変換                      │
├────────────────────────────────────────┤
│ 1変数変換    ─→  密度の補正係数          │
│    ↓               (導関数の絶対値)      │
│ 多変数変換  ─→  ヤコビアン              │
│    ↓               (行列式の絶対値)      │
│ 極座標変換  ─→  2次元正規分布の解析      │
└────────────────────────────────────────┘
          ↓
┌────────────────────────────────────────┐
│            和と積の分布                  │
├────────────────────────────────────────┤
│ 畳み込み    ─→  独立な和の分布           │
│ 商の分布    ─→  t分布、F分布の導出       │
└────────────────────────────────────────┘
          ↓
┌────────────────────────────────────────┐
│            順序統計量                    │
├────────────────────────────────────────┤
│ 最大・最小  ─→  極値統計学               │
│ 分位点      ─→  ノンパラメトリック統計    │
│ 範囲        ─→  品質管理                 │
└────────────────────────────────────────┘
```

---

## 11. 重要公式まとめ

| 項目 | 公式 |
|-----|------|
| 1変数変換 | $f_Y(y) = f_X(g^{-1}(y)) \cdot \lvert(g^{-1})'(y)\rvert$ |
| ヤコビアン | $\lvert J\rvert = \lvert\partial(x,y)/\partial(u,v)\rvert$ |
| 畳み込み | $f_{X+Y}(z) = \int f_X(x) f_Y(z-x) dx$ |
| 最大値 | $F_{X_{(n)}}(x) = [F_X(x)]^n$ |
| 最小値 | $F_{X_{(1)}}(x) = 1 - [1-F_X(x)]^n$ |
| 順序統計量 | $X_{(k)} \sim \text{Beta}(k, n-k+1)$（一様分布の場合） |

---

[確率論に戻る]({{ site.baseurl }}/semi-1/1-probability/) | [準1級トップ]({{ site.baseurl }}/semi-1/) | [トップページ]({{ site.baseurl }}/)
