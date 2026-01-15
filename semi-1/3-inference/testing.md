---
layout: default
title: 検定の基礎 - 準1級対策
description: ネイマン・ピアソンの補題、尤度比検定、UMP検定を解説
---

# 検定の基礎

仮説検定の理論的基盤と各種検定法を学びます。

---

## 1. 検定の基本概念

### 1.1 仮説の設定

- **帰無仮説** $H_0$：検定したい仮説（通常は「差がない」「効果がない」）
- **対立仮説** $H_1$：$H_0$ が棄却されたときに採用する仮説

| 仮説の種類 | 形式 |
|-----------|------|
| 単純仮説 | $H: \theta = \theta_0$ |
| 複合仮説 | $H: \theta \in \Theta$ （$\Theta$ は集合） |

### 1.2 検定統計量と棄却域

- **検定統計量** $T(\mathbf{X})$：データから計算される統計量
- **棄却域** $R$：$T \in R$ のとき $H_0$ を棄却

### 1.3 2種類の過誤

| 過誤 | 定義 | 確率 |
|-----|------|------|
| 第1種の過誤 | $H_0$ が真なのに棄却 | $\alpha$（有意水準） |
| 第2種の過誤 | $H_1$ が真なのに採択 | $\beta$ |

### 1.4 検出力（検定力）

$$\text{検出力} = 1 - \beta = P(\text{棄却} | H_1)$$

$H_1$ が真のときに正しく棄却する確率。

### 1.5 検出力関数

$$\pi(\theta) = P_\theta(T \in R)$$

- $\theta \in H_0$ のとき：$\pi(\theta) \leq \alpha$
- $\theta \in H_1$ のとき：$\pi(\theta) = 1 - \beta(\theta)$

---

## 2. ネイマン・ピアソンの補題

### 2.1 設定

単純仮説 vs 単純仮説：

- $H_0: \theta = \theta_0$
- $H_1: \theta = \theta_1$

### 2.2 尤度比

$$\Lambda(\mathbf{x}) = \frac{L(\theta_0; \mathbf{x})}{L(\theta_1; \mathbf{x})}$$

### 2.3 補題の内容

有意水準 $\alpha$ で最も検出力の高い検定（**最強力検定**）は、棄却域を

$$R = \{\mathbf{x} : \Lambda(\mathbf{x}) \leq k\}$$

とする検定である。ここで $k$ は $P_{H_0}(\Lambda \leq k) = \alpha$ を満たす定数。

### 2.4 同値な表現

$$R = \left\{\mathbf{x} : \frac{L(\theta_1; \mathbf{x})}{L(\theta_0; \mathbf{x})} \geq k'\right\}$$

（$H_1$ の尤度が相対的に大きいとき棄却）

---

## 3. 一様最強力検定（UMP検定）

### 3.1 定義

複合対立仮説 $H_1: \theta \in \Theta_1$ に対し、すべての $\theta_1 \in \Theta_1$ で最も検出力の高い検定を**一様最強力（UMP）検定**という。

### 3.2 単調尤度比

尤度比 $L(\theta_1)/L(\theta_0)$ が十分統計量 $T$ の単調増加関数であるとき、**単調尤度比**（MLR）をもつという。

### 3.3 UMP検定の存在条件

片側検定 $H_0: \theta \leq \theta_0$ vs $H_1: \theta > \theta_0$ で、分布が単調尤度比をもてば、UMP検定は

$$R = \{T \geq c\}$$

の形になる。

### 3.4 指数型分布族のUMP検定

$$f(x; \theta) = h(x) \exp(\eta(\theta)T(x) - A(\theta))$$

で $\eta(\theta)$ が $\theta$ の増加関数なら、片側検定にUMP検定が存在。

---

## 4. 尤度比検定

### 4.1 一般化尤度比

$$\Lambda = \frac{\max_{\theta \in \Theta_0} L(\theta)}{\max_{\theta \in \Theta} L(\theta)} = \frac{L(\hat{\theta}_0)}{L(\hat{\theta})}$$

- 分子：$H_0$ のもとでの最大尤度
- 分母：制約なしでの最大尤度

### 4.2 検定統計量

$$-2 \log \Lambda = 2[\ell(\hat{\theta}) - \ell(\hat{\theta}_0)]$$

### 4.3 ウィルクスの定理

大標本で：

$$-2 \log \Lambda \xrightarrow{d} \chi^2_r$$

$r$：$H_0$ で制約されるパラメータの数

### 4.4 棄却域

$$-2 \log \Lambda > \chi^2_{r, \alpha}$$ のとき $H_0$ を棄却

---

## 5. スコア検定とワルド検定

### 5.1 3つの漸近的同等な検定

| 検定 | 検定統計量 | 特徴 |
|-----|----------|------|
| 尤度比検定 | $-2[\ell(\theta_0) - \ell(\hat{\theta})]$ | 両方のMLEが必要 |
| ワルド検定 | $(\hat{\theta} - \theta_0)^2 I(\hat{\theta})$ | 制約なしのMLEのみ |
| スコア検定 | $U(\theta_0)^2 / I(\theta_0)$ | $H_0$ のもとで計算 |

### 5.2 スコア検定（ラグランジュ乗数検定）

$$S = \frac{U(\theta_0)^2}{I(\theta_0)} \xrightarrow{d} \chi^2_1$$

帰無仮説のもとでスコア関数の2乗を情報量で割る。

### 5.3 ワルド検定

$$W = (\hat{\theta} - \theta_0)^2 \cdot n \cdot I(\hat{\theta}) \xrightarrow{d} \chi^2_1$$

推定量と帰無仮説の値の差を標準化。

---

## 6. 多重比較

### 6.1 多重検定の問題

$m$ 個の検定を同時に行うと、少なくとも1つで第1種の過誤を犯す確率が増大：

$$1 - (1-\alpha)^m \approx m\alpha$$ （$\alpha$ が小さいとき）

### 6.2 ファミリーワイズエラー率（FWER）

$$\text{FWER} = P(\text{少なくとも1つの偽の棄却})$$

### 6.3 ボンフェローニ補正

各検定の有意水準を $\alpha/m$ にする：

$$\text{FWER} \leq m \times \frac{\alpha}{m} = \alpha$$

### 6.4 ホルム法

1. p値を昇順に並べる：$p_{(1)} \leq p_{(2)} \leq \cdots \leq p_{(m)}$
2. $p_{(i)} < \alpha/(m-i+1)$ を満たす最大の $i$ を見つける
3. $p_{(1)}, \ldots, p_{(i)}$ に対応する仮説を棄却

### 6.5 偽発見率（FDR）

$$\text{FDR} = E\left[\frac{\text{偽の棄却数}}{\text{総棄却数}}\right]$$

**ベンジャミニ・ホッホベルク法**：FDRを $\alpha$ に制御

---

## 7. 例題

### 例題1：ネイマン・ピアソンの補題

$X_1, \ldots, X_n \sim N(\mu, 1)$ で $H_0: \mu = 0$ vs $H_1: \mu = 1$ の最強力検定の棄却域を求めよ。

<details markdown="1">
<summary>解答を見る</summary>

### 解答

尤度比：

$$\Lambda = \frac{L(0)}{L(1)} = \frac{\exp(-\sum x_i^2/2)}{\exp(-\sum(x_i-1)^2/2)}$$

$$= \exp\left(-\frac{1}{2}\sum x_i^2 + \frac{1}{2}\sum(x_i-1)^2\right)$$

$$= \exp\left(-\frac{1}{2}\sum x_i^2 + \frac{1}{2}\sum x_i^2 - \sum x_i + \frac{n}{2}\right)$$

$$= \exp\left(-\sum x_i + \frac{n}{2}\right) = \exp\left(-n\bar{x} + \frac{n}{2}\right)$$

$\Lambda \leq k$ は $\bar{x} \geq c$ と同値。

$H_0$ のもとで $\bar{X} \sim N(0, 1/n)$ なので：

$$c = z_\alpha / \sqrt{n}$$

**答え：$\bar{x} \geq z_\alpha / \sqrt{n}$**

</details>

---

### 例題2：尤度比検定

$n = 100$, $\bar{x} = 52$, $s = 10$ のとき、$H_0: \mu = 50$ vs $H_1: \mu \neq 50$ の尤度比検定統計量を求めよ。

<details markdown="1">
<summary>解答を見る</summary>

### 解答

正規分布で分散未知の場合、尤度比検定統計量は：

$$-2 \log \Lambda = n \log\left(1 + \frac{t^2}{n-1}\right)$$

ここで：

$$t = \frac{\bar{x} - \mu_0}{s/\sqrt{n}} = \frac{52 - 50}{10/\sqrt{100}} = \frac{2}{1} = 2$$

$$-2 \log \Lambda = 100 \log\left(1 + \frac{4}{99}\right) = 100 \log(1.0404) \approx 100 \times 0.0396 = 3.96$$

これは $\chi^2_1$ 分布で評価。$\chi^2_{1, 0.05} = 3.84$ なので、$p < 0.05$。

**答え：検定統計量は約3.96**

</details>

---

### 例題3：ボンフェローニ補正

5つの検定を同時に行う。全体の有意水準を5%に保つには、各検定の有意水準をいくらにすべきか。

<details markdown="1">
<summary>解答を見る</summary>

### 解答

ボンフェローニ補正：

$$\alpha_{\text{各}} = \frac{\alpha_{\text{全体}}}{m} = \frac{0.05}{5} = 0.01$$

**答え：各検定の有意水準は1%（0.01）**

</details>

---

## 8. 重要公式まとめ

| 項目 | 公式 |
|-----|------|
| 検出力 | $1 - \beta = P(\text{棄却} \| H_1)$ |
| ネイマン・ピアソン | 棄却域：$L(\theta_0)/L(\theta_1) \leq k$ |
| 尤度比検定 | $-2\log\Lambda \sim \chi^2_r$（大標本） |
| ワルド検定 | $W = (\hat{\theta}-\theta_0)^2 nI(\hat{\theta})$ |
| スコア検定 | $S = U(\theta_0)^2/I(\theta_0)$ |
| ボンフェローニ | 各 $\alpha = \alpha_{\text{全体}}/m$ |

---

[統計的推測に戻る]({{ site.baseurl }}/semi-1/3-inference/) | [準1級トップ]({{ site.baseurl }}/semi-1/) | [トップページ]({{ site.baseurl }}/)
