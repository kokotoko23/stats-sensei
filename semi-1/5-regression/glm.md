---
layout: default
title: 一般化線形モデル（GLM） - 準1級対策
description: ロジスティック回帰、ポアソン回帰、リンク関数を解説
---

# 一般化線形モデル（GLM）

一般化線形モデル（**G**eneralized **L**inear **M**odel）は、正規分布以外の応答変数に対応できる回帰モデルの枠組みです。

---

## GLM はなぜ必要か

通常の線形回帰は「連続値の正規分布」を仮定しますが、実世界では様々な種類の応答変数があります。

```
応答変数のタイプと適切なモデル

応答変数        │ 従来の問題              │ GLM での解決
────────────────┼────────────────────────┼─────────────────
0/1（二値）     │ 予測値が0-1外になる     │ ロジスティック回帰
カウント（0,1,2...）│ 負の予測値が出る    │ ポアソン回帰
正の連続値      │ 負の予測値が出る        │ ガンマ回帰

GLM の核心：
  ・リンク関数で「予測範囲の問題」を解決
  ・指数型分布族で「分布の仮定」を柔軟に
```

---

## 1. GLMの構成要素

### 1.1 3つの構成要素

| 要素 | 説明 |
|-----|------|
| **確率分布** | 応答変数の分布（指数型分布族） |
| **線形予測子** | $\eta = \mathbf{x}^\top \boldsymbol{\beta}$ |
| **リンク関数** | $g(\mu) = \eta$（平均と線形予測子を結ぶ） |

### 1.2 指数型分布族

確率密度（質量）関数が以下の形：

$$f(y; \theta, \phi) = \exp\left\{ \frac{y\theta - b(\theta)}{a(\phi)} + c(y, \phi) \right\}$$

- $\theta$：自然パラメータ
- $\phi$：分散パラメータ
- $b(\theta)$：累積母関数

**性質**：
- $E[Y] = \mu = b'(\theta)$
- $\text{Var}(Y) = a(\phi) b''(\theta)$

### 1.3 主要な分布とリンク関数

| 分布 | 標準リンク | $g(\mu)$ |
|-----|----------|---------|
| 正規分布 | 恒等 | $\mu$ |
| 二項分布 | ロジット | $\log\frac{\mu}{1-\mu}$ |
| ポアソン分布 | 対数 | $\log\mu$ |
| ガンマ分布 | 逆数 | $1/\mu$ |

---

## 2. ロジスティック回帰

### 2.1 モデル

二値応答 $Y \in \{0, 1\}$ に対し：

$$P(Y = 1 \mid \mathbf{x}) = \pi(\mathbf{x}) = \frac{\exp(\mathbf{x}^\top \boldsymbol{\beta})}{1 + \exp(\mathbf{x}^\top \boldsymbol{\beta})}$$

ロジット変換：

$$\text{logit}(\pi) = \log\frac{\pi}{1-\pi} = \mathbf{x}^\top \boldsymbol{\beta} = \beta_0 + \beta_1 x_1 + \cdots + \beta_p x_p$$

### 2.2 オッズ比

**オッズ**：$\text{odds} = \frac{\pi}{1-\pi}$

**オッズ比**（Odds Ratio）：$x_j$ が1単位増加したときのオッズの変化

$$\text{OR}_j = e^{\beta_j}$$

- $\text{OR} > 1$：リスク増加
- $\text{OR} < 1$：リスク減少
- $\text{OR} = 1$：効果なし

### 2.3 最尤推定

対数尤度関数：

$$\ell(\boldsymbol{\beta}) = \sum_{i=1}^{n} \left\{ y_i \log\pi_i + (1-y_i)\log(1-\pi_i) \right\}$$

ニュートン・ラフソン法または反復重み付き最小二乗法（IRLS）で解く。

---

## 3. プロビット回帰

### 3.1 モデル

標準正規分布の累積分布関数 $\Phi$ を使用：

$$P(Y = 1 \mid \mathbf{x}) = \Phi(\mathbf{x}^\top \boldsymbol{\beta})$$

### 3.2 ロジスティック回帰との比較

| 項目 | ロジスティック | プロビット |
|-----|--------------|----------|
| リンク関数 | ロジット | 正規CDF逆関数 |
| 係数の解釈 | オッズ比 | やや困難 |
| 裾の重さ | 重い | 軽い |
| 使用頻度 | 高い | 経済学で多い |

近似関係：$\beta_{\text{probit}} \approx \beta_{\text{logit}} / 1.6$

---

## 4. ポアソン回帰

### 4.1 モデル

カウントデータ $Y \in \{0, 1, 2, \ldots\}$ に対し：

$$Y \sim \text{Poisson}(\mu), \quad \log\mu = \mathbf{x}^\top \boldsymbol{\beta}$$

### 4.2 係数の解釈

$x_j$ が1単位増加したときの期待値の変化：

$$\frac{\mu_{\text{new}}}{\mu_{\text{old}}} = e^{\beta_j}$$

- **発生率比**（Incidence Rate Ratio, IRR）

### 4.3 オフセット

異なる観察期間 $t_i$ を考慮：

$$\log\mu_i = \log t_i + \mathbf{x}_i^\top \boldsymbol{\beta}$$

$\log t_i$ を**オフセット**として固定。

### 4.4 過分散への対処

ポアソン分布では $E[Y] = \text{Var}(Y) = \mu$ だが、実データでは分散が大きいことが多い。

**対処法**：
- 負の二項回帰
- 準ポアソン回帰

---

## 5. モデルの評価

### 5.1 逸脱度（Deviance）

$$D = 2\left\{ \ell(\hat{\boldsymbol{\theta}}_{\text{full}}) - \ell(\hat{\boldsymbol{\theta}}_{\text{model}}) \right\}$$

- 飽和モデルとの対数尤度の差
- 小さいほど良い適合

### 5.2 AIC

$$\text{AIC} = -2\ell(\hat{\boldsymbol{\beta}}) + 2p$$

$p$：パラメータ数

### 5.3 適合度検定

逸脱度は漸近的に $\chi^2$ 分布に従う：

$$D \sim \chi^2_{n-p}$$

---

## 6. 例題

### 例題1：オッズ比の計算

ロジスティック回帰で、喫煙有無（$x$）の係数が $\beta = 0.7$ のとき、喫煙者の非喫煙者に対するオッズ比を求めよ。

<details markdown="1">
<summary>解答を見る</summary>

### 解答

$$\text{OR} = e^{\beta} = e^{0.7} \approx 2.01$$

**答え：約2.01**

喫煙者は非喫煙者の約2倍のオッズを持つ。

</details>

---

### 例題2：ポアソン回帰の解釈

交通事故件数のポアソン回帰で、「雨天」ダミー変数の係数が $\beta = 0.3$ のとき、雨天時の事故発生率は晴天時の何倍か。

<details markdown="1">
<summary>解答を見る</summary>

### 解答

発生率比：

$$\text{IRR} = e^{\beta} = e^{0.3} \approx 1.35$$

**答え：約1.35倍**

雨天時は晴天時より事故が約35%多い。

</details>

---

### 例題3：ロジットの計算

ある条件で $P(Y=1) = 0.8$ のとき、ロジット値を求めよ。

<details markdown="1">
<summary>解答を見る</summary>

### 解答

$$\text{logit}(0.8) = \log\frac{0.8}{1-0.8} = \log\frac{0.8}{0.2} = \log 4 \approx 1.39$$

**答え：約1.39**

</details>

---

## 7. 重要公式まとめ

| 項目 | 公式 |
|-----|------|
| ロジット | $\log\frac{\pi}{1-\pi} = \mathbf{x}^\top\boldsymbol{\beta}$ |
| オッズ比 | $\text{OR} = e^{\beta}$ |
| ロジスティック関数 | $\pi = \frac{e^\eta}{1+e^\eta}$ |
| ポアソン対数リンク | $\log\mu = \mathbf{x}^\top\boldsymbol{\beta}$ |
| 発生率比 | $\text{IRR} = e^{\beta}$ |
| 逸脱度 | $D = 2(\ell_{\text{full}} - \ell_{\text{model}})$ |

---

[回帰分析に戻る]({{ site.baseurl }}/semi-1/5-regression/) | [準1級トップ]({{ site.baseurl }}/semi-1/) | [トップページ]({{ site.baseurl }}/)
