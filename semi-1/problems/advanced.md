---
layout: default
title: 発展的手法の問題 - 準1級対策
description: 時系列解析、ベイズ統計、モデル選択、シミュレーションの選択式問題
permalink: /semi-1/problems/advanced/
---

# 発展的手法の問題

時系列解析、ベイズ統計、モデル選択、シミュレーションに関する問題です。

<div class="quiz-progress">
  <span class="quiz-progress-text">0 / 5 正解</span>
  <div class="quiz-progress-bar">
    <div class="quiz-progress-fill" style="width: 0%"></div>
  </div>
</div>

---

## 問題 1：ARモデル

<div class="quiz-container" data-quiz-id="adv-1" data-correct="c">
  <div class="quiz-question">
    AR(1)モデル $X_t = \phi X_{t-1} + \varepsilon_t$（$\varepsilon_t \sim \text{WN}(0, \sigma^2)$）が定常であるための条件はどれか。
  </div>
  <div class="quiz-options">
    <div class="quiz-option" data-value="a">
      <input type="radio" name="q1" id="q1a">
      <label for="q1a">$\phi > 0$</label>
    </div>
    <div class="quiz-option" data-value="b">
      <input type="radio" name="q1" id="q1b">
      <label for="q1b">$\phi < 0$</label>
    </div>
    <div class="quiz-option" data-value="c">
      <input type="radio" name="q1" id="q1c">
      <label for="q1c">$|\phi| < 1$</label>
    </div>
    <div class="quiz-option" data-value="d">
      <input type="radio" name="q1" id="q1d">
      <label for="q1d">$|\phi| > 1$</label>
    </div>
  </div>
  <button class="quiz-btn" disabled>解答を確認</button>
  <div class="quiz-feedback">
    <span class="quiz-feedback-icon"></span>
    <strong>正解：(c)</strong>
    <div class="quiz-explanation">
      AR(1)モデルの特性方程式は $1 - \phi z = 0$、根は $z = 1/\phi$。

      定常性の条件：**特性方程式の根が単位円の外側にある**

      $|1/\phi| > 1 \Leftrightarrow |\phi| < 1$

      このとき：
      - $E[X_t] = 0$（平均が一定）
      - $\text{Var}(X_t) = \frac{\sigma^2}{1-\phi^2}$（分散が有限で一定）
      - $\text{Cov}(X_t, X_{t-h}) = \phi^h \cdot \text{Var}(X_t)$（自己共分散が時点に依存しない）
    </div>
  </div>
</div>

---

## 問題 2：MA過程の性質

<div class="quiz-container" data-quiz-id="adv-2" data-correct="a">
  <div class="quiz-question">
    MA(1)モデル $X_t = \varepsilon_t + \theta \varepsilon_{t-1}$ の自己相関関数について正しいものはどれか。
  </div>
  <div class="quiz-options">
    <div class="quiz-option" data-value="a">
      <input type="radio" name="q2" id="q2a">
      <label for="q2a">$\rho_1 \neq 0$、$\rho_h = 0$（$h \geq 2$）</label>
    </div>
    <div class="quiz-option" data-value="b">
      <input type="radio" name="q2" id="q2b">
      <label for="q2b">自己相関は指数的に減衰する</label>
    </div>
    <div class="quiz-option" data-value="c">
      <input type="radio" name="q2" id="q2c">
      <label for="q2c">すべてのラグで $\rho_h = 0$</label>
    </div>
    <div class="quiz-option" data-value="d">
      <input type="radio" name="q2" id="q2d">
      <label for="q2d">$\rho_h = \theta^h$ で減衰する</label>
    </div>
  </div>
  <button class="quiz-btn" disabled>解答を確認</button>
  <div class="quiz-feedback">
    <span class="quiz-feedback-icon"></span>
    <strong>正解：(a)</strong>
    <div class="quiz-explanation">
      MA(q)モデルの自己相関関数は**ラグ $q$ で切断**されます。

      MA(1)の場合：
      - $\gamma_0 = (1 + \theta^2)\sigma^2$
      - $\gamma_1 = \theta \sigma^2$
      - $\gamma_h = 0$（$h \geq 2$）

      $\rho_1 = \frac{\theta}{1+\theta^2}$、$\rho_h = 0$（$h \geq 2$）

      | モデル | 自己相関 (ACF) | 偏自己相関 (PACF) |
      |-------|--------------|-----------------|
      | AR(p) | 減衰（指数・振動） | ラグpで切断 |
      | MA(q) | ラグqで切断 | 減衰 |
    </div>
  </div>
</div>

---

## 問題 3：ベイズ推定

<div class="quiz-container" data-quiz-id="adv-3" data-correct="b">
  <div class="quiz-question">
    ベイズ推定において、事後分布が事前分布と同じ分布族に属するとき、その事前分布を何と呼ぶか。
  </div>
  <div class="quiz-options">
    <div class="quiz-option" data-value="a">
      <input type="radio" name="q3" id="q3a">
      <label for="q3a">無情報事前分布</label>
    </div>
    <div class="quiz-option" data-value="b">
      <input type="radio" name="q3" id="q3b">
      <label for="q3b">共役事前分布</label>
    </div>
    <div class="quiz-option" data-value="c">
      <input type="radio" name="q3" id="q3c">
      <label for="q3c">ジェフリーズ事前分布</label>
    </div>
    <div class="quiz-option" data-value="d">
      <input type="radio" name="q3" id="q3d">
      <label for="q3d">経験ベイズ事前分布</label>
    </div>
  </div>
  <button class="quiz-btn" disabled>解答を確認</button>
  <div class="quiz-feedback">
    <span class="quiz-feedback-icon"></span>
    <strong>正解：(b)</strong>
    <div class="quiz-explanation">
      **共役事前分布**を使うと、事後分布が解析的に求まります。

      代表例：
      | 尤度 | 共役事前分布 | 事後分布 |
      |-----|------------|---------|
      | 二項分布 | ベータ分布 | ベータ分布 |
      | ポアソン分布 | ガンマ分布 | ガンマ分布 |
      | 正規分布（平均） | 正規分布 | 正規分布 |
      | 正規分布（精度） | ガンマ分布 | ガンマ分布 |

      事後分布のパラメータは、事前分布のパラメータとデータの統計量を組み合わせて更新されます。
    </div>
  </div>
</div>

---

## 問題 4：モデル選択

<div class="quiz-container" data-quiz-id="adv-4" data-correct="d">
  <div class="quiz-question">
    AIC（赤池情報量規準）とBIC（ベイズ情報量規準）の比較について正しいものはどれか。
  </div>
  <div class="quiz-options">
    <div class="quiz-option" data-value="a">
      <input type="radio" name="q4" id="q4a">
      <label for="q4a">AICはBICより常に大きな罰則項を持つ</label>
    </div>
    <div class="quiz-option" data-value="b">
      <input type="radio" name="q4" id="q4b">
      <label for="q4b">BICはモデルの予測性能を重視する</label>
    </div>
    <div class="quiz-option" data-value="c">
      <input type="radio" name="q4" id="q4c">
      <label for="q4c">サンプルサイズが大きいとき、AICはBICよりシンプルなモデルを選ぶ</label>
    </div>
    <div class="quiz-option" data-value="d">
      <input type="radio" name="q4" id="q4d">
      <label for="q4d">サンプルサイズが大きいとき、BICはAICよりシンプルなモデルを選ぶ</label>
    </div>
  </div>
  <button class="quiz-btn" disabled>解答を確認</button>
  <div class="quiz-feedback">
    <span class="quiz-feedback-icon"></span>
    <strong>正解：(d)</strong>
    <div class="quiz-explanation">
      罰則項の比較（$k$：パラメータ数、$n$：サンプルサイズ）：

      - $\text{AIC} = -2\ell + 2k$
      - $\text{BIC} = -2\ell + k \log n$

      $n \geq 8$ のとき $\log n > 2$ なので、BICの罰則項が大きくなります。

      | 特徴 | AIC | BIC |
      |-----|-----|-----|
      | 罰則項 | $2k$ | $k \log n$ |
      | 重視 | 予測性能 | 真のモデルの選択 |
      | 一致性 | なし | あり（$n \to \infty$ で真のモデルを選ぶ） |

      BICは大標本でより**シンプルなモデル**を選ぶ傾向があります。
    </div>
  </div>
</div>

---

## 問題 5：ブートストラップ法

<div class="quiz-container" data-quiz-id="adv-5" data-correct="c">
  <div class="quiz-question">
    ブートストラップ法について正しいものはどれか。
  </div>
  <div class="quiz-options">
    <div class="quiz-option" data-value="a">
      <input type="radio" name="q5" id="q5a">
      <label for="q5a">母集団分布を正規分布と仮定する</label>
    </div>
    <div class="quiz-option" data-value="b">
      <input type="radio" name="q5" id="q5b">
      <label for="q5b">復元抽出ではなく非復元抽出を行う</label>
    </div>
    <div class="quiz-option" data-value="c">
      <input type="radio" name="q5" id="q5c">
      <label for="q5c">元のサンプルから復元抽出を繰り返して統計量の分布を推定する</label>
    </div>
    <div class="quiz-option" data-value="d">
      <input type="radio" name="q5" id="q5d">
      <label for="q5d">ブートストラップ標本のサイズは元のサンプルサイズより大きくする</label>
    </div>
  </div>
  <button class="quiz-btn" disabled>解答を確認</button>
  <div class="quiz-feedback">
    <span class="quiz-feedback-icon"></span>
    <strong>正解：(c)</strong>
    <div class="quiz-explanation">
      ブートストラップ法の手順：

      1. 元のサンプル（サイズ $n$）から**復元抽出**でサイズ $n$ のブートストラップ標本を生成
      2. ブートストラップ標本から統計量 $\hat{\theta}^*$ を計算
      3. 1-2を $B$ 回（例：1000回）繰り返す
      4. $\hat{\theta}^*$ の分布から標準誤差や信頼区間を推定

      特徴：
      - 分布を仮定しないノンパラメトリック法
      - 複雑な統計量でも適用可能
      - 小標本では精度に限界あり

      信頼区間の構成法：パーセンタイル法、BCa法など
    </div>
  </div>
</div>

---

## 関連コンテンツ

- [理論編：時系列解析]({{ site.baseurl }}/semi-1/8-advanced/timeseries/)
- [理論編：ベイズ法とMCMC]({{ site.baseurl }}/semi-1/8-advanced/bayesian/)
- [理論編：モデル選択]({{ site.baseurl }}/semi-1/8-advanced/model-selection/)
- [理論編：シミュレーション]({{ site.baseurl }}/semi-1/8-advanced/simulation/)
- [多変量解析の問題]({{ site.baseurl }}/semi-1/problems/multivariate/)

---

[問題一覧に戻る]({{ site.baseurl }}/semi-1/problems/) | [準1級トップ]({{ site.baseurl }}/semi-1/)
