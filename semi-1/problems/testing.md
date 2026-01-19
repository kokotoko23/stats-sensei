---
layout: default
title: 検定の問題 - 準1級対策
description: ネイマン・ピアソン、尤度比検定、UMP検定の選択式問題
permalink: /semi-1/problems/testing/
---

# 検定の問題

ネイマン・ピアソンの補題、尤度比検定、UMP検定、多重検定に関する問題です。

<div class="quiz-progress">
  <span class="quiz-progress-text">0 / 10 正解</span>
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

## 問題 6：検出力

<div class="quiz-container" data-quiz-id="test-6" data-correct="c">
  <div class="quiz-question">
    検定の検出力（power）について正しいものはどれか。
  </div>
  <div class="quiz-options">
    <div class="quiz-option" data-value="a">
      <input type="radio" name="q6" id="q6a">
      <label for="q6a">有意水準と同じ値である</label>
    </div>
    <div class="quiz-option" data-value="b">
      <input type="radio" name="q6" id="q6b">
      <label for="q6b">帰無仮説が真のとき棄却する確率である</label>
    </div>
    <div class="quiz-option" data-value="c">
      <input type="radio" name="q6" id="q6c">
      <label for="q6c">対立仮説が真のとき棄却する確率である</label>
    </div>
    <div class="quiz-option" data-value="d">
      <input type="radio" name="q6" id="q6d">
      <label for="q6d">第2種の過誤の確率である</label>
    </div>
  </div>
  <button class="quiz-btn" disabled>解答を確認</button>
  <div class="quiz-feedback">
    <span class="quiz-feedback-icon"></span>
    <strong>正解：(c)</strong>
    <div class="quiz-explanation">
      検定における誤りと確率：

      | | 棄却しない | 棄却する |
      |---|---|---|
      | $H_0$ 真 | 正しい判断 | 第1種の過誤（$\alpha$） |
      | $H_1$ 真 | 第2種の過誤（$\beta$） | 正しい判断 |

      - 検出力 $= 1 - \beta = P(\text{棄却} \mid H_1 \text{真})$
      - 検出力は効果量、サンプルサイズ、有意水準に依存
      - 検出力分析で必要なサンプルサイズを決定できる
    </div>
  </div>
</div>

---

## 問題 7：スコア検定

<div class="quiz-container" data-quiz-id="test-7" data-correct="b">
  <div class="quiz-question">
    スコア検定（Rao のスコア検定）の特徴として正しいものはどれか。
  </div>
  <div class="quiz-options">
    <div class="quiz-option" data-value="a">
      <input type="radio" name="q7" id="q7a">
      <label for="q7a">制約なしの最尤推定量のみを使う</label>
    </div>
    <div class="quiz-option" data-value="b">
      <input type="radio" name="q7" id="q7b">
      <label for="q7b">帰無仮説のもとでの推定量のみを使う</label>
    </div>
    <div class="quiz-option" data-value="c">
      <input type="radio" name="q7" id="q7c">
      <label for="q7c">尤度比検定と常に同じ結果を与える</label>
    </div>
    <div class="quiz-option" data-value="d">
      <input type="radio" name="q7" id="q7d">
      <label for="q7d">小標本でも正確なp値を与える</label>
    </div>
  </div>
  <button class="quiz-btn" disabled>解答を確認</button>
  <div class="quiz-feedback">
    <span class="quiz-feedback-icon"></span>
    <strong>正解：(b)</strong>
    <div class="quiz-explanation">
      3つの漸近的に同等な検定：

      | 検定 | 使用する推定量 | 特徴 |
      |-----|--------------|------|
      | 尤度比検定 | 制約あり・なし両方 | 最も一般的 |
      | ワルド検定 | 制約なしのMLE | 信頼区間との対応 |
      | スコア検定 | 制約ありのMLE | $H_0$ 下の計算のみ |

      スコア検定は $H_0$ のもとでの計算だけで済むため、制約なしMLEの計算が困難な場合に有用。
    </div>
  </div>
</div>

---

## 問題 8：信頼区間と検定

<div class="quiz-container" data-quiz-id="test-8" data-correct="a">
  <div class="quiz-question">
    95%信頼区間と有意水準5%の両側検定の関係として正しいものはどれか。
  </div>
  <div class="quiz-options">
    <div class="quiz-option" data-value="a">
      <input type="radio" name="q8" id="q8a">
      <label for="q8a">$\theta_0$ が95%信頼区間に含まれないことと、$H_0: \theta = \theta_0$ を棄却することは同値</label>
    </div>
    <div class="quiz-option" data-value="b">
      <input type="radio" name="q8" id="q8b">
      <label for="q8b">$\theta_0$ が95%信頼区間に含まれることと、$H_0: \theta = \theta_0$ を棄却することは同値</label>
    </div>
    <div class="quiz-option" data-value="c">
      <input type="radio" name="q8" id="q8c">
      <label for="q8c">信頼区間と検定は無関係である</label>
    </div>
    <div class="quiz-option" data-value="d">
      <input type="radio" name="q8" id="q8d">
      <label for="q8d">信頼区間が広いほど検出力が高い</label>
    </div>
  </div>
  <button class="quiz-btn" disabled>解答を確認</button>
  <div class="quiz-feedback">
    <span class="quiz-feedback-icon"></span>
    <strong>正解：(a)</strong>
    <div class="quiz-explanation">
      信頼区間と仮説検定の双対性：

      $100(1-\alpha)\%$ 信頼区間を $C$ とすると：
      - $\theta_0 \notin C$ ⇔ 有意水準 $\alpha$ で $H_0: \theta = \theta_0$ を棄却

      これは同じピボット量を使っているため。

      例：$\bar{X} \pm z_{\alpha/2} \frac{\sigma}{\sqrt{n}}$ の区間の外に $\mu_0$ があれば棄却。
    </div>
  </div>
</div>

---

## 問題 9：FDR制御

<div class="quiz-container" data-quiz-id="test-9" data-correct="d">
  <div class="quiz-question">
    偽発見率（FDR: False Discovery Rate）の制御について正しいものはどれか。
  </div>
  <div class="quiz-options">
    <div class="quiz-option" data-value="a">
      <input type="radio" name="q9" id="q9a">
      <label for="q9a">ボンフェローニ補正より常に保守的である</label>
    </div>
    <div class="quiz-option" data-value="b">
      <input type="radio" name="q9" id="q9b">
      <label for="q9b">FDRは第1種の過誤の確率と同じである</label>
    </div>
    <div class="quiz-option" data-value="c">
      <input type="radio" name="q9" id="q9c">
      <label for="q9c">FDRは常にFWERより大きい</label>
    </div>
    <div class="quiz-option" data-value="d">
      <input type="radio" name="q9" id="q9d">
      <label for="q9d">Benjamini-Hochberg法はFDRを制御する方法である</label>
    </div>
  </div>
  <button class="quiz-btn" disabled>解答を確認</button>
  <div class="quiz-feedback">
    <span class="quiz-feedback-icon"></span>
    <strong>正解：(d)</strong>
    <div class="quiz-explanation">
      多重検定における誤り制御：

      - **FWER**（ファミリーワイズエラー率）：1つでも偽陽性が出る確率
      - **FDR**（偽発見率）：棄却した中での偽陽性の割合の期待値

      $\text{FDR} = E\left[\frac{\text{偽陽性の数}}{\text{棄却した数}}\right]$

      Benjamini-Hochberg法：
      1. p値を昇順にソート：$p_{(1)} \leq \cdots \leq p_{(m)}$
      2. $p_{(k)} \leq \frac{k}{m}q$ を満たす最大の $k$ を見つける
      3. $p_{(1)}, \ldots, p_{(k)}$ を棄却

      FDRはFWERより緩いので、より多くの発見ができる。
    </div>
  </div>
</div>

---

## 問題 10：ノンパラメトリック検定

<div class="quiz-container" data-quiz-id="test-10" data-correct="c">
  <div class="quiz-question">
    2群の位置の差を検定するウィルコクソンの順位和検定（マン・ホイットニーのU検定）について正しいものはどれか。
  </div>
  <div class="quiz-options">
    <div class="quiz-option" data-value="a">
      <input type="radio" name="q10" id="q10a">
      <label for="q10a">正規分布を仮定している</label>
    </div>
    <div class="quiz-option" data-value="b">
      <input type="radio" name="q10" id="q10b">
      <label for="q10b">対応のあるデータにのみ使用できる</label>
    </div>
    <div class="quiz-option" data-value="c">
      <input type="radio" name="q10" id="q10c">
      <label for="q10c">順位に基づく検定で、外れ値に頑健である</label>
    </div>
    <div class="quiz-option" data-value="d">
      <input type="radio" name="q10" id="q10d">
      <label for="q10d">t検定より常に検出力が高い</label>
    </div>
  </div>
  <button class="quiz-btn" disabled>解答を確認</button>
  <div class="quiz-feedback">
    <span class="quiz-feedback-icon"></span>
    <strong>正解：(c)</strong>
    <div class="quiz-explanation">
      ノンパラメトリック検定の特徴：

      | 検定 | 対応 | 用途 |
      |-----|-----|------|
      | ウィルコクソン順位和検定 | なし | 2群の位置の差 |
      | ウィルコクソン符号順位検定 | あり | 対応のある2群 |
      | クラスカル・ウォリス検定 | なし | 3群以上の位置の差 |

      順位検定の利点：
      - 分布を仮定しない
      - 外れ値に頑健
      - 順序尺度でも使用可能

      正規分布のときはt検定の方が検出力が高いが、歪んだ分布では順位検定が優れる。
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
