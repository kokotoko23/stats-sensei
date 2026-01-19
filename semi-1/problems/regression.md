---
layout: default
title: 回帰分析の問題 - 準1級対策
description: 重回帰、正則化、GLM、生存時間分析の選択式問題
permalink: /semi-1/problems/regression/
---

# 回帰分析の問題

重回帰分析、正則化、一般化線形モデル、生存時間分析に関する問題です。

<div class="quiz-progress">
  <span class="quiz-progress-text">0 / 10 正解</span>
  <div class="quiz-progress-bar">
    <div class="quiz-progress-fill" style="width: 0%"></div>
  </div>
</div>

---

## 問題 1：最小二乗推定量

<div class="quiz-container" data-quiz-id="reg-1" data-correct="b" data-difficulty="easy">
  <div class="quiz-question">
    重回帰モデル $\mathbf{y} = \mathbf{X}\boldsymbol{\beta} + \boldsymbol{\varepsilon}$ において、最小二乗推定量 $\hat{\boldsymbol{\beta}}$ の表現として正しいものはどれか。
  </div>
  <div class="quiz-options">
    <div class="quiz-option" data-value="a">
      <input type="radio" name="q1" id="q1a">
      <label for="q1a">$\hat{\boldsymbol{\beta}} = \mathbf{X}^\top \mathbf{y}$</label>
    </div>
    <div class="quiz-option" data-value="b">
      <input type="radio" name="q1" id="q1b">
      <label for="q1b">$\hat{\boldsymbol{\beta}} = (\mathbf{X}^\top \mathbf{X})^{-1} \mathbf{X}^\top \mathbf{y}$</label>
    </div>
    <div class="quiz-option" data-value="c">
      <input type="radio" name="q1" id="q1c">
      <label for="q1c">$\hat{\boldsymbol{\beta}} = \mathbf{X} (\mathbf{X}^\top \mathbf{X})^{-1} \mathbf{y}$</label>
    </div>
    <div class="quiz-option" data-value="d">
      <input type="radio" name="q1" id="q1d">
      <label for="q1d">$\hat{\boldsymbol{\beta}} = (\mathbf{X} \mathbf{X}^\top)^{-1} \mathbf{X} \mathbf{y}$</label>
    </div>
  </div>
  <button class="quiz-btn" disabled>解答を確認</button>
  <div class="quiz-feedback">
    <span class="quiz-feedback-icon"></span>
    <strong>正解：(b)</strong>
    <div class="quiz-explanation">
      残差二乗和 $S(\boldsymbol{\beta}) = (\mathbf{y} - \mathbf{X}\boldsymbol{\beta})^\top(\mathbf{y} - \mathbf{X}\boldsymbol{\beta})$ を最小化。

      $\frac{\partial S}{\partial \boldsymbol{\beta}} = -2\mathbf{X}^\top(\mathbf{y} - \mathbf{X}\boldsymbol{\beta}) = 0$

      正規方程式：$\mathbf{X}^\top \mathbf{X} \boldsymbol{\beta} = \mathbf{X}^\top \mathbf{y}$

      $\hat{\boldsymbol{\beta}} = (\mathbf{X}^\top \mathbf{X})^{-1} \mathbf{X}^\top \mathbf{y}$
    </div>
  </div>
</div>

---

## 問題 2：決定係数

<div class="quiz-container" data-quiz-id="reg-2" data-correct="d" data-difficulty="medium">
  <div class="quiz-question">
    決定係数 $R^2$ について<strong>正しいもの</strong>はどれか。
  </div>
  <div class="quiz-options">
    <div class="quiz-option" data-value="a">
      <input type="radio" name="q2" id="q2a">
      <label for="q2a">説明変数を追加すると $R^2$ は必ず減少する</label>
    </div>
    <div class="quiz-option" data-value="b">
      <input type="radio" name="q2" id="q2b">
      <label for="q2b">$R^2 = 1$ ならモデルは正しい</label>
    </div>
    <div class="quiz-option" data-value="c">
      <input type="radio" name="q2" id="q2c">
      <label for="q2c">$R^2$ は負の値を取りうる</label>
    </div>
    <div class="quiz-option" data-value="d">
      <input type="radio" name="q2" id="q2d">
      <label for="q2d">調整済み $R^2$ は説明変数の追加で減少することがある</label>
    </div>
  </div>
  <button class="quiz-btn" disabled>解答を確認</button>
  <div class="quiz-feedback">
    <span class="quiz-feedback-icon"></span>
    <strong>正解：(d)</strong>
    <div class="quiz-explanation">
      (a) 誤り：説明変数を追加すると $R^2$ は必ず増加（または同じ）。

      (b) 誤り：$R^2 = 1$ は完全な当てはめを意味するが、過学習の可能性もある。

      (c) 誤り：$R^2 = 1 - \frac{SS_{res}}{SS_{tot}}$ で、切片ありモデルでは $0 \leq R^2 \leq 1$。

      (d) 正しい：調整済み $R^2 = 1 - \frac{n-1}{n-p-1}(1-R^2)$ は、無駄な変数を追加すると減少する。
    </div>
  </div>
</div>

---

## 問題 3：リッジ回帰

<div class="quiz-container" data-quiz-id="reg-3" data-correct="c" data-difficulty="medium">
  <div class="quiz-question">
    リッジ回帰の推定量はどれか。ただし $\lambda > 0$ は正則化パラメータ、$\mathbf{I}$ は単位行列。
  </div>
  <div class="quiz-options">
    <div class="quiz-option" data-value="a">
      <input type="radio" name="q3" id="q3a">
      <label for="q3a">$\hat{\boldsymbol{\beta}}_{\text{ridge}} = (\mathbf{X}^\top \mathbf{X})^{-1} \mathbf{X}^\top \mathbf{y} + \lambda \mathbf{I}$</label>
    </div>
    <div class="quiz-option" data-value="b">
      <input type="radio" name="q3" id="q3b">
      <label for="q3b">$\hat{\boldsymbol{\beta}}_{\text{ridge}} = (\mathbf{X}^\top \mathbf{X} - \lambda \mathbf{I})^{-1} \mathbf{X}^\top \mathbf{y}$</label>
    </div>
    <div class="quiz-option" data-value="c">
      <input type="radio" name="q3" id="q3c">
      <label for="q3c">$\hat{\boldsymbol{\beta}}_{\text{ridge}} = (\mathbf{X}^\top \mathbf{X} + \lambda \mathbf{I})^{-1} \mathbf{X}^\top \mathbf{y}$</label>
    </div>
    <div class="quiz-option" data-value="d">
      <input type="radio" name="q3" id="q3d">
      <label for="q3d">$\hat{\boldsymbol{\beta}}_{\text{ridge}} = \mathbf{X}^\top (\mathbf{X} \mathbf{X}^\top + \lambda \mathbf{I})^{-1} \mathbf{y}$</label>
    </div>
  </div>
  <button class="quiz-btn" disabled>解答を確認</button>
  <div class="quiz-feedback">
    <span class="quiz-feedback-icon"></span>
    <strong>正解：(c)</strong>
    <div class="quiz-explanation">
      リッジ回帰は $\|\mathbf{y} - \mathbf{X}\boldsymbol{\beta}\|^2 + \lambda\|\boldsymbol{\beta}\|^2$ を最小化。

      $L_2$ 正則化により、$\mathbf{X}^\top \mathbf{X}$ に $\lambda \mathbf{I}$ を加えます。

      これにより：
      - 多重共線性があっても逆行列が存在
      - 推定量の分散が減少（バイアスとのトレードオフ）
      - 係数を0に近づける（が0にはならない）

      (d) はカーネルリッジ回帰の別表現で、同値ですが標準形ではありません。
    </div>
  </div>
</div>

---

## 問題 4：ロジスティック回帰

<div class="quiz-container" data-quiz-id="reg-4" data-correct="a" data-difficulty="easy">
  <div class="quiz-question">
    ロジスティック回帰で、係数 $\beta_j$ の解釈として正しいものはどれか。
  </div>
  <div class="quiz-options">
    <div class="quiz-option" data-value="a">
      <input type="radio" name="q4" id="q4a">
      <label for="q4a">$x_j$ が1単位増加すると、オッズが $e^{\beta_j}$ 倍になる</label>
    </div>
    <div class="quiz-option" data-value="b">
      <input type="radio" name="q4" id="q4b">
      <label for="q4b">$x_j$ が1単位増加すると、確率が $\beta_j$ だけ増加する</label>
    </div>
    <div class="quiz-option" data-value="c">
      <input type="radio" name="q4" id="q4c">
      <label for="q4c">$x_j$ が1単位増加すると、対数確率が $\beta_j$ だけ増加する</label>
    </div>
    <div class="quiz-option" data-value="d">
      <input type="radio" name="q4" id="q4d">
      <label for="q4d">$x_j$ が1単位増加すると、確率が $e^{\beta_j}$ 倍になる</label>
    </div>
  </div>
  <button class="quiz-btn" disabled>解答を確認</button>
  <div class="quiz-feedback">
    <span class="quiz-feedback-icon"></span>
    <strong>正解：(a)</strong>
    <div class="quiz-explanation">
      ロジスティック回帰：$\log\frac{p}{1-p} = \beta_0 + \beta_1 x_1 + \cdots$

      $x_j$ が1増加すると対数オッズが $\beta_j$ 増加。

      つまりオッズ $\frac{p}{1-p}$ は $e^{\beta_j}$ 倍になります。

      (b) 誤り：確率への効果は非線形。

      (c) 誤り：対数オッズであり、対数確率ではない。

      (d) 誤り：確率ではなくオッズが $e^{\beta_j}$ 倍。
    </div>
  </div>
</div>

---

## 問題 5：Cox比例ハザードモデル

<div class="quiz-container" data-quiz-id="reg-5" data-correct="b" data-difficulty="medium">
  <div class="quiz-question">
    Cox比例ハザードモデルにおいて、ハザード関数 $h(t \mid \mathbf{x})$ の表現として正しいものはどれか。
  </div>
  <div class="quiz-options">
    <div class="quiz-option" data-value="a">
      <input type="radio" name="q5" id="q5a">
      <label for="q5a">$h(t \mid \mathbf{x}) = h_0(t) + \boldsymbol{\beta}^\top \mathbf{x}$</label>
    </div>
    <div class="quiz-option" data-value="b">
      <input type="radio" name="q5" id="q5b">
      <label for="q5b">$h(t \mid \mathbf{x}) = h_0(t) \exp(\boldsymbol{\beta}^\top \mathbf{x})$</label>
    </div>
    <div class="quiz-option" data-value="c">
      <input type="radio" name="q5" id="q5c">
      <label for="q5c">$h(t \mid \mathbf{x}) = \exp(h_0(t) + \boldsymbol{\beta}^\top \mathbf{x})$</label>
    </div>
    <div class="quiz-option" data-value="d">
      <input type="radio" name="q5" id="q5d">
      <label for="q5d">$h(t \mid \mathbf{x}) = h_0(t) \cdot \boldsymbol{\beta}^\top \mathbf{x}$</label>
    </div>
  </div>
  <button class="quiz-btn" disabled>解答を確認</button>
  <div class="quiz-feedback">
    <span class="quiz-feedback-icon"></span>
    <strong>正解：(b)</strong>
    <div class="quiz-explanation">
      Cox比例ハザードモデル：

      $h(t \mid \mathbf{x}) = h_0(t) \exp(\boldsymbol{\beta}^\top \mathbf{x})$

      - $h_0(t)$：ベースラインハザード（共変量が0のときのハザード）
      - $\exp(\boldsymbol{\beta}^\top \mathbf{x})$：共変量によるハザード比

      「比例ハザード」：任意の2群のハザード比が時間によらず一定。

      半パラメトリックモデル：$h_0(t)$ を仮定せずに $\boldsymbol{\beta}$ を推定可能（部分尤度法）。
    </div>
  </div>
</div>

---

## 問題 6：多重共線性

<div class="quiz-container" data-quiz-id="reg-6" data-correct="c" data-difficulty="hard">
  <div class="quiz-question">
    多重共線性（multicollinearity）の問題として<strong>正しくないもの</strong>はどれか。
  </div>
  <div class="quiz-options">
    <div class="quiz-option" data-value="a">
      <input type="radio" name="q6" id="q6a">
      <label for="q6a">係数の推定値が不安定になる</label>
    </div>
    <div class="quiz-option" data-value="b">
      <input type="radio" name="q6" id="q6b">
      <label for="q6b">係数の標準誤差が大きくなる</label>
    </div>
    <div class="quiz-option" data-value="c">
      <input type="radio" name="q6" id="q6c">
      <label for="q6c">予測精度が必ず低下する</label>
    </div>
    <div class="quiz-option" data-value="d">
      <input type="radio" name="q6" id="q6d">
      <label for="q6d">VIF（分散拡大係数）が大きくなる</label>
    </div>
  </div>
  <button class="quiz-btn" disabled>解答を確認</button>
  <div class="quiz-feedback">
    <span class="quiz-feedback-icon"></span>
    <strong>正解：(c)</strong>
    <div class="quiz-explanation">
      多重共線性の影響：
      - 係数の推定が不安定（符号が逆転することも）
      - 標準誤差が大きくなる → 有意にならない
      - VIF $= 1/(1-R_j^2)$ が大きくなる（目安：VIF > 10 で問題）

      しかし、**予測精度は必ずしも低下しない**。共線性があっても $\mathbf{X}\boldsymbol{\beta}$ 全体としての予測は安定。

      対処法：変数選択、主成分回帰、正則化（リッジ回帰）
    </div>
  </div>
</div>

---

## 問題 7：残差診断

<div class="quiz-container" data-quiz-id="reg-7" data-correct="a" data-difficulty="medium">
  <div class="quiz-question">
    回帰分析の残差プロットで「等分散性の仮定」が満たされているとき、残差と予測値の散布図はどのようなパターンを示すか。
  </div>
  <div class="quiz-options">
    <div class="quiz-option" data-value="a">
      <input type="radio" name="q7" id="q7a">
      <label for="q7a">水平な帯状（ランダムに散らばる）</label>
    </div>
    <div class="quiz-option" data-value="b">
      <input type="radio" name="q7" id="q7b">
      <label for="q7b">漏斗形（予測値が大きいほど散らばりが大きい）</label>
    </div>
    <div class="quiz-option" data-value="c">
      <input type="radio" name="q7" id="q7c">
      <label for="q7c">曲線的なパターン</label>
    </div>
    <div class="quiz-option" data-value="d">
      <input type="radio" name="q7" id="q7d">
      <label for="q7d">右上がりの直線</label>
    </div>
  </div>
  <button class="quiz-btn" disabled>解答を確認</button>
  <div class="quiz-feedback">
    <span class="quiz-feedback-icon"></span>
    <strong>正解：(a)</strong>
    <div class="quiz-explanation">
      残差診断のパターン：

      | パターン | 意味 |
      |---------|------|
      | 水平な帯状 | 仮定が満たされている |
      | 漏斗形 | 不等分散（heteroscedasticity） |
      | 曲線的 | 非線形性（変数変換が必要） |
      | 直線的 | 誤差と説明変数が相関（内生性） |

      対処：加重最小二乗法、ロバスト標準誤差、変数変換
    </div>
  </div>
</div>

---

## 問題 8：LASSO

<div class="quiz-container" data-quiz-id="reg-8" data-correct="d" data-difficulty="hard">
  <div class="quiz-question">
    LASSO回帰の罰則項として正しいものはどれか。
  </div>
  <div class="quiz-options">
    <div class="quiz-option" data-value="a">
      <input type="radio" name="q8" id="q8a">
      <label for="q8a">$\lambda \sum \beta_j^2$（L2ノルム）</label>
    </div>
    <div class="quiz-option" data-value="b">
      <input type="radio" name="q8" id="q8b">
      <label for="q8b">$\lambda \sum \beta_j^2 + \mu \sum |\beta_j|$</label>
    </div>
    <div class="quiz-option" data-value="c">
      <input type="radio" name="q8" id="q8c">
      <label for="q8c">$\lambda \log \sum |\beta_j|$</label>
    </div>
    <div class="quiz-option" data-value="d">
      <input type="radio" name="q8" id="q8d">
      <label for="q8d">$\lambda \sum |\beta_j|$（L1ノルム）</label>
    </div>
  </div>
  <button class="quiz-btn" disabled>解答を確認</button>
  <div class="quiz-feedback">
    <span class="quiz-feedback-icon"></span>
    <strong>正解：(d)</strong>
    <div class="quiz-explanation">
      正則化回帰の比較：

      | 方法 | 罰則項 | 特徴 |
      |-----|--------|------|
      | リッジ | $\lambda \sum \beta_j^2$ | 係数を縮小、0にはならない |
      | LASSO | $\lambda \sum \|\beta_j\|$ | 変数選択（一部が0になる） |
      | Elastic Net | 両方の線形結合 | 両者の利点を組み合わせ |

      LASSOはスパース推定により、解釈しやすいモデルを得られる。
    </div>
  </div>
</div>

---

## 問題 9：ポアソン回帰

<div class="quiz-container" data-quiz-id="reg-9" data-correct="b" data-difficulty="hard">
  <div class="quiz-question">
    ポアソン回帰でリンク関数として通常使用されるものはどれか。
  </div>
  <div class="quiz-options">
    <div class="quiz-option" data-value="a">
      <input type="radio" name="q9" id="q9a">
      <label for="q9a">恒等リンク $g(\mu) = \mu$</label>
    </div>
    <div class="quiz-option" data-value="b">
      <input type="radio" name="q9" id="q9b">
      <label for="q9b">対数リンク $g(\mu) = \log \mu$</label>
    </div>
    <div class="quiz-option" data-value="c">
      <input type="radio" name="q9" id="q9c">
      <label for="q9c">ロジットリンク $g(\mu) = \log \frac{\mu}{1-\mu}$</label>
    </div>
    <div class="quiz-option" data-value="d">
      <input type="radio" name="q9" id="q9d">
      <label for="q9d">プロビットリンク $g(\mu) = \Phi^{-1}(\mu)$</label>
    </div>
  </div>
  <button class="quiz-btn" disabled>解答を確認</button>
  <div class="quiz-feedback">
    <span class="quiz-feedback-icon"></span>
    <strong>正解：(b)</strong>
    <div class="quiz-explanation">
      GLMの構成要素と典型的なリンク関数：

      | 分布 | 典型的なリンク | 用途 |
      |-----|---------------|------|
      | 正規 | 恒等 | 連続データ |
      | ポアソン | 対数 | カウントデータ |
      | 二項 | ロジット/プロビット | 二値データ |
      | ガンマ | 逆数/対数 | 正の連続データ |

      ポアソン回帰：$\log E[Y] = \mathbf{x}^\top \boldsymbol{\beta}$、つまり $E[Y] = e^{\mathbf{x}^\top \boldsymbol{\beta}}$
    </div>
  </div>
</div>

---

## 問題 10：カプラン・マイヤー推定量

<div class="quiz-container" data-quiz-id="reg-10" data-correct="a" data-difficulty="hard">
  <div class="quiz-question">
    生存時間分析のカプラン・マイヤー推定量について正しいものはどれか。
  </div>
  <div class="quiz-options">
    <div class="quiz-option" data-value="a">
      <input type="radio" name="q10" id="q10a">
      <label for="q10a">打ち切りデータを適切に扱える生存関数の推定量</label>
    </div>
    <div class="quiz-option" data-value="b">
      <input type="radio" name="q10" id="q10b">
      <label for="q10b">パラメトリックな仮定（例：指数分布）が必要</label>
    </div>
    <div class="quiz-option" data-value="c">
      <input type="radio" name="q10" id="q10c">
      <label for="q10c">共変量の効果を直接推定できる</label>
    </div>
    <div class="quiz-option" data-value="d">
      <input type="radio" name="q10" id="q10d">
      <label for="q10d">連続的な生存曲線を出力する</label>
    </div>
  </div>
  <button class="quiz-btn" disabled>解答を確認</button>
  <div class="quiz-feedback">
    <span class="quiz-feedback-icon"></span>
    <strong>正解：(a)</strong>
    <div class="quiz-explanation">
      カプラン・マイヤー推定量：

      $$\hat{S}(t) = \prod_{t_i \leq t} \left(1 - \frac{d_i}{n_i}\right)$$

      - $d_i$：時点 $t_i$ でのイベント数
      - $n_i$：時点 $t_i$ 直前のリスク集合のサイズ

      特徴：
      - ノンパラメトリック（分布の仮定不要）
      - 打ち切りを適切に処理
      - 階段関数として推定
      - 共変量の効果を見るにはCox回帰等が必要
    </div>
  </div>
</div>

---

## 関連コンテンツ

- [理論編：重回帰分析と正則化]({{ site.baseurl }}/semi-1/5-regression/regularization/)
- [理論編：一般化線形モデル]({{ site.baseurl }}/semi-1/5-regression/glm/)
- [理論編：生存時間分析]({{ site.baseurl }}/semi-1/5-regression/survival/)
- [多変量解析の問題]({{ site.baseurl }}/semi-1/problems/multivariate/)

---

[問題一覧に戻る]({{ site.baseurl }}/semi-1/problems/) | [準1級トップ]({{ site.baseurl }}/semi-1/)
