---
layout: default
title: 変数変換 - 準1級対策
description: ヤコビアン、畳み込み、順序統計量の分布を解説
---

# 変数変換

確率変数の関数の分布を求める手法を学びます。

---

## 1. 1変数の変換

### 1.1 離散の場合

$Y = g(X)$ のとき：

$$P(Y = y) = \sum_{x: g(x) = y} P(X = x)$$

### 1.2 連続の場合（単調変換）

$Y = g(X)$ で $g$ が単調増加のとき：

$$f_Y(y) = f_X(g^{-1}(y)) \cdot \left|\frac{d}{dy}g^{-1}(y)\right|$$

$g$ が単調減少でも同様（絶対値をとる）。

### 1.3 一般の変換

$g$ が単調でない場合：

$$f_Y(y) = \sum_{i: g(x_i) = y} \frac{f_X(x_i)}{|g'(x_i)|}$$

---

## 2. 多変数の変換（ヤコビアン）

### 2.1 ヤコビ行列

$(X, Y) \to (U, V)$ の変換 $u = g_1(x, y)$, $v = g_2(x, y)$ に対し：

$$\mathbf{J} = \begin{pmatrix} \frac{\partial u}{\partial x} & \frac{\partial u}{\partial y} \\ \frac{\partial v}{\partial x} & \frac{\partial v}{\partial y} \end{pmatrix}$$

### 2.2 ヤコビアン

$$|J| = \left|\frac{\partial(u, v)}{\partial(x, y)}\right| = \left|\det(\mathbf{J})\right|$$

### 2.3 変換公式

$(U, V)$ の同時密度関数：

$$f_{U,V}(u, v) = f_{X,Y}(x(u,v), y(u,v)) \cdot |J^{-1}|$$

$$= f_{X,Y}(x(u,v), y(u,v)) \cdot \left|\frac{\partial(x, y)}{\partial(u, v)}\right|$$

### 2.4 ヤコビアンの性質

$$\left|\frac{\partial(x, y)}{\partial(u, v)}\right| = \left|\frac{\partial(u, v)}{\partial(x, y)}\right|^{-1}$$

---

## 3. 代表的な変換

### 3.1 線形変換

$Y = aX + b$ のとき：

$$f_Y(y) = \frac{1}{|a|} f_X\left(\frac{y-b}{a}\right)$$

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

### 4.1 2次元

$(X, Y) \to (R, \Theta)$：

$$x = r\cos\theta, \quad y = r\sin\theta$$

ヤコビアン：

$$\left|\frac{\partial(x, y)}{\partial(r, \theta)}\right| = r$$

### 4.2 標準正規分布への応用

$X, Y \sim N(0, 1)$ が独立のとき：

$$f_{R, \Theta}(r, \theta) = \frac{1}{2\pi} r e^{-r^2/2}$$

- $\Theta \sim \text{Uniform}(0, 2\pi)$
- $R^2 \sim \chi^2_2$（$R^2 = X^2 + Y^2$）

---

## 5. 和と差の分布

### 5.1 畳み込み（Convolution）

$X, Y$ が独立で $Z = X + Y$ のとき：

$$f_Z(z) = \int_{-\infty}^{\infty} f_X(x) f_Y(z-x) dx = (f_X * f_Y)(z)$$

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

$$f_Z(z) = \int_0^{\infty} |y| f_X(zy) f_Y(y) dy$$

### 6.3 F分布の導出

$U \sim \chi^2_m$, $V \sim \chi^2_n$ が独立のとき：

$$F = \frac{U/m}{V/n} \sim F_{m, n}$$

---

## 7. 順序統計量

### 7.1 定義

$X_1, \ldots, X_n$ を並べ替えた：

$$X_{(1)} \leq X_{(2)} \leq \cdots \leq X_{(n)}$$

- $X_{(1)}$：最小値
- $X_{(n)}$：最大値
- $X_{(\lceil n/2 \rceil)}$：中央値（$n$ が奇数のとき）

### 7.2 最小値・最大値の分布

$$F_{X_{(1)}}(x) = 1 - [1 - F_X(x)]^n$$

$$F_{X_{(n)}}(x) = [F_X(x)]^n$$

密度関数：

$$f_{X_{(1)}}(x) = n[1-F_X(x)]^{n-1} f_X(x)$$

$$f_{X_{(n)}}(x) = n[F_X(x)]^{n-1} f_X(x)$$

### 7.3 $k$ 番目の順序統計量

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

$$\left|\frac{\partial(x, y)}{\partial(u, v)}\right| = u$$

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

## 9. 重要公式まとめ

| 項目 | 公式 |
|-----|------|
| 1変数変換 | $f_Y(y) = f_X(g^{-1}(y)) \cdot \|(g^{-1})'(y)\|$ |
| ヤコビアン | $\|J\| = \|\partial(u,v)/\partial(x,y)\|$ |
| 畳み込み | $f_{X+Y}(z) = \int f_X(x) f_Y(z-x) dx$ |
| 最大値 | $F_{X_{(n)}}(x) = [F_X(x)]^n$ |
| 最小値 | $F_{X_{(1)}}(x) = 1 - [1-F_X(x)]^n$ |
| 順序統計量 | $X_{(k)} \sim \text{Beta}(k, n-k+1)$（一様） |

---

[確率論に戻る]({{ site.baseurl }}/semi-1/1-probability/) | [準1級トップ]({{ site.baseurl }}/semi-1/) | [トップページ]({{ site.baseurl }}/)
