---
layout: default
title: 多変量解析の問題 - 準1級対策
description: 主成分分析、判別分析、クラスター分析、因子分析の選択式問題
permalink: /semi-1/problems/multivariate/
---

# 多変量解析の問題

主成分分析、判別分析、クラスター分析、因子分析に関する問題です。

<div class="quiz-progress">
  <span class="quiz-progress-text">0 / 5 正解</span>
  <div class="quiz-progress-bar">
    <div class="quiz-progress-fill" style="width: 0%"></div>
  </div>
</div>

---

## 問題 1：主成分分析

<div class="quiz-container" data-quiz-id="mv-1" data-correct="b">
  <div class="quiz-question">
    主成分分析において、第1主成分の係数ベクトル $\mathbf{a}_1$ はどのように求められるか。ただし $\mathbf{S}$ は共分散行列。
  </div>
  <div class="quiz-options">
    <div class="quiz-option" data-value="a">
      <input type="radio" name="q1" id="q1a">
      <label for="q1a">$\mathbf{S}$ の最小固有値に対応する固有ベクトル</label>
    </div>
    <div class="quiz-option" data-value="b">
      <input type="radio" name="q1" id="q1b">
      <label for="q1b">$\mathbf{S}$ の最大固有値に対応する固有ベクトル</label>
    </div>
    <div class="quiz-option" data-value="c">
      <input type="radio" name="q1" id="q1c">
      <label for="q1c">$\mathbf{S}^{-1}$ の最大固有値に対応する固有ベクトル</label>
    </div>
    <div class="quiz-option" data-value="d">
      <input type="radio" name="q1" id="q1d">
      <label for="q1d">$\mathbf{S}$ の対角成分を並べたベクトル</label>
    </div>
  </div>
  <button class="quiz-btn" disabled>解答を確認</button>
  <div class="quiz-feedback">
    <span class="quiz-feedback-icon"></span>
    <strong>正解：(b)</strong>
    <div class="quiz-explanation">
      第 $k$ 主成分は、$\|\mathbf{a}\| = 1$ の制約下で分散 $\mathbf{a}^\top \mathbf{S} \mathbf{a}$ を最大化します。

      ラグランジュ乗数法より：

      $\mathbf{S}\mathbf{a} = \lambda \mathbf{a}$

      これは固有値問題。分散は $\mathbf{a}^\top \mathbf{S} \mathbf{a} = \lambda$ なので、第1主成分は**最大固有値**に対応する固有ベクトルです。

      累積寄与率 $= \frac{\lambda_1 + \cdots + \lambda_k}{\lambda_1 + \cdots + \lambda_p}$ で次元削減の程度を評価します。
    </div>
  </div>
</div>

---

## 問題 2：主成分の性質

<div class="quiz-container" data-quiz-id="mv-2" data-correct="c">
  <div class="quiz-question">
    主成分分析について<strong>正しくないもの</strong>はどれか。
  </div>
  <div class="quiz-options">
    <div class="quiz-option" data-value="a">
      <input type="radio" name="q2" id="q2a">
      <label for="q2a">異なる主成分どうしは無相関である</label>
    </div>
    <div class="quiz-option" data-value="b">
      <input type="radio" name="q2" id="q2b">
      <label for="q2b">主成分の総分散は元の変数の総分散に等しい</label>
    </div>
    <div class="quiz-option" data-value="c">
      <input type="radio" name="q2" id="q2c">
      <label for="q2c">変数のスケールを変えても主成分は変わらない</label>
    </div>
    <div class="quiz-option" data-value="d">
      <input type="radio" name="q2" id="q2d">
      <label for="q2d">相関行列から求めた主成分は標準化されたデータに対応する</label>
    </div>
  </div>
  <button class="quiz-btn" disabled>解答を確認</button>
  <div class="quiz-feedback">
    <span class="quiz-feedback-icon"></span>
    <strong>正解：(c)</strong>
    <div class="quiz-explanation">
      主成分分析はスケールに依存します。

      - 共分散行列を使う場合：変数のスケール（単位）の影響を受ける
      - 相関行列を使う場合：標準化により単位の影響を除去

      例えば、身長をcmからmmに変えると、共分散行列ベースの主成分は大きく変わります。

      そのため、変数の単位が異なる場合は**相関行列ベース**の主成分分析が推奨されます。
    </div>
  </div>
</div>

---

## 問題 3：線形判別分析

<div class="quiz-container" data-quiz-id="mv-3" data-correct="a">
  <div class="quiz-question">
    2群の線形判別分析において、フィッシャーの判別関数が最大化するものはどれか。
  </div>
  <div class="quiz-options">
    <div class="quiz-option" data-value="a">
      <input type="radio" name="q3" id="q3a">
      <label for="q3a">$\displaystyle \frac{\text{群間変動}}{\text{群内変動}}$</label>
    </div>
    <div class="quiz-option" data-value="b">
      <input type="radio" name="q3" id="q3b">
      <label for="q3b">$\displaystyle \frac{\text{群内変動}}{\text{群間変動}}$</label>
    </div>
    <div class="quiz-option" data-value="c">
      <input type="radio" name="q3" id="q3c">
      <label for="q3c">群間変動 $+$ 群内変動</label>
    </div>
    <div class="quiz-option" data-value="d">
      <input type="radio" name="q3" id="q3d">
      <label for="q3d">尤度関数</label>
    </div>
  </div>
  <button class="quiz-btn" disabled>解答を確認</button>
  <div class="quiz-feedback">
    <span class="quiz-feedback-icon"></span>
    <strong>正解：(a)</strong>
    <div class="quiz-explanation">
      フィッシャーの線形判別は、射影後の変数で群の分離を最大化します。

      $J(\mathbf{w}) = \frac{\mathbf{w}^\top \mathbf{S}_B \mathbf{w}}{\mathbf{w}^\top \mathbf{S}_W \mathbf{w}}$

      - $\mathbf{S}_B$：群間共分散行列（群平均の違い）
      - $\mathbf{S}_W$：群内共分散行列（群内のばらつき）

      最適解は $\mathbf{w} \propto \mathbf{S}_W^{-1}(\boldsymbol{\mu}_1 - \boldsymbol{\mu}_2)$ です。

      これは「群間の差を大きく、群内のばらつきを小さく」する方向への射影です。
    </div>
  </div>
</div>

---

## 問題 4：クラスター分析

<div class="quiz-container" data-quiz-id="mv-4" data-correct="d">
  <div class="quiz-question">
    階層的クラスタリングの結合方法について正しいものはどれか。
  </div>
  <div class="quiz-options">
    <div class="quiz-option" data-value="a">
      <input type="radio" name="q4" id="q4a">
      <label for="q4a">最短距離法（単連結法）は鎖効果が起きにくい</label>
    </div>
    <div class="quiz-option" data-value="b">
      <input type="radio" name="q4" id="q4b">
      <label for="q4b">最長距離法（完全連結法）は細長いクラスターを作りやすい</label>
    </div>
    <div class="quiz-option" data-value="c">
      <input type="radio" name="q4" id="q4c">
      <label for="q4c">群平均法はWard法より計算が複雑</label>
    </div>
    <div class="quiz-option" data-value="d">
      <input type="radio" name="q4" id="q4d">
      <label for="q4d">Ward法はクラスター内の分散増加を最小化する</label>
    </div>
  </div>
  <button class="quiz-btn" disabled>解答を確認</button>
  <div class="quiz-feedback">
    <span class="quiz-feedback-icon"></span>
    <strong>正解：(d)</strong>
    <div class="quiz-explanation">
      階層的クラスタリングの結合方法：

      | 方法 | 特徴 |
      |-----|------|
      | **最短距離法** | 鎖効果が起きやすい（細長いクラスター） |
      | **最長距離法** | コンパクトなクラスターを作る |
      | **群平均法** | 両者の中間的な性質 |
      | **Ward法** | クラスター内分散の増加を最小化、球状クラスター向き |

      Ward法は「結合によるクラスター内平方和の増加」を最小にするペアを選びます。
    </div>
  </div>
</div>

---

## 問題 5：因子分析

<div class="quiz-container" data-quiz-id="mv-5" data-correct="b">
  <div class="quiz-question">
    因子分析と主成分分析の違いについて正しいものはどれか。
  </div>
  <div class="quiz-options">
    <div class="quiz-option" data-value="a">
      <input type="radio" name="q5" id="q5a">
      <label for="q5a">因子分析は分散を最大化する方向を求める</label>
    </div>
    <div class="quiz-option" data-value="b">
      <input type="radio" name="q5" id="q5b">
      <label for="q5b">因子分析は観測変数の相関構造を少数の潜在因子で説明する</label>
    </div>
    <div class="quiz-option" data-value="c">
      <input type="radio" name="q5" id="q5c">
      <label for="q5c">主成分分析は独自因子（誤差項）を仮定する</label>
    </div>
    <div class="quiz-option" data-value="d">
      <input type="radio" name="q5" id="q5d">
      <label for="q5d">両者の結果は常に一致する</label>
    </div>
  </div>
  <button class="quiz-btn" disabled>解答を確認</button>
  <div class="quiz-feedback">
    <span class="quiz-feedback-icon"></span>
    <strong>正解：(b)</strong>
    <div class="quiz-explanation">
      | 特徴 | 主成分分析 | 因子分析 |
      |-----|----------|---------|
      | 目的 | 分散の最大化・次元削減 | 相関構造の説明 |
      | モデル | なし（記述的） | $\mathbf{x} = \boldsymbol{\Lambda}\mathbf{f} + \boldsymbol{\varepsilon}$ |
      | 誤差項 | なし | 独自因子 $\boldsymbol{\varepsilon}$ を仮定 |
      | 回転 | 不要 | 回転で解釈しやすくする |

      因子分析モデル：
      $\mathbf{x} = \boldsymbol{\Lambda}\mathbf{f} + \boldsymbol{\varepsilon}$

      - $\mathbf{f}$：共通因子
      - $\boldsymbol{\Lambda}$：因子負荷量行列
      - $\boldsymbol{\varepsilon}$：独自因子（各変数固有の変動）
    </div>
  </div>
</div>

---

## 関連コンテンツ

- [理論編：主成分分析]({{ site.baseurl }}/semi-1/7-multivariate/pca/)
- [理論編：判別分析とSVM]({{ site.baseurl }}/semi-1/7-multivariate/discriminant/)
- [理論編：クラスター分析]({{ site.baseurl }}/semi-1/7-multivariate/clustering/)
- [理論編：因子分析]({{ site.baseurl }}/semi-1/7-multivariate/factor-analysis/)
- [回帰分析の問題]({{ site.baseurl }}/semi-1/problems/regression/)

---

[問題一覧に戻る]({{ site.baseurl }}/semi-1/problems/) | [準1級トップ]({{ site.baseurl }}/semi-1/)
