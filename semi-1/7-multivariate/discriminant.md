---
layout: default
title: 判別分析 - 準1級対策
description: フィッシャーの判別分析、マハラノビス距離、SVM、ROC曲線を解説
---

# 判別分析

判別分析（Discriminant Analysis）は、既知のグループ情報に基づいて、新しいデータがどのグループに属するかを判定する手法です。

---

## 判別分析の直感的理解

判別分析は「どちらのグループに属するか」を決める境界線を見つけます。

```
判別分析のイメージ

2つの測定値から、合格/不合格を判別したい：

  試験B │
        │    ○ ○        ○ = 合格者
        │  ○ ○ ○ ╲      × = 不合格者
        │ ○ ○ ○ ○ ╲
        │    ○ ○    ╲   判別境界
        │          ╲ ╲
        │       × × ╲
        │     × × × ×
        │   × × × × ×
        └────────────────── 試験A

判別の考え方：
「群間の差を最大化し、群内のばらつきを最小化」
  する方向を見つける

  ○ ○ ○ ○      ×  ×  ×  ×
  ←───────→  ←───────────→
  群内のばらつき  群間の差

→ この方向に射影すると、最も分離できる！
```

**LDA** = **L**inear **D**iscriminant **A**nalysis（線形判別分析）
**QDA** = **Q**uadratic **D**iscriminant **A**nalysis（二次判別分析）
**SVM** = **S**upport **V**ector **M**achine（サポートベクターマシン）
**ROC** = **R**eceiver **O**perating **C**haracteristic（受信者操作特性）
**AUC** = **A**rea **U**nder the **C**urve（曲線下面積）

---

## 1. 判別分析の種類

| 手法 | 特徴 | 仮定 |
|-----|------|-----|
| 線形判別分析（LDA） | 線形の判別境界 | 各群の分散共分散が等しい |
| 二次判別分析（QDA） | 二次曲線の判別境界 | 分散共分散が群ごとに異なる |
| フィッシャーの判別分析 | 分散比を最大化 | 分布の仮定なし |

---

## 2. フィッシャーの線形判別分析

### 2.1 基本的な考え方

2群のデータに対し、**群間分散を最大化し、群内分散を最小化**する方向を見つける。

### 2.2 数学的定式化

- 群1：$n_1$ 個のサンプル、平均 $\bar{\mathbf{x}}_1$
- 群2：$n_2$ 個のサンプル、平均 $\bar{\mathbf{x}}_2$
- 全体平均：$\bar{\mathbf{x}}$

**群間変動行列**（Between-class scatter matrix）：

$$\mathbf{S}_B = n_1(\bar{\mathbf{x}}_1 - \bar{\mathbf{x}})(\bar{\mathbf{x}}_1 - \bar{\mathbf{x}})^\top + n_2(\bar{\mathbf{x}}_2 - \bar{\mathbf{x}})(\bar{\mathbf{x}}_2 - \bar{\mathbf{x}})^\top$$

2群の場合、簡略化すると：

$$\mathbf{S}_B = (\bar{\mathbf{x}}_1 - \bar{\mathbf{x}}_2)(\bar{\mathbf{x}}_1 - \bar{\mathbf{x}}_2)^\top$$

**群内変動行列**（Within-class scatter matrix）：

$$\mathbf{S}_W = \sum_{i \in \text{群1}} (\mathbf{x}_i - \bar{\mathbf{x}}_1)(\mathbf{x}_i - \bar{\mathbf{x}}_1)^\top + \sum_{i \in \text{群2}} (\mathbf{x}_i - \bar{\mathbf{x}}_2)(\mathbf{x}_i - \bar{\mathbf{x}}_2)^\top$$

### 2.3 最適化問題

判別軸 $\mathbf{w}$ を求める：

$$\max_{\mathbf{w}} J(\mathbf{w}) = \frac{\mathbf{w}^\top \mathbf{S}_B \mathbf{w}}{\mathbf{w}^\top \mathbf{S}_W \mathbf{w}}$$

### 2.4 解の導出

**Step 1: レイリー商の最大化**

目的関数はレイリー商の形をしている：

$$J(\mathbf{w}) = \frac{\mathbf{w}^\top \mathbf{S}_B \mathbf{w}}{\mathbf{w}^\top \mathbf{S}_W \mathbf{w}}$$

**Step 2: ラグランジュの未定乗数法**

$\mathbf{w}^\top \mathbf{S}_W \mathbf{w} = 1$ という制約条件のもとで $\mathbf{w}^\top \mathbf{S}_B \mathbf{w}$ を最大化：

$$L = \mathbf{w}^\top \mathbf{S}_B \mathbf{w} - \lambda(\mathbf{w}^\top \mathbf{S}_W \mathbf{w} - 1)$$

**Step 3: 微分して0とおく**

$$\frac{\partial L}{\partial \mathbf{w}} = 2\mathbf{S}_B \mathbf{w} - 2\lambda \mathbf{S}_W \mathbf{w} = 0$$

$$\mathbf{S}_B \mathbf{w} = \lambda \mathbf{S}_W \mathbf{w}$$

**Step 4: 一般化固有値問題**

$$\mathbf{S}_W^{-1} \mathbf{S}_B \mathbf{w} = \lambda \mathbf{w}$$

**Step 5: 2群の場合の簡略化**

$\mathbf{S}_B = (\bar{\mathbf{x}}_1 - \bar{\mathbf{x}}_2)(\bar{\mathbf{x}}_1 - \bar{\mathbf{x}}_2)^\top$ より：

$$\mathbf{S}_B \mathbf{w} = (\bar{\mathbf{x}}_1 - \bar{\mathbf{x}}_2) \underbrace{(\bar{\mathbf{x}}_1 - \bar{\mathbf{x}}_2)^\top \mathbf{w}}_{\text{スカラー}}$$

これは常に $(\bar{\mathbf{x}}_1 - \bar{\mathbf{x}}_2)$ の方向を向く。

したがって：

$$\mathbf{w} \propto \mathbf{S}_W^{-1}(\bar{\mathbf{x}}_1 - \bar{\mathbf{x}}_2)$$

**直感的理解**：群内の相関構造 $\mathbf{S}_W$ を考慮しながら、群平均の差の方向を見つける。

---

## 3. マハラノビス距離

### 3.1 定義

点 $\mathbf{x}$ から平均 $\boldsymbol{\mu}$ への**マハラノビス距離**：

$$D_M(\mathbf{x}) = \sqrt{(\mathbf{x} - \boldsymbol{\mu})^\top \mathbf{S}^{-1} (\mathbf{x} - \boldsymbol{\mu})}$$

### 3.2 ユークリッド距離との違い

| 距離 | 特徴 |
|-----|------|
| ユークリッド距離 | 変数間の相関を無視 |
| マハラノビス距離 | 分散・共分散を考慮、スケール不変 |

### 3.3 判別への応用

各群の平均 $\bar{\mathbf{x}}_k$ へのマハラノビス距離を計算し、最も近い群に分類：

$$\text{判別結果} = \arg\min_k D_M^{(k)}(\mathbf{x})$$

---

## 4. 線形判別関数

### 4.1 2群の場合

判別関数：

$$L(\mathbf{x}) = \mathbf{w}^\top \mathbf{x} + w_0$$

- $L(\mathbf{x}) > 0$ なら群1
- $L(\mathbf{x}) < 0$ なら群2

### 4.2 判別係数

$$\mathbf{w} = \mathbf{S}_W^{-1}(\bar{\mathbf{x}}_1 - \bar{\mathbf{x}}_2)$$

$$w_0 = -\frac{1}{2}(\bar{\mathbf{x}}_1 + \bar{\mathbf{x}}_2)^\top \mathbf{w}$$

---

## 5. 混同行列とROC曲線

### 5.1 混同行列（Confusion Matrix）

|  | 予測：陽性 | 予測：陰性 |
|--|----------|----------|
| 実際：陽性 | TP（真陽性） | FN（偽陰性） |
| 実際：陰性 | FP（偽陽性） | TN（真陰性） |

### 5.2 評価指標

| 指標 | 定義 | 意味 |
|-----|------|------|
| 正解率（Accuracy） | $(TP+TN)/(TP+TN+FP+FN)$ | 全体の正解率 |
| 感度（Sensitivity） | $TP/(TP+FN)$ | 陽性を正しく検出 |
| 特異度（Specificity） | $TN/(TN+FP)$ | 陰性を正しく検出 |
| 適合率（Precision） | $TP/(TP+FP)$ | 陽性予測の的中率 |
| F1スコア | $2 \times \frac{適合率 \times 感度}{適合率 + 感度}$ | 適合率と感度の調和平均 |

### 5.3 ROC曲線

- 横軸：偽陽性率（1 - 特異度）= $FP/(FP+TN)$
- 縦軸：真陽性率（感度）= $TP/(TP+FN)$

**AUC**（Area Under the Curve）：ROC曲線の下の面積
- AUC = 1.0：完璧な分類
- AUC = 0.5：ランダムな分類
- AUC > 0.7：一般的に良い分類

---

## 6. サポートベクターマシン（SVM）

### 6.1 基本概念

2群を分離する**マージン最大化**超平面を見つける。

### 6.2 線形SVM

決定境界：$\mathbf{w}^\top \mathbf{x} + b = 0$

最適化問題：

$$\min_{\mathbf{w}, b} \frac{1}{2}\|\mathbf{w}\|^2$$

制約条件：$y_i(\mathbf{w}^\top \mathbf{x}_i + b) \geq 1$ （全サンプルで）

### 6.3 マージン

$$\text{マージン} = \frac{2}{\|\mathbf{w}\|}$$

### 6.4 カーネルトリック

非線形の判別境界には**カーネル関数**を使用：
- 線形カーネル：$K(\mathbf{x}, \mathbf{x}') = \mathbf{x}^\top \mathbf{x}'$
- 多項式カーネル：$K(\mathbf{x}, \mathbf{x}') = (\mathbf{x}^\top \mathbf{x}' + c)^d$
- RBFカーネル：$K(\mathbf{x}, \mathbf{x}') = \exp(-\gamma\|\mathbf{x} - \mathbf{x}'\|^2)$

---

## 7. 例題

### 例題1：線形判別関数

2群のデータがあり、群1の平均 $(3, 4)$、群2の平均 $(7, 6)$、プールした分散共分散行列が単位行列のとき、判別関数を求めよ。

<details markdown="1">
<summary>解答を見る</summary>

### 解答

$\mathbf{S}_W = \mathbf{I}$（単位行列）より $\mathbf{S}_W^{-1} = \mathbf{I}$

判別係数：

$$\mathbf{w} = \mathbf{S}_W^{-1}(\bar{\mathbf{x}}_1 - \bar{\mathbf{x}}_2) = \begin{pmatrix} 3-7 \\ 4-6 \end{pmatrix} = \begin{pmatrix} -4 \\ -2 \end{pmatrix}$$

切片：

$$w_0 = -\frac{1}{2}(\bar{\mathbf{x}}_1 + \bar{\mathbf{x}}_2)^\top \mathbf{w}$$

$$= -\frac{1}{2}\begin{pmatrix} 10 \\ 10 \end{pmatrix}^\top \begin{pmatrix} -4 \\ -2 \end{pmatrix} = -\frac{1}{2}(-40 - 20) = 30$$

判別関数：

$$L(\mathbf{x}) = -4x_1 - 2x_2 + 30$$

**答え：** $L(x_1, x_2) = -4x_1 - 2x_2 + 30$

$L > 0$ なら群1、$L < 0$ なら群2

</details>

---

### 例題2：マハラノビス距離

平均 $(5, 3)$、分散共分散行列 $\mathbf{S} = \begin{pmatrix} 4 & 0 \\ 0 & 1 \end{pmatrix}$ の分布からの点 $(9, 5)$ のマハラノビス距離を求めよ。

<details markdown="1">
<summary>解答を見る</summary>

### 解答

$$\mathbf{S}^{-1} = \begin{pmatrix} 1/4 & 0 \\ 0 & 1 \end{pmatrix}$$

$$\mathbf{x} - \boldsymbol{\mu} = \begin{pmatrix} 9-5 \\ 5-3 \end{pmatrix} = \begin{pmatrix} 4 \\ 2 \end{pmatrix}$$

$$D_M^2 = \begin{pmatrix} 4 & 2 \end{pmatrix} \begin{pmatrix} 1/4 & 0 \\ 0 & 1 \end{pmatrix} \begin{pmatrix} 4 \\ 2 \end{pmatrix}$$

$$= \begin{pmatrix} 1 & 2 \end{pmatrix} \begin{pmatrix} 4 \\ 2 \end{pmatrix} = 4 + 4 = 8$$

$$D_M = \sqrt{8} = 2\sqrt{2} \approx 2.83$$

**答え：** $2\sqrt{2} \approx 2.83$

</details>

---

### 例題3：混同行列の計算

100人の検査で、TP=40, FP=10, FN=5, TN=45 のとき、感度、特異度、適合率を求めよ。

<details markdown="1">
<summary>解答を見る</summary>

### 解答

**感度（Sensitivity）**：

$$\text{感度} = \frac{TP}{TP + FN} = \frac{40}{40 + 5} = \frac{40}{45} \approx 0.889 = 88.9\%$$

**特異度（Specificity）**：

$$\text{特異度} = \frac{TN}{TN + FP} = \frac{45}{45 + 10} = \frac{45}{55} \approx 0.818 = 81.8\%$$

**適合率（Precision）**：

$$\text{適合率} = \frac{TP}{TP + FP} = \frac{40}{40 + 10} = \frac{40}{50} = 0.80 = 80\%$$

**答え：** 感度 88.9%、特異度 81.8%、適合率 80%

</details>

---

## 8. 重要公式まとめ

| 項目 | 公式 |
|-----|------|
| 判別係数 | $\mathbf{w} = \mathbf{S}_W^{-1}(\bar{\mathbf{x}}_1 - \bar{\mathbf{x}}_2)$ |
| マハラノビス距離 | $D_M = \sqrt{(\mathbf{x}-\boldsymbol{\mu})^\top \mathbf{S}^{-1} (\mathbf{x}-\boldsymbol{\mu})}$ |
| 感度 | $TP/(TP+FN)$ |
| 特異度 | $TN/(TN+FP)$ |
| 適合率 | $TP/(TP+FP)$ |
| SVMマージン | $2/\|\mathbf{w}\|$ |

---

[多変量解析に戻る]({{ site.baseurl }}/semi-1/7-multivariate/) | [準1級トップ]({{ site.baseurl }}/semi-1/) | [トップページ]({{ site.baseurl }}/)
