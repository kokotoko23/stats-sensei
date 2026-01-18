---
layout: default
title: 検定の問題 - 準1級対策
description: ネイマン・ピアソン、尤度比検定、UMP検定の選択式問題
permalink: /semi-1/problems/testing/
---

# 検定の問題

ネイマン・ピアソンの補題、尤度比検定、UMP検定、多重検定に関する問題です。

<div class="quiz-progress">
  <span class="quiz-progress-text">0 / 5 正解</span>
  <div class="quiz-progress-bar">
    <div class="quiz-progress-fill" style="width: 0%"></div>
  </div>
</div>

---

## 問題 1：ネイマン・ピアソンの補題

<div class="quiz-container" data-quiz-id="test-1" data-correct="b">
  <div class="quiz-question">
    $H_0: \theta = \theta_0$ vs $H_1: \theta = \theta_1$ の単純仮説の検定において、ネイマン・ピアソンの補題が保証することは何か。
  </div>
  <div class="quiz-options">
    <div class="quiz-option" data-value="a">
      <input type="radio" name="q1" id="q1a">
      <label for="q1a">第1種の過誤と第2種の過誤を同時に最小化できる</label>
    </div>
    <div class="quiz-option" data-value="b">
      <input type="radio" name="q1" id="q1b">
      <label for="q1b">有意水準 $\alpha$ を固定したとき、検出力を最大化する検定が尤度比で構成できる</label>
    </div>
    <div class="quiz-option" data-value="c">
      <input type="radio" name="q1" id="q1c">
      <label for="q1c">検出力が1になる検定が常に存在する</label>
    </div>
    <div class="quiz-option" data-value="d">
      <input type="radio" name="q1" id="q1d">
      <label for="q1d">p値が一様分布に従う</label>
    </div>
  </div>
  <button class="quiz-btn" disabled>解答を確認</button>
  <div class="quiz-feedback">
    <span class="quiz-feedback-icon"></span>
    <strong>正解：(b)</strong>
    <div class="quiz-explanation">
      ネイマン・ピアソンの補題は、有意水準 $\alpha$ を固定したときに検出力を最大化する「最強力検定」が、尤度比 $L(\theta_0)/L(\theta_1) \leq k$ の形で構成できることを示します。$k$ は $P_{H_0}(\Lambda \leq k) = \alpha$ を満たすように選びます。
    </div>
  </div>
</div>

---

## 問題 2：尤度比検定の漸近分布

<div class="quiz-container" data-quiz-id="test-2" data-correct="c">
  <div class="quiz-question">
    尤度比検定統計量 $-2\log\Lambda$ の漸近分布について正しいものはどれか。ただし、$H_0$ で $r$ 個のパラメータが制約されているとする。
  </div>
  <div class="quiz-options">
    <div class="quiz-option" data-value="a">
      <input type="radio" name="q2" id="q2a">
      <label for="q2a">$N(0, 1)$（標準正規分布）</label>
    </div>
    <div class="quiz-option" data-value="b">
      <input type="radio" name="q2" id="q2b">
      <label for="q2b">$t_r$（自由度 $r$ の $t$ 分布）</label>
    </div>
    <div class="quiz-option" data-value="c">
      <input type="radio" name="q2" id="q2c">
      <label for="q2c">$\chi^2_r$（自由度 $r$ のカイ二乗分布）</label>
    </div>
    <div class="quiz-option" data-value="d">
      <input type="radio" name="q2" id="q2d">
      <label for="q2d">$F_{r, n-r}$（$F$ 分布）</label>
    </div>
  </div>
  <button class="quiz-btn" disabled>解答を確認</button>
  <div class="quiz-feedback">
    <span class="quiz-feedback-icon"></span>
    <strong>正解：(c)</strong>
    <div class="quiz-explanation">
      ウィルクスの定理により、$-2\log\Lambda \xrightarrow{d} \chi^2_r$（大標本で）。これはMLEの漸近正規性と、正規分布の二次形式がカイ二乗分布に従うことから導かれます。$r$ は帰無仮説で制約されるパラメータの数です。
    </div>
  </div>
</div>

---

## 問題 3：UMP検定

<div class="quiz-container" data-quiz-id="test-3" data-correct="a">
  <div class="quiz-question">
    一様最強力（UMP）検定が存在するのは、主にどのような状況か。
  </div>
  <div class="quiz-options">
    <div class="quiz-option" data-value="a">
      <input type="radio" name="q3" id="q3a">
      <label for="q3a">片側検定で、分布が単調尤度比（MLR）をもつとき</label>
    </div>
    <div class="quiz-option" data-value="b">
      <input type="radio" name="q3" id="q3b">
      <label for="q3b">両側検定で、分布が正規分布のとき</label>
    </div>
    <div class="quiz-option" data-value="c">
      <input type="radio" name="q3" id="q3c">
      <label for="q3c">多重検定を行うとき</label>
    </div>
    <div class="quiz-option" data-value="d">
      <input type="radio" name="q3" id="q3d">
      <label for="q3d">サンプルサイズが十分大きいとき</label>
    </div>
  </div>
  <button class="quiz-btn" disabled>解答を確認</button>
  <div class="quiz-feedback">
    <span class="quiz-feedback-icon"></span>
    <strong>正解：(a)</strong>
    <div class="quiz-explanation">
      単調尤度比（MLR）条件を満たす分布族（指数型分布族など）では、片側検定 $H_0: \theta \leq \theta_0$ vs $H_1: \theta > \theta_0$ に対してUMP検定が存在します。両側検定ではUMP検定は一般に存在しません。
    </div>
  </div>
</div>

---

## 問題 4：p値の解釈

<div class="quiz-container" data-quiz-id="test-4" data-correct="d">
  <div class="quiz-question">
    p値の正しい解釈はどれか。
  </div>
  <div class="quiz-options">
    <div class="quiz-option" data-value="a">
      <input type="radio" name="q4" id="q4a">
      <label for="q4a">帰無仮説が正しい確率</label>
    </div>
    <div class="quiz-option" data-value="b">
      <input type="radio" name="q4" id="q4b">
      <label for="q4b">対立仮説が正しい確率</label>
    </div>
    <div class="quiz-option" data-value="c">
      <input type="radio" name="q4" id="q4c">
      <label for="q4c">効果の大きさ</label>
    </div>
    <div class="quiz-option" data-value="d">
      <input type="radio" name="q4" id="q4d">
      <label for="q4d">帰無仮説が真のとき、観測されたデータ以上に極端なデータが得られる確率</label>
    </div>
  </div>
  <button class="quiz-btn" disabled>解答を確認</button>
  <div class="quiz-feedback">
    <span class="quiz-feedback-icon"></span>
    <strong>正解：(d)</strong>
    <div class="quiz-explanation">
      p値は「帰無仮説が真のとき、観測された検定統計量以上に極端な値が得られる確率」です。p値は帰無仮説が正しい確率ではありません（これはベイズ的な解釈）。また、p値が小さいことは効果が大きいことを意味しません（サンプルサイズが大きければ小さな効果でもp値は小さくなる）。
    </div>
  </div>
</div>

---

## 問題 5：多重検定

<div class="quiz-container" data-quiz-id="test-5" data-correct="b">
  <div class="quiz-question">
    20個の独立な検定を有意水準 $\alpha = 0.05$ で行うとき、すべての帰無仮説が真でも少なくとも1つが有意になる確率（ファミリーワイズエラー率）はおよそいくらか。
  </div>
  <div class="quiz-options">
    <div class="quiz-option" data-value="a">
      <input type="radio" name="q5" id="q5a">
      <label for="q5a">約 5%</label>
    </div>
    <div class="quiz-option" data-value="b">
      <input type="radio" name="q5" id="q5b">
      <label for="q5b">約 64%</label>
    </div>
    <div class="quiz-option" data-value="c">
      <input type="radio" name="q5" id="q5c">
      <label for="q5c">約 95%</label>
    </div>
    <div class="quiz-option" data-value="d">
      <input type="radio" name="q5" id="q5d">
      <label for="q5d">約 100%</label>
    </div>
  </div>
  <button class="quiz-btn" disabled>解答を確認</button>
  <div class="quiz-feedback">
    <span class="quiz-feedback-icon"></span>
    <strong>正解：(b)</strong>
    <div class="quiz-explanation">
      $\text{FWER} = 1 - (1 - 0.05)^{20} = 1 - 0.95^{20} \approx 1 - 0.358 = 0.642$

      約64%の確率で少なくとも1つの偽陽性が発生します。これが多重検定の問題であり、ボンフェローニ補正（各 $\alpha = 0.05/20 = 0.0025$）やFDR制御が必要になる理由です。
    </div>
  </div>
</div>

---

## 関連コンテンツ

- [理論編：検定の基礎]({{ site.baseurl }}/semi-1/3-inference/testing/)
- [推定の問題]({{ site.baseurl }}/semi-1/problems/estimation/)
- [信頼区間の問題]({{ site.baseurl }}/semi-1/problems/interval/)

---

[問題一覧に戻る]({{ site.baseurl }}/semi-1/problems/) | [準1級トップ]({{ site.baseurl }}/semi-1/)
